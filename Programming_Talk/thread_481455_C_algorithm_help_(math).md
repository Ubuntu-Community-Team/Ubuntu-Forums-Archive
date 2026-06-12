---
title: "C algorithm help (math)"
date: 2007-06-22
forum: Programming Talk
---

### Post by Curtisc on 2007-06-22
I'm having a hard time coming up with an algorithm to do what I need to do, and I thought maybe someone in here might be able to shed some light on it.

What I have is a list of coordinates in 3D space, and at each point is a data value (like temperature).  They are randomly distributed in X and Y, and there are 12 layers in the Z direction (each layer has the same X and Y coordinates).  The list is organized as follows:
x1
y1
z1
x1
y1
z2
...
xn
yn
z12

What I need to be able to do is find the points that are closest to a user-specified line on the Z-plane so that I can interpolate the data values at each point to that line.  Right now, I'm just trying to get orthographic slices to work.  I drew a little diagram to try to get the concept across - the red line is the line I'm trying to interpolate to, the black dots are the points, and the green lines are the within-range threshold.

It's easy enough to find the nodes that are within range, but I'm a little stumped on the interpolation.  Since the grid is not structured, I can't just do a linear interpolation between two nodes.

---

### Post by batrick on 2007-06-22
> **Curtisc said:**
> I'm having a hard time coming up with an algorithm to do what I need to do, and I thought maybe someone in here might be able to shed some light on it.

What I have is a list of coordinates in 3D space, and at each point is a data value (like temperature).  They are randomly distributed in X and Y, and there are 12 layers in the Z direction (each layer has the same X and Y coordinates).  The list is organized as follows:
x1
y1
z1
x1
y1
z2
...
xn
yn
z12

What I need to be able to do is find the points that are closest to a user-specified line on the Z-plane so that I can interpolate the data values at each point to that line.  Right now, I'm just trying to get orthographic slices to work.  I drew a little diagram to try to get the concept across - the red line is the line I'm trying to interpolate to, the black dots are the points, and the green lines are the within-range threshold.

It's easy enough to find the nodes that are within range, but I'm a little stumped on the interpolation.  Since the grid is not structured, I can't just do a linear interpolation between two nodes.

If I understand you problem correctly, what you want to do is take a given line on the Z plane and find the distance points are from that line?

For illustration purposes, I'm thinking you need to find the vector PQ: 
[http://www.mathematics-online.org/inhalt/aussage/aussage514/](http://www.mathematics-online.org/inhalt/aussage/aussage514/)

What you can do is take your line, and find the inverse of the slope to construct a perpendicular line.

y - y1 = m'(x - x1)

You will use the coordinates of your point for y1 and x1. This line forms the shortest distance from your point to your line. Then it is a simple matter of finding where this line intersects with your User's line to get the interpolated point.

---

### Post by Soybean on 2007-06-22
If batrick's advice solves your problem, then I'm completely misinterpreting the issue and you should ignore me. ;) 

I think you may need to clarify the requirements a bit at this part:
> **Curtisc said:**
> What I need to be able to do is find the points that are closest to a user-specified line on the Z-plane so that I can **interpolate the data values at each point to that line**.

Here's the first thing that pops into my head... it's not really interpolation, I don't think, but my vague recollection of interpolation doesn't really apply in a situation like what you're describing:

For each point on the line, calculate the distance to every data point. Calculate a weighted average of the data values, weighted by the inverse of distance.
  (sum of (value / distance)) / (sum of (1 / distance))


Another possibility is to connect the points to the line using those perpendiculars batrick described, and where the perpendicular for a particular point hits your line, assign the point's value to that spot on the line. Then you can interpolate between the assigned spots. This doesn't account for distance, though. That is, a point further from the line has just as much effect on the line's value as a closer point.

I guess another thing you could do, if it makes sense with the nature of your data, is draw a line connecting two points on opposite sides of your target line, then interpolate a value between them at the point where it intersects your line. This doesn't work in real 3d-space, but it works on 2d slices (with some types of data).

