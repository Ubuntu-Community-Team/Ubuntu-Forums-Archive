---
title: "OpenGL"
date: 2008-12-09
forum: Programming Talk
---

### Post by supernova1 on 2008-12-09
I would like to start programming OpenGl apps in C and eventually work on some game programming.  I haven't found any linux oriented opengl web sites with good examples.  Does anyone know any good books, or any good web sites?  People keep recommending [http://nehe.gamedev.net/](http://nehe.gamedev.net/), everything on this site is windows oriented, unless I am missing something.

Thanks,

David

---

### Post by snova on 2008-12-09
OpenGL is OpenGL no matter where you use it. The biggest differences you will encounter between platforms while you begin will be the method by which you bind OpenGL calls to a window, which is necessarily different. For example, Windows uses WGL, X uses XGL, and so on. GLUT provides an abstration layer around them, though.

I have The OpenGL Superbible on my bookshelf, which I have no reason to dislike... It seems quite accessible.

---

### Post by supernova1 on 2008-12-09
I realise that OpenGL is OpenGL, but I learn by code examples, and it is really hard to find all of the Windows specific code and pull it out and replace with linux specific code.  All of the examples out there are windows specific, it would be nice to have something linux specific.  Thanks for the book though, I will have to check that out.  If anyone else has any other book, or web resources that are good, let me know.

Thanks,

David

---

### Post by snova on 2008-12-09
Well, if you want Linux specific, look up XGL (which actually would be portable to other platforms using X).

You'd probably be better staying portable, though. Find a cross-platform widget toolkit that has OpenGL capabilities.

---

### Post by e^(i*pi) on 2008-12-10
I do all of my OpenGL programming using GLUT (the OpenGL Utility Toolkit).  GLUT provides sort of a lowest common denominator, giving you access to the capabilities that any windowing system should have, but none of their specific features.  It might not be optimal if you are wanting to do Linux programming and Linux only, but you should be able to find a good deal of code built using GLUT, all of which should work under Linux (unless the author includes some windows specific header file).  If you are interested in seeing what is possible with it, there is a program you can download in the repos call Celestia.  It is listed under education and comes in two versions, one using the Gnome windowing utilities and the other using GLUT.  It is a cool program and it really shows what GLUT can do.

---

### Post by zomtec on 2008-12-10
[http://nehe.gamedev.net/is](http://nehe.gamedev.net/is) a very good starting point.
Most examples have a linux/SDL download link at the bottom of the page.

SDL provides a simple interface for OpenGL + it provides platform independant window/event handling.

---

### Post by Kazade on 2008-12-10
Hey,

I'm actually one of the guys running NeHe. I would recommend you take a look at the new lessons which use SDL: [http://nehe.gamedev.net/wiki/NewLessons.ashx](http://nehe.gamedev.net/wiki/NewLessons.ashx)

The old lessons are really dated now, and some of them won't compile on a modern compiler. The later ones are OK though.

We do plan to extend those new lessons and migrate them to OpenGL 3.0, at the moment I'm snowed under writing an OpenGL book, but expect some new tutorials around March time. If you have any questions just post on the NeHe forum, I also hover around here A LOT! ;)

Luke

---

### Post by supernova1 on 2008-12-10
Thanks everyone, I am sure this will help me get started.

---

