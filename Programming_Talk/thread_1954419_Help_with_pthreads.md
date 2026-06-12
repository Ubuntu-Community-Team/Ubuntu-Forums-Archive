---
title: "Help with pthreads"
date: 2012-04-08
forum: Programming Talk
---

### Post by DBQ on 2012-04-08
Hi everybody.

Could somebody please enlighten me, about what could in theory be causing this error in my pthreads program?

```

pthread_mutex_lock.c:62: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.

``` 

Thank You!

---

### Post by MadCow108 on 2012-04-08
likely some memory corruption
try running valgrind on it.

---

