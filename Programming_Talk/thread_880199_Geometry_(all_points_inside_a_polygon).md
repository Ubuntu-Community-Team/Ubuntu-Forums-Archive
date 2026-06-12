---
title: "Geometry (all points inside a polygon)"
date: 2008-08-04
forum: Programming Talk
---

### Post by nitro_n2o on 2008-08-04
Hi,

I was wondering if anybody knows an algorithm that will return all the integer points lying within a given boundary (e.g inside a polygon define by 6 points) 

so, given a bunch of points defining a closed shape; how to get all points inside that shape 

Thanks a lot

---

### Post by CptPicard on 2008-08-04
[http://en.wikipedia.org/wiki/Point_in_polygon](http://en.wikipedia.org/wiki/Point_in_polygon)

A simple way would be just to find the min and max of the polygon in given dimensions, just producing all integer points, and then filtering according to this... but I am sure you can adapt it further.

---

### Post by nitro_n2o on 2008-08-04
Thanks for the reply, I was trying to find a faster way to do it though.. 
I think I should probably start with brute force way then find a fancier solution. 

Thanks!

---

### Post by CptPicard on 2008-08-04
Considering that the majority of integer points inside the bounding box are likely to be inside the polygon, you aren't really wasting much time querying in that sense. 

Perhaps one could make use of closeness of nearby points and their presence in the same part of the space partition... look at the planar partition idea where the polygon is divided into slabs. But I get the feeling that even if you got many integer points at once from each "slab" you would end up wasting more actual computation time in your data structures and more complicated algorithm than you would need if you just went through the points and queried individually using a simpler method.

---

### Post by nitro_n2o on 2008-08-04
yeah I think you are right! :)
I've implemented it and it seems fast enough 

Thanks a lot

---

### Post by hod139 on 2008-08-04
If you know the polygon will always be convex there are faster algorithms available.  A good website for geometry algorithms (with lots of free C code implementations) is available at:
  [http://geometryalgorithms.com/algorithm_archive.htm](http://geometryalgorithms.com/algorithm_archive.htm)

The chapter on point in polygon is here: 
  [http://geometryalgorithms.com/Archive/algorithm_0103/algorithm_0103.htm](http://geometryalgorithms.com/Archive/algorithm_0103/algorithm_0103.htm)

---

### Post by CptPicard on 2008-08-04
For a convex polygon it is possible to do a whole row of integer points at once until you hit the opposing edge of the polygon... just do a planar partition along the x-axis (so that you get horizontal divisions) first, then it is trivial to find integer points inside the slabs.

(Works analogously in the other direction ofc)

---

