---
title: "Why are my threads (largely) in serial order?"
date: 2014-11-03
forum: Programming Talk
---

### Post by IAMTubby on 2014-11-03
Hello,
 Please see my code below, where I invoke 100 threads. I have the following questions. Please see the log file attached when referring to the below questions.

1. Why are my threads largely in serial order? I find it to be mostly in ascending order from 0-99. Shouldn't the order of threads be not able to predict?
2. Some threads like 68 etc are executed many times. The only reason I can think of is it's getting thrown out by another thread and then coming back to print again. But I do have a mutex lock - mutex unlock inside the function which prints the thread id.
3. Why don't I see all numbers between 0-99? Thread ids from 71 onward are missing and possibly some more in between 0 and 71.

```

#include <stdio.h>
#include <pthread.h>


void* fun(void*);


pthread_mutex_t lock;
int counter = 0;


int main(void)
{
 int ret = 0;
 pthread_t th[100];
 int i = 0;


 pthread_mutex_init(&lock, NULL);
 
 for(i=0;i<100;i++)
 {
  pthread_create(&th[i], NULL, fun, &i);
 }
 
 //sleep
 for(i=0;i<100;i++)
  pthread_join(th[i],NULL);


 pthread_mutex_destroy(&lock);
 return 0;
}


void* fun(void* arg)
{
 int i = 0;
 pthread_mutex_lock(&lock);
 int* ptr = (int*)arg;

/* I get threads in serial order even upon un-commenting this for loop */
 /*for(i=0;i<0xFFFFFFFF;i++)
 {
 }*/
 printf("ThreadID : [%d]\n",*ptr);
  
 pthread_mutex_unlock(&lock); 
 //return NULL;
}

```

Please advise
Thanks.

---

### Post by spjackson on 2014-11-03
The answer to all of your questions is that you are passing the same address to every single thread. When you do
```

printf("ThreadID : [%d]\n",*ptr);

```
You are printing whatever the value of main's i variable is at this point in time, not the value when fun was first called.

I suggest you do something like this.

```

int thread_args[100];

for(i=0;i<100;i++)
 {
  thread_args[i] = i;
 }

for(i=0;i<100;i++)
 {
  pthread_create(&th[i], NULL, fun, &(thread_args[i]));
 }

```
Then you will get a more sensible picture of the order in which each thread reaches the printf statement (which is in fact the order in which they reach the pthread_mutex_lock call).

---

### Post by IAMTubby on 2014-11-03
> **spjackson said:**
> The answer to all of your questions is that you are passing the same address to every single thread.
I suggest you do something like this.

```

int thread_args[100];

for(i=0;i<100;i++)
 {
  thread_args[i] = i;
 }

for(i=0;i<100;i++)
 {
  pthread_create(&th[i], NULL, fun, &(thread_args[i]));
 }

```
Then you will get a more sensible picture of the order in which each thread reaches the printf statement (which is in fact the order in which they reach the pthread_mutex_lock call).
spjackson, such a simple solution to all my three questions. Thank you so much. It works now.

---

### Post by IAMTubby on 2014-11-27
> **spjackson said:**
> 
I suggest you do something like this.

```

int thread_args[100];

for(i=0;i<100;i++)
 {
  thread_args[i] = i;
 }

for(i=0;i<100;i++)
 {
  pthread_create(&th[i], NULL, fun, &(thread_args[i]));
 }

```

I'm sorry spjackson, but how's this even working? The pthread_create which calls fun is [B]still running in a loop controlled by i, and thread_args[i] depends on i.

EDIT : 
[/B]I just thought about it some more> **spjackson said:**
> You are printing whatever the value of main's i variable is at this point in time, not the value when fun was first called.
Which means in multi-threaded programs, the value of i  at "this point in time" is expected to be different from when it was called.
So, do you mean to say that the value of i changes between the time when it calls the function, and when it actually comes inside the function definition? Wow! :)

Is that because main is also a thread just like any other thread, in which you are making all these calls. But the new threads you have created also try to co-exist in the environment, and that brings about the change? Please clarify. Happy Thanksgiving!

---

### Post by ofnuts on 2014-11-28
In you code you pass the address of "i". Now consider this:

[LIST]
[*]the main code sets i=59 and starts thread #59
[*]thread#59 starts running, and then is interrupted
[*]the main code sets i=60 and starts thread #60
[*]thread #60 runs, reaches the printf instruction, fetches the value of i and prints a 60
[*]the scheduler put thread #59 back to execution, it reaches the printf instruction, fetches the value of i and prints a 60, too. In fact it could be put back to execution much later, and will print whatever the i variable is set to that the time.
[/LIST]

The worst case would be that your main thread runs uninterrupted and starts 100 threads, then all threads execute and they all print "100".

spjackson's fix is that each thread is passed a pointer to data that is specific to the thread, and that will not change while the thread is running.

Why are the thread more or less in order? Because even if you can't really predict when they threads are going to be scheduled, the scheduler algorithm has an "age" criteria, so, all other things being equal, the first interrupted thread s more likely to be put back to run state.

---

