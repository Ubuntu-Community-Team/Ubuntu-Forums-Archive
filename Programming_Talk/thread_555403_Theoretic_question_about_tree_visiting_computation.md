---
title: "Theoretic question about tree visiting computational cost"
date: 2007-09-20
forum: Programming Talk
---

### Post by mallo on 2007-09-20
Hi,
I implemented a quadtree data structure.
For one method I need to visit the whole tree to retrieve a list of leaf. (I know it's expansive...).

I ask myself what is the computational cost but I cannot figure it out. I think it's probably O(n^2) or more with n=number of nodes.

Anyone is fresh of the subject and can help me?

Thank you ;).

P.S.: The software will be released under GPLv3.

---

### Post by CptPicard on 2007-09-20
> **mallo said:**
> 
For one method I need to visit the whole tree to retrieve a list of leaf. ... n=number of nodes.


There's your answer. Supposing you're doing the usual recursion thing, you'll be processing each node once, and you've got a tree of n nodes, so your cost is O(n)... or are you looking at the cost in terms of number of leaves? In which case you're still O(n) IIRC as in log-access time trees the amount of nodes above leaves is below a constant factor times number of leaves...

EDIT: this assumes that when you're combining the result lists from below in the recursion, your list join cost is constant. If that is linear, you will be spending n log n time joining lists... (off the top of my head)

---

### Post by mallo on 2007-09-20
You're probably right ;), your reasoning appears consistent.
Thank you a lot for the answer ;)

---

