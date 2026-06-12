---
title: "function that calculate distance"
date: 2009-02-09
forum: Programming Talk
---

### Post by fokuslee on 2009-02-09
Hi all 
This is a 2d problem, 

I need a function that calculate distance given 2 end points of the line, and a 3rd point not on the line.  
my approach is from a vector (C) from given line endpoint to the 3rd point then take a dot product of (C) and the unit vector of given line, then find the length of (C) and solve distance with pythagorean theorem.  

This is pretty lengthy, is there a faster way to do this? 
b/c i will have to do this around 100K times.

---

### Post by pp. on 2009-02-09
sqrt( (x2-x1)**2 + (y2-y1)**2 ) ?

---

### Post by fokuslee on 2009-02-09
I need to calculate the distance between a point and a line.  
not 2 points on a straight line.  Sorry for not being clear

---

### Post by matteojg on 2009-02-09
I'm not sure I understand this problem.

You are given the coordinates of two points A and B ( which of course can define a line ), right?

Then you are given a third point C not on the line AB.

What exactly is the distance you are trying to find?

---

### Post by PythonPower on 2009-02-09
I've always been better at "more abstract" maths but here's a method:

Instead of treating the first two points as a line segment, treat them as a line (infinite length). So your line's gradient is m and it's y-axis intercept c. And the point is at (x, y).

Then:
n = -1/m
d = y-nx

And now you have the equation of the perpendicular line that goes through the point (x, y). Check to see where it intersects with your line segment. If it doesn't intersect, try either end-point of the segment.

Either way you can get the second point. Then just use the Pythagorean theorem.

I should note, I am not very confident in what I have just said - check it! I need sleep... :P

---

### Post by Can+~ on 2009-02-09
There's a simple equation for the distance from a point to a line:

(p, q) being the outside point.

Ax + By + C = 0 beign the equation that describes de line. The distance between the two is:

| Ap + Bq + C |
sqrt(A^2 + B^2)

From there, you can work the solution.

---

### Post by discodover on 2009-02-09
Check this link out.  Seems straight forward to me.
[http://local.wasp.uwa.edu.au/~pbourke/geometry/pointline/]("http://local.wasp.uwa.edu.au/~pbourke/geometry/pointline/")

---

### Post by fokuslee on 2009-02-09
Thanks for all of your replies, so many cool way to do it. 
Since my problem is set up basically with 3 points
i have taken this approach
[http://www.worsleyschool.net/science/files/linepoint/method3.html](http://www.worsleyschool.net/science/files/linepoint/method3.html)
[http://mathdemo.gcsu.edu/mathdemos/trianglearea/trianglearea.html](http://mathdemo.gcsu.edu/mathdemos/trianglearea/trianglearea.html)
Basically, use a linear combination of trapezoid to get triangle area then use a = 0.5 bh to get height (distance)

---

### Post by Krupski on 2009-02-09
> **fokuslee said:**
> Hi all 
This is a 2d problem, 

I need a function that calculate distance given 2 end points of the line, and a 3rd point not on the line.  
my approach is from a vector (C) from given line endpoint to the 3rd point then take a dot product of (C) and the unit vector of given line, then find the length of (C) and solve distance with pythagorean theorem.  

This is pretty lengthy, is there a faster way to do this? 
b/c i will have to do this around 100K times.

What you are dealing with is a simple triangle.

And, Pythagoras will only work on right triangles.

All you have to do is imagine the two "missing" vectors and solve the resulting triangle.

---

### Post by haemulon on 2009-02-10
I didn't quite understand the problem as stated.

---

### Post by Reiger on 2009-02-10
> **Krupski said:**
> What you are dealing with is a simple triangle.

And, Pythagoras will only work on right triangles.

All you have to do is imagine the two "missing" vectors and solve the resulting triangle.

Yup. Consider the line AB with length z, then imagine a point on that line S such that AS = t and SB = z-t and that SC = h (height of the triangle).

You can now solve for h^2 = (AC)^2 - t^2 and h^2 = (BC)^2 - (AB-t)^2.

Which equates to: 0 = (AC)^2 - (BC)^2 - (AB)^2 + 2(ABt). Find t. Then consider that if you're not dealing with an infite line AB but rather with a segment, meaning that the distance to C is (AC) if t is negative, and (BC) if t is larger than (AB). In all other cases, it's h.

---

