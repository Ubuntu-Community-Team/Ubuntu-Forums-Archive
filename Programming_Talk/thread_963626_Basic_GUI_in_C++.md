---
title: "Basic GUI in C++"
date: 2008-10-30
forum: Programming Talk
---

### Post by nerdpride on 2008-10-30
Hello people of the internet. I was wondering were is the best place to start programming GUI in ubuntu. I know c++ and am a little tired of terminal applications. I know there are various layout softwares out there. Does anybody know where I can find a guide to a good one.

---

### Post by Idefix82 on 2008-10-30
This is the best place to start:
[http://www.gtk.org/]("http://www.gtk.org/")
Under the "Documentation" link there are a couple of tutorials, among others this newbie tutorial:
[http://zetcode.com/tutorials/gtktutorial/]("http://zetcode.com/tutorials/gtktutorial/")

Good luck!

---

### Post by nerdpride on 2008-10-30
Thanks. I would close the thread but i want to take a poll. Who Prefers GTK+?

---

### Post by snova on 2008-10-30
Asking about the "best" is entirely subjective, and generally a bad idea.

I personally like Qt. There are others who like GTK+, some who prefer lesser known ones...

I suggest you take a look at the API's of each toolkit and decide which one looks easiest to use.

---

### Post by nerdpride on 2008-10-30
> **snova said:**
> Asking about the "best" is entirely subjective, and generally a bad idea.


You are entirely right I'll edit that

---

### Post by LaRoza on 2008-10-30
See my wiki and the stickies.

QT, GTK and wxWidgets are all popular.

---

### Post by hessiess on 2008-10-30
Personally my preference leans towards WX Wigits, it wraps around other frameworks(GTK, win32 etc) so the result always looks native.

Though saying that I haven't created anything more than simple tests with any GUI framework, cout/cin interfaces take less time to make and(for the most part) function adequately :).

---

### Post by samjh on 2008-10-30
GTK+/GTKmm:
Very popular, fairly light-weight, written in C.  For C++, you should probably use GTKmm, which is the C++ implementation of GTK+.  Uses its own look-and-feel with native imitations.

Qt:
Very popular, middle-weight, written in C++.  Not just a GUI toolkit, it contains comprehensive threading, networking, database, internationalisation, and other libraries in one clean package.  For GUI, it uses its own look-and-feel with themes for each supported platform.

wxWidgets:
Less popular than the two above, but still quite popular.  Uses native widget drawing, so it has excellent look-and-feel for each platform it supports.  Written in C++.  Somewhat complex and difficult to learn (IMHO).

FLTK:
Very light-weight and easy to use.  On the flip-side, it look very plain (ie. not as pretty as GTK+ or Qt, and doesn't even try to imitate native look-and-feel).

There are more.  But those are probably the most well-known for C++.

---

### Post by Envergure on 2009-01-22
GTK:  Base of GNOME and XFCE;  I don't use this one becuase it lacks a "knob" widget.

Qt:  Base of KDE;  Uses a patch-based messaging system rather than the usual callback-based system used in FLTK, GTK, Windows.  Qt also has considerations for multithreading, OpenGL, and sound, and lots of other stuff.

FLTK:  My favourite;  Can be very ugly if used impropperly.  Very simple to learn, lightweight, but it's hard to install the 2.0 version (Ubuntu repos have 1.1 by default).  The documentation is very good.  Download ZynAddSubFX to see FLTK in action.

---

### Post by WitchCraft on 2009-01-22
wxWidgets is the best, technically and legally. 
However, it's not too well documented with tutorials.

---

