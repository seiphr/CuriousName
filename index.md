---
layout: default
---

> ‘I think prime numbers are like life. They are very logical but you could never work out the rules, even if you spent all your time thinking about them.’
> 
> _Christopher John Francis Boone_

# Win a Prize if Your Name is a Prime Number!

Every day, when Christopher arrives at the Theater im Seefeld, he chooses two seats in each row at random as his selected prime number seats. Anyone sitting in a selected prime number seat has the chance to win a prize!*

Prime numbers can only be divided by themselves and 1. 2 is the first prime number because 1 can only be divided by 1. There are no known formulas to help discover new prime numbers, which is maybe why Christopher finds them so interesting…

## How to Play

Give each letter in your name a value from 1 to 26 (`a=1`, `b=2`, etc.)

<style>
  .table-container {
    width: 100%;
    overflow-x: auto; /* Enable horizontal scrolling */
  }
  .custom-table {
    border: 1px solid black;
    border-collapse: collapse;
    width: 100%;
  }
  .custom-table th, .custom-table td {
    border: 1px solid black;
    padding: 4px;
    text-align: center;
  }
  .custom-table th {
    background-color: #f2f2f2;
    font-weight: bold;
  }
</style>
<div class="table-container">
    <table class="custom-table">
        <tr>
            <th>A</th>
            <th>B</th>
            <th>C</th>
            <th>D</th>
            <th>E</th>
            <th>F</th>
            <th>G</th>
            <th>H</th>
            <th>I</th>
            <th>J</th>
            <th>K</th>
            <th>L</th>
            <th>M</th>
            <th>N</th>
            <th>O</th>
            <th>P</th>
            <th>Q</th>
            <th>R</th>
            <th>S</th>
            <th>T</th>
            <th>U</th>
            <th>V</th>
            <th>W</th>
            <th>X</th>
            <th>Y</th>
            <th>Z</th>
        </tr>
        <tr>
            <td>1</td>
            <td>2</td>
            <td>3</td>
            <td>4</td>
            <td>5</td>
            <td>6</td>
            <td>7</td>
            <td>8</td>
            <td>9</td>
            <td>10</td>
            <td>11</td>
            <td>12</td>
            <td>13</td>
            <td>14</td>
            <td>15</td>
            <td>16</td>
            <td>17</td>
            <td>18</td>
            <td>19</td>
            <td>20</td>
            <td>21</td>
            <td>22</td>
            <td>23</td>
            <td>24</td>
            <td>25</td>
            <td>26</td>
        </tr>
    </table>
</div>

Add up the numbers and see if they make a prime number. Like Scooby Doo (113), or Sherlock Holmes (163), or Doctor Watson (167).

If your name equals a prime number, please come to the foyer during the interval or after the show, and ask one of the ushers there for a Curious Prize. We will double-check your calculation for you 🙂

### Example (Scooby Doo)

> S=19, C=3, O=15, O=15, B=2, Y=25, D=4, O=15, O=15
>
> `19 + 3 + 15 + 15 + 2 + 25 + 4 + 15 + 15 = 113`

113 is a prime number, so Scooby Doo would win a prize!

## Check Your Calculation


<style>
    /* Style for the form and the result text */
    form {
        margin-bottom: 20px;
    }
    .result {
        margin-top: 20px;
        color: red;
        font-weight: bold;
    }
</style>
<form onsubmit="handleSubmit(event)">
    <label for="name">Enter your full name:</label>
    <input type="text" id="name" name="name" placeholder="Scooby Doo">
    <button type="submit">Submit</button>
    <p></p>
    <div id="result" class="result" style="display: none;"></div>
</form>

_Note: Only use characters A-Z (no umlauts, special characters, or numbers). Enter your full name (first and last name)._

* * *

_Please remember turn your phone off during the show!_

_Your name will be processed locally on your device and not shared on stored anywhere._

_*Prizes are subject to availability._

<!-- Include the canvas-confetti library from a CDN -->
<script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>

<script>
    const letterToNumber = {
        A: 1,
        B: 2,
        C: 3,
        D: 4,
        E: 5,
        F: 6,
        G: 7,
        H: 8,
        I: 9,
        J: 10,
        K: 11,
        L: 12,
        M: 13,
        N: 14,
        O: 15,
        P: 16,
        Q: 17,
        R: 18,
        S: 19,
        T: 20,
        U: 21,
        V: 22,
        W: 23,
        X: 24,
        Y: 25,
        Z: 26
    };

    function handleSubmit(event) {
        // Prevent the default form submission behavior
        event.preventDefault();
        
        // Get the value of the text input field
        const inputValue = event.target.elements.name.value;

        // Clean the input value of any non A-Z characters
        const cleanedInputValue = removeNonLetters(inputValue).toUpperCase();

        // Split characters
        const splitString = cleanedInputValue.split('');

        let sum = 0;
        splitString.forEach(element => {
            sum += letterToNumber[element];
        });

        // Display the result text
        var resultDiv = document.getElementById('result');

        var isPerfectNumber = isPerfectNumber(sum);
        var isPrimeNumber = isPrime(sum);
        if (isPerfectNumber) {
            resultDiv.textContent = "Your name equals " + sum + "\r\n\r\nWhich is not a prime number. BUT it is a PERFECT NUMBER!!!\r\n\r\nTalk to someone from the Front of House team in the foyer to claim your prize (look for the 'ZEST' badge on their shirt).\r\nPerfect numbers are really cool. Perfect numbers are positive integers that equal the sum of their proper divisors (excluding itself). For instance, 6 has proper divisors 1, 2, and 3, and 1 + 2 + 3 = 6.";
        }
        else if (isPrimeNumber) {
            resultDiv.textContent = "Your name equals " + sum + "\r\n\r\nWhich is a PRIME NUMBER!!!\r\n\r\nTalk to someone from the Front of House team in the foyer to claim your prize (look for the 'ZEST' badge on their shirt).";
        }
        else {
            resultDiv.textContent = "Your name equals " + sum + "\r\n\r\nWhich is unfortunately not a prime number.";
        }
        resultDiv.style.display = 'block';

        if (isPrimeNumber || isPerfectNumber) {
            // Trigger the confetti effect
            confetti({
                particleCount: 100,
                spread: 70,
                origin: { y: 0.6 }
            });
        }
    }

    function removeNonLetters(str) {
        // Use a regular expression to match and remove non-letter characters
        return str.replace(/[^a-zA-Z]/g, '');
    }

    function isPrime(num) {
        // Check if num is less than 2, which is not prime
        if (num < 2) return false;

        // Check all numbers from 2 to the square root of num
        for (let i = 2; i <= Math.sqrt(num); i++) {
            // If num is divisible by any of these numbers, it is not prime
            if (num % i === 0) return false;
        }

        // If no divisors are found, num is prime
        return true;
    }

    function isPerfectNumber(num) {
        // A perfect number must be greater than 1
        if (num <= 1) return false;

        let sum = 0;

        // Loop through all numbers from 1 to num/2
        for (let i = 1; i <= num / 2; i++) {
            // If i is a divisor of num, add it to the sum
            if (num % i === 0) {
                sum += i;
            }
        }

        // Return true if the sum of divisors equals the number, false otherwise
        return sum === num;
    }
</script>