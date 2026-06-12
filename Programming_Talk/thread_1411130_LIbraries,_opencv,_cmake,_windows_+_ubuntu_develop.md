---
title: "LIbraries, opencv, cmake, windows + ubuntu development"
date: 2010-02-19
forum: Programming Talk
---

### Post by savagetwinky on 2010-02-19
I have quite a few questions, i'm sure i'll be able to find directions all over the place on how to cobble together something but i can't seem to find anything on how to deal with extra libraries. The one in particular I'm am goign to use for a senior project is opencv, but the problem is we can't really install anything on the computers we are going to use. We'll be using it on both windows and ubuntu and my question is do you have to install the libraries.
 
Is there any way to just build libraries for open cv and just reference them relative to the folder the project is in? This is for both using g++ and visual studio 2008, and possibly minigw , though i've never used minigw so probably not. I think this is so basic its hard to find anything on it.
 
After that how would i use cmake to make configurations so i could use my source code in both visual studio 2008 and ubuntu.
 
Another question i have, since i'm a bit of a minimal list, what are the files i actually need from opencv? is there any way to just take the source code, discard everything else and just build the libraries? Would i realisticly be able 
 
I had my laptop up and running with opencv1.1 and it broke and since this now is going to be have to be moved around since i'll be working on it it a lab, linux or windows, the more of it i can fit on my flashdrive the better since i won't be able to install it. And even if i could install it i'd have to install it on every machine i work on or kill the person that took mine.
 
thank you if any one can help.

---

### Post by Unterseeboot_234 on 2010-02-25
Personally, I like the NetBeans java IDE, adding the C/C++ plug-in. Seems to be faster for development and the price is right. You need the gnu package for gcc.

You need linkages to all the opencv .h files, eg cx.h, highgui.h, etc. (and mind you, I am struggling with all this. I've already lost some work I had cooking 3 weeks ago). Seek out advice from the google group

**[[COLOR="Blue"]OpenCV google[/COLOR]]("http://groups.yahoo.com/group/OpenCV/")**

In theory, after you have a bundled byte, your program should run.

You will have to get it straight in your head what is a C implementation and the available C methods of OpenCV; C++ is distinct with more methods. Refer to the OpenCV wiki section on "building your own code"

[B][URL="http://opencv.willowgarage.com/wiki/InstallGuide"]
[COLOR="Blue"]OpenCV wiki[/COLOR][/URL][/B]

And for even more fun, you can use Java for your front end. The JavaCV (in the google groups) project allows coupling with the different OpenCV architectures. The FAINT java OpenCV is a complete package with a compiled OpenCV optimized for the Intel CPU (won't work with AMD).

The hard part is the linkage, which can be a bear coming back to a project after 3 weeks.

**[[COLOR="Blue"]JavaCV[/COLOR]]("http://groups.google.com/group/javacv")**

**[[COLOR="Blue"]FAINT[/COLOR]]("http://faint.sourceforge.net/")**

And, of course, you need the only book available on OpenCV

[B]
[[COLOR="Blue"]O'Reilly, Learning OpenCV[/COLOR]]("http://www.oreilly.de/catalog/9780596516130/")[/B]

Good luck.

---

