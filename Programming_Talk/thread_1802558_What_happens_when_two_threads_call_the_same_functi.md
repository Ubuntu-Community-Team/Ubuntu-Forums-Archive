---
title: "What happens when two threads call the same function?"
date: 2011-07-12
forum: Programming Talk
---

### Post by TheHimself on 2011-07-12
I'm trying to use pthreads but don't know what happens when two simultaneous threads call the same function. I think two independent copies of the function and its internal variables would be created?

---

### Post by Npl on 2011-07-12
dunno, either the universe explodes or it just works fine.
Depends on what you do in this function, if you arent **writing** static or global (atleast shared between the threads) data then everything is fine, local variables live on the stack and threads have their own stack each, so aslong there isnt anything that can change outside of the thread then it doesnt matters how many threads are accessing the function (the code of the function exists only once btw).

as soon as you write shared resources somewhere outside of a thread using them you ought to know what you can do, and what you shouldnt do, but that highly depends on what you want to archive. Luckily most of the times its only your program that will behave odd, but always think of the imploding universe if you write threaded code!

---

### Post by ve4cib on 2011-07-12
As Npl said, it depends greatly on what the function does.  If the function uses only local variables the you're fine.  Two completely independent copies of the function's variables are created, one for each thread.

The tricky stuff starts when the threads make use of shared data (static/global variables, pointers to shared memory, external files, and the like).  If both threads write to the same place you can easily run into data corruption issues -- a common problem when synchronizing multi-threaded programs.

To deal with those kinds of problems I suggest you do some research and read about mutexes and semaphores if you're not familiar with them already.  They of course have their own fun problems (deadlocks and resurce starvation chief among them), but no solution is perfect.

---

### Post by JupiterV2 on 2011-07-12
You also need to be aware, at least with C and C++, of which standard library functions you are using. You need to be careful to know when you need to use re-entrant functions when multi-threading.

---

### Post by Simian Man on 2011-07-12
> **JupiterV2 said:**
> You also need to be aware, at least with C and C++, of which standard library functions you are using. You need to be careful to know when you need to use re-entrant functions when multi-threading.

*Cough* strtok *Cough*.

---

