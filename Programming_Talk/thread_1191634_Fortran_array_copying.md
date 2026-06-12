---
title: "Fortran array copying"
date: 2009-06-19
forum: Programming Talk
---

### Post by squaregoldfish on 2009-06-19
Hi there,

Using Fortran90, I'm reading an indeterminate amount of data into a 3-dimensional array of the form:

REAL, DIMENSION(<latitude>,<longitude>,<time>)

where I'd like the time dimension to expand as data is read in.

Since I can't change the size of the array once it's been declared, I presume that the best approach is to declare a new array, copy the existing data into it, then continue populating it. Assuming this is the best approach (I'm open to suggestions!), what's the most efficient way of copying the first array into the beginning slots of the new, larger array? Given that the array will ultimately contain around 30 million data points, I think that looping through the array manually will be far too slow.

Thanks in advance,
Steve.

---

