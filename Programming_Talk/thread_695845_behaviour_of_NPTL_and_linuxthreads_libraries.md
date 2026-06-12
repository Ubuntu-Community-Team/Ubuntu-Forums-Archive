---
title: "behaviour of NPTL and linuxthreads libraries"
date: 2008-02-13
forum: Programming Talk
---

### Post by howgee on 2008-02-13
Hi all,

I have the following problem using ubuntu 7.10 server.
I need to spawn many threads in one of my applications, potentially hundreds. The same code works perfectly fine on other unix platforms. However, on ubuntu 7.10 server if I use the default NPTL implementation of posix threads, my code gives up when calling pthread_create() returning EAGAIN almost immediately: I am able to create no more than 46 threads.

If I do

setenv LD_ASSUME_KERNEL 2.4.10

an compile again the code, this time linking with linuxthreads,
the code is able to spawn hundreds of threads (more than 1000). However, linuxthreads is old and has other problems (threads have each a different PID, no signals per thread etc). 

Is there a way using NPTL to have more threads per process?
I have read tons of different web pages, and it looks like ubuntu 7.10 server already ships with a huge limit w.r.t. the number of threads per process (so I do not need to recompile glibc etc).

What is the correct way to increase the number of threads per process?
Changing /etc/security/limits.conf does not work, changing the limit related to the maximum number processes  using the shell does not work etc. Any clue?

Thank you in advance, and best regards.

---

### Post by stroyan on 2008-02-13
You could easily run out of address space if your program is creating a large stack for each thread. The stack space per thread can be limited by using "ulimit -s" before starting a program or by using pthread_attr_setstacksize with thread attributes passed into pthread_create. Here is a small example limiting stack size.
```

#include <pthread.h>
#include <stdio.h>
#include <errno.h>
#include <stdlib.h>
#include <unistd.h>

void *thread_func(void *arg)
{
    return (void*) 0;
}

int main(int argc, char *argv[])
{
    int result;
    pthread_attr_t attr;
    pthread_t thread;

    result = pthread_attr_init(&attr);
    if (result) { perror("pthread_attr_init failed"); exit(1); }
    result = pthread_attr_setstacksize(&attr, 1024*1024);
    if (result) { perror("pthread_attr_setstacksize failed"); exit(1); }
    result = pthread_create(&thread, &attr, thread_func, (void *) 0);
    if (result) { perror("pthread_create failed"); exit(1); }
    result = pthread_join(thread, NULL);
    if (result) { perror("pthread_join failed"); exit(1); }
    return 0;
}
```

---

### Post by howgee on 2008-02-14
Hi, thank you for your reply.

I am aware I can setup a thread stack size by setting properly the thread attribute using a size which is multiple of the page size in use on a particular system. However, reducing the stack size has adverse effects on the code: when I try this, it does not work correctly anymore. 

The question then is: why linuxthreads is able to create so many threads w.r.t. NPTL?  Does linuxthreads simply use less stack space? I do not think so, but anyway, being able to create on a default installation of ubuntu 7.10 server only 46 threads in the same process appears to be totally useless.

Is dealing with the stack size the only possible user tunable option with NPTL? It seems strange that this behaviour only depends on the amount of available memory, given that, on different unix systems running with the same amount of memory I am able to create thousands of threads inside a single process versus 46 on ubuntu 7.10 server with NPTL (again, linuthreads can spawn more than 1000 on the same machine). 

Please let me know.
Thank you again for your kind assistance.
Best regards,

Massimo

---

### Post by stroyan on 2008-02-14
I wonder if you are exceeding a low setting of kernel.threads-max.
You can check that setting with ```
/sbin/sysctl kernel.threads-max
```
But you should have a high default value.
I don't see the low limit that you do.
With default values on a 32-bit ubuntu 7.10 system I can start 383 threads with 8 MB stacks before running out of address space and failing with ENOMEM.
The limit in my case is maximum virtual address space rather than available virtual memory space.
The linuxthreads stack size would default to 2 MB, allowing many more threads by default.
As I understand it, the linuxthreads virtual memory usage is also based on actual pages of stack touched by each thread rather than allocating up front.
I see that you get EAGAIN, which would be expected when exceeding a threads-max limit.
You may learn more about what is causing the low limit by using the strace command to record the system calls made by your program and the results of those calls.

---

### Post by howgee on 2008-02-15
Hi,

I have verified as suggested the value of kernel.threads-max:

/sbin/sysctl kernel.threads-max
kernel.threads-max = 16255

in /usr/include/bits/local_lim.h I see the following

/* The number of threads per process.  */
#define _POSIX_THREAD_THREADS_MAX       64
/* This is the value this implementation supports.  */
#define PTHREAD_THREADS_MAX     16384

