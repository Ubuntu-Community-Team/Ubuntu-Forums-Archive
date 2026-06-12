---
title: "How to get corefiles?"
date: 2006-05-17
forum: Programming Talk
---

### Post by DevSolar on 2006-05-17
Hi there,

I'm new to the Ubuntu brand of Linux. I've got a problem: Ubuntu does not seem to generate coredumps when a program is abort()ed or segfaults. Is this a configuration issue, and if yes, how can I activate coredumps?

I need those for debugging. (And no, there's no viable workaround.)

Thanks in advance!

---

### Post by llonesmiz on 2006-05-17
To activate coredumps you should use the shell command **ulimit** with the option **-c limit**. By default it is set to **0.**
For example:
```
ulimit -c unlimited
``` or if you want to limit the size of the coredump you could write:
```
ulimit -c 1024
``` (or any other number)

---

### Post by DevSolar on 2006-05-17
That actually did the trick; thanks!

---

