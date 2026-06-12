---
title: "OpenGL"
date: 2006-06-16
forum: Programming Talk
---

### Post by tehDeuce on 2006-06-16
Hey.  I want to try out OpenGL programming, but I can't figure out what packages I need to install to get started.  What do I need to do to get an environment set up where I can develop OpenGL applications (in C or C++ please.  While I love Python, it isn't really fitting for what I want to do)?
Thanks.

---

### Post by Scratty on 2006-06-17
I think you need something like the mesa-packages (libgl1-mesa*), freeglut (for ui and such) (freeglut3*) and the opengl utility library GLU (libglu1-mesa*). Be sure to get those packages that end with "-dev", these are needed for development in particular. Additionally you may need the right opengl stuff for you gfx hardware, which in my case is nvidia-glx-legacy and nvidia-glx-legacy-dev (or nvidia-glx*, legacy is for older cards).

I hope I haven't lied too much.

---

### Post by gord on 2006-06-17
you will also want sdl and its dev packages to handle your opengl window

---

### Post by tehDeuce on 2006-06-17
Thanks.  Does anyone know where I could get the tk library?  According to my tutorial "This library is not to be confused with Tk of Tcl/Tk." so I'm not too sure of what package to get.

---

