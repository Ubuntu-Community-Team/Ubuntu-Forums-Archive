---
title: "circular arc approximating polylines"
date: 2008-10-09
forum: Programming Talk
---

### Post by fokuslee on 2008-10-09
I have small line segments approximating circular arcs but they are just small segments of straight lines.  Is there an alogorithm to construct cirular arcs (with angle and radius) from these collection of small segments? 
I take any language or just the algorithm itself.  
But python or VB is a plus.
Hopefully someone find this is an insteresting problem :) 
Thanks a bunch!!!

---

### Post by stroyan on 2008-10-09
I presume you want to match a series of line segments to a single
circular arc.  (Otherwise you could just exactly match each line segment
to one circular arc with a really big radius. ;-) )

That sounds like a job for a least squares fit algorithm.
There is a general page on it at [http://en.wikipedia.org/wiki/Least_squares](http://en.wikipedia.org/wiki/Least_squares) .

You could pin the ends of the arc at the two most distant points and
then just solve for the position of the arc's center along the line that
is equidistant between the end points.  The value to minimize could
be the difference between the radius and the distance from the center
to each vertex.  There is support for solving least squares fit in the
python-scientific package.

---

### Post by fokuslee on 2008-10-09
I understand the part of finding the center along a line equal distant to the vertex but i can not minimize the difference between (center to vertex) and radius since radius is unknown.  
whoever i maybe able to use circles general form as model function and try to find coefficients such that it best approximate the collection of line end points (line segments that make up the circle) 
Also in the collection i have genuine lines two like approximate arcs and true line segments, i will need to somehow distinguish between those that make up the arc and those true lines.
Any thought on this?

---

