---
title: "how float variable store in memory"
date: 2014-02-10
forum: Programming Talk
---

### Post by srikanth2 on 2014-02-10
In GDB how to find float variable storage in memory ..
and i want how float value converting into binary form .. can any one explain this ..!!!!!


Thanks you ---

---

### Post by Bachstelze on 2014-02-10
There is no special storage area in memory for floating-point variables, they are stored in exactly the same way as any other variable.

---

### Post by srikanth2 on 2014-02-10
or can know how the float point variable into binary number ..???

---

### Post by Dave_L on 2014-02-10
Does this help?
[http://students.byu.edu/~cs124ta/references/readings/floating%20point%20numbers.html](http://students.byu.edu/~cs124ta/references/readings/floating%20point%20numbers.html)

---

### Post by srikanth2 on 2014-02-10
Thank You Dave_L ... But i need an example with explaination .... :

---

### Post by MadCow108 on 2014-02-10
the wiki articles describes the common representation:
[http://en.wikipedia.org/wiki/Floating_point](http://en.wikipedia.org/wiki/Floating_point)

but how exactly its done depends on the platform, there are plenty variations.

with gdb you can print it by reinterpreting it as an integers of equal size:

p *(int64_t*)(address-of-double)
p *(int32_t*)(address-of-float)

---

