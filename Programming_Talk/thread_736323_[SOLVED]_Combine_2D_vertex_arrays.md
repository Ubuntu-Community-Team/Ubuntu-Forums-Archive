---
title: "[SOLVED] Combine 2D vertex arrays"
date: 2008-03-26
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-26
As far as my understand goes, what I am asking for is some rather complicated code... I need to take multiple 2D vertex arrays, that overlap each other, and combine their shapces... for example:
[IMG]http://www.geocities.com/boosterrpg/example1.png[/IMG]
While this could be done in the first place, manually... the physics engine I'm using  demands it be done this way (it doesn't support concave shapes). Admittedly, I would like to do it this way even regardless of the fact that I *have* to do it this way.

As I understand it, I need something that will more or less take the existing points on the shapes, find the collision points in those lines (which is where new vertecies would need to be), discard the now unused points, and return it all in a form that isn't merely a list of vertecies, but is in fact the list *in order* so that when its drawn it isn't a jumbled mess.

Admittedly, I haven't tried working on this myself yet, I figure it will be a rather formidable undertaking, and I'd like to save time where I can (for instance having someone else point out to me the code). I will, however, in all likely-hood, be working on it after I post this very message.

As I understand it, it will take even more work to give me something that has the empty space in the middle, if the shapes would have it (you know, like a circle of rectangles), and if you don't know how to do it, it is not required...

---

### Post by CptPicard on 2008-03-26
Actually computing set operations of shapes is a pretty classical computational geometry excercise, you'll find ready algorithms for it. A really good textbook on all this is Berg, Kreveld, Overmars, Schwarzkopf: Computational Geometry, Algorithms and Applications.

A Google for "2D shape union algorithm" should yield some kind of results as well.

---

### Post by Lux Perpetua on 2008-03-26
From your illustration, it seems you are just trying to find the union of two or more polygons. 

There are reasonably fast and simple algorithms for this, and at least one such algorithm would be covered in any decent computational geometry textbook. In fact, you could probably get some good ideas just by searching the internet for "polygon union" or something similar. 

**Edit:** I originally suggested an algorithm here, but I realized it wasn't as simple as I made it sound, so I removed it. 

The textbook suggested by CptPicard is an excellent book for all things computationally geometric. It will directly give you an algorithm for this (as a special case of overlaying planar subdivisions), but it also gives you some references for faster algorithms (if I recall correctly; the book is at home, and I'm not. ;-))

---

### Post by CptPicard on 2008-03-26
... and the edge intersection algorithm is O(n log n) in vertices if implemented properly, see the abovementioned textbook.

---

### Post by Lux Perpetua on 2008-03-26
Oops...I just edited my post out from under you, didn't I? Sorry, your post wasn't there when I modified mine. 

To those wondering, the algorithm I suggested was to find the intersections among the edges and then for each of the new edges to determine if it is an edge of the union by seeing if it falls inside one of the input polygons. 

Actually, for general polygons, no algorithm can be better than O(n^2), since the union could have O(n^2) complexity if the two input polygons have O(n) vertices. (Think of two combs right on top of each other but rotated 90° relative to each other.)

---

