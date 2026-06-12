---
title: "pthread creation"
date: 2020-11-15
forum: Programming Talk
---

### Post by sundaresh on 2020-11-15
My simple test program to see if SIGTERM is raised when a pthread exits or if a SIGABRT is raised when a pthread is killed, compiles and executes but does not produce any of the printf output in the program.

---

### Post by spjackson on 2020-11-15
We would need to see some code in order to be able to determine why it is not doing what you expect. However, as I understand it, when a pthread exits, it does not raise any signal, nor does it when sent a signal via pthread_kill.

---

### Post by TheFu on 2020-11-15
> **sundaresh said:**
> My simple test program to see if SIGTERM is raised when a pthread exits or if a SIGABRT is raised when a pthread is killed, compiles and executes but does not produce any of the printf output in the program.

Perhaps start with saying the language involved?  Bash can capture signals, for example. pthreads are part of 20+ languages, perhaps 100+.  Are you programming in Raku? [https://raku.org/archive/rfc/178.html](https://raku.org/archive/rfc/178.html)

And showing some code?

---

