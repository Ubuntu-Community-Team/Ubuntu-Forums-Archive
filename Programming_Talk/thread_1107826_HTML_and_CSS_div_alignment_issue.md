---
title: "HTML and CSS div alignment issue"
date: 2009-03-27
forum: Programming Talk
---

### Post by samjh on 2009-03-27
I'm making a website using CSS divs for layout (ie. not tables).  Here's the basic layout:

```

+-----------------------------------------------------------+
|+---------------------------------------------------------+|
||                      HEADER                             ||
||                                                         ||
|+---------------------------------------------------------+|
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                       MAIN                                |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|+---------------------------------------------------------+|
||                      FOOTER                             ||
|+---------------------------------------------------------+|
+-----------------------------------------------------------+
```
I've set the MAIN div to have a minimum height of 700px, so it will enlarge itself if the stuff in it is big enough, but won't shrink to less than 700px tall.

The problem I have is with the FOOTER.  I need the FOOTER div to stay at the bottom of the MAIN.  If the MAIN part is large enough to fill the 700px or larger, then the FOOTER obviously is pushed to the bottom and that's fine.  But if the stuff in the MAIN part isn't big enough to fill 700px vertically, then the FOOTER section rides up to just below whatever other content is in MAIN, defeating the whole purpose of MAIN's minimum height.

Any tips please? :)

---

### Post by hastur on 2009-03-27
hi,

a simple solution if defining the height of the footer is acceptable : you should simply put the footer outside the main div.
after you can either :
- adjust the height of both main and footer div, so that the resulting height is 700px (example : 650px for main, 50px for footer).
- or if you don't want the height of the footer to be a fixed pixel value, but adjust to the height of the font, then set the footer height in em (example 1.5em), then give it a negative top margin (-1.5em) and finally add a bottom padding to the main div (1.5em). the footer will stay at the bottom of the main div, overlapping the main div but not its content, and have an "variable" height.

---

### Post by tturrisi on 2009-03-27
...or use a 4th DIV, a container, and put all other divs in it, and order the html as such:

<div id="container">
<div id="header">stuff</div>
<div id="main">stuff</div>
<div id="footer">stuff</div>
</div>

and adjust widths & heights accordingly.

---

### Post by samjh on 2009-03-27
> **tturrisi said:**
> ...or use a 4th DIV, a container, and put all other divs in it, and order the html as such:

<div id="container">
<div id="header">stuff</div>
<div id="main">stuff</div>
<div id="footer">stuff</div>
</div>

and adjust widths & heights accordingly.

I can't believe I didn't think of that!

Thanks a lot. :)

---

### Post by matmatmat on 2009-03-27
I did it using this:
[PHP]
clear:both;
[/PHP]
don't know if that's what you want though...

---

### Post by ZuLuuuuuu on 2009-03-27
> **matmatmat said:**
> I did it using this:
[PHP]
clear:both;
[/PHP]
don't know if that's what you want though...

It is a whole different thing. It is used so that the div placed after floating divs are placed right.

---

### Post by tturrisi on 2009-03-28
> **samjh said:**
> I can't believe I didn't think of that!

Thanks a lot. :)

You're welcome.

Now, you can use css to center the page as well.  The below enables css centering to function in all browsers.  Be sure to declare text-alignment in your content divs (header, main, footer).

body {
text-align:center;}

#container {
width:990px;
margin:0px auto;}

---

### Post by Tibuda on 2009-03-28
> **tturrisi said:**
> Now, you can use css to center the page as well.  The below enables css centering to function in all browsers.  Be sure to declare text-alignment in your content divs (header, main, footer).

body {
text-align:center;}

#container {
width:990px;
margin:0px auto;}
add a text-align: left; to #container too, unless you want your content to be centered. 
990px won't look good on old 800x600 monitors. better use max-width: 990px, and a hack for IE6 (which can't understand max-width). this way you get a flexible layout for older monitors.
```
body { text-align:center; }
#container { max-width:990px; margin:0px auto; text-align:left; }
* html #container { width:990px; }
```

---

### Post by tturrisi on 2009-03-29
I used 990px as an example.
It won't render nice on 800x600 screens though.
I used to do all my sites to accomodate 800x600.
However, today's most common screen resolution is 1024x768 due to lowered price of flat panel LCD monitors & laptops.  CRTs are disappearing.
No need to design for 800x600 anymore.
[http://www.w3schools.com/browsers/browsers_display.asp](http://www.w3schools.com/browsers/browsers_display.asp)
[http://www.superiorwebsys.com/blog/21/Most_Common_Screen_Resolutions](http://www.superiorwebsys.com/blog/21/Most_Common_Screen_Resolutions)
[http://www.screenresolution.org/](http://www.screenresolution.org/)

---

### Post by Tomosaur on 2009-03-29
Careful with min / max heights in CSS! Lots of people still use IE6 which doesn't support them (I think it's fixed in IE7 though).

---

### Post by Mickeysofine1972 on 2009-03-29
one idea is to have a pixel wide div inside the has a set height of the min-height you need the floated right and display block.

that way he div never collapses smaller than the divs height and gets bigger when more content is added.

Mike

---

