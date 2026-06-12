---
title: "Triangles displayed in parallel projection"
date: 2012-07-30
forum: Programming Talk
---

### Post by emiller12345 on 2012-07-30
Dos any body know if there is there a way to quickly sort a series of n triangles so that when drawn in that order, they will appear to have the correct depth, assuming none of the triangles overlap?

Any references would be a great help.

---

### Post by trent.josephsen on 2012-07-30
I'm confused by the phrase "appear to have the correct depth". Could you rephrase perhaps?

---

### Post by emiller12345 on 2012-07-30
> **trent.josephsen said:**
> I'm confused by the phrase "appear to have the correct depth". Could you rephrase perhaps?

Yeah, sorry.  I'm trying to determine which triangles will appear in front of which triangles, from a single perspective.  So lets say I have a set of triangles, and I already know these triangles do not intersect, how would I go about sorting them.

i.e.
```

pt_1a = {0,0,1}
pt_1b = {0.5,0,0.75}
pt_1c = {0,0.5,0.75}
trianlge1 = {pt_1a, pt_1b,pt_1c}

pt_2a = {0,0,1}
 pt_2b = {1,0,0}
 pt_2c = {0,1,0}
 trianlge2 = {pt_2a, pt_2b,pt_2c}

```

From the z direction, on of these triangles will appear to be in front of the other. Is there an algorithm to do this?

---

### Post by mevun on 2012-07-30
It's too hard for me to think in 3-d.  Can you define the equivalent problem in 2-d?

I think that would consist of a set of line segments in an x-y plane which do not intersect.  Are these line segments parallel to each other, simply don't intersect, and can they share endpoints?

Is there a "perspective" x,y point from which you're trying to look for the closest one?

Because it seems that when the perspective point is at (0,0) and all line segments have positive x-values, the closest line segment has the lowest x-value.  If the perspective point is some other value, then one can calculate the distance to all line segment endpoints and the line with the closest endpoint would seem to be the closest.

I am not sure this is the problem you are trying to present.

---

### Post by PaulM1985 on 2012-07-31
I am wondering why you need to do this.  If this is because you want to render the nearest last, then you could just do this in OpenGL since it would handle this for you.

Alternatively, you could take every corner of a triangle, create a line going through that point in the direction of the view, check if this line intersects any of the other triangles in 3d, get this intersection point and see if the z co-ordinate is nearer to the camera than the vertex.

You can check if a line intersects a triangle by first checking if the line intersects the 3d plane containing the triangle, then checking if the intersection point is inside the triangle.

Paul

---

### Post by emiller12345 on 2012-07-31
> **PaulM1985 said:**
> Alternatively, you could take every corner of a triangle, create a line going through that point in the direction of the view, check if this line intersects any of the other triangles in 3d, get this intersection point and see if the z co-ordinate is nearer to the camera than the vertex.


Yes I like this idea. Thank you. I was contemplating a system of randomly generated rays rays to do this, but thought it would be very slow.  As you pointed out, the end points of the triangles are the most important part.

Thank you again.

---

### Post by PaulM1985 on 2012-07-31
> **PaulM1985 said:**
> get this intersection point and see if the z co-ordinate is nearer to the camera than the vertex.

Just realised that this line is technically wrong based on what I said previously.  If your camera is pointing in the z-direction then of course this will work.  The correct, and more generation solution, is to compare the lengths of the vectors from the camera to the intersection point and from the camera to the triangle vertex.

I thought I would correct this in case someone wanted to do this in the future.

Paul

---

