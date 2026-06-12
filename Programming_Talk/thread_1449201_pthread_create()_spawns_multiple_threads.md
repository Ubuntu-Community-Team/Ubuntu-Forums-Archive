---
title: "pthread_create() spawns multiple threads"
date: 2010-04-07
forum: Programming Talk
---

### Post by DBQ on 2010-04-07
Hi everybody.

I have a problem. In the for loop I create n threads. However, when I run the program through GDB I see that each single pthread_create() call spawns multiple threads. Why is this happening?

---

### Post by tookyourtime on 2010-04-07
Well does the function that you start in the new thread end up creating more threads itself?

And what is the code for your loop?

---

### Post by DBQ on 2010-04-07
My code is something like this:

```

void* thread_func()
{
   sleep(100);
   pthread_exit();
}

for(i=0; i < 10; ++i)
{
   pthread_create();
}

```

---

### Post by tookyourtime on 2010-04-07
Sorry I still think more information is needed to be able to find the problem.

Full source code, how many more threads are created than expected? 
And what is the aim of the program?

---

