---
title: "C Linked data structures"
date: 2009-03-14
forum: Programming Talk
---

### Post by heamaster on 2009-03-14
Hi!
I am coding a game in C and I would like to hear your opinion about this:
I will have a large game world with many (hundreds) objects in it with their position saved in variables X and Y.
I am wondering the best way to save these objects to quickly find specific objects by their position (it shall be possible to get all objects within a certain distance from an object).

Thanks! ;)

---

### Post by stevescripts on 2009-03-14
hmm ... my first impression here would be to use some sort of tree implementation.

Good luck!

---

### Post by Gordon Bennett on 2009-03-14
> **heamaster said:**
> Hi!
I am coding a game in C and I would like to hear your opinion about this:
I will have a large game world with many (hundreds) objects in it with their position saved in variables X and Y.
I am wondering the best way to save these objects to quickly find specific objects by their position (it shall be possible to get all objects within a certain distance from an object).

Thanks! ;)

[Quadtrees]("http://en.wikipedia.org/wiki/Quadtree")

---

