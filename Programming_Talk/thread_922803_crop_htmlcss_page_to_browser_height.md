---
title: "crop html/css page to browser height"
date: 2008-09-17
forum: Programming Talk
---

### Post by mpgarate on 2008-09-17
Im working on a website, and would like to set it to crop the page to the height of the browser display window to prevent the scrollbar. Is there an easy way to do this using html / css? Sorry i'm new at this

---

### Post by LaRoza on 2008-09-17
I am not sure what you want. 

Could you give a better example of what you want?

---

### Post by mpgarate on 2008-09-17
[http://power-pirate.com/simple/](http://power-pirate.com/simple/)

that is my website. I would like the reflection portion of the bottom of the image to be cut off by the bottom of the browser if there is not room for it to all be visible, rather than create a scrollbar

---

### Post by drubin on 2008-09-17
I think they would like the web page to be "shrunk" down to the size of the browser windows to provent the scroll bars from appearing. 

Basically setting the body's size to the size of the window. 

Why would you want to "crop"/remove some information from your website?

---

### Post by LaRoza on 2008-09-17
> **mpgarate said:**
> [http://power-pirate.com/simple/](http://power-pirate.com/simple/)

that is my website. I would like the reflection portion of the bottom of the image to be cut off by the bottom of the browser if there is not room for it to all be visible, rather than create a scrollbar

You could control the window with ECMAScript (to get rid of scroll bars), but why would you want to? [http://www.w3schools.com/HTMLDOM/met_win_open.asp](http://www.w3schools.com/HTMLDOM/met_win_open.asp)

Just a word of advice, don't try to force a way of looking, but try to make it flexible to work in all sorts of environments.

---

### Post by mpgarate on 2008-09-17
I'm open to suggestions, but I wanted to go this route because as you can see if you click one of the links on the top, when opened the whole pages shifts because then the scrollbar is not there.

---

### Post by FranMichaels on 2008-09-17
Look into the overflow property.

[http://www.w3.org/TR/CSS2/visufx.html](http://www.w3.org/TR/CSS2/visufx.html)

CSS3 may have the more advanced options you need.
[http://www.w3.org/TR/css3-box/#overflow](http://www.w3.org/TR/css3-box/#overflow)

---

### Post by drubin on 2008-09-17
> **LaRoza said:**
> Just a word of advice, don't try to force a way of looking, but try to make it flexible to work in all sorts of environments.

+1 

Do not try and make users have to use your site the way you would like. try make your site suite all users.

---

### Post by mpgarate on 2008-09-17
I understand what you're suggesting there.. but do you understand my issue with the scrollbar? Sorry im not too experienced at this.. but this is the most clear solution i can think of

---

### Post by LaRoza on 2008-09-17
> **mpgarate said:**
> I understand what you're suggesting there.. but do you understand my issue with the scrollbar? Sorry im not too experienced at this.. but this is the most clear solution i can think of

Use a script to open a window. Set the height and width, have no scroll bars and use CSS to prevent any changes.

---

