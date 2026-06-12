---
title: "pthreads questions"
date: 2009-08-28
forum: Programming Talk
---

### Post by verymagicalguy on 2009-08-28
I'm very new to writing multithreaded code in general. I'm trying to implement multithreading in C++ using pthreads to load something from disk.

I'm wondering if there's anyway to get the return value from a thread created by pthreads_create. (Or is that not even possible since the return value must be void?)

I'm trying to prevent race conditions between threads.

Also, I'm trying to use OpenSceneGraph, is there a better way to multithread with it? I can't seem to find much about multithreading with it online. 

Thanks!

---

### Post by napsy on 2009-08-28
Avoid using threads, if possible. They only lead to frustrated debugging.
If you return from your thread, you will end it's executions. So what you probably want is a variable that can be accessed by a thread and another function.

---

### Post by verymagicalguy on 2009-08-28
> **napsy said:**
> Avoid using threads, if possible. They only lead to frustrated debugging.
If you return from your thread, you will end it's executions. So what you probably want is a variable that can be accessed by a thread and another function.

Any recommendation besides pthreads then? Thanks!

---

### Post by napsy on 2009-08-28
pthreads are "de facto" implementation of threads on linux. There are some other but I don't have any experience with them.

If you know what are you doing and protecting shared resources, then it should be ok to use as many threads as needed in your program.

---

### Post by MadCow108 on 2009-08-28
an alternative to pthreads would be openMP
openMP is incredibly easy just add a few pragmas and your code is parallised
but it's restricted to shared memory systems.

if you have a distributed memory system consider MPI

---

### Post by smakand on 2009-08-28
Wait you need a return value from a thread? What is your main thread going to be doing while the other thread is loading?
What you probably need is something like this
[https://computing.llnl.gov/tutorials/pthreads/#Mutexes](https://computing.llnl.gov/tutorials/pthreads/#Mutexes)
And pass the pointer of resource you loaded.

And there's nothing wrong with pthreads or multithreading.

---

### Post by RocketRanger on 2009-08-28
To expand on smakands answer. You'll want to read up on semaphores to accomplish what you need. You don't want to return a value from a thread you want to exchance data between your threads.

Helpful?

---

### Post by dribeas on 2009-08-29
You cannot return anything from the function but you can use shared memory to exchange data among threads. Do not forget to provide mechanisms to make your data exchange thread safe. 

Now with C++, if you can use some higher level libraries, I can recommend you boost::threads (really simple and powerful) the tutorials on-line should be fairly simple to follow. The new standard threading mechanisms in C++ (C++0x, or 1x... whenever) have been tailored after boost::threads, so this will also be an investment on the future.

---

### Post by soltanis on 2009-08-29
I'm echoing a previous poster here when I recommend OpenMP. This system is surprisingly easy to use, and if you are using pthreads you are on a shared memory system anyway. Parallelizing loops is as simple as one pragma and creating worker threads is not that much harder.

OpenMP takes advantage of multiprocessor systems to speed up your code. Even on a single core system, I think it can produce speedups if your code is waiting for I/O.

---

### Post by dwhitney67 on 2009-08-29
I'm confused; why does everyone seem to think that it is not possible to return a value from a thread?  It _is_ possible.

The start routine for a pthread has the following signature:
```

void* (*start_routine)(void*)

```

Thus as an example, one could implement their thread program as:
```

#include <stdio.h>
#include <pthread.h>

void* my_thread(void* arg);

int main()
{
   pthread_t tid;
   int       arg = 10;
   int       status = 0;

   pthread_create(&tid, 0, my_thread, &arg);

   pthread_join(tid, (void**) &status);

   printf("status = %d\n", status);
}

void* my_thread(void* arg)
{
   int status = 200;
   return (void*)status;
}

```

P.S.  Sorry for writing the code in C and not C++; but hopefully the gist is there.  If you are using Boost threading, then obtaining the thread status is even easier.

---

