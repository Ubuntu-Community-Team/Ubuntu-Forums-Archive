---
title: "fork() in a thread"
date: 2008-11-24
forum: Programming Talk
---

### Post by jordanguyoflove on 2008-11-24
Hi,

What happens when fork() (creating a new process) is called in a thread?

I read that it either duplicate all threads or duplicates the thread that invoked the fork.

But I can't understand how they could be 2 options. :confused:


Thanks.

---

### Post by snova on 2008-11-24
It starts a new process.

The tricky thing about fork() is that it returns twice, once in each process. The parent process will get the child PID as the return value, the child will get 0 (as I recall).

If you called it in a thread, the result would be two threads and one subprocess.

---

### Post by stroyan on 2008-11-24
The fork call will create a new process with one thread.
You can confirm that by reading "man fork".
A threaded program can make specific functions be called
in each thread before and after fork by calling pthread_atfork().
That gives threads an opportunity to put resources into
a good state before fork and restore them to their normal
state after a fork.  See "man pthread_atfork" for more details.

---

