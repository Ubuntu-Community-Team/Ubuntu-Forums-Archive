---
title: "[Python]Rotating a point about another point"
date: 2008-11-08
forum: Programming Talk
---

### Post by ghem on 2008-11-08
Hello, 

I am trying to write a small game in pyglet, in which several images will have to rotate around a point that is not the center of the image.  I tried to write a function to do this, but it doesn't work:

[PHP]
from math import *

def prot(point, orig, ang):
    point[0] -= orig[0]
    point[1] -= orig[1]

    point = [(point[0]*cos(ang)) - (point[1]*sin(ang)), (point[0]*sin(ang)) + (point[1]*cos(ang))]
    
    point[0] -= orig[0]
    point[1] -= orig[1]
    return point

print prot([5, 5], [0, 0], 45)[/PHP]
The program runs fine, but it returns [-1.6279076785819435, 6.8811275667592415].  If it is rotating [5, 5] about the origin, then it should return [0, 5] or [5, 0] depending on which way it rotates.

Can someone please help me get this function to work?

---

### Post by WW on 2008-11-08
Just a few comments:
[list]
[*] sin() and cos() use radians, not degrees.  45 degrees is pi/4 radians.
[*] If you rotate (5,5) 45 degrees counter-clockwise, the new point is (0,7.071) (approximately), not (0,5).
[*] *Add* the origin back to the point after rotating.  You currently subtract it again.
[/list]

---

### Post by gschoep on 2010-01-06
Don't forget that the second point can be y or z

This is complete code.

```

[COLOR=Black]from math import * [/COLOR]

def rotate2d(degrees,point,origin):
    """
    A rotation function that rotates a point around a point
    to rotate around the origin use [0,0]
    """
    x = point[0] - origin[0]
    yorz  = point[1] - origin[1]
    newx = (x*cos(radians(degrees))) - (yorz*sin(radians(degrees)))
    newyorz  = (x*sin(radians(degrees))) + (yorz*cos(radians(degrees)))
    newx += origin[0]
    newyorz  += origin[1] 
 
    return newx,newyorz 
```

---

