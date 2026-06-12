---
title: "shmget and shmat"
date: 2011-08-06
forum: Programming Talk
---

### Post by NumerataNero on 2011-08-06
How gan i determine which memory is free to use shmget to allocat a shared segment?
What is the best way to get an address so I can use that in both processes?
thanks Rob

---

### Post by dwhitney67 on 2011-08-06
> **NumerataNero said:**
> How gan [sic] i determine which memory is free to use shmget to allocat a shared segment?

**shmget()** will allocate the memory based on the size you request, and will return a unique id value that can be used for subsequent operations (ie **shmat()**).  You need to ensure that the application that creates the shared memory and the other application that also attaches to it both use the same **key_t** value.

---

### Post by NumerataNero on 2011-08-09
Ok, thanks. I will do some testing.

---

