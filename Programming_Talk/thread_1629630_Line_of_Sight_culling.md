---
title: "Line of Sight culling?"
date: 2010-11-24
forum: Programming Talk
---

### Post by roadkillguy on 2010-11-24
Hi everyone,

  I've been writing a game with presumably random boxes. I've implemented view frustrum culling, backface culling, and even display lists. It's still not fast enough for my tastes, and I was wondering if there was any way to tell whether a face will be behind another. 

Maybe I could check whether the entire screen has been rendered to? 

A point in the right direction would be great.  (I'm using c++)

  Thanks.

---

### Post by StephenF on 2010-11-24
In case you have not seen this yet.

[http://en.wikipedia.org/wiki/Hidden_surface_determination](http://en.wikipedia.org/wiki/Hidden_surface_determination)

---

### Post by roadkillguy on 2010-11-24
I read somewhere that glBegin() and glEnd() were really slow.. what's the alternative?

---