/* Minimum size for a thread.  We are free to choose a reasonable value.  */
#define PTHREAD_STACK_MIN       16384

but in /usr/include/nptl/bits/local_lim.h I see also

/* The number of threads per process.  */
#define _POSIX_THREAD_THREADS_MAX       64
/* We have no predefined limit on the number of threads.  */
#undef PTHREAD_THREADS_MAX

Which one is the correct one: should I count on 16384 threads or as suggested by the NPTL include on an unbounded number of threads?
Also, I see that the minimum amount of memory in bytes for a thread stack size is 16384. As far as I know, I can not use less than this amount of memory, at least on all the other unix systems I know. Is Linux different?
In my previous experiments, setting less memory for the stack size resulted in my code behaving wrongly. Linux is confusing me...

Apparently, it is not a problem due to system's configuration.
I will try using strace on a simple test code which just continues calling pthread_create() until it fails. I will let you know the results.

---

### Post by stroyan on 2008-02-15
> **howgee said:**
> 
in /usr/include/bits/local_lim.h I see the following

/* The number of threads per process.  */
#define _POSIX_THREAD_THREADS_MAX       64
/* This is the value this implementation supports.  */
#define PTHREAD_THREADS_MAX     16384

/* Minimum size for a thread.  We are free to choose a reasonable value.  */
#define PTHREAD_STACK_MIN       16384

but in /usr/include/nptl/bits/local_lim.h I see also

/* The number of threads per process.  */
#define _POSIX_THREAD_THREADS_MAX       64
/* We have no predefined limit on the number of threads.  */
#undef PTHREAD_THREADS_MAX

Which one is the correct one: should I count on 16384 threads or as suggested by the NPTL include on an unbounded number of threads?
Also, I see that the minimum amount of memory in bytes for a thread stack size is 16384. As far as I know, I can not use less than this amount of memory, at least on all the other unix systems I know. Is Linux different?
In my previous experiments, setting less memory for the stack size resulted in my code behaving wrongly. Linux is confusing me...

On ubuntu 7.10 there is no limit on PTHREAD_THREADS_MAX.
You can confirm that with the command
getconf PTHREAD_THREADS_MAX
or the system call
sysconf(_SC_THREAD_THREADS_MAX);
But pthread_create can fail for lack of resources.

You wrote that you are using ubuntu 7.10.
But those files don't match ubuntu 7.10.
Looking at my installation I see usr/include/bits/local_lim.h in package libc6-dev.
But no package provides /usr/include/nptl/bits/local_lim.h.
What release do you have?
What are the contents of /etc/lsb-release/etc/lsb-release ?

The PTHREAD_STACK_MIN value is the minimum requestable size of a thread stack.
It is a mere 16 K bytes.
But it is not the default size of a thread stack.
The default thread stack with NPTL follows the setting of 'ulimit -s'.
On my system that is 8 megabytes.

---

### Post by howgee on 2008-02-16
You are right.
I was told that the system was an ubuntu 7.10 server distribution. Looking at /etc/lsb-release I can confirm that the system I am working on is instead an ubuntu 6.06 (codename dapper).

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

Using my shell (tcsh) I can see the following using limit:

limit
cputime      unlimited
filesize     unlimited
datasize     unlimited
stacksize    65536 kbytes
coredumpsize 0 kbytes
memoryuse    unlimited
vmemoryuse   unlimited
descriptors  2048 
memorylocked unlimited
maxproc      2048 


in my .cshrc I am actually setting the following

limit descriptors 2048
limit stacksize 64M
limit maxproc 2048


so I have modified this to look like 
limit stacksize 8M

limit
cputime      unlimited
filesize     unlimited
datasize     unlimited
stacksize    8192 kbytes
coredumpsize 0 kbytes
memoryuse    unlimited
vmemoryuse   unlimited
descriptors  2048 
memorylocked unlimited
maxproc      2048 


now, when I try again my simple test I am (finally!) able to launch 382 threads. So it is just a matter of available memory.

Thank you very much for your assistance, I really appreciated your help which led to a fast solution to the problem. One last question: what is the minimal amount of memory that I should use to have more threads and the code fully working without problems? Is 4MB enough? I could try by trial and error different amounts of stack memory, but if you know this please let me know.

Best regards,
Massimo

---

### Post by stroyan on 2008-02-16
The necessary stack size depends entirely on the behavior of the particular applications you run.  The stack is used to allocate local variables in procedures.
Programs can allocate variables as local variables on stack, as static variables in the data area, or using malloc or new on the much larger heap.
It is good practice to make large allocations in the heap.  But some programs will create more local variables than they should rely on space for.
And how much they allocate on the stack can vary with different data sets, causing a limit to work one time and fail the next time.
You will need to be cautious in your trial-and-error experiments.

---

