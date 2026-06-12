---
title: "/usr/include/sys/ is gone. I have compiling problem."
date: 2015-08-06
forum: Packaging and Compiling Programs
---

### Post by newcfd on 2015-08-06
/usr/include/sys/  was moved to /usr/include/x86_64-linux-gnu/sys, but the g++ compiler paths were never updated after this move. 
All the headers 
#include <stddef.h>    /* ptrdiff_t */
#include <stdio.h>     /* snprintf */
#include <stdlib.h>    /* malloc, free */
#include <string.h>    /* strdup, strerror, memset */
#include <sys/time.h>  /* struct timeval */
#include <sys/types.h> /* pid_t, fd_set */
#include <sys/wait.h>  /* waitpid */
#include <sys/stat.h>  /* open mode */
#include <unistd.h>    /* pipe, close, fork, execvp, select, _exit */
#include <fcntl.h>     /* fcntl */
#include <errno.h>     /* errno */
#include <time.h>      /* gettimeofday */
#include <signal.h>    /* sigaction */
#include <dirent.h>    /* DIR, dirent */
#include <ctype.h>     /* isspace */
are unavailable. 

The thread sheds some light
[http://stackoverflow.com/questions/14014669/system-includes-moved-on-ubuntu-g-cannot-resolve-reg-eip](http://stackoverflow.com/questions/14014669/system-includes-moved-on-ubuntu-g-cannot-resolve-reg-eip)

It is awkward to create a /usr/include/sys/ and make soft links. Any other solutions?

---

### Post by newcfd on 2015-08-07
I installed libc6-dev and brought /usr/include/sys back.

---

