---
title: "Please help me get started with a C++ IDE"
date: 2005-07-01
forum: Programming Talk
---

### Post by leohart on 2005-07-01
Hi everyone,

I have been trying unsuccessfully to find a C++ IDE. It turns out I can use g++ to compile and run my little HelloWorld.cpp.

However, when I use KDevelop and/or Anjuta, it just keeps asking for a make file or says some weird errors and cannot build the executable file. T-T

What am I suppose to do? I think I need help on these stuff:
First, what is a make file? 
How do I build/code it in either KDevelop or Anjuta?

Or

A step-2-step guide to compile my HelloWorld.cpp in an IDE.

Thanks guys.

---

### Post by trivialpackets on 2005-07-01
[QUOTE=leohart]Hi everyone,

I have been trying unsuccessfully to find a C++ IDE. It turns out I can use g++ to compile and run my little HelloWorld.cpp.

However, when I use KDevelop and/or Anjuta, it just keeps asking for a make file or says some weird errors and cannot build the executable file. T-T

What am I suppose to do? I think I need help on these stuff:
First, what is a make file? 
How do I build/code it in either KDevelop or Anjuta?

Or

A step-2-step guide to compile my HelloWorld.cpp in an IDE.

Thanks guys.[/QUOTE]
 I've had this issue when trying to compile a workspace on anjuta, but if I just choose to open file, and open the file, then that seems to compile without issue.  That being said, my own personal preference is to open the file and compile with the command prompt.   I do use Jedit/anjuta/kdevelop or whatever to do most of my editing, depending upon what I'm working on for the searching tools, but I do my compiling from command prompt, as I"m currently learning fortran too and use it, so I just kind of do it with all.

---

### Post by trivialpackets on 2005-07-01
Another thing that I've found with anjuta, make sure that you have of course the build-essential, but also I needed to install libtool in order for my projects to build properly.  Good luck.

---

### Post by odrop on 2005-07-02
With KDevelop, the probably easiest road you can follow is to load up KDevelop->Click on Project in the menu bar->Click on New Project then step through that wizard.

(To give you a little more boost, if you just have some simple code, Select C++ in the list, then Simple Hello World Program, file out a name for it, and just click Next for the next few screens and then Finish, what it does then is create a bunch of files you dont need to worrie about now, but you get everything you need to start developing inside KDevelop.  Then if you want, cut and paste your other source file inside the one it presents you with. Click on Execute and you're off and running.)

Also, another thing to watch out for, if you have Kdevelop 3.2, you'll need libtool installed, otherwise you might get an error when you try to compile.

You might also want to read the help file for KDevelop, its documentation is pretty good and explains a lot of your questions.

---

### Post by leohart on 2005-07-02
Thanks for the libtool tips. I would try that out. Hopefully I got it to run correctly.

---

