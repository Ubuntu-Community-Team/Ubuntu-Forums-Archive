---
title: "Opengl: 3 coordinates or 4?"
date: 2009-07-23
forum: Programming Talk
---

### Post by Hospadar on 2009-07-23
I'm writing a little test game to sharpen up some skills, it's written in python and opengl.

The question is whether it's faster to use 3-coordinate vertex data, or 4-coordinate (homogeneous) data.  It seems to me like if I just send in 3 coordinates, opengl will just add the 4th coord (w) and not worry about whether or not things need to be divided by w.  Furthermore it seems like less data actually needs to get sent to the GPU that way.

I'm not actually using the 4th point (it's always set to one) but the little point class I made to do transformations that need to be done outside of opengl (it's basically a numpy.ndarray wrapper) stores the w-coord so I can do full matrix-style transformations.

Bottom line, it's trivial for me to do things either way, but I'm just wondering if anyone knows for sure which would be faster.

Also note, I'm using vertex arrays for everything, so with 3-coord data all my arrays will be smaller too, but I'm more concerned with speed.

---

### Post by stroyan on 2009-07-23
As a rule, sending less data will be faster.
It won't rule out perspective division, as any initalW coordinate could result in a variable value after transformation.
But it will be able to reduce data transfer and memory accesses.
That may make your program faster.
There may be some other bottleneck such as rasterization that actually produces the same performance for either 3 or 4 coordinates.

---

### Post by efikkan on 2009-07-23
The forth coodinate is used for rotation around three axis and other advanced matrix manipulations. Normally the forth coordinate is not required in vertex coordinates.

---

### Post by Can+~ on 2009-07-23
Another thing, take a look at [Soya3d]("http://home.gna.org/oomadness/en/soya3d/index.html") (Or the branched project: [Pysoy]("http://www.pysoy.org/browser")). It's an Object Oriented wrapper for OpenGL for python (and OpenAL, SDL, etc).

---

