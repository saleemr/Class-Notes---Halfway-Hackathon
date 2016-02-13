# Class-Notes---Halfway-Hackathon
Halfway Hackathon


Halfway Hackathon

Congratulations! Today we are at the halfway point in our class. Let's celebrate with a hackathon! A hackathon is a great opportunity to work on a larger, real-world project, while reviewing and solidifying the core concepts that we've covered in the first half of the course.


Step 1: Make a Plan

Take a few minutes to brainstorm some project ideas. This could be related to your community site, a stand-alone project, or just a crazy mash-up site to help you practice different coding concepts
Review the Step 3: Coding section below to consider the different concepts that we hope to practice during this project.
In groups of four, hold a standup meeting to present your plan of what you'd like to accomplish, and potential stumbling blocks.
If someone mentions being concerned about a concept that you feel solid on, offer to be a resource for them if they have questions.

Step 2: Set up a GitHub repo

Open the Terminal and run:
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
Go to GitHub and sign in or sign up for an account
Create a new repository on GitHub by clicking the new repository menu, upper-right
Follow the instructions presented in the new repository
If you'd like to know more about the philosophy behind version control, check out The Git Parable

Step 3: Coding

The following lists the core web development skills that you should feel comfortable using in your project thus far:

Use Markdown to create a README.md file introducing your project. Push to GitHub and see it rendered on your repository's main page
Create an HTML document using the following HTML tags:
html, head, title, body
header and paragraph tags
bold and italic tags
divs and spans
ordered and unordered lists
images and links
horizontal rule and line break
Use a style attribute on an HTML element, then a <style> tag in the head, then a <link> tag to a separate .css document to include CSS styles in your page. Try to use the following CSS properties at a minimum:
color, background-color, background-image
font-size, font-family
height, width, max-width
margin, padding, border, border-radius
Refactor your code to use classes and ids.
Use some complex CSS selectors such as descendent selectors
Use an iframe to embed videos or maps on your page
Use float and and position: fixed to position some elements
Create an HTML form incorporating various inputs (text, password, email, textarea, radio, checkbox, select menu, submit, etc)
Make your form live using Formspree
Use the Bootstrap grid system to lay out your page
Use some pre-written Bootstrap CSS classes on various elements of your page
Use alert, prompt, and console.log where appropriate
Set and retrieve values from JavaScript variables
Use document.querySelector in conjunction with textContent and innerHTML to retrieve and place content on the page
Use if, elseif and else to implement branching logic on the basis of comparing variables and values
Use logical and (&&), logical or (||), and the ternary operator
Use while loops to do work multiple times until a condition is met
Use the Math object and parseInt
Use jQuery to select existing HTML elements on the page
Use jQuery's .css(), .attr(), .text(), .html(), .append(), and .val() to both get and set values
Use some jQuery effects like .show(), .slideDown() and .fadeOut()

Stretch Goals

Use some of Bootstrap's JavaScript utilties
Try incorporating some jQuery Plug-ins

Step 4: Deploy & Promote

Deploy your code to Github Pages using your command line tools
Post a link on Slack so your classmates can enjoy your work
Send it to your friends and family members so they can be proud of you
Social media?

Step 5: Profit?

Monetize
Monetize
Monetize

A note regarding best practices

Try to decipher the code below. What does it do?

