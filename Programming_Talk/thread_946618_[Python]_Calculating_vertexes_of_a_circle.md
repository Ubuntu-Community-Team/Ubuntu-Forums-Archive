---
title: "[Python] Calculating vertexes of a circle?"
date: 2008-10-13
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-13
So I tried to calculate the vertexes of a circle, while I don't know anything about trinometry.
The goal is to draw a circle with given position, radius and precision (amount of segments/vertexes).

I tried to convert this thing to python:
```

Circle:
glBegin(GL_TRIANGLE_FAN)
glVertex2f(x1, y1)
for angle# = 0 to 360 step 5
glVertex2f(x1 + sind(angle#) * radius#, y1 + cosd(angle#) * radius#)
next
glEnd()
return

```
I copied it from here: [http://basic4gl.wikispaces.com/2D+Drawing+in+OpenGL]("http://basic4gl.wikispaces.com/2D+Drawing+in+OpenGL")
[SIZE="1"]I am just trying to learn OpenGL, and I use it to render on pygame surfaces because pygame can't draw half-transparent triangles with textures etc.
That's why here is so much OpenGL involved.[/SIZE]

And came up with this:
```

    def circle(self, pos, radius, color1, color2, precision=10):
        """ Draws a circle at given position with given radius, color and round. """
        glBegin(GL_LINE_LOOP) #GL_TRIANGLE_FAN
        glColor4f(color1[0], color1[1], color1[2], color1[3])
        glVertex2f(pos[0], pos[1])
        glColor4f(color2[0], color2[1], color2[2], color2[3])
        #x = int(round(360/precision))
        for angle in range(0, 360, precision):
            glVertex2f(pos[0] + degrees(sin(angle)) * radius, pos[1] + degrees(cos(angle)) * radius)
        glEnd()

```

As you see, I am using opengl to draw stuff. The coordinates start from top-left corner and get bigger towards bottom-right corner, as they usually do everywhere.

But my function draws just a weird looking star:
[IMG]http://img264.imageshack.us/img264/422/opengltestet0.png[/IMG]
[SIZE="1"]The black rectangle in the top-left corner is because I use compiz fusion, which makes those black rectangles into screenshots. 
Sometimes there are tons of them, sometimes just few. It is a bug, nothing to do with my topic or the circle, don't care about it.[/SIZE]

**So how to draw a nice looking circle like this:**
[IMG]http://www.webkinesia.com/games/images/poly.png[/IMG]

Thanks for your help.

---

### Post by BackwardsDown on 2008-10-13
I don't know anything about OpenGL but, at this line:

glVertex2f(pos[0] + degrees(sin(angle)) * radius, pos[1] + degrees(cos(angle)) * radius)

You seem to convert your sin() to degrees, but they already are right? On the page to who you are linking they are not seem to do that, maybe thats the problem?

---

### Post by PandaGoat on 2008-10-13
*ehh* sine and cosine do not have units.  They are a ratio of two sides of a right triangle. 

sin and cos in python take an angle in radians, and since you are iterating through 1 to 360 (degrees) you need to convert the angle to radians:
```

cos(degrees(angle))
sin(degrees(angle))

```

You should only go from 1 to 360 by the way, 0 and 360 will produce the same vertex.  Moreover, it seems you do not understand how this works.

Lets say P is a point that lies on a circle whose center is the origin and whose radius is R.  The Cartesian coordinates of P are given by x = R*cos(angle) and y = R*sin(angle), where angle is the angle between the positive x-axis and a line drawn from the origin to P.  Now lets call the center of the circle it's location, point L.  To generate vertexes for a circle at point L iterate through 1 to 360 and do x = L.x + R*cos(angle), y = L.y + R*sin(angle).

If you want more precision, you need to decrease how you increment the angle in the loop.  Also, for example, if you increment by .5, start at .5 and stop at 360.

Sorry if this is not a good explanation--it probably isn't--I was just bored.

---

### Post by WW on 2008-10-13
The previous posters have pointed out one problem with your code: the argument of the sin and cos functions is the angle measured in *radians*, not degrees.  If you prefer to leave your loop expressed in degrees, something like this should work:
```

        for angle in range(0, 360, precision):
            theta = pi*angle/180.0
            glVertex2f(pos[0] + radius*cos(theta), pos[1] + radius*sin(theta))

```
You will also have to import pi, if you haven't already, by including this line somewhere earlier in your code:
```

from math import pi

```
(or add it to the line where you import sin and cos).

---

### Post by crazyfuturamanoob on 2008-10-14
Thanks. Got it working with this:
```

    def circle(self, pos, radius, color1, color2, precision=10):
        """ Draws a circle at given position with given radius, color and round. """
        glBegin(GL_TRIANGLE_FAN) #GL_TRIANGLE_FAN / GL_LINE_LOOP
        glColor4f(color1[0], color1[1], color1[2], color1[3])
        glVertex2f(pos[0], pos[1])
        glColor4f(color2[0], color2[1], color2[2], color2[3])
        step = int(360/precision)
        for angle in range(0, 360, step):
            theta = pi*angle/180.0
            glVertex2f(pos[0] + radius*cos(theta), pos[1] + radius*sin(theta))
        glVertex2f(pos[0]+radius, pos[1])
        glEnd()

```
Now I got a nice looking circle with inner/outer colors, radius, and precision:
[IMG]http://img135.imageshack.us/img135/86/openglcirclevc4.png[/IMG]
And because the color arguments also accept alpha values, 
I can even make the circle partially transparent from it's center or borders. :popcorn:

---

