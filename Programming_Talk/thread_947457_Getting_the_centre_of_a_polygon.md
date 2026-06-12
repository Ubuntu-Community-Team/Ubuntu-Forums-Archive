---
title: "Getting the centre of a polygon?"
date: 2008-10-14
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-14
I got a polygon's pointlist. But how to get the centre point of the polygon?

---

### Post by slavik on 2008-10-14
average the coordinates of the points ... ?

---

### Post by mike_g on 2008-10-14
Yep, slavik is right.

Loop through each point on the polygon building a sum of the x, y and z co-ords. Then divide each sum by the number of points. In pseudo code:
```

sum_x = sum_y = sum_z = 0

foreach(p in point_list)
    sum_x += p.x
    sum_y += p.y
    sum_z += p.z

center_x = sum_x / point_list.length
center_y = sum_y / point_list.length
center_z = sum_z / point_list.length
```

---

### Post by hod139 on 2008-10-14
> **slavik said:**
> average the coordinates of the points ... ?
Vertex averaging will not find the centroid of a polygon in general (it only works for some simply polygons) because it neglects the positions for all other points in the polygon.  The common counter-example is a polygon with a concentration of vertices at one end:
```

            *
*              *
            * 

```In this polygon, averaging the vertices will produce a location close to the cluster of vertices.

The correct term for a polygon center is "centroid", and can be computed in closed form.  It required computing the average of the polygon.
For examples with the formula: [http://en.wikipedia.org/wiki/Centroid#Centroid_of_polygon](http://en.wikipedia.org/wiki/Centroid#Centroid_of_polygon)
or [http://ozviz.wasp.uwa.edu.au/~pbourke/geometry/polyarea/]("http://ozviz.wasp.uwa.edu.au/%7Epbourke/geometry/polyarea/")

---

### Post by hod139 on 2008-10-14
> **mike_g said:**
> Yep, slavik is right.

See my post

> 
Loop through each point on the polygon building a sum of the x, y and z co-ords. 
Polygons are by definition 2D.  A polytope can be higher dimensional.

---

### Post by mike_g on 2008-10-14
yeah, averaging can produce weird results for some types of polygons. Often where the point is not inside the polygon. I never really got how you would find the centeroid for those types of polygons; maybe I should read the links.

Also, when doing stuff such as rotating a polygon on a center point obtained by averaging the vertexes the center point can change with the rotation which can cause the shape to move in ways you dont want. Or at least thats what I found anyway.

---

