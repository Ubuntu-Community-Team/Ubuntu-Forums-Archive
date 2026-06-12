---
title: "pthread_cond_timedwait question"
date: 2011-02-13
forum: Programming Talk
---

### Post by t1497f35 on 2011-02-13
Hi,
is there any sensitive difference in CPU usage between this function and pthread_cond_wait?

I'm just thinking which one to use when I know the average wait will be several seconds..

---

### Post by MadCow108 on 2011-02-13
> 
The pthread_cond_timedwait() and pthread_cond_wait() functions shall block on a condition variable
...
The pthread_cond_timedwait() function shall be equivalent to pthread_cond_wait(), except that an error is returned if the absolute time specified by abstime passes (that is, system time equals or exceeds abstime) before the condition cond is signaled or broadcasted, or if the absolute time specified by abstime has already been passed at the time of the call.

timed_wait stops blocking after a certain _maximum_ amount of time or if the condition occurs.
the non timed wait blocks until the condition occurs, and waits forever if this does not happen.

in terms of cpu usage there is no difference during the wait, both send the process to sleep until the condition occurs (or the timeout is exceeded)

---

### Post by t1497f35 on 2011-02-13
Thanks, I've been wondering whether one method uses more CPU than the other.

---

