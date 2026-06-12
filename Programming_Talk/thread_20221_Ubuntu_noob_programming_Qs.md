---
title: "Ubuntu noob programming Qs"
date: 2005-03-15
forum: Programming Talk
---

### Post by weresheep on 2005-03-15
Hi all,

First post, be gentle  :)

I am interested in doing some graphics programming and am wondering what would be the bast way of doing this on Ubuntu GNU/Linux (or indeed GNU/Linux in general)?

Let me explain a bit.

I am a Software Engineer by profession and know my way around C/C++ but I am fairly new to GNU/Linux. The software I do at work is mainly system software. Back in my University days I took a couple of "computer graphics in C" classes and had a lot of fun making simple drawing programs in DOS.

Ideally, I'd like a simple, lightweight way to pop a window on the screen and then just draw into it using simple primitives. I've had a quick look at GTK+ and it looks quite nice, especially as it fits well with a C style of programming (I prefer C to C++).

Is GTK+ well suited to this sort of task?
If so, how do I go about getting a GTK+ development system on my Ubuntu set up?

Many thanks in advance for any help, advice or pointers. I'd really like to be able to just play around with programming again as opposed to it being 'just' a job.

-weresheep

---

### Post by sas on 2005-03-15
[QUOTE=weresheep]Hi all,

First post, be gentle  :)

I am interested in doing some graphics programming and am wondering what would be the bast way of doing this on Ubuntu GNU/Linux (or indeed GNU/Linux in general)?

Let me explain a bit.

I am a Software Engineer by profession and know my way around C/C++ but I am fairly new to GNU/Linux. The software I do at work is mainly system software. Back in my University days I took a couple of "computer graphics in C" classes and had a lot of fun making simple drawing programs in DOS.

Ideally, I'd like a simple, lightweight way to pop a window on the screen and then just draw into it using simple primitives. I've had a quick look at GTK+ and it looks quite nice, especially as it fits well with a C style of programming (I prefer C to C++).

Is GTK+ well suited to this sort of task?
If so, how do I go about getting a GTK+ development system on my Ubuntu set up?

Many thanks in advance for any help, advice or pointers. I'd really like to be able to just play around with programming again as opposed to it being 'just' a job.

-weresheep[/QUOTE]
 a text editor to code, gcc to compile and glade to build the UI is what most people are using afaik

---

### Post by toojays on 2005-03-15
I imagine GTK+ is quite fine for basic drawing stuff; after all, it was originally made to support the Gimp drawing program. Another library which came to mind is [SDL](http://www.libsdl.org/). [This tutorial](http://andrew.textux.com/tutorials/tut1/tutorial1.html) (which I haven't tried) shows how you can setup a surface to draw on. There are other tutorials on the SDL website.

When it comes to setting up a development system on Ubuntu, the first thing you need to do is install the "build-essential" package. This will install the GCC compiler toolchain. After that, you need to install the development version of whatever libraries you are using. So for instance, if you are using GTK+, you need to install libgtk2.0-dev. This will install the headers and the static library for the corresponding package.

Where you go from there is a matter of personal preference. If you prefer to use an IDE, Eclipse, Ajunta and KDevelop are all supposed to be good. I prefer to use Emacs and GNU Make.

Welcome and good luck!

---

### Post by weresheep on 2005-03-15
Hi, thanks for the replies.

sas:
Sorry if I wasn't clear, I wasn't asking how to get a basic development environment set up, it was more the specific packages for the particular GUI library (GTK+ etc.). 

toojays:
"libgtk2.0-dev"
Ah, excellent, that sounds like the right thing for me. As for IDE, I'm a VIM man myself :)

Thanks again, guys.
-weresheep

---

