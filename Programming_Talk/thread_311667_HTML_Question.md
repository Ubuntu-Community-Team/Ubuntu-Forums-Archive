---
title: "HTML Question"
date: 2006-12-03
forum: Programming Talk
---

### Post by derby007 on 2006-12-03
How would i change the font in a 'text' box...ie. to **bold**. Eg. I have a calendar & when the cursor/mouse goes over (mouseover) the '2nd', a bit of text is displayed in the 'text box. ie. i want this in BOLD: '2nd: New Album Released'

Fraction of Calendar:
.
.
<TD ALIGN=center bgcolor="#ff0505" 
    onMouseOver="document.myform.name.value='2nd: New Album Released'"
    onMouseOut="document.myform.name.value=''">
    <font color="white">2</font></TD>
.
.
<form name="myform"> 
    <input type="text" name="name" size="25" id="ip" > 
</form> 
.
.

---

### Post by addicted68098 on 2006-12-03
You should start using modern HTML and CSS, but anyways the 'b' tag or the 'th' tag instead of 'td'.

---

### Post by ZuLuuuuuu on 2006-12-03
Yeah I agree, and also learning JavaScript will be good for you because the code does not seem to be standard JavaScript and it may not work on Firefox.

But I don't think putting *b* tag will solve the problem if you want the text in textbox to be bold.

Anyway, you can also use CSS via the *style* attribute like this:

```
<input type="text" name="name" size="25" id="ip" style="font-weight: bold">
```

Here, *font-weight* is the CSS property and *bold* is it's value. You can learn more about CSS (Cascading Style Sheets) on:

[http://www.w3schools.com/css/](http://www.w3schools.com/css/)

---

### Post by johnnymac on 2006-12-03
Yes...I agree with everyone else - look into using CSS it's a far better way of handling styling in your HTML pages than just in-lining a font setting.

---

### Post by addicted68098 on 2006-12-03
> **ZuLuuuuuu said:**
> Yeah I agree, and also learning JavaScript will be good for you because the code does not seem to be standard JavaScript and it may not work on Firefox.

But I don't think putting *b* tag will solve the problem if you want the text in textbox to be bold.

Anyway, you can also use CSS via the *style* attribute like this:

```
<input type="text" name="name" size="25" id="ip" style="font-weight: bold">
```

Here, *font-weight* is the CSS property and *bold* is it's value. You can learn more about CSS (Cascading Style Sheets) on:

[http://www.w3schools.com/css/](http://www.w3schools.com/css/)

Actually its DOM. and firefox supports DOM like any other browser made after 1998. It is support by Java Flash and Javascript. It allows you edit HTML as i f it is XML, and enables easy obkect based programming. [http://w3schools.com/DOM](http://w3schools.com/DOM). Its perfectly valid Javascript.

---

### Post by derby007 on 2006-12-04
Cheers, i'm just a beginner at HTML, JavaScript, CSS, hense my code seems ancient...!! I'm guessing what u mean (modern HTML and CSS) is to do MOST/ALL of the formatting in CSS. Q in CSS: whats the diff in using 'class' & 'id', say DIV tags> eg: <DIV id=one"> OR <DIV class="two">  ? :-k

---

### Post by daz4126 on 2006-12-04
ids can only be applied to one element only.
classes can be used on more than one element.
Try not to go overboard on using classes and ids - you can usually style an element without them.

I would suggest getting a copy of [this book]("http://www.sitepoint.com/books/html1/?SID=c203c63a1ba075e2a9a42ca2a7a7b935")

DAZ

---

### Post by coder_ on 2006-12-04
I always suggest [http://www.w3schools.com](http://www.w3schools.com) to new users to xhtml and css as well as javascript.

But also, a good community is [http://www.sitepoint.com](http://www.sitepoint.com) for web development.


-- So yeah, just thought I'd give you some handy little links  :)...

---

### Post by daz4126 on 2006-12-05
This site is good
[http://www.htmldog.com/guides/cssintermediate/classid/]("http://www.htmldog.com/guides/cssintermediate/classid/")

DAZ

---

### Post by Ben Sprinkle on 2006-12-05
For a good example of css. Look at my site: [http://www.goatcd.org/forums/index.php](http://www.goatcd.org/forums/index.php) and take a look at the css file for it: [http://www.goatcd.org/forums/skins/default/styles.css](http://www.goatcd.org/forums/skins/default/styles.css) (I think is link)

The main site uses a different css: [http://www.goatcd.org/style.css](http://www.goatcd.org/style.css)

Have fun. :)

---

