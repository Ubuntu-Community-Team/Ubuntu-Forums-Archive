---
title: "About CPU optimization ?"
date: 2012-08-25
forum: Programming Talk
---

### Post by prismctg on 2012-08-25
How can i do "CPU optimization" in python ? actually i haven't any concept about doing this kind of staff :(

---

### Post by MadCow108 on 2012-08-25
what do you mean cpu optimizations?
optimizing your python program for certain cpu types?

you can't really do that directly in python, as it is running a sort of virtual machine not the real cpu. The virtual machine does the low level cpu stuff for you.

you can write inline C/C++ code with various libraries like scipy.weave which would allow this though.

But the better way is to use appropriate modules which do the cpu type optimizations for you, like numpy or write your own C/C++ extension module in a similar way.

Another option is using pypy which compiles to machine code just in time.
But it optimizations using modern simd cpu instructions is still in a pretty early stage there.

---

