---
title: "simple pthread problem c++"
date: 2007-05-19
forum: Programming Talk
---

### Post by monkeyking on 2007-05-19
If I have 2 threads calling a function in my program,

are the local variables in this function shared between my threads or are they only for the calling thread?

thanks in advance

---

### Post by thumper on 2007-05-19
Any variables that you have declared normally are available for both threads.

However you need to be concerned about variables changing state in one thread and being read from another as there is the possibility of unexpected changes.  Even more concerning is changing the state in both threads at the same time.  This is where mutexes are used.

---

### Post by slavik on 2007-05-20
the only variables that are shared by threads are global variables

if you really want to know, change the variable and print it's address. the reason for changing it is because the linux kernel does a copy on write when it forks, same might be true for pthreads. if the threads report different address after the change then you can be 100% sure that that variable isn't shared :)

---

### Post by thumper on 2007-05-20
> **slavik said:**
> the only variables that are shared by threads are global variables
No, that isn't right.

> **slavik said:**
> if you really want to know, change the variable and print it's address. the reason for changing it is because the linux kernel does a copy on write when it forks, same might be true for pthreads. if the threads report different address after the change then you can be 100% sure that that variable isn't shared :)
When it forks yes, with pthreads no.

---

### Post by monkeyking on 2007-05-20
Well ok.

Is there a way to make the global variables not shared between the threads.
Like having a different addres space.

---

### Post by slavik on 2007-05-20
for globals, no ...

@thumper, what pthread library are you using??? last I check (1 month ago) NTPL 2.4 (edgy 6.10 pthread implementation) did as I wrote in my previous post (globals are shared between threads).

sharing of global threads is (was?) the whole point of threads, since sharing memory between processes is trickier ...

---

### Post by slavik on 2007-05-20
@thumper: [http://ubuntuforums.org/showthread.php?t=388837](http://ubuntuforums.org/showthread.php?t=388837)

look at my code and wonder how the main thread can see the changes done by the child threads. global variables are used to share data between the main thread and the child threads.

edit: sorry for double post

---

