---
title: "openGL"
date: 2005-02-28
forum: Programming Talk
---

### Post by chillysoup on 2005-02-28
Hey all I'm new here

I recently started using Ubuntulinux (came from fedora cora) and I want to try and program openGL, which is where I run into a problem.
I have installed what I think I need of glut and mesa by selecting packages in synaptic, but I still get an error when I try to compile:
/usr/bin/ld: cannot find -libGL
and same with -libGLU and -lXu

I first tried with -lMesaGL and such, but understand that they are not called that here. 
$ whereis libGL => libGL: /usr/lib/libGL.a /usr/lib/libGL.so
So it should be able to find it ?

I'm pretty much lost here, I'd appreciate if someone could give me some pointers. I am starting out with openGL and don't know much about it

---

### Post by Daniel G. Taylor on 2005-03-01
You might try compiling with -lGL and -lGLU instead of -libGL (or does that do the same thing? I'm stuck on Windows right now).

Here is something I googled up real fast that may help you:
[http://www.ece.eps.hw.ac.uk/~dml/cgonline/hyper00/openglcomp.html](http://www.ece.eps.hw.ac.uk/~dml/cgonline/hyper00/openglcomp.html)

---

### Post by chillysoup on 2005-03-02
Thanks!
I got it working now, going:
-lglut -lGL -lGLU -L/usr/X11R6/lib -lXmu -lX11 -lXi -lm

---

