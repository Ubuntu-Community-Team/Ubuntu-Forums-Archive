---
title: "webdevelopers help needed!"
date: 2007-03-16
forum: Programming Talk
---

### Post by ncappel1 on 2007-03-16
Hello, I am trying to help my sister debug some code on our website,[ www.acasa5terre.it/]("http://www.acasa5terre.it/") She made it with NVU. Though we both have a little knowledge of xhtml and css, we can't figure out what's wrong!

the problem: in microsoft IE ver 5.x and ie 6 the website has an odd layout, these huge whitespaces are present where they shouldn't be. On other browsers (firefox, safari, opera) this has not shown up as a problem.

I've always heard that ie had display issues, but i've never really come up against them like this! is it an issue related with compliance to "standards compliance"  or bad coding?

attached are some screenshots, and the css stylesheet

any help is appreciated!
Nicola

---

### Post by Mirrorball on 2007-03-16
Welcome to the wonderful world of fascinating IE CSS bugs. Be prepared to scream, pull your hair out and want to kill Bill Gates with your own hands. I will analyze your style sheet and see if I can spot the culprit. If not, I wish you good luck in your debugging.

---

### Post by Mirrorball on 2007-03-16
OK, here is the first tip: when you set the width, always set padding-left and padding-right to zero. Also when you set the height, always set padding-top and padding-bottom to zero. Also add *display: inline* to *#sidebar*. Maybe it will solve your problem.

---

### Post by RedSquirrel on 2007-03-18
> **ncappel1 said:**
> Hello, I am trying to help my sister debug some code on our website,[ www.acasa5terre.it/]("http://www.acasa5terre.it/") She made it with NVU. Though we both have a little knowledge of xhtml and css, we can't figure out what's wrong!

the problem: in microsoft IE ver 5.x and ie 6 the website has an odd layout, these huge whitespaces are present where they shouldn't be. On other browsers (firefox, safari, opera) this has not shown up as a problem.

I've always heard that ie had display issues, but i've never really come up against them like this! is it an issue related with compliance to "standards compliance"  or bad coding?

attached are some screenshots, and the css stylesheet

any help is appreciated!
Nicola


At the very least, I would recommend moving your banner image out of the sidebar div (in your XHTML):

```
<div id="wrap">

<img style="width: 761px; height: 121px;" alt="mare e cappero" src="indexbanner.jpg" />

<div id="sidebar">

...
...
...

```You'll have to adjust a few things after that, but it shouldn't be too hard. :)

---

### Post by ncappel1 on 2007-03-18
A great big thank you to you all. By playing with your suggestions I was able to figure out the problem.

After repositioning the banner image out of the side bar (RedSquirrel) and putting the display: inline in several places, I was able to get it to line halfway. The image was still not lineing up, exactly. I happened to highlight everything with the mouse and noticed that is wasn't just empty space, it was an area of exactly equal size as the banner right above the main text. 

I had my suspisions and they were verified when I found an extraneous div id="container" right above the first line of text. I removed it, and voila, it was picture perfetto. 

Grazie mille (thanks a thousand!) everybody!
Nicola

---

