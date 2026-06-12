---
title: "Getting angle beetween two points, and moving a point in an angle, in python"
date: 2008-09-09
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-09
So how can I get the angle from one point to another? Like drawing a line beetween two points, then getting the angle of the line?

And how can I move a 2d coordinate forward in a certain angle? All this should be in python.

---

### Post by WW on 2008-09-09
You can use atan2(deltay,deltax) to get the angle.  E.g.
```

from math import atan2, pi

# point 1
x1 = 0.5
y1 = 0.0

# point 2
x2 = -0.5
y2 = -1.0

deltax = x2 - x1
deltay = y2 - y1

angle_rad = atan2(deltay,deltax)
angle_deg = angle_rad*180.0/pi

print "The angle is %.5f radians (%.5f degrees)." % (angle_rad,angle_deg)

```

---

### Post by dribeas on 2008-09-09
> **crazyfuturamanoob said:**
> So how can I get the angle from one point to another? Like drawing a line beetween two points, then getting the angle of the line?

And how can I move a 2d coordinate forward in a certain angle? All this should be in python.

You need three points or two lines to define an angle. I would assume that you mean the angle of the line with respect to horizontal/vertical?

Some basic [trigonometry]("http://www.clarku.edu/~djoyce/trig/") will tell you how to compute the angle.

---

### Post by WW on 2008-09-09
> **crazyfuturamanoob said:**
> 
And how can I move a 2d coordinate forward in a certain angle? All this should be in python.
Use sine and cosine...
```

from math import sin, cos, pi

# starting point
x0 = 1.0
y0 = 1.5

# theta is the angle (in radians) of the direction in which to move
theta = pi/6

# r is the distance to move
r = 2.0

deltax = r*cos(theta)
deltay = r*sin(theta)

# new point
x1 = x0 + deltax
y1 = y0 + deltay

print "The new point is (%.5f,%.5f)." % (x1,y1)

```

---

### Post by crazyfuturamanoob on 2008-09-10
WOW! I actually did not believe I'd get that good answers! THANK YOU!!! :popcorn:

---

