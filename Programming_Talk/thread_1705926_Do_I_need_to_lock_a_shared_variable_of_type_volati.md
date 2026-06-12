---
title: "Do I need to lock a shared variable of type volatile sig_atomic_t in a multithreaded"
date: 2011-03-13
forum: Programming Talk
---

### Post by guest_user on 2011-03-13
Q1) Do I need to lock a shared variable of type volatile sig_atomic_t in a multithreaded program?
Q2) also, is it safe to call pthread_mutex_lock or pthread_rwlock_wrlock in a signal handler?

the reason I ask this is because I have a multithreaded server and when I type ctrl-c which generates SIGINT, I want the signal handler to modify a shared boolean variable exitFlag from false to true so that the server thread would upon looking the next time at the shared variable determine that it is time to exit and return cleanly(that means, stop accepting any new connections and join any threads handling existing transactions after they have completed). 

language is C/C++

---

### Post by Tony Flury on 2011-03-13
> **guest_user said:**
> Q1) Do I need to lock a shared variable of type volatile sig_atomic_t in a multithreaded program?

Can more than one thread change the variable, if so can they change it to anything they want, or does it only go from FALSE to TRUE? If it is only a flag and can only be set (and never cleared) you probably don't need to worry about locking it, as two threads trying to change it will both change it to TRUE - so it wont matter in which order they do things.
If it can bet set or cleared by any thread at any time - you will need to lock it to avoid one thread setting it and another clearing it.

---

