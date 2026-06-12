---
title: "Breaking a 2D polygon into pieces when something hits it hard?"
date: 2008-11-30
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-30
I want to do this with a 2D triangle/polygon, with smaller polygons.
[IMG]http://i62.photobucket.com/albums/h102/animeaid/example2.png[/IMG]
Like breaking this into smaller triangles with same principle as above.
[IMG]http://tbn3.google.com/images?q=tbn:PzDbfkRisL8RkM:http://upload.wikimedia.org/wikipedia/commons/thumb/e/e4/Triangle-acute.svg/460px-Triangle-acute.svg.png[/IMG]
How could this be done in PseudoCode?

And I want the subdivisions to look cool, like real cracks, 
instead of just linearly dividing each triangle it into another 3 triangles.

The bullet has variables for direction and speed, so the cracks could vary depending on these.

---

### Post by pp. on 2008-11-30
Before you think about coding, you ought to have more than a general idea of what your code will have to accomplish.

Try describing the "cracks" (in words or formulas) or try drawing the desired cracks into your triangle.

---

### Post by fiddler616 on 2008-11-30
Think it through, and I wouldn't mess with cracks for now.

What happens when the bullet hits?[COLOR=White]
 The old shape (coordinates (x1, y1)+(x2, y2)) dies, and is replaced by two new ones (x1, y1)+([x2+x1]/2, [y1+y2]/2)  and ([x2+x1]/2, [y1+y2]/2)+(x2, y2)
[/COLOR] 
(That should point you in the right direction)

I don't know a thing about game programming (so don't hold me to this) but just applying logic leads to some interesting hypotheses. Edit: I whited out the answers. Don't spoil yourself if you don't have to.


...and later:
What about cracks?[COLOR=White]

 They're the tangents of randomly dampened sine waves, it seems to me. Explore!

[/COLOR]

---

### Post by CptPicard on 2008-11-30
Well, thinking about this analogously to your square example, you may want to consider applying the recursive principle for a division of the triangle you get from drawing lines from each corner of the triangle to the opposite side's midpoint...

---

### Post by Mickeysofine1972 on 2008-11-30
Well my first take on it would be to try seeing what it looks like to split the triangle along the normal in the inward direction of the velocity vector.

... well you had to ask :D
```

// get the normal for this edge
normal = Vector(faceStartvector - faceEndVector)
normal.normalise()
normal = normal.transpose()


// project onto the edge
normal *= dot_product(velocity, normal)
projection = velocity - normal
intersectingPoint = faceStartvector + projection

// make the new triagles
newTriangle1 = [triagleP1 , intersectingPoint, triangleP3]
newTriangle1 = [triagleP3 , intersectingPoint, triangleP2]


```I only broke it into two but you get the idea
Mike

---

