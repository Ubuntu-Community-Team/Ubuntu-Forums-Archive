---
title: "Need to identify points (algorithm trouble)"
date: 2006-09-25
forum: Programming Talk
---

### Post by MdaG on 2006-09-25
I have an algorithm that I cannot figure out how to create. I have five points in the xy-plpane and I have to decide which one is upper, lower, center, left and right. The points are not always nicely laid out such that I can use max and min functions to decide which is which.
ex.) p[i] = [xi, yi]
p[0] = [-11.01, -7.88]
p[1] = [-13.06, -8.65]
p[2] = [-9.73, -7.15]
p[3] = [-16.64, -8.45]
p[4] = [-10.30, -7.22]

Here I believe that (Am i wrong?)
center = p[0]
lower = p[1]
right = p[2]
left = p[3]
upper = p[4]

Two points are never equal in my case so I don't need to think about that, but in the example above I get a problem. There p[2] is both right and upper, but as I see it, it should only be right, p[4] is better suited (in this example) to be upper.

I'm writing in Python so I'm sure there's an easy, stable and swift way to do it. I've done a few solutions to it, but they won't work for all kinds of constellations of five points...

---

