---
title: "2D/3D Graphics in C?"
date: 2009-08-28
forum: Programming Talk
---

### Post by sprince09 on 2009-08-28
Hi guys, I've got some C code I've written to perform particle swarm optimizations on a set of functions I don't like solving analytically. I'd like to be able to visualize the particles in the swarm moving my function space (either a 2D line or a 3D surface).

In the past, I've used a hack-ish method where I just fork a new process and make a system call to gnuplot or an octave script which handles my plotting.

```

...
...

fork();
if(pid == 0){
    system("octave -qf my-plotting-script.m");
    exit(0);
}
...
...

```

There's a lot of overhead and other junk that I really don't care for with this method, so I'd like to just be able to spawn my graphs natively in my C code. I've looked into SDL but haven't been able to find a good C tutorial for it, and I'm a bit lost with it.

Are there other 2D/3D graphics libraries (or SDL tutorials) out there that I should know about? Or even better, some native C plotting libraries?

---

### Post by jimi_hendrix on 2009-08-28
one may always use opengl, sdl is good if you just need rectangles

---

### Post by shadylookin on 2009-08-28
I would use opengl. Most tutorials however are in c++ even though the library itself is in c. I'm sure if you have your heart set on c and don't want to use c++ there's a tutorial out there somewhere for you.

---

### Post by Can+~ on 2009-08-28
I wouldn't write a whole library for OpenGL for a single task, I bet this has been solved multiple times, something like [PlPlot]("http://plplot.sourceforge.net/").

---

### Post by hessiess on 2009-08-29
Don't use SDL on its own without OpenGL as its resolution dependent, which is bad considering the highly variable monitor resolutions from one comp to another. Using OpenGL solves this problem but it is very low level, so you could use Irrlicht(Cross platform 3D graphics engine), which is also perfectly capable of 2D rendering(2D is a subset of 3D).

---

### Post by sprince09 on 2009-08-31
Well, I've ended up using the SDL graphics package (libsdl-gfx1.2-dev package for anyone who's interested), and at least for just drawing a quick and dirty 2D graph (at exactly 1 resolution), it works nice. 

I've also discovered SciPy for python in my search, which has a pretty complete graphing module, but I don't think python will be able to run at the same speed my C code is at, and that's a bit of an issue in this application. 

PLPlot looks intruiging, I'll see what that has to offer, and if it doesn't work out, I guess I'm using opengl.

Thanks all

** Edit **
After reading through the documentation for PLPlot, it looks like that's exactly what I need, thanks for the suggestion!

---

