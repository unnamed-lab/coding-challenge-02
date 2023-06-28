# Newsletter Form Page From Frontend Mentor Challenge
### Replicated by Unnamed.

I worked on replicating the challenge from scratch with the aid of the design image and instructions with project CSS rendered by the SASS preprocessor (Not committed).

## Project Overview

**The JavaScript file** ```.\js\script.js``` :
### Stating The Variable
```
//  Define Variables
const circleSmallIcons = document.querySelectorAll(".checked");
const circleBigIcons = document.querySelector(".check-lg");
const svgCheck = `<svg viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg" fill="#000000"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"><path fill="#ffffff" d="M17.47 250.9C88.82 328.1 158 397.6 224.5 485.5c72.3-143.8 146.3-288.1 268.4-444.37L460 26.06C356.9 135.4 276.8 238.9 207.2 361.9c-48.4-43.6-126.62-105.3-174.38-137z"></path></g></svg>`;

const inputEmail = document.querySelector("#email_input");
const inputErrorText = document.querySelector(".input_error");
const submitBtn = document.querySelector("#submit_btn");
const dismissBtn = document.querySelector("#dismiss-modal");
const overlay = document.querySelector(".overlay");
const modal = document.querySelector(".modal");

// Add the SVG element into the icon variables
circleBigIcons.innerHTML = svgCheck;
for (let i = 0; i < circleSmallIcons.length; i++) {
  circleSmallIcons[i].innerHTML = svgCheck;
}
```

### The Input Validation Function
```
/*  Setup the error state   */

//  Returns false if the input type is valid and true vice versa
const validateEmail = (email) => {
  const re =
    /^(([^<>()[\]\.,;:\s@\"]+(\.[^<>()[\]\.,;:\s@\"]+)*)|(\".+\"))@(([^<>()[\]\.,;:\s@\"]+\.)+[^<>()[\]\.,;:\s@\"]{2,})$/i;
  return re.test(email);
};

const invalidInput = function () {
  const userInput = inputEmail.value;
  if (validateEmail(userInput) === false) {
    //  If the input is empty and type not valid
    inputErrorText.classList.remove("hidden");
    inputEmail.classList.add("warning");
    return false;
  } else {
    //  If the input is not empty and type valid
    inputErrorText.classList.add("hidden");
    inputEmail.classList.remove("warning");
    return true;
  }
};
```

### Modal and Overlay
```
/*  Setup modal popup   */

const modalPopUp = function (bool = true) {
  if (bool === true) {
    //  If the parameter is specified as true
    overlay.classList.remove("hidden");
    modal.classList.remove("hidden");
  } else {
    //  If the paramete is specified as false
    overlay.classList.add("hidden");
    modal.classList.add("hidden");
  }
};
```

### Update Modal Email Display
```
/* Update email preview in success slide */

let userEmailAddress = document.querySelector("#yourEmail");
const updateEmailPreview = function (input) {
  userEmailAddress.textContent = input;
};

```

### Event Listeners
```
/*  Setup Event Listeners   */

//  Removes the modal when the dismiss button is pressed
dismissBtn.addEventListener("click", function () {
  modalPopUp(false);
});
//  Removes the modal when the overlay is pressed
overlay.addEventListener("click", function () {
  modalPopUp(false);
});
//  Removes the modal when the Escape key (on your keybord) is pressed
window.addEventListener("keydown", function (e) {
  if (e.key === "Escape") modalPopUp(false);
});
//  Removes the modal when the submit button is pressed
submitBtn.addEventListener("click", function () {
  invalidInput();
  if (invalidInput() === true) modalPopUp(true);
});
```

**The CSS file** ```.\css\style.css```.


**The Design files** ```.\design```.

### _Credits to Frontend Mentor for the challenge - [Challenge](https://www.frontendmentor.io/challenges/newsletter-signup-form-with-success-message-3FC1AZbNrv)_

*Incase of any potential errors, feel free to reach out to me on [Twitter](https://twitter.com/unnamed_labs) :)*