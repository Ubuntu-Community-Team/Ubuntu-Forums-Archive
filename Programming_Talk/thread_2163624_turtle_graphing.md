---
title: "turtle graphing"
date: 2013-07-19
forum: Programming Talk
---

### Post by Sky001 on 2013-07-19
Hello everyone,
I've been wetting my fingers with python for a little while now. The below code works fine, except I don't understand why it doesn't return an error. sz is not defined, atleast not anywhere visible, yet no error is returned. might anyone be able to explain this? 

```

#!/usr/bin/env python3

import turtle
import random

def drawmltsqr(t,sz):
    """Make turtle,t, draw multicolored squares of size sz!"""
    for hue in["red", "green", "purple", "hotpink"]:
        t.pensize(2)
        t.speed(10)
        t.color(hue)
        t.forward(sz)
        t.left(90)

wn = turtle.Screen()
wn.setworldcoordinates(-1000,-1000,1000,1000)

lance = turtle.Turtle()
size = 100
for i in range(20):
    drawmltsqr(lance, size)
    size = size + 40
    lance.forward(40)
    lance.left(18)

wn.exitonclick()
```

---

### Post by nidzo732 on 2013-07-19
There is no need to define sz, it's defined in the parameter list of the drawmltsqr function.

---

