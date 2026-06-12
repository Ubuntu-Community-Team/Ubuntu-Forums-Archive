---
title: "Pthread Question: Is Unlocking a Mutex from a Different Thread Supported?"
date: 2009-08-11
forum: Programming Talk
---

### Post by kresyzig on 2009-08-11
It seems that unlocking a mutex from a thread that is different from the one where it was locked is not supported by POSIX standards:

       pthread_mutex_unlock  unlocks  the given mutex. [B]The mutex is assumed to
       be  locked  and    owned  by  the     calling   thread   on     entrance   to
       pthread_mutex_unlock[/B].    If   the   mutex  is  of  the  ``fast''  kind,
       pthread_mutex_unlock always returns it to the unlocked state. If it  is
       of the ``recursive'' kind, it decrements the locking count of the mutex
       (number of pthread_mutex_lock operations performed on it by the calling
       thread),  and  only  when this count reaches zero is the mutex actually
       unlocked.

       On ``error checking'' mutexes, pthread_mutex_unlock actually checks  at
       run-time  that  the mutex is locked on entrance, and that it was locked
       by the same thread that is now calling pthread_mutex_unlock.  If  these
       conditions are not met, an error code is returned and the mutex remains
       unchanged.  ``Fast'' and ``recursive'' mutexes perform no such  checks,
       thus  allowing a locked mutex to be unlocked by a thread other than its
       owner. **This is non-portable behavior and must not be relied upon**.

If I actually need to do something equivalent, what is the most efficient way to do it?

For example, let's say that I have a main thread and 2 "slave" threads and that I want to activate the slave threads at some point in the main thread and wait for them to complete before continuing. Right now I am doing the following:

Main Thread:
Lock Mutex Ai
Lock Mutex Bi
Lock Mutex Af
Lock Mutex Bf
CONTINUE=true
Start Thread A
Start Thread B
...
FOR LOOP {
   //Ask the slave threads to start
   Unlock Mutex Ai
   Unlock Mutex Bi
   ...
   //Do some stuff while the threads are running
   ...
   //Wait for the threads to complete
   Lock Mutex Af
   Lock Mutex Bf
   Read Thread A result
   Read Thread B result
   Combine Thread A & B results
   ...
}
...
//Stop the threads
CONTINUE=false
Unlock Mutex Ai
Unlock Mutex Bi
Unlock Mutex Af
Unlock Mutex Bf
Wait for Thread A to terminate
Wait for Thread B to terminate

Thread A:
INFINITE LOOP {
   Lock Mutex Ai
   IF(CONTINUE) {
     ...
     //Compute stuff
     ...
     Store result
   } ELSE return
   Unlock Mutex Af
}

Thread B:
INFINITE LOOP {
   Lock Mutex Bi
   IF(CONTINUE) {
     ...
     //Compute stuff
     ...
     Store result
   } ELSE return
  Unlock Mutex Bf
}

To me it seems to be an efficient way to do parallel processing (for a particular application where the results from both slave threads need to be combined after each iteration). Is there another way that is as efficient, but POSIX-compliant, to do the same thing?

Thanks!

---

### Post by dwhitney67 on 2009-08-11
IMO, you should not rely on a mutex to control the execution of a thread.  Use it to protect against concurrent access to data that two or more threads may use.

As for your problem description, I haven't a clue about what you have stated.  As a rule of thumb, when you have doubts about what you are doing, it is best to describe what you want to accomplish, not how you want to do it.  For all we know, there might be a better/simpler approach to meeting your requirements.

P.S.  Maybe what you need is condition signal (ie. pthread_cond_wait()).

---

### Post by kresyzig on 2009-08-11
> **dwhitney67 said:**
> IMO, you should not rely on a mutex to control the execution of a thread.  Use it to protect against concurrent access to data that two or more threads may use.

Why exactly is it bad to rely on a mutex to control the execution, even if it is done in such a way that it cannot create a dead lock or a race condition?

> As for your problem description, I haven't a clue about what you have stated.  As a rule of thumb, when you have doubts about what you are doing, it is best to describe what you want to accomplish, not how you want to do it.  For all we know, there might be a better/simpler approach to meeting your requirements.What I want to do is to process some objects in parallel (it can be large arrays of data, histograms to be filled or normalized, evaluate the bin content for a given array, etc), and then return them to the main thread where they are eventually combined to generate a single value. This code has to be very general and be able to handle all kinds of objects, so I cannot be really more specific than that. What is important though is that the threads cannot start processing data again until the main thread requires it and then once they are done they must notify the main thread in some way. So I guess the pseudo-code I wrote in my first message pretty much describes what I need to do. I have an algorithm already that optimizes the number of threads and which tasks are assigned to them... The main issue I think is to make my code POSIX-compliant while minimizing overhead.

> P.S.  Maybe what you need is condition signal (ie. pthread_cond_wait()).Well, I know that I could rewrite my code by using signals, but this would be slower since it would lock and unlock mutexes many times...

---

### Post by slavik on 2009-08-12
locking/unlocking a mutex is not slow, because the mutex lives inside your process (unlike semaphores).

seems like your issue is a communication issue. so what you should do is write a thread-safe queue "class" to hold whatever data you need. You will have 2 of these queues, 1 for data, the second for results. since the queues are threadsafe, there will be some mutex that has to be locked before queue is changed (data added/removed) and unlocked after such operation. you can also have the queue limit itself to how many things it can store by putting a lock in and not releasing it when it has some number of things in it (if you are concerned about memory usage).

hope this helps.

---

### Post by Cenoforums on 2009-08-15
> It seems that unlocking a mutex from a thread that is different from the one where it was locked is not supported by POSIX standards:

The questions is not whether it is or it isn't standard, a mutual exclusion lock is used to ensure mutual exclusion on a **critical section**. I don't see any of that in your code. Do your threads even have a variable in common, say an array?

I'm trying to understand why you chose to do something so complicated. I think I understand what you're trying to do, but because you're using mutex locks do control flow instead of the actual access to information it's hard to tell. Does the following code do the same as yours?

main thread:

FOR() {

start thread_a, thread_b

//Do some stuff while the threads are running

pthread_join(thread_a and thread_b)
read&combine results
}

thread_a:
//compute stuff

thread_b:
//compute stuff

---

### Post by RossPJohnson on 2011-02-11
> **Cenoforums said:**
> 

I think I understand what you're trying to do, but because you're using mutex locks to do control flow instead of the actual access to information it's hard to tell. Does the following code do the same as yours?

main thread:

FOR() {

start thread_a, thread_b

//Do some stuff while the threads are running

pthread_join(thread_a and thread_b)
read&combine results
}

thread_a:
//compute stuff

thread_b:
//compute stuff

This is a somewhat late response, but as the thread stopped at this point it's worth
commenting.

The above will do the job, but starting new threads and joining them for each iteration is very inefficient. Instead, start your threads and synchonise them.

Try googling "pthreads producer consumer solutions"

Also effective are pthread_barrier_wait and pthread_cond_wait if the problem suits.

---

### Post by slavik on 2011-02-12
dead thread

---

