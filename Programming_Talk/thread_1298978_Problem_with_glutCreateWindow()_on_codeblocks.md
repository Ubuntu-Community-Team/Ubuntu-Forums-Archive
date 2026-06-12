---
title: "Problem with glutCreateWindow() on codeblocks"
date: 2009-10-23
forum: Programming Talk
---

### Post by dsnettleton on 2009-10-23
So I'm new to code::blocks, and this is my first time programming OpenGL in Linux.  I'm familiar with GLUT from using it on Windows, and it's supposed to be cross-platform.  I'm using the Code::Blocks IDE, which I really like so far.  I downloaded and linked all the necessary libraries, but for some reason when I use glutCreateWindow(), it's not really a "window" that's created.  That is to say, my OpenGL scene is being drawn, but it's just sort of floating on its own.  There's a spot for it on the taskbar, so I can minimize and close it using that, but there's no actual frame to the window.  I tried using the Code::Blocks OpenGL wizard to see if I was doing something wrong, and the exact same thing happens.  What can I do to solve this?

Thanks in advance,
--D. Scott Nettleton

---

### Post by Zugzwang on 2009-10-23
Have you tried turning off the desktop 3d effects? That's a common cause for such problems and if that's the reason, it is not really a problem in your program.

---

### Post by dsnettleton on 2009-10-23
Brilliant.  I have Compiz-Switch because I turn desktop effects on and off for so many things, and I still didn't think to try it out.  This problem won't crop up with my final release, will it?

---

### Post by Can+~ on 2009-10-23
Actually, yes.

But compiz usually manages better fullscreen things, so setting it to fullscreen solves the issue (at least for my driver/setting).

---

