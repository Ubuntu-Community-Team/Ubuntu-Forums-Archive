---
title: "Polygonal 2D map loading/saving for a game, where should I start?"
date: 2008-11-20
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-20
If I wanted a polygonal 2D map system for a game, how should I do it?

I just want to save/load coordinates of triangles. Like a file containing information about polygons.


Should I use linked lists? Arrays? Using a 3D map engine but ignoring z coordinates? Or how about SVG images?

I'm lost. Can't keep my mind clear. Give me some suggestions on how to do this.

Edit: Always forgot, it's C.

---

### Post by Sacrifice on 2008-11-20
You could use the arrays of C++,  they can be made with two dimenisons.

Or you could use the matrixes in Perl.

---

### Post by crazyfuturamanoob on 2008-11-20
> **Sacrifice said:**
> You could use the arrays of C++,  they can be made with two dimenisons.

Or you could use the matrixes in Perl.

I use C, not C++. And as I have heard, implementing C++ into C is nasty.

And I use this like structures for coordinates:
```

// point
typedef struct
{
    float x, y;
} point;

// line
typedef struct
{
    point a, b;
} line;

// triangle
typedef struct
{
    point a, b, c;
} triangle;
```
That's all I got so far.

---

### Post by Tony Flury on 2008-11-20
when you say a polygonal 2D map, what exactly do you mean ?

your data structures are only ever going to build a multitude of triangles on a completely flat surface - and if all you have is a flat surface - why bother with triangles - why not just map a big square with a texture.

If you want height information, then you have to define your point structure with three elements (x,y,z) - and then uses your graphics engine to translate the 3D map into 2D graphics, based on the viewing position and angle.

---

### Post by Reiger on 2008-11-20
Without knowing any real C:

(a) Map is a series of fixed-length triangles, by induction from...
(b) Triangle is a series of fixed-length coordinates, by induction from...
(c) Coordinate is a series of fixed-length float values.

So all we need is either a prefix or a suffix to distinguish between a point on its own, a line consisting of 2 points, or a triangle consisting of 3 points. If these are all the options you got, it's a simple as 1 byte prefix which indicates the number of bytes ahead to read as one <type> struct.

---

### Post by crazyfuturamanoob on 2008-11-21
How about modeling the 2D polygon map with Blender 3D, then load it in game, and ignore z values?

---

