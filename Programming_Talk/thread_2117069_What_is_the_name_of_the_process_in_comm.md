---
title: "What is the name of the process in comm?"
date: 2013-02-17
forum: Programming Talk
---

### Post by AADAS on 2013-02-17
I know that the comm array holds the name of the process but how is stored?
([http://lxr.free-electrons.com/source/include/linux/sched.h](http://lxr.free-electrons.com/source/include/linux/sched.h) row 1337)

---

### Post by The Cog on 2013-02-17
The definition there is:
```
   char comm[TASK_COMM_LEN]; 
```
so comm is an array of chars of length TASK_COMM_LEN. 
But since the name of an array is a pointer to its first char, you could also regard comm as a char*.
At least, that's if my memory serves me right.

---

### Post by AADAS on 2013-02-17
I mean how the name is stored.Is it process.o or process or some other way?

---

