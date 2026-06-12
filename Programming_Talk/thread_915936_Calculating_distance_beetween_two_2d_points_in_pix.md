---
title: "Calculating distance beetween two 2d points in pixels?"
date: 2008-09-10
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-10
So how can I calculate distance beetween two 2d points in python? :confused:

---

### Post by Reiger on 2008-09-10
Call me stupid but when did good ole' Pythagoras ever fail in multi-dimensional spaces?
In 2D:
Given two points (x0,y0) and (x1,y1):
sqrt((x0-x1)^2 + (y0-y1)^2)

Assuming the square root function is directly available as sqrt in Python.

---

### Post by cmat on 2008-09-10
Close but to use exponents in Python, they must be in the form "x ** y".

To use the "sqrt()" function you need to "import math".

```
import math

x1 = 56.0
y1 = 23.0
x2 = 120.0
y2 = -234.0

print math.sqrt( ( x1-x2 )**2 + ( y1-y2 )**2 )

```

---

### Post by Reiger on 2008-09-10
Yeah well, actually I don't know Python. :D Just pointing out there exists that famous formula ;)

---

### Post by dribeas on 2008-09-10
> **crazyfuturamanoob said:**
> So how can I calculate distance beetween two 2d points in python? :confused:

What is your definition of 'distance in pixels'? The distance given before is Cartesian distance, which is common life distance, but there are others, as Manhattan distance (sum of horizontal plus vertical distance (minimum number of pixels you must step over to get from point a to point be by crossing only sides and not diagonals)...

Manhattan_distance = ( x2 - x1 ) + ( y2 - y1 )

---

### Post by jimi_hendrix on 2008-09-10
this might be what your all saying and im missing it but i think theres a postulate that says the distance between two points is the difference is the absolute value of the difference in their coordinat

---

### Post by Lux Perpetua on 2008-09-11
> **dribeas said:**
> What is your definition of 'distance in pixels'? The distance given before is Cartesian distance, which is common life distance, but there are others, as Manhattan distance (sum of horizontal plus vertical distance (minimum number of pixels you must step over to get from point a to point be by crossing only sides and not diagonals)...

Manhattan_distance = ( x2 - x1 ) + ( y2 - y1 )
More accurately, |x2 - x1| + |y2 - y1| (note absolute values).

---

### Post by dribeas on 2008-09-11
> **Lux Perpetua said:**
> More accurately, |x2 - x1| + |y2 - y1| (note absolute values).

Right :)

---

### Post by maximinus_uk on 2008-09-11
The distance from pixel(a,b) to pixel(c,d) *in pixels* is the modulus of the larger number of either (a-c) or (b-d); subtract 2 from this number if you wish to exclude the start and end points.

This is to do with how pixels are rendered on a grid. Agreed, it differs from pythag!

I first came across this when using Bresenhams algorithm ([http://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm]("http://en.wikipedia.org/wiki/Bresenham%27s_line_algorithm")) many many years ago. We were calculating how pixels would need to be rendered on a given line; turns out the answer is trivial to calculate - and you don´t need pythag.

---

