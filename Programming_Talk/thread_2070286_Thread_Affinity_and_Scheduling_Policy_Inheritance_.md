---
title: "Thread Affinity and Scheduling Policy Inheritance C/C++"
date: 2012-10-12
forum: Programming Talk
---

### Post by akvino on 2012-10-12
Does the child thread in POSIX standard, inherit the affinity and priority of the parent thread?
Does the child thread in POSIX standard, inherit the scheduling policy from the parent thread?

---

### Post by dwhitney67 on 2012-10-12
> **akvino said:**
> Does the child thread in POSIX standard, inherit the affinity and priority of the parent thread?

AFAIK, it does not do so, although if you do not specify a priority for the thread, then presumably it will have the same priority as the parent thread.  If you want a new thread to inherit the attributes of the parent thread, use pthread_attr_setinheritsched() using the appropriate option of PTHREAD_INHERIT_SCHED.

Read the man-page for pthread_setschedparam for more details.

As for the affinity, I do not know.  I have never used this feature.

> **akvino said:**
> 
Does the child thread in POSIX standard, inherit the scheduling policy from the parent thread?
Again, AFAIK, it does not.  Refer to my response above.

---

### Post by akvino on 2012-10-12
so on the man page I found this:
[http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_create.3.html](http://www.kernel.org/doc/man-pages/online/pages/man3/pthread_create.3.html)


Linux-specific details

       The new thread inherits copies of the calling thread's capability sets (see
       capabilities(7)) and CPU affinity mask (see sched_setaffinity(2)).


So it appears that it gets affinity.

---

