---
title: "_close vs close?"
date: 2009-08-29
forum: Programming Talk
---

### Post by rogerr on 2009-08-29
Hi everyone!
 This is my first post! :)
 I need to port a program from freeBSD to ubuntu. I have the source, I can compile it, but at linking time I get the following errors:

tq.c:(.text+0x142): undefined reference to `_close'
tq.c:(.text+0x14d): undefined reference to `_close'
tq.c:(.text+0x179): undefined reference to `__isthreaded'
tq.c:(.text+0x189): undefined reference to `_pthread_mutex_lock'
tq.c:(.text+0x1ad): undefined reference to `__isthreaded'
tq.c:(.text+0x1bd): undefined reference to `_pthread_mutex_unlock'
tq.c:(.text+0x1c8): undefined reference to `_close'
tq.c:(.text+0x1d3): undefined reference to `_close'
tq.c:(.text+0x1ff): undefined reference to `_close'
tq.c:(.text+0x21a): undefined reference to `_dup2'
tq.c:(.text+0x225): undefined reference to `_close'
tq.c:(.text+0x23f): undefined reference to `_dup2'
tq.c:(.text+0x261): undefined reference to `_dup2'
tq.c:(.text+0x27d): undefined reference to `_dup2'
tq.c:(.text+0x288): undefined reference to `_close'
tq.c:(.text+0x293): undefined reference to `_close'
tq.c:(.text+0x2b3): undefined reference to `_close'
tq.c:(.text+0x2dd): undefined reference to `_execve'
tq.c:(.text+0x2ee): undefined reference to `__isthreaded'
tq.c:(.text+0x2fe): undefined reference to `_pthread_mutex_unlock'
tq.c:(.text+0x328): undefined reference to `_close'
tq.c:(.text+0x34a): undefined reference to `_close'
tq.c:(.text+0x361): undefined reference to `__isthreaded'
tq.c:(.text+0x371): undefined reference to `_pthread_mutex_lock'
tq.c:(.text+0x389): undefined reference to `__isthreaded'
tq.c:(.text+0x399): undefined reference to `_pthread_mutex_unlock'
/tmp/ccKg1wzA.o: In function `pclose':
tq.c:(.text+0x3af): undefined reference to `__isthreaded'
tq.c:(.text+0x3bf): undefined reference to `_pthread_mutex_lock'
tq.c:(.text+0x3fa): undefined reference to `__isthreaded'
tq.c:(.text+0x40a): undefined reference to `_pthread_mutex_unlock'
tq.c:(.text+0x437): undefined reference to `__isthreaded'
tq.c:(.text+0x447): undefined reference to `_pthread_mutex_unlock'
tq.c:(.text+0x47e): undefined reference to `_wait4'

How should I link it to eliminate these errors? Anyway what is the difference between close and _close, dup2 and _dup2, etc? (In the source code _close and _dup2 is written...)

Thx,
rogerr

---

### Post by dwhitney67 on 2009-08-29
You should refer to the man-pages for each of those functions.

As for the pthread related functions, you will need to link with POSIX thread library.  For example:
```

gcc MyProg.c -lpthread -o myprog

```

To the best of my knowledge, to obtain the man-pages:
```

sudo apt-get install manpages-devel

```
There might be other similar man-page packages, but I cannot recall them.

---

### Post by rogerr on 2009-08-29
Hi Dwhitney67,
 Thanks for the reply.
 I do use -lpthreads so it cannot be an issue:
 >  gcc -I/usr/include/libxml2  -L/usr/libs -lxml2 -lpthread tq.c

 I also read the man pages (close and dup2), but found nothing about _close and _dup2.
 I'm interested in 2 things:
i, if I can fix it with the linker(in Makefile)?
ii, if not, than what is the difference between close and _close. Can I change safely _close to close in the source file?

Thx,
rogerr

---

### Post by dwhitney67 on 2009-08-29
I have never seen _close(), nor _dup() or _dup2().  I would imagine their equivalents are close(), dup(), and dup2(), respectively.

Upon closer examination of your "undefined reference" errors, it is quite apparent that your code relies heavily on the underscore-prefixed version of many functions.  For example, I am accustomed to seeing pthread_mutex_lock(), not the version as outlined in your error messages.  The former version is covered by the POSIX pthread library (-lpthread).

---

### Post by rogerr on 2009-08-29
Ok, because I didn't have better idea I solved it this way:

> 
#define _close close
#define _dup2 dup2
#define _wait4 wait4
#define _execve execve
#define _pthread_mutex_unlock pthread_mutex_unlock
#define _pthread_mutex_lock pthread_mutex_lock


Now I have only one thing to fix:
> undefined reference to `__isthreaded'

Man pages didn't help me to explain what is this variable for, but googling around I found that this is really (free/net/open)BSD specific. 
I also found something about it's purpose:
> /*
 * This global flag is non-zero when a process has created one
 * or more threads. It is used to avoid calling locking functions
 * when they are not required.
 */
extern int	__isthreaded;


My question is if we have something similar to it in Ubuntu/linux systems?

---

### Post by soltanis on 2009-08-29
I don't think so, but why don't you declare that variable and set it to one?

Since you are compiling to a linux target, it should be completely irrelevant (read: the linux pthreads library either has its own internal version or in any case does not look up the value of this variable); and if the program uses it anywhere (it looks like it does) the value of the variable indicates that the program is indeed threaded (which it is, if you are using pthreads).

---

### Post by Arndt on 2009-08-31
> **rogerr said:**
> Hi Dwhitney67,
 Thanks for the reply.
 I do use -lpthreads so it cannot be an issue:
 

 I also read the man pages (close and dup2), but found nothing about _close and _dup2.
 I'm interested in 2 things:
i, if I can fix it with the linker(in Makefile)?
ii, if not, than what is the difference between close and _close. Can I change safely _close to close in the source file?

Thx,
rogerr

Do you really want /usr/libs? The usual place is /usr/lib.

---

### Post by nvteighen on 2009-08-31
Are you actually calling stuff you should call?... underscores are usually used in static functions... that you aren't going to be able to call (at least, trivially).

---

### Post by rogerr on 2009-09-03
> **soltanis said:**
> I don't think so, but why don't you declare that variable and set it to one?

Since you are compiling to a linux target, it should be completely irrelevant (read: the linux pthreads library either has its own internal version or in any case does not look up the value of this variable); and if the program uses it anywhere (it looks like it does) the value of the variable indicates that the program is indeed threaded (which it is, if you are using pthreads).

 Works great thanks. I also thought about it, but first I wanted to make sure that in Ubuntu/linux environment there is nothing similar to it.

---

### Post by rogerr on 2009-09-03
> **nvteighen said:**
> Are you actually calling stuff you should call?... underscores are usually used in static functions... that you aren't going to be able to call (at least, trivially).

Well I removed underscores as I mentioned above. Anyway this program is not written by me, I just have to use it under Ubuntu, and was written to FreeBsd On FreeBsd it compiled without problem.

---

