---
title: "posix thread calling external program"
date: 2010-04-15
forum: Programming Talk
---

### Post by andradx on 2010-04-15
Hey. I'm basically trying to replicate what is achieved with a call to execvp() while programming in POSIX threads. The reason it needs to be in POSIX threads arise from having to set the program running in a specific core which can be done with a call to pthread_setaffinity_np().


How can I make the thread execute an external and executable application in the same fashion as one would using execvp()?



Thanks.

---

### Post by heikaman on 2010-04-15
Hi, you can set the affinity of a process:

1- fork
2- getpid
3- sched_setaffinity (man sched_setaffinity)
4- exec?

Hope this helps

---

### Post by MadCow108 on 2010-04-15
I'm not entirely sure but I don't think that works

a thread and a process are not the same thing.
Executing an external program usually involves creating a process and not a thread.

But heikaman solution should work

---

### Post by andradx on 2010-04-15
I didn't know how to migrate a process to a different core. I suspected that a thread couldn't run an executable, hence my question:)

That solved my problem. Thank you.

---

