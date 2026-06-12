---
title: "web programming....page layout."
date: 2008-01-18
forum: Programming Talk
---

### Post by hockey97 on 2008-01-18
Hi  I am working on my website layout. I am using gimp on windows.

I created my art in gimp and I save it in .png format

I   am using html tables to use those images to make a good looking table.

The problem I run into is that in gimp it is  at a good size but when I post it on the html table in my website  I get the image very very small you only see a line with the color of that tab top of the table. a 3d looking tab.

my questions is how do you guy's  make images to fit nicely on a webpage??  any tips??

---

### Post by lswest on 2008-01-18
you can resize it to fit the table, or you can find the exact dimensions of the table/row or column you want to put it in, and make the art accordingly

---

### Post by argraff on 2008-01-18
it sounds like your table doesn't know how big it is. Did you add in your height and width?

---

### Post by hockey97 on 2008-01-18
yes this is what I have:

<table width="128" height="30"  border="0" cellpadding="0" cellspacing="0">

I made the backround image to be created with those values.

and  the other art are the dimensions of the cells their in.

But it just still shows the art very small they shrink to a point where the images are lines.

---

### Post by argraff on 2008-01-18
Ah. I think I know what's going on. Because there's nothing in there (the background image doesn't count) it's collapsing the table.

Are you using CSS at all? If so, simply give the cell you want your background a unique id and set the height and width in the CSS.

However, I'm guessing that you're not using CSS since you're designing with a table so:
make a gif in GIMP that's completely transparent and 1px square. Name it, say, 'spacer.' Add it to your image directory.

Now add an img tag inside the cell you have with the background. Give the spacer image the dimensions of the background image.

*NOTE* This is not really the proper way to do this - CSS would be much better - but it'll work.

Let me know how it goes! :)

---

