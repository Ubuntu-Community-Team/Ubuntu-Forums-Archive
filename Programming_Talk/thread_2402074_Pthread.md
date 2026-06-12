---
title: "Pthread"
date: 2018-09-25
forum: Programming Talk
---

### Post by sundaresh on 2018-09-25
Is a pthread_rwlock held by a thread automatically released if the thread holding it is killed or abnormally terminated, so the other threads waiting on the lock can acquire it ?

---

### Post by wildmanne39 on 2018-09-25
*Thread moved to **Programming Talk for a more appropriate fit**.*

---

### Post by spjackson on 2018-09-26
I wouldn't claim to be an expert in the finer details of pthreads but it seems to me that by default the lock is not released on process termination so waiting threads would continue to block. However, if you set the Robust attribute, this circumstance can be cleaned up by other threads. See [http://man7.org/linux/man-pages/man3/pthread_mutexattr_getrobust.3p.html](http://man7.org/linux/man-pages/man3/pthread_mutexattr_getrobust.3p.html)

---

### Post by sundaresh on 2018-09-26
I think I'll just try ```
pthread_setcancelstate()
``` and ```
pthread_setcanceltype()
```. If this is not enough additionally I'll try ```
pthread_cleanup_push()
``` and ```
pthread_cleanup_pop()
```.

---

