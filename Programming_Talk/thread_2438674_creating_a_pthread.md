---
title: "creating a pthread"
date: 2020-03-16
forum: Programming Talk
---

### Post by sundaresh on 2020-03-16
```
#include<stdio.h>
#include<pthread.h>

void *mt(void *b) {
      printf("\nReached here\n\n");
      return b;
}

int main() {
     pthread_t i;
     int a;

    if(pthread_create(&i, NULL, &mt, (void *)&a)) printf("thread creation failed\n");
    return 0;
}

```

when compiled with cc -pthread mt.c it compiles fine, but when executed, it does not print anything. Why ?

---

### Post by spjackson on 2020-03-16
pthread_create succeeds, then immediately you return from main. returning from main terminates all running threads and stops your program. So your mt function never gets chance to print its message, well it might or might not: it's a race condition. To correct this, in main you need to wait for the thread to complete.

---

### Post by sundaresh on 2020-03-20
Just to say thank you. Sorry for the delay. Too nervous and too scared to actually try it out and see though. But the actual test program was similar but not exactly this since I wanted to see if malloc was thread safe. Since threads can be user space and 3rd party, so I figured if I allocated some memory within a thread and assigned it to a global variable and soon after freed the memory and terminated the thread, then referencing the allocated memory in main should result in SIGSEGV, which was what I was expecting. But I was not succesfull. But independently anyway, I would like to know if I am right in making such an assumption. If there are no agreed upon bare minimum set of requirements or as one may call it a base standard, it makes it very hard to write portable code, and highly limits the target audience and restricts the usefulness of a particular piece of s/w does it not.

---

### Post by spjackson on 2020-03-21
> **sundaresh said:**
> I wanted to see if malloc was thread safe. Since threads can be user space and 3rd party

glibc's malloc is thread safe. I think that mallocs that you are likely to come across in this day and age will be thread safe. It is guaranteed to be in C11 (but not in C99).
> 
so I figured if I allocated some memory within a thread and assigned it to a global variable and soon after freed the memory and terminated the thread, then referencing the allocated memory in main should result in SIGSEGV, which was what I was expecting. But I was not succesfull.

You will not necessarily get a SIGSEGV, and in fact you probably won't. What you will get is undefined behaviour. You can't draw any conclusion about the thread safety of malloc from that. The following code does not SIGSEGV for me.
```

#include <stdlib.h>
#include <string.h>
#include <stdio.h>

int main()
{
    char * from = "Hello, world!";

    char * freed = malloc(1 + strlen(from));
    free(freed);

    strcpy(freed, from); // Do not do this - undefined behaviour.
    puts(freed); // or this.

    return 0;
}

```
> 
But independently anyway, I would like to know if I am right in making such an assumption. If there are no agreed upon bare minimum set of requirements or as one may call it a base standard, it makes it very hard to write portable code, and highly limits the target audience and restricts the usefulness of a particular piece of s/w does it not.
I'm not fully sure that I understand what you are asking. There's C11 and there's POSIX.

---

### Post by sundaresh on 2020-03-24
Problem solved. I got the desired behavior I need. It is possible to implement memory locking mechanism's independent of the threading facility altogether. Thank you. SIGSEGV is a totally different thing and unnecessary but the reason I was thinking along those lines was, if a thread allocates memory, but terminates without freeing it, this will clearly result in memory leakage or unused unclaimed memory; but the behavior of malloc as per the basic C language standard although UNIX based is not operating system specific and a threading facility is not a part of the standard C library, so I figured if pthread which is a POSIX standard for threads implements malloc with reference to threads, then the pthreads facility could possibly claim unreleased memory, particularly LINUX since LINUX implements threads in kernel space, although I feel being lightweight, thread's should always be user-space and an optional part of the basic standard C library, implemented on any system with the basic standard C compiler, so C programs using just these standard features, run without a hitch on all platforms which provide a standard C compiler with a standard C library.

---

