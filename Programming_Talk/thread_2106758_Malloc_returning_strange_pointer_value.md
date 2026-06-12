---
title: "Malloc returning strange pointer value"
date: 2013-01-20
forum: Programming Talk
---

### Post by krsus on 2013-01-20
Hi!

I am trying to write a C program. I find that malloc at times is returning strange values. It is not NULL pointer. I made a wrapper on malloc and printed some details.

Note: I have added test code as an attachment with this post.

.....
Malloc request for 13 bytes. Total: 550. Retval: 0x60e390 
Malloc request for 40 bytes. Total: 590. Retval: 0x60e3b0 
Malloc request 21 bytes. Total: 611. Retval: 0x60e3e0 
Malloc request 22 bytes. Total: 633. Retval: 0x7fffec0008c0 

Program received signal SIGSEGV, Segmentation fault.

As you can see from above, my program has allocated only 600+ bytes. However, suddenly malloc which was earlier returning decent values like 0x60e3e0 returned a pointer 0x7fffec0008c0. Access to this pointer is causing segfault. 

Other info: Program is multi-threaded and two threads allocate memory (I guess this should not be a problem), I am compiling this on ubuntu (Linux ubuntu 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux). My gcc version is gcc (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2 and GCC flag used is -g.  Glibc version information is "GNU C Library (Ubuntu EGLIBC 2.15-0ubuntu20) stable release version 2.15"

I am totally confused why malloc is returning such values. Even more, why is a memset to a valid malloc causing segfault?

I just noticed that program had more compile flags. I wrote a test program and tried to replicate the situation. It crashed in the first instance itself. I am adding the code, compile command and the program o/p below

Test.c
```
#include "debug.h"
#include <pthread.h>

void *fn1(void *unused)
{
    int arr[]={10,22,33,44,11,5,10,100};
    int i=0;
    char *ptr;
    int sz=0;

    sz=sizeof(arr)/sizeof(int);

    while(1)
    {
        sleep(2);
        ptr=malloc(arr[i]);
        memset(ptr,0,arr[i]);
        i++;
        if(i==sz)i=0;
    }

    return 0;
}

void *fn2(void *unused)
{
    int arr[]={10,22,33,44,11,5,10,100};
    int i=0;
    char *ptr;
    int sz=0;

    sz=sizeof(arr)/sizeof(int);

    while(1)
    {
        sleep(2);
        ptr=malloc(arr[i]);
        memset(ptr,0,arr[i]);
        i++;
        if(i==sz)i=0;
    }

    return 0;
}

int main()
{
    pthread_t pt1,pt2;

    pthread_create(&pt1,NULL,fn1,NULL);
    pthread_create(&pt2,NULL,fn2,NULL);

    while(1)sleep(300);
}
```debug.h
```
#ifndef __EXCLUDE_DEBUG__

#define trace printf("--- %s %s %d ---\n",__FILE__,__func__,__LINE__);
#define MALLOC_CHECK_ 3

#if defined(malloc)
#undef malloc
#endif //defined(malloc)
#define malloc(x) rmm_malloc_(x,__FILE__,__LINE__)

#endif
```rmm_malloc.c
```

#include <stdio.h>


void *rmm_malloc_(unsigned int x, unsigned char *pucFile,unsigned int uiLine)
{
    static unsigned int uiTotal=0;
    void *ptr;
    uiTotal+=x;

    ptr=malloc(x);
    printf("Malloc request from %s %d for %d bytes. Total: %d. Retval: %p \n",pucFile,uiLine,x,uiTotal,ptr);

    return ptr;
}

```Compilation: 
```
gcc -L/usr/lib/x86_64-linux-gnu -lcurl -lpthread test.c debug/rmm_malloc.c -Iinclude -pthread -g
```(I was expecting that -lpthread should be enough to compile this. However, I had to add -pthread. Else, I was getting an error from linking stage that it could not find pthread_create)

o/p
```
 gdb ./a.out 
<gdb stuff>
(gdb) r
Starting program: /home/user/src/a.out 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[New Thread 0x7ffff77fd700 (LWP 16076)]
[New Thread 0x7ffff6ffc700 (LWP 16077)]
Malloc request from test.c 16 for 10 bytes. Total: 10. Retval: 0x7ffff00008c0 

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0x7ffff77fd700 (LWP 16076)]
__memset_sse2 () at ../sysdeps/x86_64/multiarch/../memset.S:364
364    ../sysdeps/x86_64/multiarch/../memset.S: No such file or directory.
(gdb) bt
#0  __memset_sse2 () at ../sysdeps/x86_64/multiarch/../memset.S:364
#1  0x0000000000400744 in fn1 (unused=0x0) at test.c:17
#2  0x00007ffff7bc4e9a in start_thread (arg=0x7ffff77fd700) at pthread_create.c:308
#3  0x00007ffff78f1cbd in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:112
#4  0x0000000000000000 in ?? ()

```Thanks,
Suseelan

---

### Post by MadCow108 on 2013-01-20
if you compile with -Wall you will get this:
```
test.c:19:3: warning: implicit declaration of function ‘rmm_malloc_’ [-Wimplicit-function-declaration]
```

so it is not declared making int an int(void) function so you lose the first 4 bytes of the pointer on 64 bit.
declare it in debug.h and it should work.
this default warning should also be a clue:
```
test.c:19:6: warning: assignment makes pointer from integer without a cast [enabled by default]
```

as for the lpthread thing, libraries must be after objects needing them on the command line, but you should still prefer -pthread as it does other stuff than just linking (see the manpage).

---

### Post by dwhitney67 on 2013-01-20
> **krsus said:**
> I was expecting that -lpthread should be enough to compile this.

Break your bad habit...

```

gcc [compiler flags] [source module(s)] [library flags] [libraries]

```

Do not specify the libraries (e.g. -lpthread) before your source module.

---

### Post by trent.josephsen on 2013-01-20
At what point in your programming process did you stop and think, "Yes, hiding the standard malloc() with a macro of the same name that has different behavior is a great idea! There's no way this can go wrong or make it hard for other people to debug"?

---

### Post by krsus on 2013-01-20
Thanks MadCow and others for the solution and suggestion. I was thinking that int should match word size and that should not cause the issue. Anyway, I learned a lesson that warning should be dealt with, even if they appear insignificant, before I try to resolve issues like this. I will also take care of the gcc argument order in future. Also, the debug code is temporary. I will get rid of it in production version.

---

