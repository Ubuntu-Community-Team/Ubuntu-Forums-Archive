---
title: "Objective-C?"
date: 2008-05-22
forum: Programming Talk
---

### Post by paintba||er on 2008-05-22
Well, I'm a (happy) Mac user for the most part, so naturally I program mostly in OS X, and I love Cocoa and Objective-C.  But I'd like to start writing apps for Linux, and I can't seem to find anything that matches up with Cocoa.  I've been trying Qt, but it's just not as good as Cocoa, and I can't bring myself to like C++.  I've been trying to find some way I can use Objective-C, but all I've been able to find was GNUstep, but from what I've read it isn't too great.  Just reading Aaron Hillegass's description of it is enough to scare me away...

So are there any other options?  I'd really like to use Objective-C...

---

### Post by LaRoza on 2008-05-22
> **paintba||er said:**
> Well, I'm a (happy) Mac user for the most part, so naturally I program mostly in OS X, and I love Cocoa and Objective-C.  But I'd like to start writing apps for Linux, and I can't seem to find anything that matches up with Cocoa.  I've been trying Qt, but it's just not as good as Cocoa, and I can't bring myself to like C++.  I've been trying to find some way I can use Objective-C, but all I've been able to find was GNUstep, but from what I've read it isn't too great.  Just reading Aaron Hillegass's description of it is enough to scare me away...

So are there any other options?  I'd really like to use Objective-C...

You can use Objective-C in Linux.  Cocoa as far as I know is for OS X only. 

[http://www.foldr.org/~michaelw/objective-c/](http://www.foldr.org/~michaelw/objective-c/)

I see GTK binding for it.

---

### Post by paintba||er on 2008-05-22
Oh, I guess I should've been more specific.  I'm looking for a GUI toolkit that I can use with Objective-C.  And perhaps I'm mistaken, but I didn't think GTKKit was still being maintained?

---

### Post by ZuLuuuuuu on 2008-05-22
AFAIK, GNUstep is the only maintained GUI/Foundation library on Linux and Windows for Objective-C. I don't have much experience but written "Hello World" kind of examples using GNUstep. It is not that bad on Linux but on Windows it has got some serious issues. It also provides that you don't have to write different codes between MacOS/Linux/Windows and still use native Cocoa library on MacOS which is a great plus. I advice you to give it a try ;)

---

### Post by hardyn on 2008-05-22
Paintballer,

I fell onto a thread a few weeks back about some apple developers trying to get into QT for better x-platform compatiblity... according to the original poster he found QT better and worse than Cocoa; perhaps worth a look to find this thread, perhaps compair notes with this guy?  he seems to have similar interests to you.

---

### Post by paintba||er on 2008-05-22
Alright, I guess I'll try out GNUstep.  This is what scared me away from it:

[quote=Aaron Hillegass]The effort may be a noble one, but using GNUstep is not for the faint of heart:

[LIST]
[*]GNUstep is difficult to install.
[*]The tools are buggy and crash regularly.
[*]Porting your application from Mac OS X is difficult because the file formats for nib files are different under GNUstep. (While the OpenStep API is open, Apple has kept the nib file format closed and proprietary.)
[*]The interface that GNUstep creates is a decent copy of the NeXT UI.  It was a slick look in 1994, but now the look and feel are like neither the Mac nor a normal X11 application.
[*]Quartz and the Apple Window Server run natively on Mac OS X.  GNUstep attempts to graft this graphics model onto whatever back end it is using.  (On most systems, X11 serves as the back end.)  The performance and aesthetics may disappoint users who are familiar with Mac OS X.
[/LIST][/quote]

But I guess that being a former NeXT and Apple employee it is likely that he is a bit biased...

It also seems like distributing any applications you use GNUstep for will be quite a pain...

---

### Post by Zanti on 2008-06-15
Alright, I guess I'll try out GNUstep. This is what scared me away from it:

Quote:
Originally Posted by Aaron Hillegass
The effort may be a noble one, but using GNUstep is not for the faint of heart:

    * GNUstep is difficult to install.
     (snip)

I use GNUStep, actually in a GNUStep environment right now.  This is from the homepage for GNUStep:
More on  what GNUstep is...

For readers of the book: Cocoa Programming for Mac OS X, 2nd ed. We have some clarifications for the chapter on GNUstep. 

this is the link to the clarifications:
[http://www.gnustep.org/resources/BookClarifications.html](http://www.gnustep.org/resources/BookClarifications.html)

Happy Coding :)

---

