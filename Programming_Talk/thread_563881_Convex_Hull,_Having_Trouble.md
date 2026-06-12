---
title: "Convex Hull, Having Trouble"
date: 2007-09-30
forum: Programming Talk
---

### Post by Lster on 2007-09-30
Hi everyone

As I find graphic programming especially hard, I have decided to challenge myself. I am trying to solve a create the complex hull of some points using the gift wrapping algorithm.

EDIT: My problem was with orientation testing - see Lux Perpetua's post.

Thanks,
Lster

---

### Post by Lster on 2007-09-30
* Bump *

---

### Post by gnusci on 2007-09-30
Why don't you give a look to **Triangle** code:

[http://www.cs.cmu.edu/~quake/triangle.html](http://www.cs.cmu.edu/~quake/triangle.html)

which does Convex Hulls:

[http://www.cs.cmu.edu/~quake/triangle.convex.html](http://www.cs.cmu.edu/~quake/triangle.convex.html)

I would say it is very easy to understand, better than post a snip of code which is hard analyse.

---

### Post by Lux Perpetua on 2007-09-30
Lster - Are you familiar with the orientation test? It's a geometric predicate, "Orient2D(p, q, r)," which is 1 if p, q, r are in counterclockwise order, -1 if they are in clockwise order, and 0 if they are collinear. For gift wrapping: if p is the last point you chose, q is the point you're thinking of adding next, and r is any other point, you need p, q, r to be in counterclockwise order (assuming you're wrapping counterclockwise). If they're not, then you need to replace q with r. Gift wrapping is essentially a brute-force implementation of that. 

As for implementing Orient2D...you should definitely know that before attacking *any* geometric algorithm. ;)

gnusci - Since Lster is doing this as a personal challenge, using somebody else's code sort of defeats the purpose.

---

### Post by Lster on 2007-09-30
EDIT: Everything if working great now! Thank you very much for your help guys! As I am not very familiar with your Orient2D function, could you recommend a good reference on it?

Thank you again!
Lster

---

### Post by Lux Perpetua on 2007-09-30
```
            if ( orient ( X [ p ] , X [ i ] , X [ n ] ) )
                n = i; 
```That's not how orientation works. There are three possibilities: positive, negative, and zero. It's not a boolean proposition.

There's another problem, which is that you don't have the right stopping condition. You should stop when you run out of points, i. e., when the point you need to add next is already on the convex hull. When that happens, it can only be first vertex of the convex hull, though, so it's easy to detect. (That ignores numerical robustness issues; in real-world code, you would want to be more careful.)

---

### Post by Lster on 2007-09-30
Good points. Thank you!

---

### Post by DMills on 2007-09-30
If you don't have them already, the "Graphics gems" books (IIRC there are at least 5 of them), are well worth tracking down for all sorts of cool algorithmic tricks. 

Regards, Dan.

---

