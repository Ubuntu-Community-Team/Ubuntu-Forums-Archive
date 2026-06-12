---
title: "Basic screen graphics under C++"
date: 2010-03-27
forum: Programming Talk
---

### Post by gnometorule on 2010-03-27
Just to learn about it, I would like to write a simple package that implements simple geometric functions to be drawn on the screen, such as

class point
line(point a, point b)
triangle(point a, point b, point c), 
etc.

Could anyone point me in the right direction where to read about this, or what keyword I should google? Working under Gnome in Ubuntu 9.10, using ISO C++ with g++. 

If it is impossible/hard to draw straight on the screen, opening a 

window(point base, int horizontal, int vertical),

then draw within that windows would be fine too (goes w/o saying, all fct names are fcts I intend to write once ready).

Many thanks!

---

### Post by heikaman on 2010-03-27
I think you should start here [http://nehe.gamedev.net/]("http://nehe.gamedev.net/")

---

### Post by TheLions on 2010-03-27
> **gnometorule said:**
> Just to learn about it, I would like to write a simple package that implements simple geometric functions to be drawn on the screen, such as

class point
line(point a, point b)
triangle(point a, point b, point c), 
etc.

Could anyone point me in the right direction where to read about this, or what keyword I should google? Working under Gnome in Ubuntu 9.10, using ISO C++ with g++. 

If it is impossible/hard to draw straight on the screen, opening a 

window(point base, int horizontal, int vertical),

then draw within that windows would be fine too (goes w/o saying, all fct names are fcts I intend to write once ready).

Many thanks!

you should try glut

---

### Post by gnometorule on 2010-03-27
From a quick check, Glut/OpenGL look very good and might be exactly what I was looking for (will take me a while to read through). I'll keep this open a little longer in case anyone has other comments, but tyvm to you two already.

---

### Post by pbrane on 2010-03-28
For something a little more light weight that openGL or could try looking into *cairo*. Cairo support is integrated into GTK+ starting with version 2.8.
Cairo is a 2D graphics library. For C++ use gtkmm and cairomm.

---

### Post by gnometorule on 2010-03-28
Having played a bit with

[http://nehe.gamedev.net/lesson.asp?index=01](http://nehe.gamedev.net/lesson.asp?index=01),

I HIGHLY suggest you don't waste your time on it. The 'hello world' program (about a compact 5+ pages long which eases hunting down errors) produces about a page full of error messages when compiled; mostly, I think, lacking #defines. I included <GL/freeglut.h> and compiled with -lglut, which works as I've played successfully using other source codes. But this page, written for VC++ 6 and apparently closely tied to some of its or Windows innards, is pretty much totally useless for Unix/Ubuntu.

I've made some progress using

[http://www.lighthouse3d.com/opengl/glut/index.php?1](http://www.lighthouse3d.com/opengl/glut/index.php?1)

 - written for Windows environment too, but so far easily used in Ubuntu. Code compiles and, mostly, does what is promised - although not quite, already in lesson 2. I realize that Khronos claims to maintain glut, but not documentation, it seems. 

If anyone has another good source that actually helps with Ubuntu directly, that'd be great.

---

