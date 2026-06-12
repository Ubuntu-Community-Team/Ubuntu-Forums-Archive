---
title: "passing array values in javascript"
date: 2014-11-15
forum: Programming Talk
---

### Post by maclenin on 2014-11-15
Can someone untangle why the following code...

```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
a(myArray);
document.body.innerHTML += '<div id = "click" onclick = "d(\'' + myArray + '\');"><br>pass myArray via onlick (to function d)<br></div>';
}

function a(a_array) {
document.body.innerHTML += "<br> function a: " + a_array[0] + "<br>";
b(a_array);
}

function b(b_array) {
document.body.innerHTML += "<br> function b: " + b_array[1] + "<br>";
c(b_array);
}

function c(c_array) {
document.body.innerHTML += "<br> function c: " + c_array[2] + "<br>";
}

function d(d_array) {
document.body.innerHTML += "<br> function d: " + d_array[0] + "<br>";
}

create_myArray();

```

...when run and after clicking...

```
pass myArray via onlick (to function d)

```

...yields (in [jsbin]("http://jsbin.com/")):

```
function a: apple

function b: banana

function c: grape

pass myArray via onlick (to function d)

function d: a

```

Essentially, I am having difficulty maintaining the "structure" of myArray when I try to pass its value(s) using onclick!

Thanks for any guidance!

---

### Post by The Cog on 2014-11-15
Your onclick is building a string. This is how that div looks in the element inspector of a browser:
```
<div id="click" onclick="d('apple,banana,grape');"><br>pass myArray via onlick (to function d)<br></div>
```
Of course, the 0th element of 'apple,banana,grape' is 'a'.

Your problem is that you are writing source code - passing an existing array into source code isn't easy.

Easiest would be to make the array global and have the function use the global name:
```
function create_myArray() {
myArray = ["apple", "banana", "grape"];
a(myArray);
document.body.innerHTML += '<div id = "click" onclick = "d(myArray);"><br>pass myArray via onlick (to function d)<br></div>';
}
```

If you want to keep the array more private, you can attach it to the clickable element:
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
a(myArray);
document.body.innerHTML += '<div id = "click" onclick = "d(this.myArray);"><br>pass myArray via onlick (to function d)<br></div>';
document.getElementById("click").myArray = myArray;
}
```

Or you can use JSON.stringify to insert a source-code representation of the current array contents. But of course that results in a new array being created when the element is clicked, and it won't carry any changes that are made to the original array after the div code is written to the document:
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
a(myArray);
document.body.innerHTML += '<div id = "click" onclick = \'d('+JSON.stringify(myArray)+')\';><br>pass myArray via onlick (to function d)<br></div>';
}
```

---

### Post by maclenin on 2014-11-15
Thanks, **The Cog**!

I think I've had a few too many brushes with Crockford to lean in the direction of the "evil" global var!

If myArray is uniquely-named, will I still need the "this" in order to stress that, indeed, this is the very myArray (object) to which I am referring via this div id-specific onclick?

I've given your "private" example a go via jsbin - and my project code - it seems to have solved the riddle!

```
document.body.innerHTML += '<div id = "click" onclick = "d(myArray);"><br>pass myArray via onlick (to function d)<br></div>';
document.getElementById("click").myArray = myArray;
```

Any suggested sources for javascript learning / betterment? Great advice - but I don't want to just take / deploy your wisdom and run!

Will mark the thread accordingly!

Thanks, again!

---

### Post by The Cog on 2014-11-15
Glad you got a working solution.

Yes, global vars can be troublesome. So the "private" example is probably the way I would choose although there are probably others I haven't thought of.

You need some way of getting hold of the "private" array. The fact that the name is unique is irrelevant - it's not global so you cannot just call it by name. Using this from the click handler is a nice shortcut that only works inside the click handler. You have already seen how to access it from anywhere: document.getElementById("click").myArray.

The only javascript book I have read was "Javascript: the good parts" which I found very helpful. It needs reading lots of times though - a bit more sinks in each time.

---

### Post by maclenin on 2014-11-16
**The Cog**!

A quick follow-up - I am trying to provide 3 unique onclick "instances" access to myArray (via the iD variable):
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
var iD = myArray;
var i;
for (i = 0; i < 3; i += 1) {
document.body.innerHTML += '<div id = "click' + i + '" onclick = "d(' + i + ', iD);"><br>button: ' + i + ' | click to pass myArray via onlick (to function d)<br></div>';
document.getElementById("click" + i).iD = iD;
}
}

function d(i, d_array) {
document.body.innerHTML += "<br>result: " + i + " | function d: " + d_array[0] + "<br>";
}

create_myArray();


```

However, only "click2" (via button: 2) seems to enjoy access to myArray. A click of each "button" yields the following:

```
button: 0 | click to pass myArray via onlick (to function d) < ----- (via console: ReferenceError: iD is not defined)

button: 1 | click to pass myArray via onlick (to function d) < ----- (via console: ReferenceError: iD is not defined)

button: 2 | click to pass myArray via onlick (to function d) 

