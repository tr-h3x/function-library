# function-library
MDN function library active learning

*For visually appealing instructions, visit:

https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Return_values


INSTRUCTIONS

First of all, make a local copy of the function-library.html file from GitHub. This is a simple HTML page containing a text <input> field and a paragraph. There's also a <script> element, in which we have stored a reference to both HTML elements in two variables. This little page will allow you to enter a number into the text box, and display different numbers related to it in the paragraph below.
Let's add some useful functions to this <script> element. Below the two existing lines of JavaScript, add the following function definitions:
function squared(num) {
  return num * num;
}

function cubed(num) {
  return num * num * num;
}

function factorial(num) {
  if (num < 0) return undefined;
  if (num == 0) return 1;
  let x = num - 1;
  while (x > 1) {
    num *= x;
    x--;
  }
  return num;
}
Copy to Clipboard
The squared() and cubed() functions are fairly obvious — they return the square or cube of the number that was given as a parameter. The factorial() function returns the factorial of the given number.
Next, we're going to include a way to print out information about the number entered into the text input. Enter the following event handler below the existing functions:
input.addEventListener('change', () => {
  const num = parseFloat(input.value);
  if (isNaN(num)) {
    para.textContent = 'You need to enter a number!';
  } else {
    para.textContent = `${num} squared is ${squared(num)}. `;
    para.textContent += `${num} cubed is ${cubed(num)}. `;
    para.textContent += `${num} factorial is ${factorial(num)}. `;
  }
});
Copy to Clipboard
Here we are adding a listener to the change event. It runs whenever the change event fires on the text input — that is, when a new value is entered into the text input, and submitted (e.g., enter a value, then un-focus the input by pressing Tab or Return). When this anonymous function runs, the value in the input is stored in the num constant. Next, we do a conditional test. If the entered value is not a number, an error message is printed to the paragraph. The test looks at whether the expression isNaN(num) returns true. The isNaN() function to test whether the num value is not a number — if so, it returns true, and if not, it returns false. If the test returns false, the num value is a number. Therefore, a sentence is printed out inside the paragraph element that states the square, cube, and factorial values of the number. The sentence calls the squared(), cubed(), and factorial() functions to calculate the required values.
Save your code, load it in a browser, and try it out.