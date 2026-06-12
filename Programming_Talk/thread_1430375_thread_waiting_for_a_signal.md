---
title: "thread waiting for a signal"
date: 2010-03-15
forum: Programming Talk
---

### Post by cybo on 2010-03-15
it seems like some people think that i ask for solutions for homeworks on these forums, so right from the beginning i'd like to say that i never ask for solutions on forums, i'm not interested in them. in fact i don't even want to see the solutions. where is the fun in solving the problem when you already have the solution?

the following question is not a homework question, however it did come out of several homeworks i already solved and i'm simply curious about it. i also would like to say that i'm relatively new to threads but interested in learning more about them.

say i created several threads (using pthreads library). these threads need to do something when a signal arrives. this signal is periodic. how would you go about threads waiting for a signal to arrive? 

below is some pseudo code:
```

void* mythread(void* arg) {
  printf("i'm in the thread\n");

  // wait for a signal to arrive

  // after the signal arrived print this
  printf("the signal has just arrived\n"); // this most likely will have to be done in the signal handler
}

```

i know how to setup the signal handler (through sigaction) and how to generate a signal but i can't figure out how to make a thread wait for signal.

any help is appreciated.

---

### Post by Xyro on 2010-03-15
Take a look at mutexes... muticies? Silly English language...

[man pthread]("http://www.manpagez.com/man/3/pthread/")

---

### Post by cybo on 2010-03-15
are there any other suggestions?

---

### Post by ApEkV2 on 2010-03-15
> **Xyro said:**
> Take a look at mutexes... muticies? Silly English language...

haha +1

@ op, in my limited knowledge of anything (so it seems), since threads share the caller's stack, you could use global switches.
But that seems quite an ugly solution though.

I'd wait for the better ppl to post comments though.

---

### Post by Linteg on 2010-03-15
> **cybo said:**
> are there any other suggestions?
Condition variables: [https://computing.llnl.gov/tutorials/pthreads/#ConditionVariables](https://computing.llnl.gov/tutorials/pthreads/#ConditionVariables)

---

### Post by johnl on 2010-03-15
> **Xyro said:**
> Take a look at mutexes... muticies? Silly English language...

[man pthread]("http://www.manpagez.com/man/3/pthread/")

I think in this case you would want a semaphore instead of a mutex.  Take a look at 'man sem_wait' which even helpfully includes an example at the bottom.

You would want to post to the semaphore (sem_post) in your signal handler, and wait for it (sem_wait) in your thread.

As an added bonus, sem_post is listed as one of the few functions that are actually safe to use in a signal handler.  Take a look at the "Async-signal-safe functions" section in 'man 7 signal' for more information about this.

Edit:
It's also worth noting that pthread conditionals are not safe to use in a signal handler:

> 
It is not safe to use the pthread_cond_signal() function in a signal handler that is invoked asynchronously. Even if it were safe, there would still be a race between the test of the Boolean pthread_cond_wait()  that could not be efficiently eliminated.

---

### Post by cybo on 2010-04-07
@everyone thank you

---

