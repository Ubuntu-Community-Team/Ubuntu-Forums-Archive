---
title: "Make an alarm/reminder in python/c/c++"
date: 2009-10-14
forum: Programming Talk
---

### Post by nipunreddevil on 2009-10-14
i wish to make a very simple program which will say ring an alarm after every half an hour of my sitting on the computer.Although many such may be available i want to make for myself,a simple one.Please provide thoughts

---

### Post by dwhitney67 on 2009-10-14
Do you know how to write any software?  A simple infinite while- or for-loop, with a sleep function call (for 1800 seconds), will suffice to provide you the control you needed to perform a repeated action every 30 minutes.

Something like:
```

forever
{
   sleep 1800
   Sound Alarm
}

```

The construct applies to Python, C/C++, or even shell script, of course, with each language having their own respective syntax.

---

### Post by nipunreddevil on 2009-10-14
I wish to avoid infinite loops that's why i asked.

---

### Post by StunnerAlpha on 2009-10-14
> **nipunreddevil said:**
> I wish to avoid infinite loops that's why i asked.

Well you are going to need a loop if you want something to occur repeatedly. You can have a do-while or while loop and specify it to loop infinitely until a certain input is received. Or if you don't want to do an infinite loop, have it loop for a certain number of times...

---

### Post by kavon89 on 2009-10-14
If you want an ability to nicely stop the program/script, try something like this with a condition between the sleep and action of playing the alarm:

```

while(true) {
   sleep(1800);
   if(signalRecieved) break;
   sound.play(alarm);
}

```

This way, once you send the program the signal, the next time it wakes up it will break out of the loop.

You would probably need to create another thread for this loop and in the main execution have it wait for some input to change the boolean value in the thread which is sleeping. (actually even easier than that is to just have the main execution wait on input and once received just return.)

---

### Post by MindSz on 2009-10-14
There's a function called alarm() in C.

It activates the SIGALRM signal which can then be caught with signal().

Here's a sample code I found on the net

```
#include <stdio.h>
#include <sys/time.h>
#include <signal.h>
#include <stdlib.h>

volatile sig_atomic_t keep_going = 1;

void catch_alarm(int);

int main()
{
    signal(SIGALRM, catch_alarm);
    alarm(1);

    while (keep_going);

    return EXIT_SUCCESS;
}

void catch_alarm(int sig)
{
    printf("Alram Occurred");
    keep_going = 0;
}

```

In catch_alarm() you can do whatever you want; launch other processes or whatever you might need to do once the alarm has gone off.

Note: The alarm() function is in SECONDS. There's also a ualarm() function if you need more precision. Its use is slightly different tho.

Another Note: This method is capable of waking the program up from a sleep() command :) So if you do sleep(5), but set alarm(3) the program will wake up in 3 seconds and execute catch_alarm().

---

### Post by korvirlol on 2009-10-14
you could just create a simple script to play some sound, and have cron run it on specified intervals, thus avoiding any looping.

---

### Post by nipunreddevil on 2009-10-14
> **korvirlol said:**
> you could just create a simple script to play some sound, and have cron run it on specified intervals, thus avoiding any looping.

May you please elaborate a little.

---

### Post by benj1 on 2009-10-14
> **korvirlol said:**
> you could just create a simple script to play some sound, and have cron run it on specified intervals, thus avoiding any looping.

you would have a loop it would just be in cron not your script

at OP add an entry to /etc/cronjob

[min] [hour] [day of month] [month] [day of week] [program to be run]
eg 0,15,30,45 * * * * /usr/bin/beep
will run beep every 15 minutes

if you want to learn programming tho, this isnt it

---