But... I have a feeling I'm oversimplifying things. This may take more advanced math than I can remember. I definitely took some linear algebra and calculus courses way back when, but I've managed to block most of it out. :D

---

### Post by Curtisc on 2007-06-22
Thanks guys - I think I do need to clarify what the problem is exactly.  Batrick - it's a little bit more than simply finding the distance from the line, because I need to be able to define points that are on the line and then calculate the data value at that point.  The problem is that my mesh is unstructured, so I don't have two points on either side of the line that, when joined, are perpendicular to my line.  You guys have helped me to clarify the major problem - that is, I don't have discrete points along the line.  I think I'm going to play with the idea of connecting points and finding the intersections.  Since my data isn't "true" 3D, just identical stacked 2D slices, this should give me something

If it helps any, the data is the output from a model simulating the hydrodynamics of a harbour.  The reason I want to be able to do this slicing thing is  to visualize a cross-section of the flow patterns, ideally at an arbitrary angle, but for now I'm just looking at simple x and y direction cuts.  Interpolation in the z-direction (to look at the flow at a specified depth) is really easy because the nodes are all aligned, but the other cases are not so simple.

---

### Post by batrick on 2007-06-22
Depending on how accurate you want these to be, you can do some pretty simple regressions to obtain your interpolated data. If you take points "within range" of your line and construct (visually) a y-x plot of the data, where x is the point on the user line (this value of x is shared with the point being plotted) and y is the "value" of the data (temperature, NOT location). I'm deliberately avoiding the y part of your data points, i.e. how far they are from your user line. If you want to take these into consideration, the math becomes a bit more involved.  After you have this plot, you can form a regression (linear probably). Using this regression, you can take arbitrary x values and find the y (or temperature) at that point on your user line.

At least I think that's what you want to do, apologies if I still don't quite understand the problem.

---

### Post by pbrockway2 on 2007-06-22
You could take the Z-plane containing the line along which you wish to estimate the values and construct the Delaunay triangulation. ([http://en.wikipedia.org/wiki/Delaunay_Triangulation](http://en.wikipedia.org/wiki/Delaunay_Triangulation)).  The points on the line (and all the points on the Z-plane) each lie within one particular triangle and you can estimate the data value as the average of the data values at that triangle's vertices - weighted by the distance to the vertices.

The point about the Delaunay triangulation is that it provides your "grid" with some notion of points that are "neighbours" of one another.  It is these neighbours that participate in the linear interpolation (or some other scheme).

The wikipedia article doesn't bring out the aspect of the Delaunay triangulation that is relevant here: you can tessellate (divide up into polygons) the Z-plane based on the data points you have by associating with each data point all the points of the plane that are closest to that point.  Two data points can be considered neighbours when their associated polygons have a common edge.  Amazingly these neighbouring points and the edges joining them do triangulate the Z-plane.

---

### Post by Curtisc on 2007-06-23
Doh!  pbrockway2, you just reminded me that I have triangles and not just points.  That's why I posted to this forum, I figured there was something simple missing.  I've already got a connectivity table, I just need to use it.

---

### Post by pbrockway2 on 2007-06-23
Assuming I understand what you're trying to do...

(1) Find the intersection of each triangle side with the target line.

For instance if the line has equation x=X (you've drawn it as vertical) and you have a triangle side from (X1,Y1) to (X2,Y2), you would check X1<=X<=X2 and if so calculate the point of intersection as:

(X, Y1 + (X-X1)/(X2-X1) * Y2)

(2) Calculate the interpolated data "value" at this point.  For instance if the two points given above had (actual) values V1 and V2, the calculated value would be V given by:

V = V1 + (X-X1)/(X2-X1) * V2

(3) Use the values V (from step 2) lying along the target line to interpolate the value at any other point along this line.

---

