---
title: "Drawing a line in C++"
date: 2007-12-08
forum: Programming Talk
---

### Post by joebanana on 2007-12-08
I have a file with x,y coordinates and I need to draw a picture with simple lines. I know how to do it in Java but I would like to use C++ because I am also using dijkstra algorithm and it would be faster. I only programmed in console till now. Can someone point me to where to start.

---

### Post by rzrgenesys187 on 2007-12-08
Good thread, i would like to know this as well

---

### Post by subs on 2007-12-08
this is where i learnt it from

> [http://www.glenmccl.com/virt_cmp.htm](http://www.glenmccl.com/virt_cmp.htm)

---

### Post by joebanana on 2007-12-08
Tried the program and I dont see any lines just a text output :)

---

### Post by CptPicard on 2007-12-08
My own impression is that a properly implemented Dijkstra is not much slower in Java than in C++. Actually, if keep a bit of track of how many objects you spawn and make sure your memory management time costs don't get out of hand, JIT-compiled Java doesn't lose to C++ substantially even in heavy algorithms. I would in particular recommend using just a table-implemented binary heap instead of something like a Fibonacci heap.

The performance gain you can get from compiled languages these days comes from lower-level tweaks and compiler optimizations, not general running speed.

And also of course the line-drawing is not the bottleneck here, but I guess you already got that ;)

---

### Post by xtacocorex on 2007-12-08
I would use 2D SDL and would send you the link to the ubuntu game programming wiki, but have forgotten it.  There are tutorials on 2D and 3D rendering.

---

