---
title: "how to get a thread's ID in c/c++ gnu, gettid() is not implemented"
date: 2007-01-24
forum: Programming Talk
---

### Post by murapogilo on 2007-01-24
Hi,

The function gettid is not implemented. I am using Kubuntu 6.10 as operating system.

gettid() returns the thread ID of the current process. This is equal to the process ID (as returned by getpid(2)), unless the process is part of a thread group (created by specifying the CLONE_THREAD flag to the clone(2) system call). All processes in the same thread group have the same PID, but each one has a unique TID. 

I know from the man pages you could use syscall but I don't know how. Can someone help me by posting the C code to get the thread id?

---

### Post by lnostdal on 2007-01-24
Hum, use `getpid' instead?

```

#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>


int main(int argc, char **argv)
{
  printf("PID of this process: %d\n", getpid());
  return(0);
}

```

lars@ibmr52:~/programming/c$ gcc -Wall -g -lpthread a.c -o a
lars@ibmr52:~/programming/c$ ./a
PID of this process: 4782
lars@ibmr52:~/programming/c$ ./a
PID of this process: 4783
lars@ibmr52:~/programming/c$ ./a
PID of this process: 4787

Hm .. but if you want to use threading I'd definitively go for pthreads instead of messing with clone etc.:

```

#include <stdio.h>
#include <pthread.h>
#include <sys/types.h>
#include <unistd.h>


typedef void*(*start_routine_t)(void*);


void* someThread(void* tmp)
{
  printf("PID of this process: %d\n", getpid());
  printf("The ID of this thread is: %u\n", (unsigned int)pthread_self());
  sleep(2); // Keep it alive so we're sure the second thread gets a unique ID.
  return NULL;
}


int main(int argc, char **argv)
{
  printf("PID of this process: %d\n", getpid());
  pthread_t thread1, thread2;
  pthread_create(&thread1, NULL, someThread, NULL);
  sleep(1); // Hack to avoid race for stdout.
  pthread_create(&thread2, NULL, someThread, NULL);
  pthread_join(thread1, NULL);
  pthread_join(thread2, NULL);
  return(0);
}


/*
  lars@ibmr52:~/programming/c$ gcc -Wall -g -lpthread a.c -o a && ./a
  PID of this process: 6542
  PID of this process: 6542
  The ID of this thread is: 3085212576
  PID of this process: 6542
  The ID of this thread is: 3076819872
 */

```

---

### Post by murapogilo on 2007-01-24
Thanks for your reply Inostdal

> use `getpid' instead? 
- I can't. I have to use it according to the guide of my practical training. There was also an assignment where I had to use getpid. At the university they use another linux distribution. I believe Suse. gettid() is dependent of the type of linux distribution :( 

> Hm .. but if you want to use threading I'd definitively go for pthreads instead of messing with clone etc.: 
- Yes, I use pthreads.

With **ps -eLo pid,tid,lwp:14,com** I can see all the information I need but I need to prompt the ID of the pthread that is created. This can only be done by gettid() or by using a system call to get the thread id.

Is there anyone who knows how to do this? or give me directions where I may find the solution?

For compiling the C source I use gcc, gcc-4.1

---

### Post by lnostdal on 2007-01-24
nasty, but:
```

  printf("The ID of this of this thread is: %ld\n", (long int)syscall(224));

```
?

---

### Post by murapogilo on 2007-01-24
Thank you very very much Inostdal!

The solution you post works and I can finish my work on time. I have just one question for you:
Where did you get the function number? In case I run into a similar problem but also to my interest.

Thanks in advance

---

### Post by lnostdal on 2007-01-24
> **murapogilo said:**
> Thank you very very much Inostdal!

The solution you post works and I can finish my work on time. I have just one question for you:
Where did you get the function number? In case I run into a similar problem but also to my interest.

Thanks in advance

Glad to help :)

I found it here:

```

lars@ibmr52:~/programming/lisp/swgtk$ grep gettid /usr/include/asm-i386/unistd.h 
#define __NR_gettid             224

```

---

### Post by JD82 on 2008-06-16
> **Getting the Thread Identifiers**

The function [FONT="Courier New"]pthread_self()[/FONT] can be called to return the ID of the calling thread. It is prototyped by:

[FONT="Courier New"]pthread_t pthread_self(void);[/FONT]

It is use is very straightforward:

```
#include <pthread.h>
pthread_t tid;
tid = pthread_self();
```
Bye

---

### Post by gldblade on 2008-06-30
@JD82

The man page for gettid says:

> 
The thread ID returned by this call is not the same thing as a POSIX thread ID (i.e., the opaque value returned by pthread_self(3)).


---

### Post by Oliver_H on 2009-10-02
pid_t gettid(void);

can be replaced by the following system call :

[FONT=Courier New]#include <sys/syscall.h>[/FONT][FONT=Courier New]
pid_t tid = (pid_t) syscall (SYS_gettid);[/FONT]

---

