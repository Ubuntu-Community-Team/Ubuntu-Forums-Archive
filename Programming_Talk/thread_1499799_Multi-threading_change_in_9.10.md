---
title: "Multi-threading change in 9.10?"
date: 2010-06-02
forum: Programming Talk
---

### Post by BillRebey on 2010-06-02
I have a program that runs two threads that use a resource that's protected by a mutex (pthread_mutex_lock/unlock).  

The threads accesses the resource in fairly tight loops with the typical "lock-access-unlock" pattern.

This used to work extremely well, such that when one thread issued an unlock, if the other thread was waiting to run, it would get a chance to run.

That doesn't happen any more after migrating from Ubuntu 8.10 to 9.x.  Now what happens is once a thread gets hold of the resource in its tight loop, it locks-uses-unlocks to its heart's content, and the other thread never gets a chance to run.  Each time an "unlock" is done, any waiting thread SHOULD get a chance to run.

Has this behavior changed intentionally?  Is there something new/special that I need to do when building my apps to get threads to work right?

Relevant compiler options are just "-pthread" (plus some debug [-g] options and a few -Warning options).

This software was worked for a long time, and suddenly quit.  I'm baffled!

Thanks for any help.

---

### Post by ssam on 2010-06-02
have you tested with a range of kernels?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by BillRebey on 2010-06-02
I've tried it with kernel 2.6.28 from Ubuntu 9.04, and it works better than it does in my kernel 2.6.31 from Ubuntu 9.10.

Apparently there is SOMETHING about the kernels that's different.  I need it to work with off-the-shelf Ubuntu installations, though, so I can't go around mixing-and-matching kernels.

Any thoughts on how I might FORCE a mutex_unlock in one thread to cause the next waiting thread to be granted the lock?

---

### Post by uOpt on 2010-06-02
Well, the kernel is doing a sensible thing. Just giving the mutex right back to the same thread is more efficient as you don't have to reschedule the other thread. Ever.

Overall I wonder whether you have enough CPU cycles spent outside that lock. It sounds like you do not, otherwise this problem wouldn't happen. If you do not have significant CPU cycles (or real time wait or something) outside the lock the question is why do you multithread this piece of code in the first place? It might be faster to just do the thing in question without threads and without locks.

If all of this is really unavoidable, I think you should wrap this in a condition variable which should give a more even chance for waiting threads to get the lock. But this increases the overhead even more, so again you need to have a look at whether you have significant enough work outside the lock in the first place.

---

### Post by BillRebey on 2010-06-02
uOpt,

Thanks for the thoughts and comments.  I have plenty of resources available (CPU), it's just that the scheduler got changed recently and doesn't work the same as it used to.  

The solution was to specifically set the priorites of each thread, such that the "stranded" thread (which uses the resource in question much less frequently) had a HIGHER priority than the thread that spins on the resource and hogs it.  This forced the scheduler to give the previously-stranded thread access to the resource every time it was unlocked while the stranded thread was waiting on it, thus providing EXACTLY the behavior I need.

If anyone else has this problem, pthread_setschedparam() is your friend.  In its simplest form, here's how to get a thread running with a specific priority:   

```

pthread_attr_t attr;
pthread_attr_init(&attr);

pthread_t hThread;

pthread_create (&hThread, &attr, (void *(*)(void *))functionToCall, pDataToThatFunction);

struct sched_param param;
param.sched_priority = priority;	// This is the priority number to assign the new thread

pthread_setschedparam (hThread, SCHED_FIFO, &param);

```

---

### Post by uOpt on 2010-06-02
The question remains: are you actually doing anything significant outside the lock?

If not then you need to re-think multithreading that piece.

If yes then it should be possible for the second thread to never get the lock.

---

### Post by MadCow108 on 2010-06-02
if your lock is really in such a tight loop doing so little work you should consider a different synchronization scheme.
A normal mutex has significant costs for context switches, so the kernel will try to avoid it resulting in your problem.
It has no place in a tight loop used by multiple threads.

If you can't avoid the locking , you can probably improve the situation with a spinlock or even atomics.

---

### Post by dwhitney67 on 2010-06-02
> **BillRebey said:**
> uOpt,

Thanks for the thoughts and comments.  I have plenty of resources available (CPU), it's just that the scheduler got changed recently and doesn't work the same as it used to.


You may be right, but you maybe wrong.

I wrote a small app that exercises two threads, which happen to do the exact same thing, and that is merely to increment a counter to a certain value N (ie. 10000).  To increment their respective counter, the threads must acquire a lock on a mutex that is shared between the two.

Sometimes Thread-1 finishes it's task before Thread-2, and sometimes it is the other way around.  This tells me that my 9.10 OS is giving each thread a fair share of the CPU, and the fact that one finishes first over the other is merely coincidental/luck.

So, what are your threads doing?  I almost bet they are doing more in their "tight" loop than mine are.