var i = 1, n = 5, j
while (i <= n){
j = 1;
var msg = '';
if (i === 1) {
msg += 'Welcome ' + i;
} else if (i > 1) {
msg += 'Welcome ' + i + ', meet';
}
while (j < n) {
if( j > 0 && j < i) {
if (j === i - 1) {
if (j === 1) {
msg += ' ' + j;
} else {
msg += ' and ' + j;
}
} else {
if (j === 1 && i === 3){
msg += ' ' + j;
} else {
msg += ' ' + j +',';
}
}
}
console.log(msg)
j++;
}
Pretty tough right? Here are some problems:

No indentation
Obscure variable names
A bit verbose
What happens when we clean it up?

var guest_number,
    announcement_message,
    arrival_number = 1,
    total_number_of_guests = 5;

while (arrival_number <= total_number_of_guests) {
  guest_number = 1;
  announcement_message = 'Welcome ' + arrival_number;

  if (arrival_number > 1) {
    announcement_message += ', meet ' + guest_number;

    while (++guest_number < arrival_number ) {
      if (guest_number !== arrival_number - 1) {
        announcement_message += ', ' + guest_number;
      } else {
        announcement_message += ' and ' + guest_number;
      }
    }
  }
  arrival_number++;
  console.log(announcement_message);
}



Advanced Functions

Functions are values, just like numbers, strings, arrays and objects. They can be saved to variables:

var say_hi = function () {
  console.log('hi');
};

var greeter = say_hi;

say_hi();
greeter();

say_hi = function () {
  console.log('meh');
};

say_hi(); // ??
greeter(); // ??
They can be passed as arguments (inputs) to functions:

var runner = function (fn) {
  console.log('Invoking a function now!');
  fn();
};

runner( function(){ console.log('okay'); } );
runner(say_hi);
runner(greeter);

runner( say_hi() ); // ??
Exercise 1: Write a function answer_logger that takes a function as input, runs it, and places the return value from that function invocation into a div#answer

We can test answer_logger using the following code, we should not need to change it at all.

answer_logger(function(){
  return "I should appear in div#answer!";
});
Submit Your Code



Exercise 2: Write a function answer_collector that takes an array of functions as an input and runs each of them, in turn. Each time you run a function, collect its return value and add it to a results_array. Return the results array from answer_collector.

We can test answer_collector with this code:

var fn1 = function () {
  return "this should be the first value in results array";
};

answer_collector([fn1, function(){ return "this should be the second value in results array"; }]);
Submit Your Code



Not only can functions be passed as inputs, they can also be returned as outputs.

var returns_a_func = function () {
  return function(){ console.log('BOOP!'); };
};

// have we booped yet?
var booper = returns_a_func();

// how about now?
booper();
Function define their own local scope. Variables declared within a function invocation are available only inside of that function. It's as if invocations are surrounded by one-way mirrors, they can see out and access variables named in their parent scope, but code running outside can't see in to access parameters or variables defined inside.

var word = 'original';
var phrase = " is the word";

var word_changer = function (new_word) {
    var word = new_word;
    console.log(word + phrase);
};

console.log(word + phrase); // ??
console.log(new_word + phrase); // ??
word_changer('changed');
console.log(word + phrase); // ??
console.log(new_word + phrase); // ??

// what's different here?
var leaky_word_changer = function (new_word) {
    word = new_word;
    console.log(word + phrase);
};

leaky_word_changer('changed');
console.log(word + phrase); // ??
console.log(new_word + phrase); // ??
Exercise 3:

Write a function secret_keeper that defines a variable secret inside its code block.
Try to access the secret variable from outside the function scope using your JS console. Make sure it's safe!
Allow the user to invoke secret_keeper with two strings as arguments
$().append() the two strings to the page with the secret word in between
Submit Your Code



Returned functions retain scope access at the point they were defined. This is called closure. The scope chain is established at the point WHERE THE KEYWORD function IS WRITTEN, not where it is invoked.

var returns_a_func = function () {
  var word = 'I can see inside';
  return function(){ console.log('BOOP! ' + word); };
};

var word = 'I can see outside';

var new_booper = returns_a_func();
new_booper(); // what does this log? why?

var returns_a_func = function () {
  var number = 5;
  return function(){ console.log( "The number is: " + number); };
};

var number = 4;
var fn = returns_a_func();
fn(); // what will this log? why?

var func_runner = function(func){
  var number = 3;
  func();
};

func_runner(fn); // what will this log? why?
Exercise 4: Write a function multiplies_by that takes a number as input and returns a function that, when invoked with a second number as an argument multiplies the two numbers together.

We can test multiplies_by with this code, we should not need to change it at all.

var times5 = multiplies_by(5);
times5(4); // 20

var times10 = multiplies_by(10);
times10(32); // 320
Submit Your Code



Functional Programming with Underscore

Underscore is a JavaScript Library (like jQuery). It provides a bunch of pre-written code for solving common programming challenges. While jQuery helps web developers interact with the DOM, Underscore focuses on providing useful helpers for Functional-style programming.

Include the Underscore library in an empty HTML document, along with an array of products (you can use your own from the e-commerce exercise or use this one) and try the following:

first: Pass _.first() the array of products and display the returned object in a "featured" section of your site.

last: Pass _.last() the array of products and display the returned object in a "clearance" section of your site.

filter: Use _.filter() to display only products that belong to the "books" category.

reject: Use _.reject() to display only products that are priced below $20.

uniq: Use _.uniq() to ensure that their are no duplicate selling points in any products before displaying them.

map: Use _.map() to grab the picture_url of all products for sale, assign each to the src property of a new <img> tag and return that DOM element. Pass the result of calling _.map() directly into a$('#container').append() expression to create a photo montage.

pluck: Use _.pluck() to quickly retrieve a list of the names of all products for sale to list them in an index

reduce: Pass a shopping cart (array of objects) to _.reduce() and use it to add up the total price of the order.

contains: Determine if the order _.contains() a copy of 'Twilight'. If so, display a drastic message to the user asking them to re-evaluate their life choices.

every: Use _.every() to determine if every item in the order has a price tag less than $10. If so, call the user a cheapskate!

some: Use _.some() to determine if any item in the order has a price tag of $100 or more. If so, chide the user for their profligacy!

extend: Use _.extend() to merge two objects together. What would this be good for?

Submit Your Code



Reimplementing Underscore

Ok, now that we've tried them all out, let's try rebuilding a few from scratch. Download the following HTML document and open it in your code editor to get started

Submit Your Code


===============================
From Jeff Cousins to Everyone: (09:34 PM)
var randomColor = '#' + Math.random().toString(16).slice(2, 8)
'#' + Math.random()
Math.random().toString(16)
Math.random().toString(16).slice(2, 8)



From Elifaz to Everyone: (09:26 PM)
coderbyte
bonfires from Freecodecamp
From Jeff Cousins to Everyone: (09:27 PM)
codewars
codeevalFrom Ronny Rosabal to Everyone: (09:26 PM)
do you have a recommendation for a website with coding challenges?
From Fulcrum Hack Reactor to Everyone: (09:26 PM)
leetcode
From Elifaz to Everyone: (09:26 PM)
coderbyte
bonfires from Freecodecamp
From Jeff Cousins to Everyone: (09:27 PM)
codewarshttps://www.youtube.com/watch?v=mRsn27eJnqQ

From Elifaz to Everyone: (09:24 PM)
CS50 is awesome..
From Fulcrum Hack Reactor to Everyone: (09:24 PM)
https://www.youtube.com/watch?v=mRsn27eJnqQ
From Jeff Cousins to Everyone: (09:24 PM)
I did a week of CS50
Then found out about HR
From Elifaz to Everyone: (09:25 PM)
Did you went through Mario?

Events

// we've defined a function and set it equal to a variable
var fn = function () {
  console.log('heeey')
}

// of course, we can invoke it manually
fn()

// Alternately, we can ask the browser to run it at a later time

// The below is called an event handler, take a guess at what it does...
// Add it to an HTML document containing a div#target and test it out
document.querySelector('#target').addEventListener('click', fn)

// Often times, instead of using a variable, we'll just define the function inline
document.querySelector('#target').addEventListener('click', function() {
  console.log('same deal')
})
An event handler is a function (subroutine) that is run each time a specific type of input is received from the user.


Exercise:

Make the above code work inside a script tag in an HTML document (you'll need a #target element on the page)
Define a function beeper
Create a button on the page
Every time the user clicks a button, add an HTML element to the bottom of the page with the word "beep"
Also change the body's background color each time a user clicks the button. Hint:
var randomColor = '#' + Math.random().toString(16).slice(2, 8)
How does this work?


Submit Your Code



Ok, that's the native JavaScript syntax for adding event handlers to the page. Now let's see jQuery's way:

$('div').on('click', function(){
  console.log('A div has been clicked!')
})

// shortcut
$('#target').click(function(){
  $('#target').show().css('color', 'red').text('boom goes the dynamite!')
})

Exercise:

Make the above code work inside a script tag in an HTML document
Create a div with the text "show me the money". If the user clicks on it, show them the money!
Create a div with the text "show me the Oprah". If the user clicks on it, show them the Oprah!
Create a div with the text "show me the Opera". If the user clicks on it, show them the Opera!
Make it so that when a user clicks on one item to show it, all the others hide first if they are already shown.
When a user clicks on an item that is already shown, hide it instead.

Submit Your Code



$('#target').on('mouseover', function(){
  $('#target').addClass('highlighted')
})
$('#target').on('mouseleave', function(){
  $('#target').removeClass('highlighted')
})

Exercise:

Place the above code into a script tag in an HTML document
Make sure there is a #target element on the page and that it has a non-zero height and width
Define CSS rules for the 'highlighted' class
Make sure everything is wired up correctly and works as you would expect
Place an image on the page that disappears when you place your mouse over a particular div#magic. Maybe this one of Margaret Hamilton.
How many different ways can you think of to accomplish that task?

Submit Your Code



var mouse_tracker = function(event){
  console.log(event.pageX, event.pageY, !!event.which)
})

$('body').on('mousemove', mouse_tracker)

Exercise:

How can we inspect the event object in the console? What properties and methods does it have?
Do click events and mouseover events get arguments passed into each invocation of their event handler functions as well? Do they have the same properties?
Create a small position: fixed <img> that follows the cursor around the screen. Maybe a gif of a puppy walking.
Figure out how to hide the cursor with CSS
Make the image follow the mouse only if the mouse button is pressed

Submit Your Code



In addition to the arguments keyword, each function invocation also has access to the calling context via the this keyword. Event handlers are called in the context of the element that received the event.

var el_finder = function(event){
  console.log("calling el_finder for:", this, event.target)
  $(this).attr('id', 'active');
}

$('div').click(el_finder)

Exercise:

Place the above code in an HTML document with at least one div and test it out.
Create an HTML document with at least 5 paragraphs
Give each paragraph a unique id attribute
Create a div#output at the top of the page
Create a click handler that shows the id attribute of the last paragraph that was clicked on in the div#output
Change the color and background-color of a clicked-on div to make it stand out
When you click on another div, clear the special styling of any perviously clicked-on divs
Is this easier to do by styling directly with .css() or by adding and removing a class name? Try both ways

Submit Your Code



$('button#go').on('click', function(){
  $('#output').text( $('input#color').val() )
})

Exercise:

Guess what does the code above does. How would you go about testing your theory?
Place the above code in a fresh HTML document
Create the correct HTML elements referenced by the click handler
When a user types a color into the input and presses the go button, change the background color of the page to that color

Submit Your Code



$('input#type').on('keypress', function (e) {
  $('label').text(e.keyCode)
})

$('body').on('keypress', function(e){
  String.fromCharCode(e.keyCode)
})

Exercise:

Try out the above code in an appropriately set up HTML document
What's the difference between the event's keyCode property and the actual letter?
What's the difference between putting the keypress handler on the input and on the body?
If the keypress handler is placed on the body and we type into the input, does the event handler run? Why is this?
Create a keylogger that concatenates every letter the user types to a string called "nsa_surveillance"
Show the user everything they've typed in a div#output
Create your own version of Type Racer

Submit Your Code



Exercise: There exist jQuery event handlers .focus() and .blur() Figure out what they do and then use them productively in an HTML document


Submit Your Code


