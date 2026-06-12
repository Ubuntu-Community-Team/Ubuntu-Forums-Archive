---
title: "How do I implement Glade3 + png (or better, svg) icons for a GTK UI?"
date: 2012-07-24
forum: Programming Talk
---

### Post by Tyblitz on 2012-07-24
Hello ubuntu community,

This is my first post on this forum. I am trying to help the developers of a program called GTK Radiant (homepage at: [http://icculus.org/gtkradiant/]("http://icculus.org/gtkradiant/")), 
which is often used on Windows, but made in Linux (Debian). It's a level editor for quake3 based shooters.

The look of the program is very old in windows ( windows 95-ish) and I wanted to do the following:

1) Upgrade the UI to a standard Win UI with Glade3.
2) Upgrade the icon format from old bmps to svg/ or at least png.
3) eventually change which icons appear in the toolbar.

The developer of a popular fork of Radiant (Darkradiant, homepage at: [http://darkradiant.sourceforge.net/]("http://darkradiant.sourceforge.net/")) has successfully done just what I wanted to do with Radiant.

I tried looking at programs like Inkscape & Gimp, which both use SVG icons, but the files and coding are too much of a mess for me.

My problem: I am NOT a programmer. I understand the basics of programming, but am not able to write code. The source code of the Radiant is available on github

If anyone could answer any of my questions; or better yet, look into the program; I would be very grateful.

So what I need help with/ answers to:
1),2),3) - Questions already mentioned 

/* for next questions you need to view the sourcecode on github */

4) - Where can I find the files that link to the Windows API?
5) - Where are the files that link to the bitmaps/ determine the bmp format?
6) - How can I eventually implement svg files?

Help is enormously appreciated!

-Tyblitz

---

### Post by alexfish on 2012-07-25
most tools are available from the command line

installing inkscape  helps with the libs side of things , if a novice

most svg files can be edited with any text editor,

inkscape will format the svg into a readable (easy to understand format)

so install inkscape , make 2 squares on the form , save as standard svg

open up the editor , and read through the data.

will post later on some pointers on converting

but first you need to look at the man pages for convert

```
man convert
```

the easiest to make ui editor have a look at bacon

search or google 

bacon converter  , they also have a forum ;)

regards

alexfish

---

### Post by Tyblitz on 2012-07-25
Thank you alexfish, I'll surely start having a look at Bacon and how to handle the XML files of the SVGs. I already knew that they're text though, and I have Inkscape installed too. 

However, I wish to compilte the endprogram on my Windows computer, not my linux (I can't even get the program to compile properly there, partially because I'm quite new to Ubuntu). I'll be waiting for your next post :).
This part'll keep me busy for a while....

However still need help for linking these svgs in the source files.

Till then, 

-Tyblitz

---

### Post by alexfish on 2012-07-26
the only thing I can think of is cygwin , 

[http://www.cygwin.com/](http://www.cygwin.com/)

see if the members are aware of it

regards

alexfish

ADDED:

Just had a though,  JC Fuller may have some knowledge in this area as regards the gtk bits in windows , he is also a member of the forum mentioned.

if your not used to programming gtk + svg , it going to be difficult , if you have the development files install have a look libsvg
paste this link into your browser

file:///usr/share/doc/librsvg2-dev/html/RsvgHandle.html#RsvgHandle.object-hierarchy

---

