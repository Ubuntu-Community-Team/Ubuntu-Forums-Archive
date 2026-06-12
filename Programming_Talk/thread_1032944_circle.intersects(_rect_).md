---
title: "circle.intersects( rect )"
date: 2009-01-06
forum: Programming Talk
---

### Post by sandyd on 2009-01-06
Ive used the circle.intersects function to see how many times the circle (thats drawn at the place where i click the mouse) intersects a floating rectangle each time i click. is there a function to see how many times it DOESN'T intersect?

P.S. i can't just subtract the total clicks because on some occasions, the circle will intersect multiple objects and i want to know how many shots were fired that actually hit something and how many shots that didn't hit anything at all,  not how many objects were destroyed

---

### Post by CptPicard on 2009-01-06
Umm.. I do not understand the context of the question, but... uh... a circle and rectancle intersect a maximum of 8 times, so perhaps the amount of times they don't intersect is 8 - intersections? :confused:

---

### Post by Zugzwang on 2009-01-07
> **carlee said:**
> Ive used the circle.intersects function to see how many times the circle (thats drawn at the place where i click the mouse) intersects a floating rectangle each time i click. is there a function to see how many times it DOESN'T intersect?


As CptPicard wrote, it is hard to guess what you are actually meaning. Nevertheless, it look like that you are actually referring to something simple. So you have some code like:

```

for r in rectangles:
  for c in circles:
    if c.intersects(r) then:
      do some stuff
```

You can use a boolean variable to track if you had some hit.

```

for r in rectangles:
  hit = false
  for c in circles:
    if c.intersects(r) then:
      hit = true
      do some stuff
  if not hit:
    do whatever you want if there's no hit
```

Note that this is just the general idea, no ready-to-use code!

---

