---
title: "Swing, AWT, SWT, Qt, or wxWidgets for Java"
date: 2010-05-03
forum: Programming Talk
---

### Post by patrickaupperle on 2010-05-03
What do you think would be the best GUI toolkit to use for a java application?

---

### Post by themusicwave on 2010-05-03
I certainly would choose Swing over AWT.

I really haven't tried anything other than Swing with Java.  So I can't speak too much to the other options.  I've done some QT(by some I mean 1 program) in Python and it was nice.

I think for Java, Swing is the best supported option out there.  It can be a bit painful at times, but it really isn't that bad.  Also, most of the tutorials and examples out there are written in Swing so it will be easy to find lessons and documentation.

Finally, if you plan to distribute this program that is a consideration as well.  If you use something other than Swing or AWT you will need to include them when you distribute in addition to Java.

Although I guess if you know one of the others in a different language already it would be easy to use what you already know.

What are you making this program for?

---

### Post by Tak11 on 2010-07-23
SWT most definitely, it has a bit of a learning curve, but it was created for a reason.

Swing and SWT both were build on a layer of AWT, they are higher level graphical toolkits.

Swing however is slower, and uglier, it is build into java so that is nice, however you have to change settings in java to get Swing to look native.

SWT actually uses native components when it can, so it looks like any other application on whatever platform it runs on. and is much faster than swing. also you can even take it a step higher with JFace (which i don't have much experience with so might want to check it out on your own.)

[http://en.wikipedia.org/wiki/JFace](http://en.wikipedia.org/wiki/JFace)

I still integrate a lot of AWT into my graphical applications when i need to get onto a lower level (ex. grabbing window focus etc.) but it shouldn't really be used to construct your entire application.

wxWidgets is kind of cool, however you will run into some issues cross platform, not only that but its java binding isn't the primary implementation so support will be limited, and it wont be as kind to java as API's built specifically for it.

^ pretty much same goes for Qt though i also have limited experience with it.

---

### Post by endotherm on 2010-07-23
here is how I learned it:
AWT - old and obsolete. replaced by SWING

SWT - a set of IBM extensions to the java runtime that provide gui objects that are improved over AWT, but the SWT libraries must be included with the application as they are not in the jre. SWT was best when SWING was still in its infancy, but this is no longer true

SWING - a Sun replacement for AWT. I have most recently choosen to use swing because its as good as anything else, but doesn't require me to ship an swt.jar. 

QT- good stuff but requires the QT platform be installed.

never tried the widgets.

---

### Post by KdotJ on 2010-07-23
Swing is going to be your easiest option really. It looks better than AWT for sure, and as it is part of the java framework you own't need to include other libraries in your application. It is also very, very well documented. Swing does look somewhat ugly, but, you can change the LookAndFeel of Swing to match the platform you're working on. It does ok, not perfect but ok...

---

