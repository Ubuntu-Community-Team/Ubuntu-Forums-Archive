---
title: "Using GLew in Intrepid Ibex"
date: 2008-12-05
forum: Programming Talk
---

### Post by sickasabat on 2008-12-05
I am trying to run a opengl demo program from the internet. But when I compile I get this error:

GL/GLew.h: No such file or directory

I have tried compiling with:

gcc demo.c -o demo `sdl-config --cflags --libs` -lGL -lGLEW

gcc demo.c -o demo `sdl-config --cflags --libs` -lGL -lGLew

gcc demo.c -o demo `sdl-config --cflags --libs` -lGLEW

gcc demo.c -o demo `sdl-config --cflags --libs` -lGLew

I have the libglew-dev package installed and I can't find any explanation on the internet. Can someone help me?

---

### Post by Kazade on 2008-12-05
glew.h is lower case. I just installed the libglew-dev package to check. Change the #include statement to have a lower case GL in glew.h.

---