result: 2 | function d: apple
```

I can't quite seem to figure out how to "iterate" (access to) the myArray value(s) across multiple onclick instances!

Thanks, again, **The Cog**, for any wisdom (and for the additional Crockford reference)!

---

### Post by The Cog on 2014-11-16
You still don't get that your javascript is writing code. By the time that the click is acted on, the function create_myArray has finished and returned, and its variables have ceased to exist.
The code you write into the page (use the browser's element inspector) looks like this:
```
<div id="click0" onclick="d(0, iD);"><br>button: 0 | click to pass myArray via onlick (to function d)<br></div>
```
but iD is not a global variable. iD is undefined. The fact that some time ago there was a function running that had a private variable called iD is irrelevant. 

The object that you clicked has a member called iD because you attached it earlier, but if you want to refer to that you need to be specific. Since in a click handler, **this** refers to the clicked object, **this.iD** works nicely.

I don't understand how the last function is picking up anything called iD. But it seems to be a left-over from somewhere and is not reliable. For instance, this code has broken it (I added another line to the document):
```
for (i = 0; i < 3; i += 1) {
document.body.innerHTML += '<div id = "click' + i + '" onclick = "d(' + i + ', iD);"><br>button: ' + i + ' | click to pass myArray via onlick (to function d)<br></div>';
document.getElementById("click" + i).iD = iD;
}
document.body.innerHTML += "<br/>Try it!<br/>"
}

function d(i, d_array) {
document.body.innerHTML += "<br>result: " + i + " | function d: " + d_array[0] + "<br>";
}

```

---

### Post by maclenin on 2014-11-16
I appreciate your candor.

A. Here is what I hope I understand:

1. I can use the for loop in function create_myArray to assign unique values to 3 separate onclick instances (where myArray is not passed as an argument):
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
var i;
for (i = 0; i < myArray.length; i += 1) {
document.body.innerHTML += '<div id = "click' + i + '" onclick = "a(\'' + myArray[i] + '\', ' + i + ');"><br>onclick instance ' + i + '<br></div>';
}
}

function a(fruit, i) {
document.body.innerHTML += "<br>" + fruit + "&nbsp;" + i + "<br>";  
}

create_myArray();
```

1.a. Yielding (after function create_myArray has finished / returned / private variables destroyed):
```
onclick instance 0 *WITH* generated source: <div id = "click0" onclick = "a(apple, 0);"><br>onclick instance ' + i + '<br></div> *WHICH AFTER* onclick *YIELDS* apple 0

onclick instance 1 *WITH* generated source: <div id = "click1" onclick = "a(banana, 1);"><br>onclick instance ' + i + '<br></div> *WHICH AFTER* onclick *YIELDS* banana 1

onclick instance 2 *WITH* generated source: <div id = "click2" onclick = "a(grape, 2);"><br>onclick instance ' + i + '</div> *WHICH AFTER* onclick *YIELDS* grape 2

```

B. What I don't quite understand:

2. If this snippet "works" (where myArray is passed as an argument), as in your "private" example:
```
document.body.innerHTML += '<div id = "click" onclick = "a(this.myArray, 0);"><br>onclick instance<br></div>';
document.getElementById("click").myArray = myArray;
}

function a(fruit, i) {
document.body.innerHTML += "<br>" + fruit[i] + "&nbsp;" + i + "<br>";  
}

```

2.a. Yielding (after function create_myArray has finished / returned / private variables destroyed):
```
onclick instance *WITH* generated source: <div id = "click" onclick = "a(myArray, 0);"><br>onclick instance<br></div> *WHICH AFTER* onclick *YIELDS* apple 0
```

3. Why can't this snippet work the same way as 2. (where myArray is passed as an argument), though, in iterative fashion, similar to 1.?
```
for (i = 0; i < myArray.length; i += 1) {
document.body.innerHTML += '<div id = "click' + i + '" onclick = "a(this.myArray, ' + i + ');"><br>onclick instance ' + i + '<br></div>';
document.getElementById("click" + i).myArray = myArray;
}
}

function a(fruit, i) {
document.body.innerHTML += "<br>" + fruit[i] + "&nbsp;" + i + "<br>";  
}
```

3.a. Yielding (after function create_myArray has finished / returned / private variables destroyed):
```
[I]onclick instance 0 WITH generated source: <div id = "click0" onclick = "a(myArray, 0);"><br>onclick instance ' + i + '<br></div> WHICH AFTER onclick SHOULD YIELD apple 0

onclick instance 1 WITH generated source: <div id = "click1" onclick = "a(myArray, 1);"><br>onclick instance ' + i + '<br></div> WHICH AFTER onclick SHOULD YIELD banana 1[/I]

onclick instance 2 *WITH* generated source: <div id = "click2" onclick = "a(myArray, 2);"><br>onclick instance ' + i + '</div> *WHICH AFTER* onclick *YIELDS* grape 2
```

Is there no way to iteratively pass myArray to onclick, so that each iteration has access to myArray values, as shown for the single onclick instance, in example 2. / 2.a.?

As posted, earlier - in practice, onclick instance 0 and onclick instance 1 yield (in 3.a.): *TypeError: Cannot read property '0' of undefined* and *TypeError: Cannot read property '1' of undefined*, respectively.

