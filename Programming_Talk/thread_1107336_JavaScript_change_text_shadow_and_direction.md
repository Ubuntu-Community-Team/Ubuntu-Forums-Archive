---
title: "JavaScript change text shadow and direction"
date: 2009-03-26
forum: Programming Talk
---

### Post by tashe on 2009-03-26
Hi
I want to change the color and the direction and color of the shadow of a text in a DIV area randomly. So far I've made a function that uses random

function senka()
{
var random1=Math.floor(Math.random()*360);
tekst.style.color = "#"+random1;
}

<h1 id="tekst" >Text here</h1>
<input type="button" value="click" id="b" onclick="senka()" />


this only changes the color of the text. I've no idea how to set or change the shadow or the direction using javascript.
anyone with the knowledge?
thank you in advance

P.S. When I press DOT after tekst.style I dont see anything related to shadow.

---

### Post by Reiger on 2009-03-26
Whether or not text is right-to-left or left-to-right can be defined with the CSS direction property. Whether browsers (a) implement that property and (b) allow direct JavaScript access to it (expose it through the API) is another matter. Opera 10 does (a) at least, haven't checked on (b). 

Of course, if a browser does (a) but doesn't (b) wrapping things in a class="rtl" or class="ltr" attribute works (with appropiate CSS for .rtl and .ltr). Proper shadow could be simulated by manipulating multiple elements stacked on top of each other.

---

