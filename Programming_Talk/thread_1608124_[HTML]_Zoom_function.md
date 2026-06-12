---
title: "[HTML] Zoom function"
date: 2010-10-28
forum: Programming Talk
---

### Post by erotavlas on 2010-10-28
Hi,

I would like to add a manual zoom function to my website in html. The zoom have to be similar to a zoom of the browser and it must be variable by button on home page. Can you help me?

Thank you

---

### Post by Tony Flury on 2010-10-28
> **erotavlas said:**
> Hi,

I would like to add a manual zoom function to my website in html. The zoom have to be similar to a zoom of the browser and it must be variable by button on home page. Can you help me?

Thank you
There is nothing in HTML itself that does a zoom. This easiest way of doing that is by using a set of CSS Style sheet, and have different font sizes defined in different style sheets, and your button attaches a different style sheet to the page when clicked. I think (although I am not certain) you can get CSS's to scale images too.

---

### Post by epicoder on 2010-10-28
A simple solution would be javascript.
Say I have an element that I want to vary in size:
[HTML]<p>Some text</p>[/HTML]I can use javascript to change the size of that text on the fly, first by giving the element an "id" attribute, which is an easy way to identify an element in javascript:
[HTML]<p id=text>Some text</p>[/HTML]Then by making a method in javascript that changes the font size (embed this in the head section of your page):
[HTML]<script type=text/javascript>
function changetext() {
var text=document.getElementById('text');
text.style.fontSize="150%";
}
</script>[/HTML]Finally, I would add a button that activates this javascript method:
[HTML]<p id=text>Some text</p>
<input type=button value="Change size of text" onclick=changetext() />[/HTML]You can set fontSize in javascript with all the normal css units, such as em, %, or px.

---

### Post by TheBuzzSaw on 2010-10-28
^^^ Be sure to wrap your attributes in quotes properly

[php]<p id="text">Some text</p>[/php]

---

### Post by epicoder on 2010-10-28
Technically you don't have to, but you should. I'm just lazy. :D

---

### Post by TheBuzzSaw on 2010-10-28
> **sh228 said:**
> Technically you don't have to, but you should. I'm just lazy. :D

Well yeah. In today's browsers, you can get away with murder in HTML. :P

---

### Post by erotavlas on 2010-10-29
Thank you for your fast answer. What is the best and simple way for realize the zoom function? With CSS sheet or with javascript methods?

---

### Post by Tony Flury on 2010-10-29
I would suggest that you have more control with CSS - but javascript might be simpler.

Any site that i have seen that implements clickable zoom uses style sheets.

---

### Post by erotavlas on 2010-10-29
Can you suggest to me where I can find a simple example?

---

