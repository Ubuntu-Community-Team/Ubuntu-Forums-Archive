---
title: "netbeans 6.8 c++ increase stack size"
date: 2010-05-05
forum: Programming Talk
---

### Post by Xender1 on 2010-05-05
I am trying to create some very large arrays, and have all my code working for small test cases. When it came time for me to use it on the actual data (sizes of 10,000) i get a segmentation fault and it is because of the stack size that is set as default is not large enough. Is there a way i can easily increase the stack size without having to rewrite my code using 'new' to add them on the heap? thanks!

---

### Post by Xender1 on 2010-05-05
i did some searching and found that if i added -Wl,--stack,16777216 to project properties > linker> additional options it should work, but my code is saying it does not know the command --stack

---

### Post by MadCow108 on 2010-05-05
you can increase the stacksize with ulimit -s newsize
normal is around 8mb (check with ulimit -a)

but the question is:
why are you using so much stack?
use the heap instead, it is much bigger (~ size of the ram) and the error handling is gracefuller
stack running out pulls everything down with it, too little ram can be handled

the only drawback is a slightly slower allocation time (mostly negligible, if not preallocate a pool).

It is well worth rewriting your code.

---

