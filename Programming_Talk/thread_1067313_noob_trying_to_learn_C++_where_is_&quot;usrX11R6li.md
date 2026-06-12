---
title: "noob trying to learn C++: where is &quot;/usr/X11R6/lib&quot; ??"
date: 2009-02-11
forum: Programming Talk
---

### Post by lethalfang on 2009-02-11
I'm auditing a c++ programming course. The course is based on MS visual studio, but I want to do things in linux terminal, so I've a few extra things to figure out. 

One program requires a Xwin library in /usr/X11R6/lib, as in:
g++ blah-blah-blah...... -L /usr/X11R6/lib -lX11

But /usr/X11R6/lib is nowhere to be found in ubuntu 8.10. 

Where is that library?
If it's already in the system, where do I find it?

Thanks in advance!

---

### Post by AliTabuger7 on 2009-02-11
I'm guessing you need to install a dev package, but i don't know which one.

---

### Post by lensman3 on 2009-02-11
Find the file "libX11*".  I think you could drop the /usr/X11... off the command line because the linker will find it in either /usr/lib or /usr/lib64 (for 64 bit systems).  That library is the X11 link library and is already in use by the GUI on your system.

---

### Post by Sorivenul on 2009-02-11
So you're trying to develop a program based on Xlib? AFAIK, you will need the "libx11-dev" package, available in the repositories.

---

### Post by lethalfang on 2009-02-11
Thanks! You guys are right!
Those library files are now in /usr/lib, and since that's the ubuntu default, I can drop the "-L /usr/X11R6/lib" line. 
:guitar:

---

