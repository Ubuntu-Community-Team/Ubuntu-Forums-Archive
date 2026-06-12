---
title: "Rotating a line from a fixed point in python/pygame"
date: 2009-09-16
forum: Programming Talk
---

### Post by donkyhotay on 2009-09-16
I'm working on a FOSS [project](code.google.com/p/tether) that needs a rotation indicator, and I'm having problems getting it to work accurately. I need it so that the indicator points in the correct direction in degrees, so that if it's at 90 degrees it's pointing straight left, at 180 degrees it's pointing straight down, along with every point in the middle in a complete 360 degree arc. I currently have it drawing a simple line in pygame with one end locked into place, however I can't accurately figure out how to calculate where the other end should be. Obviously I can do it manually by doing something like
```

if degree = 90:
  pygame.draw.line((startx, starty), ((startx + 5), starty)
if degree = 180:
  pygame.draw.line((startx, starty), ((startx ), starty + 5)

```
for each and every possible angle but that is inefficient and I know there has to be a (relatively) simple equation that will do this all at once for me. Anyone have any ideas on how I should code this?

---

### Post by Reiger on 2009-09-16
Sines and cosines.

---

### Post by WitchCraft on 2009-09-16
> **donkyhotay said:**
> I'm working on a FOSS [project](code.google.com/p/tether) that needs a rotation indicator, and I'm having problems getting it to work accurately. I need it so that the indicator points in the correct direction in degrees, so that if it's at 90 degrees it's pointing straight left, at 180 degrees it's pointing straight down, along with every point in the middle in a complete 360 degree arc. I currently have it drawing a simple line in pygame with one end locked into place, however I can't accurately figure out how to calculate where the other end should be. Obviously I can do it manually by doing something like
```

if degree = 90:
  pygame.draw.line((startx, starty), ((startx + 5), starty)
if degree = 180:
  pygame.draw.line((startx, starty), ((startx ), starty + 5)

```
for each and every possible angle but that is inefficient and I know there has to be a (relatively) simple equation that will do this all at once for me. Anyone have any ideas on how I should code this?

What you need is the x and y coordinates of the starting point and the ending point of the line.

So you need two (x,y) sets.
start is always gonna stay the same, since it is a fixed point.

end can be thought of as the x,y coordinates of a point on a circle with radius one. 

Yend= sin(alpha)
Xend= cos(alpha)

for an angle "ALPHA" in degrees.

one circle of radius one has a circumference of 2 * pi, so 360 degrees equal 2*pi times the radius, in short rad.

360 deg = 2pi rad

1 deg = 2/360 pi rad = 1/180*pi *rad


so you calculate the angle in radians:
x degree = x /180* pi radian

So we now have the angle phi, which is alpha, just that it is measured in radiant, because the trigonometric functions work with radiant.

so you have the function:
sin(Alpha/180.0*pi)
cos(Alpha/180.0*pi)

For the coordinates of radius != 1, you only need to do a centric stretching with the radius of the circle (aka length of your line, which i assume to be 5 after what i have read):

Xend := radius*cos(alpha/180.0*pi)
Yend := radius*sin(alpha/180.0*pi)

where pi is 3.1415926535897932384626433832795028841971693993751

---

### Post by Can+~ on 2009-09-16
```
sin a = _ opposite _
        hypotenuse

cos a = _ adjacent _
        hypotenuse 
```

You know the radius (hypotenuse) and you have the angle, so you can compute sin and and cosine after converting them to radians.

---

### Post by MadCow108 on 2009-09-16
this page should contain everything you need:
[http://en.wikipedia.org/wiki/Rotation_matrix](http://en.wikipedia.org/wiki/Rotation_matrix)

---

### Post by donkyhotay on 2009-09-16
Thanks for the replies, this is definitely what I'm looking for though I think I'm doing something wrong here. I have tried:
```

print"temp rotation = ", rotation
endX = 5 * math.cos(rotation/180*math.pi)
endY = 5 * math.sin(rotation/180*math.pi)
print"endX, endY = ", endX, ", ", endY

```
rotation of course is the angle in degrees from 1-360 however the output I get as rotation changes is:
```

temp rotation =  1
finalX, finalY =  5.0 ,  0.0
temp rotation =  2
finalX, finalY =  5.0 ,  0.0
temp rotation =  3
finalX, finalY =  5.0 ,  0.0
temp rotation =  4
finalX, finalY =  5.0 ,  0.0
temp rotation =  5
finalX, finalY =  5.0 ,  0.0
temp rotation =  6
finalX, finalY =  5.0 ,  0.0
temp rotation =  7
finalX, finalY =  5.0 ,  0.0
temp rotation =  8
finalX, finalY =  5.0 ,  0.0
temp rotation =  9
finalX, finalY =  5.0 ,  0.0
temp rotation =  10
finalX, finalY =  5.0 ,  0.0

```
and so on. Obviously something is wrong with my calculation. Any further ideas?

---

### Post by unutbu on 2009-09-16
Put
```

from __future__ import division
```

at the top of the file. This will make division of integers return a float.
As it stands, with Python versions < 3.0, division of two integers returns an integer. In Python 3.0, division of two integers returns a float.

Or, if you prefer, you could also do this: 
```

endX = 5 * math.cos(rotation/**180.0***math.pi)
endY = 5 * math.sin(rotation/**180.0***math.pi)
```

---

### Post by donkyhotay on 2009-09-16
Thanks, thats what I was looking for.

---

### Post by Can+~ on 2009-09-16
Use math.radians()

[PHP]#!/usr/bin/env python

import math

def triangular(radius):
	return lambda a: (radius*math.cos(math.radians(a)), 
	                  radius*math.sin(math.radians(a)))

# Goneometric Circle
coord = triangular(1)

for i in xrange(0, 361, 45):
	x,y = coord(i)
	
	print "angle: %d, coord %.3f, %.3f"  % (i, x, y)[/PHP]

---

### Post by donkyhotay on 2009-09-16
Problem was the fact it was doing integer division when a float was needed. Unutbu's 2nd suggestion got it working. Thanks everyone, it's working properly now.

---

