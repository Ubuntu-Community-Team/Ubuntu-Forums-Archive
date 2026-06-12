---
title: "Simpe asynchronous thread comunication?"
date: 2009-09-24
forum: Programming Talk
---

### Post by fredscripts on 2009-09-24
Hi!

I have 2 threads (pthreads, in C) running each one its own job (not related). In any moment of time, I need that one thread sends information to the other(say an integer), then the other receives it, and change its behaviour depending on the value.

I know how to do that with Processes (signal handler). I've read about thread conditions and so on, but I get kind of confused as I want it completely  asynchronous, avoiding one thread checking continuously if the other wants to send info to him.

Anyone can suggest (if possible post some sample code in C with pthreads), a signal/interruption asynchronous communication between 2 threads?

Thanks!

---

### Post by TheBuzzSaw on 2009-09-24
What you're asking for is a pretty tall order (in my experience, at least). I know it sounds enticing to use an asynchronous interrupt to communicate with another thread, but it is really much better to just have one thread set a variable in the other thread. That second thread doesn't have to be "constantly checking". Just have it check periodically when it is done with some of its work.

Have pseudo object A call B->heyYou(). Have it set a variable in object B, and B will get to it as soon as it can (make sure you make that variable **volatile**). The implications of interrupting thread B are not the best. Does the interrupt stop B mid-statement? Does the signal start some process outside of thread B?

Maybe someone with more experience in signal passing can come clean up after my post, but I personally advise against it.

What exactly are these threads doing?

---

### Post by doas777 on 2009-09-24
hmmm. 

the only environment that i have ever done that in is .net. using a callback delegate event.

---

### Post by CptPicard on 2009-09-24
Queues.

---

### Post by dwhitney67 on 2009-09-24
> **fredscripts said:**
> Hi!

I have 2 threads (pthreads, in C) running each one its own job (not related). In any moment of time, I need that one thread sends information to the other(say an integer), then the other receives it, and change its behaviour depending on the value.

I know how to do that with Processes (signal handler). I've read about thread conditions and so on, but I get kind of confused as I want it completely  asynchronous, avoiding one thread checking continuously if the other wants to send info to him.

Anyone can suggest (if possible post some sample code in C with pthreads), a signal/interruption asynchronous communication between 2 threads?

Thanks!

Protect the data using a mutex; it is as simple as that.  Before attempting to access the data, ensure that your thread locks the mutex, and after reading the value, unlock the mutex.

If you forsee the data changing often, then employ a queue (as CptPicard) suggested.  This queue would need to be thread-safe, thus once again a mutex would come into play.

If the thread that depends upon a value-change has performed all actions necessary since the value last changed, and then is waiting until the value (or an item is inserted into a queue), the best thing to do is to employ a condition-signal.  The condition-signal employs the use of a mutex.

In conclusion, the mutex is your "friend".  :-)

Here's a brief application that employs the use of a pthread condition, mutex, and lastly, an int.  (Sorry, the queue implementation, while trivial, is left as an exercise).
```

#include <pthread.h>
#include <unistd.h>
#include <stdio.h>

typedef struct
{
   pthread_cond_t  cond;
   pthread_mutex_t mutex;
} Condition;


typedef struct
{
   Condition cond;
   int       value;
} SafeInfo;


void* threadOne(void* arg)
{
   SafeInfo* info = (SafeInfo*) arg;

   const int was = info->value;

   pthread_cond_wait(&info->cond.cond, &info->cond.mutex);

   printf("Info received... was %d, now is %d.\n", was, info->value);

   pthread_exit(0);
}

void* threadTwo(void* arg)
{
   SafeInfo* info = (SafeInfo*) arg;

   usleep(100);

   info->value = 20;

   pthread_cond_signal(&info->cond.cond);

   pthread_exit(0);
}

int main()
{
   pthread_t tid1, tid2;
   SafeInfo  info;
   int*      status;

   pthread_cond_init(&info.cond.cond, 0);
   pthread_mutex_init(&info.cond.mutex, 0);

   info.value = 10;

   pthread_create(&tid1, 0, threadOne, (void*) &info);
   pthread_create(&tid2, 0, threadTwo, (void*) &info);

   pthread_join(tid1, (void**) &status);
   pthread_join(tid2, (void**) &status);

   pthread_cond_destroy(&info.cond.cond);
   pthread_mutex_destroy(&info.cond.mutex);

   return 0;
}

```

P.S.  My information may be wrong, but I believe Message Queues are thread-safe.  See mq_open(), mq_send(), etc.

---

### Post by fredscripts on 2009-09-25
Thanks so much!

---

