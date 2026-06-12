---
title: "Equation to Rolling sphere/ball"
date: 2008-02-29
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2008-02-29
Hey Guys

I've been looking all over for a good way to work out how much a ball or sphere rotates when rolling any ideas?

I know that the circumference of a ball is:

2*PI*Radius

and that PI == 180degrees 

but would the value in degrees relate to the units travelled when a sphere rolls?

i think i'm on the right track but can find any further maths info HELP!

Mike

---

### Post by hyperair on 2008-02-29
Supposing the ball rolls in a straight line, then the number of turns it makes, multiplied by the circumference equals to the distance it travels. But if it doesn't go in a straight line... then I'm not so sure.

---

### Post by cb951303 on 2008-02-29
it's been a while since I took a dynamics lesson but if I remember correctly

angular speed (w) = 2 * PI * frequency (f)  [rd/s]
so lets say if the ball rolls for t seconds then the rotating it does = w * t [rd]

---

### Post by WW on 2008-02-29
If a ball with radius R rolls *in a straight line* for distance D, then the total rotation is D/R radians, or (180/Pi)*D/R degrees.

---

### Post by Lux Perpetua on 2008-03-02
If anybody is interested in the case of a path that is not necessarily straight, then I believe the net rotation matrix **R**(s) of the sphere after rolling for a total distance of s can be found as the solution of the following differential equation: [list][*]**R'**(s) = (1/r)**A**(s)**R**(s),[*]**R**(0) = **I** (the identity matrix).[/list]r is the radius of the sphere, and **A**(s) is the matrix ```
[ 0      0      x'(s) ]
[ 0      0      y'(s) ]
[-x'(s) -y'(s)  0     ],
```where x(s) and y(s) are the coordinates of the path at length s. (Note: the parameter s doesn't actually need to be the distance traveled; you can reparametrize if convenient.) 

If the path is a straight line, then **A**(s) is a constant matrix, and the differential equation can be solved exactly, giving you one version of the formulas of the previous posters. In general, I don't know if there is an explicit solution to that equation, but you could still approximate it.

I also tried to consider the generalization where the sphere rolls on a surface that isn't necessarily flat, but my solution to that turned out to be incorrect, so I'll leave that be.

---

