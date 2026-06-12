---
title: "Delay accuracy not correct"
date: 2010-01-05
forum: Programming Talk
---

### Post by akvseiji on 2010-01-05
**This is my Ubuntu info**:
Distribution **ID**: Ubuntu
Distribution **Release**: 8.04
Distribution **CodeName**: hardy
Distribution **Description**: "Ubuntu 8.04.3 LTS"

**And this is my kernel info**:
Kernel **name**: Linux
Kernel **release**: 2.6.24-24-generic
Kernel **version**: #1 SMP Tue Jul 7 19:46:39 UTC 2009

I'm using c programming.


This is my program:
```
#include <stdio.h>
#include <time.h>


int main()
{
    int count = 0, sec = 1;

    while(1)
    {   if(count >= 1000)
        {   printf("%dsec\n", sec++);
            count = 0;
        }

        usleep(1000);
        count += 1;
    }
}
```

This program **should print** "%dsec" **every 1 second**
by looping 1000 microseconds for 1000 times.

But **what happens is:   it print every 4 seconds!!!**.

From what I see, it takes longer than actual 1000 microseconds to execute usleep(1000).
So I try running usleep(1) for 1000 loop.
Surprisingly, it make no difference. Still print every 4 seconds.

Then I try running usleep(100000) for 10 loop.
It print almost every 1 second, but still longer than actual 1 second.

My question is: **Why the delay accuracy is not correct??** and
**How to solve it??**



I run that program on **other PC** and it **worked well**.
This is other PC ubuntu info:
Distribution ID: Ubuntu
Distribution Release: 9.04
Distribution CodeName: jaunty
Distribution Description: "Ubuntu 9.04"

And this is other PC kernel info:
Kernel name: Linux
Kernel release: 2.6.28-17-generic
Kernel version: #58-Ubuntu SMP Tue Dec 1 18:57:07 UTC 2009


Any idea guys??

---

### Post by CptPicard on 2010-01-05
Well, to begin with...

> 
       The  usleep() function suspends execution of the calling process for (at least) usec microseconds.  The
       sleep may be lengthened slightly by any system activity or by the time spent processing the call or  by
       the granularity of system timers.


Is there "system activity" going on?

---

### Post by akvseiji on 2010-01-05
Sorry I'm asking: what is "system activity"?

When I run the program using terminal, there are no other programs or applications open.


I found some info on internet:
*There are HPET(High Precision Event Timer) in ACPI(Advanced Configuration and Power Interface) function in PC that will impact this accuracy of the sleep timer.*

---

### Post by CptPicard on 2010-01-05
Well, anything that might be running. :) There's a lot of stuff going on in the background.

The way you're doing it -- accumulating 1000x the error each second -- I wouldn't be surprised that the result is off. After all, usleep only guarantees you "at least" the amount of microseconds... being "accurate" would require some sort of real-time OS stuff, I suppose. But I would look into background processes or perhaps scheduling settings(?) if this works on some other box.

---

### Post by akvseiji on 2010-01-05
> **CptPicard said:**
> -- accumulating 1000x the error each second -- I wouldn't be surprised that the result is off.

Well.. I was surprised because it doesn't happen in other PC..

I'm looping 1000x because I want to make a counter that count every 1 millisecond.
Or is there any other better way to do it??

I have tried using nanosleep(), but the result are just the same.

---

### Post by CptPicard on 2010-01-05
> **akvseiji said:**
> 
I'm looping 1000x because I want to make a counter that count every 1 millisecond.
Or is there any other better way to do it??


Well, if it really has to count every millisecond, then no, but it seems to me that in this case something actually happens only every second...

---

### Post by dwhitney67 on 2010-01-05
> **akvseiji said:**
> Sorry I'm asking: what is "system activity"?

:roll:

> 
When I run the program using terminal, there are no other programs or applications open.

There are many other programs running, including the terminal that you are using.  Check your process statuses:
```

ps -ef

```

