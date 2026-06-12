---
title: "catching problematic signals into a file"
date: 2010-09-29
forum: Programming Talk
---

### Post by linux_noob0 on 2010-09-29
Hi, I'd like to know if there's a way to record signals like SIGSEGV and SIGABRT into a file. For example, if I have a program called prog, and I execute it from terminal like:
```
./prog
```
it does something, but it touches some forbidden memory and produces a SIGSEGV... I'd like to record that information...

Also, if someone knows how to limit the memory and time given to a program (actual time, not general user time), I'd be really thankful for sharing!

Thanks! :)

---

### Post by dwhitney67 on 2010-09-29
AFAIK, you can catch any signal, with the exception of SIGKILL (9).

Here's how to catch SIGSEGV:
```

#include <signal.h>
#include <string.h>
#include <stdlib.h>
#include <stdio.h>


void sighandler(int signo)
{
   printf("caught signal %d\n", signo);
   exit(signo);
}

int main()
{
   struct sigaction sa;

   memset(&sa, 0, sizeof(sa));

   sa.sa_handler = sighandler;
   sigemptyset(&sa.sa_mask);

   sigaction(SIGSEGV, &sa, NULL);

   int* i = 0;
   int  j = *i;   /* illegal operation that will generate a SIGSEGV */

   printf("j = %d\n", j);

   return 0;
}

```
You can place quick/simple code in the signal handler, such as toggling a semaphore; don't make it overly complex because you never know -- another signal may be sent.

---

### Post by linux_noob0 on 2010-09-29
Thanks a lot!! :)

---