Thanks, again, for any (advancement of my) knowledge.

---

### Post by The Cog on 2014-11-16
1/1a will not work. The onclick definition is **onclick="a(apple, 0);"** This code is trying to pass a variable called apple. The variable apple will probably be undefined, so this code will end up calling **a(Undefined, 0)**. If you wanted to pass the string 'apple', you would have to put quotes round it like this: **onclick="a('apple', 0);"**

2/2a does not work as I thought it did. This just proves that I don't understand javascript either. I thought I was attaching the array to the div element, but it seems not. It seems that you cannot set dom objects like that after all. My code was instead picking up the "lying around" copy that I didn't understand anyway.

So the question remains, how do you preserve a copy of the array after the create_myArray function returns if you can't use a global variable. It needs preserving somehow so that the click handlers can gain access to it. At this stage, I have to admit I don't know. Perhaps I need to read that javascript book again.

---

### Post by maclenin on 2014-11-17
**The Cog**!

If you copy and paste these two snippet samples, separately, into [jsbin]("http://jsbin.com/"), (or "build-your-own" test.html and test.js files) and click on the onclick instance(s), you'll see that something is, indeed, working.

1. Taken from 1. / 1.a. above (where myArray is not passed as an argument):
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
var i;
for (i = 0; i < myArray.length; i += 1) {
document.body.innerHTML += '<div id = "click' + i + '" onclick = "a(\'' + myArray[i] + '\', ' + i + ');"><br>onclick instance ' + i + '<br></div>';
}
}

function a(fruit, i) {
document.body.innerHTML += "<br>" + fruit + "&nbsp;" + i + "<br>";  
}

create_myArray();
```

2. Taken from 2. / 2.a. above (where myArray is passed as an argument):
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
document.body.innerHTML += '<div id = "click" onclick = "a(myArray, 0);"><br>onclick instance<br></div>';
document.getElementById("click").myArray = myArray;
}

function a(fruit, i) {
document.body.innerHTML += "<br>" + fruit[i] + "&nbsp;" + i + "<br>";  
}

create_myArray();
```

3. Yep, I (almost) agree...
> **The Cog said:**
> So the question remains, how do you preserve a copy of the array after the create_myArray function returns if you can't use a global variable. It needs preserving somehow so that the click handlers can gain access to it. At this stage, I have to admit I don't know. Perhaps I need to read that javascript book again. 
...though I think, more specifically (given the result of running snippet 2.), the question should be how do you preseve a copy / value of the array across multiple onclick instances - simultaneously - so that each instance can be executed, in any sequence, any number of times, after create_myArray has "returned" (see Extra credit). 

Crockford?! Crockford?!

Extra credit:
```
function create_myArray() {
var myArray = ["apple", "banana", "grape"];
document.body.innerHTML += '<div id = "a_click"><br>a click<br></div>';
document.body.innerHTML += '<div id = "b_click"><br>b click<br></div>';
document.body.innerHTML += '<div id = "c_click"><br>c click<br></div>';
document.getElementById("a_click").onclick = (function (myArray) {return function () {a(myArray, 0);};}) (myArray);
document.getElementById("b_click").onclick = (function (myArray) {return function () {a(myArray, 1);};}) (myArray);
document.getElementById("c_click").onclick = (function (myArray) {return function () {a(myArray, 2);};}) (myArray);
}

function a(fruit, i) {
console.log(fruit, i);
document.body.innerHTML += "<br>" + fruit[i] + "&nbsp;" + i + "<br>";  
}

create_myArray();
```
Each respective instance of onclick has access to myArray values at the time the instance is created - with a single click of either "a click" or "b click" or "c click" passing myArray values to "function a". However, only a single onclick instance can be executed per create_myArray "cycle". Curiouser and curiouser.

---

### Post by The Cog on 2014-11-18
You've been reading that book, haven't you! 
Freezing a reference to the array inside another function still doesn't seem to work. Adding to innerHTML seems to be what destroys things.

I can't think of any way that avoids having at least one global variable. It seems common to create a myApp object to use as a container for all other persistent variables:
myApp = {
     "myArray" : ["apple", "banana", "grape"],
    "version" : 28
}
You can add properties to this object as the program progresses.
```
function create_myArray() {
myApp = {"myArray" : ["apple", "banana", "grape"],
	"version" : 73
}
document.body.innerHTML += '<div id = "a_click" onclick="a(myApp.myArray, 0)"><br>a click<br></div>';
document.body.innerHTML += '<div id = "b_click" onclick="b(\'myArray\', 1)"><br>b click<br></div>';
document.body.innerHTML += '<div id = "c_click" onclick="b(\'myArray\', 2)"><br>c click<br></div>';
}

function a(fruit, i) {
document.body.innerHTML += "<br>" + fruit[i] + "&nbsp;" + i + "<br>";  
}

function b(aname, aindex) {
document.body.innerHTML += "<br>" + myApp[aname][aindex] + "&nbsp;" + aindex + "<br>";  
}


create_myArray();

```

---

