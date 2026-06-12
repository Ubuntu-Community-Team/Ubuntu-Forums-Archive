---
title: "pthreads &amp; variables"
date: 2009-07-29
forum: Programming Talk
---

### Post by CryptiniteDemon on 2009-07-29
Okay, so I'm starting out with pthreads and I'm wondering if it's possible to change the variable I pass along with pthread_create.

At the moment I'm not concerned with race conditions and mutexes. I just want to see if I can do this simple thing.  For instance, I have the following code that I can't get to work.  The idea is that "int i" is 5 at first, and then the thread changes it to 7.

So can I do it or not?

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <pthread.h>
 
static void wait_thread(void)
{
    time_t start_time = time(NULL);
    while (time(NULL) == start_time)
    {
    }
}
 
static void *thread_func(void * number)
{
    number = (int*) 7;
    return NULL;
}
 
int main(void)
{
    int i = 5;
    pthread_t thread;
    if (pthread_create(&thread, NULL, thread_func, (void *) &i) != 0)
    {
        return EXIT_FAILURE;
    }
	
	wait_thread();
	printf("%i\n", i);
    if (pthread_join(thread, NULL) != 0)
    {
        return EXIT_FAILURE;
    }
 
    return EXIT_SUCCESS;
}

```

---

### Post by Zugzwang on 2009-07-29
Sure you can. But you are using pointers incorrectly at the moment. Also, your "wait_thread" function won't do what it is supposed to. Instead, wait until the threads have been finished before accessing the variable again:

[PHP]
#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <pthread.h>

static void *thread_func(void * number)
{
    *((int*)(number)) = 7;
    return NULL;
}
 
int main(void)
{
    int i = 5;
    pthread_t thread;
    if (pthread_create(&thread, NULL, thread_func, (void *) &i) != 0)
    {
        return EXIT_FAILURE;
    }
	
    if (pthread_join(thread, NULL) != 0)
    {
        return EXIT_FAILURE;
    }

    printf("%i\n", i);
 
    return EXIT_SUCCESS;
}
[/PHP]

---

### Post by CryptiniteDemon on 2009-07-29
That worked.  Thank you much sir.

---