P.S.  Here's my thread routine (written in C++):
```

   static void* run(void* arg)
   {
      Thread* t = reinterpret_cast<Thread*>(arg);

      for (int i = 0; i < 10000; ++i)
      {
         pthread_mutex_lock(&(t->myMutex));

         ++(t->myCounter);

         pthread_mutex_unlock(&(t->myMutex));
      }

      std::cout << "Thread " << t->myId << " is done." << std::endl;

      return 0;
   }

```

---

### Post by BillRebey on 2010-06-09
Thanks everyone for your comments, but as often happens many have misunderstood the nature of the problem and have suggested "don't do that" as a cure.

The code is indeed designed quite correctly, and there is a great deal of work going on inside the lock, including disk I/O.  Spins or atomics are wholly inappropriate here.  The "tightness" of the "tight loop" that I mentioned isn't insdide the lock at all;  the tightness is between one UNlock call and the next lock call - at the end of the loop as it cycles around for the next iteration.  

The whole purpose of the thread is to run periodically and drain a queue.  Not threding this part of the program would defeat the purpose of the program.  The "hogging" thread in question (the one that drains the queue) and the "starved" thread (the one that fills it) both access the same queue - one fills it steadily, but slowly, and the other empties it only periodically, but ravenously.  (I.e., the filler might add and entry every 100 milliseconds, but the drainer might need to drain the entire queue every 10 minutes).  Both activities must occur without unduly stalling the other.  

The proper solution - or the real "cure" - is not to avoid the issue altogether but to properly prioritize the threads so that when the higher-priority "filler" is waiting on the lock, it will be scheduled in as soon as the lower-priority drainer releases the lock from removing and item, thus allowing the two threads to properly interleave.

---

### Post by Axos on 2010-06-09
The queue is locked while a request is being processed? The traditional design is to lock the queue while an item is being added or removed. As soon as an item is removed, the lock is released and the item is processed. Adding an item to the queue and processing an item should not be mutually exclusive.

---

### Post by uOpt on 2010-06-09
> **BillRebey said:**
> 
The proper solution - or the real "cure" - is not to avoid the issue altogether but to properly prioritize the threads so that when the higher-priority "filler" is waiting on the lock, it will be scheduled in as soon as the lower-priority drainer releases the lock from removing and item, thus allowing the two threads to properly interleave.

That doesn't sound like a proper solution at all. What happens if you have more than two threads? What you effectively do is after try-n-erroring you have found that penalizing the main thread happens to do what you want right now. It won't for long.

And you completely misunderstood what we were saying. We weren't concerned about the amount of work going in inside the lock. We are concerned about the amount of work outside the lock. It sounds like you do nothing there. Otherwise how would the main thread always be able to grab the mutex right away again?

---

### Post by BillRebey on 2010-06-09
Axos,  it's a long story that heralds back to a port of a product from a microcontroller platform to full-blown Ubuntu;  the two platforms work very differently.

At any rate, a Q  item can't be removed from the Q until it's delivery has been confirmed, and while the queueing system DOES have a "read now and advance later" mechanism so that I can fetch an item, send it, and only advance the Q after delivery confirmation, I can't allow the queue writer thread to write to the Q until after the "advance" (or "rollback", in the event of deliver failure) is called;  it's a shortcoming of the Q system;  both the reader and writer mess with the same data, so they have to mess with it exclusively.  I'm working on a new queueing mechanism, but for today, this has to work.

You're quite right, though, in your observation...a system that locks up the whole danged queueing sytem while it's trying to deliver something from it is just plain horse puckey!  For today, though...I'm just trying to make it work.

---

### Post by dwhitney67 on 2010-06-09
> **BillRebey said:**
> Axos,  it's a long story that heralds back to a port of a product from a microcontroller platform to full-blown Ubuntu;  the two platforms work very differently.

At any rate, a Q  item can't be removed from the Q until it's delivery has been confirmed, and while the queueing system DOES have a "read now and advance later" mechanism so that I can fetch an item, send it, and only advance the Q after delivery confirmation, I can't allow the queue writer thread to write to the Q until after the "advance" (or "rollback", in the event of deliver failure) is called;  it's a shortcoming of the Q system;  both the reader and writer mess with the same data, so they have to mess with it exclusively.  I'm working on a new queueing mechanism, but for today, this has to work.

You're quite right, though, in your observation...a system that locks up the whole danged queueing sytem while it's trying to deliver something from it is just plain horse puckey!  For today, though...I'm just trying to make it work.

You make it sound like you are engrossed in rocket science!

Multi-threaded applications that employ the use of a queue have been around for decades; there's nothing magical about it.  Either the developer need to ensure the queue they choose is thread-safe, or they use one that already is (eg. Message Queue).

---

### Post by Axos on 2010-06-09
Ah, legacy code. I understand now (only too well).

---

