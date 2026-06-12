---
title: "Delicious Cake"
date: 2008-04-09
forum: Programming Talk
---

### Post by thegom on 2008-04-09
I found this [http://fudge.fit.edu/Problems/Archive/Delicious_Cake]("http://fudge.fit.edu/Problems/Archive/Delicious_Cake") interesting problem over on fudge.fit.edu, a social coding site I found the other day, and I'm a bit stumped on how to solve it.

Any hints? What kind of problem class does this fall into, and what kind of algorithm would you use to solve it?

(This isn't an omg plz do my homewurk post, I'm just interested in how one would do this)

Cheers,

Gom

---

### Post by CptPicard on 2008-04-10
My first attempt would be a simple recursion. You start by taking a single square in a corner, and then proceed to divide the rest in the same fashion. Once you're divided all, add one. Coming back up your recursion, you add a neighbouring square to your corner, go down again... etc

---

### Post by slavik on 2008-04-10
number each possible place to cut and number them. then look for valid cutting combinations. :)

---

### Post by Can+~ on 2008-04-10
For a second I thought this would be a portal-joke.

This was a triumph though.

---

### Post by CptPicard on 2008-04-10
Actually, you also need to combine the the recursion with memoization, otherwise you're constantly recomputing the amount of combinations in the subareas. This will probably yield a dynamic programming algorithm.. I'll think of it.

---

