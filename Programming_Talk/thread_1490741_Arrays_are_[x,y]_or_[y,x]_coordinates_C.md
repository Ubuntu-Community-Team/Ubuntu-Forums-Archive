---
title: "Arrays are [x,y] or [y,x] coordinates? C"
date: 2010-05-22
forum: Programming Talk
---

### Post by pieguy on 2010-05-22
My initial thinking was the conventional x,y coordinates, but I'm starting to think its y,x.  Just need conformation.

The first pic is y,x and the second is x,y.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157918&stc=1&d=1274563992[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=157921&stc=1&d=1274564368[/IMG]

---

### Post by Bachstelze on 2010-05-22
It's whatever you want it to be. In memory, there are no rows or columns.

---

### Post by StephenF on 2010-05-22
For dumping to a console the y,x scheme holds true. There is no correspondence with any of the quadrants of the Cartesian plane. In GUI toolkits the top left coordinate of a drawable surface is also 0,0.

In general it is quantity y of x of type. The spacial mapping is coincidental to the left to right, top to bottom writing system so others may think differently.

---

### Post by MadCow108 on 2010-05-22
C uses row major storage for its arrays, which means [y,x]

if you need column major you can always linearize your data yourself:
array[col + NCOLS*row] // row major equal to array[NROWS][NCOLS]
array[row + NROWS*col] // column major (fortrans default)

---

### Post by Queue29 on 2010-05-22
> **Bachstelze said:**
> It's whatever you want it to be. In memory, there are no rows or columns.
**Not true not true not true.**

> **MadCow108 said:**
> C uses row major storage for its arrays, which means [y,x]

if you need column major you can always linearize your data yourself:
array[col + NCOLS*row] // row major equal to array[NROWS][NCOLS]
array[row + NROWS*col] // column major (fortrans default)



And this is sometimes a lot more important sometimes than you might think. In anything that is to be high-performance, it is necessary to take into consideration the way data from RAM is loaded into the cache, which means explicitly organizing your data row major or column major, depending on how the language you are working with works behind the scenes. To the best of my knowledge, gcc cannot optimize things like this, however the intel compiler can. 


Here is a 'fun' walk-through a former professor of mine made which demonstrates just how important organizing data and operations can be, by implementing a matrix-matrix multiplication function in C. 

[http://z.cs.utexas.edu/wiki/LA.wiki/OptimizingGemm](http://z.cs.utexas.edu/wiki/LA.wiki/OptimizingGemm)

---

### Post by wmcbrine on 2010-05-22
C doesn't actually have multi-dimensional arrays as a language construct. If you have something like "int foo[10][10]", that's an array of arrays of integers.

---

### Post by croto on 2010-05-22
[QUOTE=Queue29;9344481]**Not true not true not true.**

I agree that they can be whatever you want them to be, and I also agree with the performance considerations. For instance: a[.][.]...[x] is next in memory to a[.][.]...[x+1] so it is faster to traverse the matrix last index first, first index last. However, if you want to call the last index row or column is up to you.

---

