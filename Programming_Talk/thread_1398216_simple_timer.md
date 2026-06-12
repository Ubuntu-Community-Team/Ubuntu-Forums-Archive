---
title: "simple timer"
date: 2010-02-04
forum: Programming Talk
---

### Post by Mr.Carramba on 2010-02-04
Hi,

I tested a c code for simple timer, but the function is never called. Any ideas why?

```

#include <signal.h>
#include <stdio.h>
#include <string.h>
#include <sys/time.h>

void timer_handler (int signum)
{
 static int count = 0;
 printf ("timer expired %d times\n", ++count);
}

int main ()
{
 struct sigaction sa;
 struct itimerval timer;

 /* Install timer_handler as the signal handler for SIGVTALRM. */
 memset (&sa, 0, sizeof (sa));
 sa.sa_handler = &timer_handler;
 sigaction (SIGVTALRM, &sa, NULL);

 /* Configure the timer to expire after 250 msec... */
 timer.it_value.tv_sec = 0;
 timer.it_value.tv_usec = 1000000;
 /* ... and every 250 msec after that. */
 timer.it_interval.tv_sec = 0;
 timer.it_interval.tv_usec = 1000000;
 /* Start a virtual timer. It counts down whenever this process is
   executing. */
 setitimer (ITIMER_VIRTUAL, &timer, NULL);
 printf("while starting\n");
 /* Do busy work. */
 while (1);
}


```

this is working on CentOS 5, but not on ubuntu 9.10

---

### Post by Marlonsm on 2010-02-04
I've tested it in Ubuntu 9.10 an it's also not working here, it stops at "while starting".
I don't know what might have gone wrong...

---

### Post by Zugzwang on 2010-02-04
Perhaps you want to check the return value of your call to "setitimer".

---

### Post by Mr.Carramba on 2010-02-04
> **Zugzwang said:**
> Perhaps you want to check the return value of your call to "setitimer".

good idea, it return -1. But this does not give me clue how to solve it and why its so.

---

### Post by Zugzwang on 2010-02-04
> **Mr.Carramba said:**
> good idea, it return -1. But this does not give me clue how to solve it and why its so.

Oh, it does. Check the man-page of "setitimer" for possible error causes and change your program to output the error cause. Finally, consider using a debugger to check the contents of the "timer" structure before the call. Is it ok? If your program behaves differently in the debugger, you are likely to not have initialised all values in the "timer" struct.

---

### Post by Mr.Carramba on 2010-02-04
I found the problem. it was 
```
timer.it_interval.tv_usec = 100000;
``` that was the problem

by setting 

```

timer.it_interval.tv_usec = 999999;

```

[http://manpages.ubuntu.com/manpages/gutsy/man2/setitimer.2.html#toptoc5](http://manpages.ubuntu.com/manpages/gutsy/man2/setitimer.2.html#toptoc5)
states:

> 
POSIX.1-2001 says that setitimer() should fail if a  tv_usec  value  is
        specified  that  is  outside  of the range 0 to 999999. 

Linux should have fixed this bug from March 2007. dunno why it worked in CentOS.

---