You may want to consider using the real-time timer.  Here's some code that exercises it:
```

#include <signal.h>
#include <time.h>
#include <assert.h>
#include <string.h>
#include <unistd.h>
#include <stdio.h>

int count = 0;

void sigHandler(int signo)
{
   if (signo == SIGRTMAX)
   {
      ++count;
   }
}

int main()
{
   /* Setup the signal */
   struct sigaction sigact;

   sigemptyset(&sigact.sa_mask);

   sigact.sa_flags   = SA_SIGINFO;
   sigact.sa_handler = sigHandler;

   sigaction(SIGRTMAX, &sigact, 0);

   /* Setup the timer */
   struct sigevent sigev;

   memset(&sigev, 0, sizeof(sigev));

   sigev.sigev_notify          = SIGEV_SIGNAL;
   sigev.sigev_signo           = SIGRTMAX;
   sigev.sigev_value.sival_int = 1;

   timer_t timer;

   int rtn = timer_create(CLOCK_REALTIME, &sigev, &timer);
   assert(rtn == 0);

   /* start the timer */
   struct itimerspec itimer = { {1, 0}, {1, 0} };   /* 1 sec time period, that we want repeated. */
   rtn = timer_settime(timer, 0, &itimer, 0);
   assert(rtn == 0);

   while (count < 10)
   {
      sleep(10);  /* this is interruptible by the timer */

      printf("%d seconds have passed...\n", count);
   }

   return 0;
}

```

---

### Post by Hellkeepa on 2010-01-05
HELLo!

Walking out on a limb here, but it almost sounds as if the user want to count how many ms a certain task takes to complete. Instead of adding the huge overhead of counting each and every ms individually, you should just take the end time minus the start time and have your answer.

Unfortunately I'm not familiar enough with C to be able to give you a function that gives you the current time in ms, but you might be able to find something here:
[http://bytes.com/topic/c/answers/219279-getting-time-milliseconds](http://bytes.com/topic/c/answers/219279-getting-time-milliseconds)
(It's a very interestring conversation, if nothing else.)

Happy codin'!

---

### Post by dwhitney67 on 2010-01-05
> **Hellkeepa said:**
> HELLo!

Walking out on a limb here, but it almost sounds as if the user want to count how many ms a certain task takes to complete. Adding the huge overhead of counting each and every ms individually, you should just take the end time minus the start time and have your answer.

You might be correct; the OP did not really offer any insight as to what he is after.

To compute time-deltas with reasonable resolution, one can use gettimeofday(), before and after the critical section that needs to be measured.

---

### Post by Can+~ on 2010-01-05
Well, it all boils down what the OP wants to do. If he is fooling around with timers, then there's no problem.

On the other hand, if you (the OP) want to check the availability of a certain resource (say, a shared memory page), consider using signals and a more event-driven paradigm, POSIX provides quite a lot of tools for that, as using while..sleep is a type of [busy-waiting]("http://en.wikipedia.org/wiki/Busy_waiting").

---

### Post by Arndt on 2010-01-06
> **Can+~ said:**
> Well, it all boils down what the OP wants to do. If he is fooling around with timers, then there's no problem.

On the other hand, if you (the OP) want to check the availability of a certain resource (say, a shared memory page), consider using signals and a more event-driven paradigm, POSIX provides quite a lot of tools for that, as using while..sleep is a type of [busy-waiting]("http://en.wikipedia.org/wiki/Busy_waiting").

I thought busy-waiting was refraining from sleeping, and repeatedly checking whatever you're waiting for.

---

### Post by CptPicard on 2010-01-06
> **Arndt said:**
> I thought busy-waiting was refraining from sleeping, and repeatedly checking whatever you're waiting for.

Well, polling with sleep is still active and... less busy :) It is always better to get signalled only when you need to.

---

### Post by akvseiji on 2010-03-04
I think I found the reason for the delay problem.
It is due to the way that Ubuntu process the time.

See "man setitimer"
[http://linux.die.net/man/2/setitimer](http://linux.die.net/man/2/setitimer)

 

From the article, under “Bugs” section it stated

On Linux, timer values are represented in jiffies.
On Linux/x86 (where, since kernel 2.6.13, 
the **default jiffy is 0.004 seconds**).

That’s why when I looping usleep(1000) for 1000 times, it delay 4 seconds, because 1000times x 0.004 = 4 seconds.

By default, Ubuntu 8.04 LTS is using kernel 2.6.4.


This is my understanding..
it is correct??

If yes, how we can fix this?

---

