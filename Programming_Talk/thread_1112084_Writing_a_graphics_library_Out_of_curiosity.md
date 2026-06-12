---
title: "Writing a graphics library? Out of curiosity"
date: 2009-03-31
forum: Programming Talk
---

### Post by 2weird on 2009-03-31
I am just curious about how people go about writing a graphics library. There are many implementations of OpenGL that provide a high-level interface to graphics programming, I would like to know how these are implemented, how are all the low level interactions with graphics cards etc. done? Does Linux have a built in library that allows me to do low-level stuff (in C possibly)?

I have heard of svgalib, is it used to implement GLs or is there anything lower?

I am just a geek with a lot of time, but I don't know where to start, so the help/suggestions is much appreciated.

---

### Post by 2weird on 2009-04-10
bump

---

### Post by hessiess on 2009-04-10
On Linux, Interfacing with the graphics card is done using OpenGL. The implementation of OpenGL is provided by the graphics drivers, which are almost always propiatery. If you want to learn how drivers work, download one of the open-source ones and dig through the code ;).

A graphics lib is a collection of features built on top of this to make it easier to do some spasific thing. For example, OpenGL only provides a method for drawing triangles, and matracies for transforming them. If you wanted animated scene nodes for example, you would implement a class which stores multiple `states' of a mesh (vertex animation), or a system to calculate wated bone transformations. this would then output a different mesh depending on the frame, and you can pass this to OpenGL to render it.

Quad-Ren for example, is a lib to provide a resolution independent, hardware accelerated API for drawing bitmap images without the complexity of using OpenGL directilly. It also has a number of features targeted at game dev, frame based animations and (in the future) bezier curve based collision detection for example.

---

### Post by skullmunky on 2009-04-10
OH wow, I'm going to go and check out Quad-Ren, that looks terrific.

---

### Post by soltanis on 2009-04-10
Unfortunately, most open source drivers suck (they don't really implement 3D, and they're much slower than propriatary ones)

---

### Post by JFASI on 2009-04-10
I'm doing just this, although it seems my library is a little deeper than what you want to do. Here are some details: 

I'm doing everything in CPU, just cuz I want to have some fun with it, so all my matrix libraries and lighting is custom. 

I'm using SDL for pixel-level access to the screen as well as for input.

---

