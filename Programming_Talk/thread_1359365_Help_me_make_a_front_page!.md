---
title: "Help me make a front page!"
date: 2009-12-19
forum: Programming Talk
---

### Post by gjoellee on 2009-12-19
I have been thinking about a new front page on my website, but unfortunately I have a lack of knowledge when it comes to making code from the ground up. Modifying and tweaking code is not a problem.

However i have a new concept for my website (see attachment for what i want). I found something similar on the web for a while ago, but i can't find it again so I am asking you (yes, YOU) to create the base code for me.

Could you make something similar to this for me, (stick to CSS and HTML. Please do not use PHP).

If you got any questions, don't be afraid to ask!

---

### Post by gjoellee on 2009-12-19
Whooops...forgot attachment:

---

### Post by kwyto on 2009-12-19
check [http://www.w3schools.com]("http://www.w3schools.com/html/html_intro.asp")
there you can find html, css, javascript, and many other tutorials
good luck and goog code!!!!

---

### Post by Can+~ on 2009-12-19
Two things about this:

[LIST=1]
[*]We don't do things for free. It's a fine opportunity for you to learn, specially, your design is very simple to achieve. Create 3 divs, and apply rules to them, and you'll see that you can get there, just have w3schools at hand, and you will be able to do it.
[*]It's a terrible front page. Not in terms of design (which isn't spectacular, either), but in terms of usability. You know what happens with fancy flash introductions, or minimalistic front pages (like this one)? They get ignored, people jump to the actual content directly. That's why you don't see these pages in sites like digg, engadget, arstechnica, etc. They usually throw you directly to the main feed, and you can choose your content/section from there, or a form of login in case of sites like Facebook.
[/LIST]

---

### Post by gjoellee on 2009-12-20
> **Can+~ said:**
> Two things about this:

[LIST=1]
[*]We don't do things for free. It's a fine opportunity for you to learn, specially, your design is very simple to achieve. Create 3 divs, and apply rules to them, and you'll see that you can get there, just have w3schools at hand, and you will be able to do it.
[*]It's a terrible front page. Not in terms of design (which isn't spectacular, either), but in terms of usability. You know what happens with fancy flash introductions, or minimalistic front pages (like this one)? They get ignored, people jump to the actual content directly. That's why you don't see these pages in sites like digg, engadget, arstechnica, etc. They usually throw you directly to the main feed, and you can choose your content/section from there, or a form of login in case of sites like Facebook.
[/LIST]

1. It was worth a try...

2. Hmmmm....you gave me an other idea...

---

### Post by Barriehie on 2009-12-20
So when you do get something up and running give us a link; easier to help that way! :)

Barrie

---

### Post by AndThenWhat on 2009-12-20
Those rounded corners will take a lot of code unless you use images, but the basics would just take a table.

```

<html>
<head>
     <title>your site's title</title>
     <style type="text/css">
           any CSS you want goes here
           .spacingclass {
              cell-spacing: 20px
           }
     </style>
</head>
<body>
   <table>
      <tr class="spacingclass">
        <td><h1>Tuly Stupid</h1></td>
        <td><h1>Users</h1></td>
        <td><h1>Community</h1></td>
      </tr>
   </table>
</body>
</html>

```

That's roughly what you're looking at minus all of the css to change the box colors.

---

### Post by Hellkeepa on 2009-12-21
HELLo!

I would recommend against abusing tables for layout purposes, for many reasons (google "why not tables" for a list). All that's needed here is 3 DIV-blocks, with the same class applied to them.
As for rounded corners, this is quite easy to achieve with the sliding doors technique, and other similar CSS-tricks.

Happy codin'!

---

