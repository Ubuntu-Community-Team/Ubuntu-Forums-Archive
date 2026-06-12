---
title: "Semaphore for N process"
date: 2011-11-19
forum: Programming Talk
---

### Post by Mr.Pytagoras on 2011-11-19
Hi

I'm not sure whether this is the right subforum but here is the problem:

I'm trying to understand the semaphores
I have a task that I have a N proceses and I have to ensure that it will get executed one after another

P1 > P2 > P3 > .. > PN

I think that it could be done with one semaphore and a variable that will store the process number to be executed, and when the process P1 stop it increment the variable to 2 and the process P2 then can start. However I'm not quite sure how can I do it, nor do I understant the whole semaphore concepth.

Is here a good soul that would explain it to my?

Many thanks

---

### Post by San_SS! on 2011-11-19
To be simple, a semaphore is a "structure" to synchronize processes in a multi-process environment. Semaphores have an internal positive integer value and processes can interact with the semaphore using **ONLY** two functions **acquire** and **release** which execute atomically. Their behavior is as follows:

**Acquire:** Wait until the value is greater than 0, when it is, decrease it by one and continue execution.

**Release:** Increase the value of the semaphore by 1.

What you are trying to make are barriers using semaphores. It can be done using only one semaphore and a value but it wouldn't be practical.

I would recommend using a "split binary semaphore"(a group of semaphores whose sum of their value is 0 or 1) having N semaphores, one for each process. All starting with 0 except for p1's semaphore that starts with one.

Basically the idea is that each process waits til its semaphore gives him green light, do what needs to be done and gives green light to the next:

```
process i:

acquire(sem[i]);
//Do work
release(sem[i+1]);
```

Hope this helps ya,
Bye Bye

---

### Post by Mr.Pytagoras on 2011-11-20
Thanks a lot

Just out of curiosity how would it looks like with one semaphore

And why is it no practical?

---

### Post by San_SS! on 2011-11-20
If you had only one semaphore and one variable each process would be something like this:

```

process i:

cond = True;
while cond
   acquire(semaphore);
   if (var == i)
      cond = False;
   else
      release(semaphore)
end while
//do work
var = var + 1;
release(semaphore);

```

in that way each time there's a change in process they are all asking if they are the one who process, this is a loss of cpu time. AND you can't guarantee that the program will finish due tu the fact that there's no guarantee that the semaphore is fair in who wakes up, so if one process beats the others in acquiring the semaphore you will end up in an infinite loop.

---

### Post by Mr.Pytagoras on 2011-11-20
> **San_SS! said:**
> If you had only one semaphore and one variable each process would be something like this:

```

process i:

cond = True;
while cond
   acquire(semaphore);
   if (var == i)
      cond = False;
   else
      release(semaphore)
end while
//do work
var = var + 1;
release(semaphore);

```in that way each time there's a change in process they are all asking if they are the one who process, this is a loss of cpu time. AND you can't guarantee that the program will finish due tu the fact that there's no guarantee that the semaphore is fair in who wakes up, so if one process beats the others in acquiring the semaphore you will end up in an infinite loop.

Thanks

I think I understant the concept 

So the execution of the process stops at the *acquire(semaphore);* line and that there it is waiting for anather process in this case i-1 to call a release(semaphore) and to ensure that the whole group of processes could start the semaphore has to be inicialized at 1.
Do I understant it correctly?

Anyway thanks you a lot

---

### Post by San_SS! on 2011-11-20
Yeah, you're right. Each process does something like this:
"While it is not my turn: grab the semaphore control, check whether it's my turn or not. If not release the semaphore. Do my job, increase the value so i tell the next process it's its turn and release the semaphore."

The problem here is that in the while you can not guarantee how long it will take to the corresponding process to grab the semaphore's control.

---

### Post by ve4cib on 2011-11-20
> **Mr.Pytagoras said:**
> Hi

I'm not sure whether this is the right subforum but here is the problem:

I'm trying to understand the semaphores
I have a task that I have a N proceses and I have to ensure that it will get executed one after another

P1 > P2 > P3 > .. > PN


You could do this fairly easily with n semaphores (one for each thread).  Create n semaphores (integers s1, s2, ..., sn) and set them all to 1 (locked).  Start all of the threads, and unlock s1.  When you enter the thread you lock its semaphore (i.e. thread 2 would lock s2 first), then do its processing, unlock its semaphore, and then unlock the semaphore for the next process.

Each thread's code would look something like this:

```

// Thread X
lock(sx);
doStuff();
unlock(sx);
unlock(sx+1);

```


A more concrete example:
```

// initialization in main:
int s1, s2, ..., sn;  // create n semaphores
for i=1 to n
   lock(si);  // lock all of them

for i=1 to n:
   startThread(i);  // start all of the threads

// unlock s1, so that thread #1 can execute
unlock(s1);

----------

// Thread 1:
lock(s1);
doStuff();
unlock(s1);
unlock(s2);

----------

// Thread 2:
lock(s2);
doStuff();
unlock(s2);
unlock(s3);

----------

// Thread 3:
lock(s3);
doStuff();
unlock(s3);
unlock(s4);

...

// Thread n:
lock(sn);
doStuff();
unlock(sn);
// there is no sn+1, so there's no additional unlock here

```

Each thread tries to lock its semaphore (which is initially locked).  Therefore it is blocked.  Once thread X executes it unlocks the semaphore for thread X+1, allowing thread X+1 to lock its own semaphore and execute.  This continues for thread X+2, X+3, etc... up to thread n.  Obviously there is no semaphore for thread n, so it only has a single unlock operation at the end.

---

### Post by Mr.Pytagoras on 2011-11-22
Thanks

You have really helped me. I understant it now.

---

