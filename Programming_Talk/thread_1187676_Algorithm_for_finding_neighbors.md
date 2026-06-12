---
title: "Algorithm for finding neighbors"
date: 2009-06-14
forum: Programming Talk
---

### Post by dracule on 2009-06-14
Hey all, 

I was writing an algorithm in python where i have about 10k objects floating on screen and I want to find the neighbors of just one object. 

What do you guys recommend for finding the neighbors? Right now it just iterates through all the objects and uses a simple distance formula to filter out if they are inside of the radius, but it is much, much too costly. 

So i want to find the objects within X radius of my object without iterating through all my objects.

So if you guys could just give me some pointers it would be super. I can modify my program to however it should be. 

Thanks

---

### Post by Can+~ on 2009-06-14
One easy way to optimize that algorithm, is to remove redundant checks.

For example (for objects A,B,C,D,E):

```
A checks if it collides with B
A checks if it collides with C
A checks if it collides with D
A checks if it collides with E
**B checks if it collides with A** (already checked)
B checks if it collides with C
B checks if it collides with D
B checks if it collides with E
**C checks if it collides with A** (already checked)
**C checks if it collides with B** (already checked)
C checks if it collides with D
C checks if it collides with E
D checks.......
...............
```

(n-1)*n


could be reduced to:

```
A checks if it collides with B
A checks if it collides with C
A checks if it collides with D
A checks if it collides with E
B checks if it collides with C
B checks if it collides with D
B checks if it collides with E
C checks if it collides with D
C checks if it collides with E
D checks if it collides with E
```

(Which is a progressive sum on (n-1) ) (n-1)*(n-2) / 2

---

### Post by leandromartinez98 on 2009-06-14
Define the distance within which you want to consider the object to be a neighbour, lets say, 20 px. Then, classify each element in the screen in a grid of 20 px size, using simple operations:

for object in group
  i = integer(x(object) / gridsize)
  j = integer(y(object) / gridsize)
  add object to group specified by indiced (i,j)
done

This takes O(n) operations, obviously.

Then, for example, if your object is in the group (5,5),
you just need to check which are the objects in the same square
or in adjacent ones.

This algorithm is O(n) if the distribution of objects is more
or less homogeneus. This is sometimes called "linked cell method"
in molecular dynamics simulations.

---

