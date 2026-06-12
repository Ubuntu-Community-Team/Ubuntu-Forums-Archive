---
title: "Arbitrary inaccuracy seen in time measurement [gettimeofday() and clock_gettime()]"
date: 2014-09-23
forum: Programming Talk
---

### Post by lu333031 on 2014-09-23
I need to get accurate timestamps for a data stream (100s of microSec accuracy). For the most part, I am able to get the correct clock value but from time to time, there seems to be some delays. The deviation is arbitrary and I am unable to see any patterns. 

Problem seen on Ubuntu 12.04 (32-bit).

No other OS is installed on the system and no other apps are running while running the test.
Problem seen with both gettimeofday() and clock_gettime() calls. Interestingly, when the
timestamp is off in one, it is off in the other as well, leading me to suspect that the kernel is
going off to do something before attending to the clock/time related calls.

The following (compilable) code snippet illustrates the problem (no real data is being read
here, only time is read every 100uS. But the timestamps are skewed from time to time) -

```

/***************************************************
 * File myts.c
 ***************************************************/

#include <stdio.h>
#include <time.h>
#include <sys/time.h>

#define NSEC_PER_SEC      1000000000  /* nSecs in a second */
#define USEC_PER_SEC      1000000     /* uSecs in a second */

typedef struct timespec   timespec_t;
typedef struct timeval    timeval_t;
typedef struct timezone   timezone_t;


int main()
{
    timespec_t timeSpec;
    timeval_t  timeVal;
    timezone_t timeZone;

    unsigned long usTStamp1, usTStamp2, uTStampDiff;
    unsigned long nsTStamp1, nsTStamp2, nTStampDiff;

    while (1)
    {
        usleep(100);

        if ((gettimeofday(&timeVal, &timeZone) == -1)  ||
            (clock_gettime((int)CLOCK_MONOTONIC, &timeSpec) == -1))
        {
            fprintf(stderr, "\nSys call error (TStamp1)!\n");
            continue;
        }

        /* Save timestamp in uSec */
        usTStamp1 = timeVal.tv_usec +
                    (timeVal.tv_sec * USEC_PER_SEC);

        /* Save timestamp in nSec */
        nsTStamp1 = timeSpec.tv_nsec +
                    (timeSpec.tv_sec * NSEC_PER_SEC);

        /* Sleep 100us between timestamps */
        usleep(100);

        if ((gettimeofday(&timeVal, &timeZone) == -1)  ||
            (clock_gettime( (int)CLOCK_MONOTONIC, &timeSpec) == -1))
        {
            fprintf(stderr, "\nSys call error (TStamp2)!\n");
            continue;
        }

        /* Save timestamp in uSec */
        usTStamp2 = timeVal.tv_usec +
                    (timeVal.tv_sec * USEC_PER_SEC);

        /* Save timestamp in nSec */
        nsTStamp2 = timeSpec.tv_nsec +
                    (timeSpec.tv_sec * NSEC_PER_SEC);

        uTStampDiff = usTStamp2 - usTStamp1;
        nTStampDiff = nsTStamp2 - nsTStamp1;

        fprintf(stderr, "%lu    %lu\n", uTStampDiff, nTStampDiff);

    } /* while (1) */
}

/***************************************************/

```


Code compiled and run as follows:

```

>  gcc -o  myts  myts.c  -lrt
>  ./myts   >  myts.txt   2>&1
```

If you run the program for 4-5 seconds and abort with a Ctrl-C, myts.txt shows 2 colums of data. 

Coln. 1 is the difference between 2 consecutive timestamps in microSec obtd. using gettimeofday().
Coln. 2 is the difference between 2 consecutive timestamps in nanoSec obtd. using clock_gettime().

Consecutive samples are 100uS apart but it appears that the smallest sleep the system is capable of is about
165-170uS (which is acceptable for our purposes). From time to time, the time difference is anywhere from
200-4000uS instead of ~170uS.  This is causing the problem as the data is timestamped incorrectly. When the
deviation in timestamp occurs, it seems to occur for both calls (thus eliminating the cause of error as a specific
call).

Can anybody explain these arbitrary anomalous timestamps and suggest a way to prevent this?
Running the program with "nice -20" did not help.

Thanks.

Lu

---

### Post by ofnuts on 2014-09-24
When you says that "No other application is running", you are saying that "ps -eaf " returns an empty list, which is hard to believe? On a workstation (vs real-time) system like Ubuntu there is always something running in the background.

The man page for sleep() says:

> The **usleep**() function suspends execution of the calling thread for (at least) *usec* microseconds. The sleep may be lengthened slightly by any system activity or by the time spent processing the call or by the granularity of system timers.

For some value of "slightly".  But given that a Linux timeslice is around 5ms, you cannot really expect much better in the accuracy of a usleep(). If you want time accuracy, you need to be part of the kernel.

---

### Post by spjackson on 2014-09-24
> **lu333031 said:**
> leading me to suspect that the kernel is going off to do something before attending to the clock/time related calls.

Your suspicion is correct - see the man page for usleep.
> 
Can anybody explain these arbitrary anomalous timestamps and suggest a way to prevent this?
Running the program with "nice -20" did not help.

Your requirements suggest that you need a RTOS; Ubuntu is not a RTOS.

---

### Post by tgalati4 on 2014-09-24
I would be curious if the Realtime Kernel can get down to the desired accuracy.  [https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel](https://help.ubuntu.com/community/UbuntuStudio/RealTimeKernel)

You might need a stripped down linux, like TinyCore and activate the realtime features and do some testing.

What is your timing specification?  100's of microseconds is not very specific.  Is that 0.5 second data interval (plus or minus 150 microseconds)?

---

### Post by Michael_McKenney on 2014-09-24
On my Windows Servers I configure W32TIME and NTP services.  MS SQL Server will stop working if time is 5 minutes off.  The main Active Directory service goes out every 3 minutes and gets time from NTP Naval Servers tick and tock.  This keeps the server time within 0.003 of a second, according to the logs.   I have found documentation on Ubuntu NTP Settings.  At home it does not matter if the time is off by seconds.

---

### Post by tgalati4 on 2014-09-24
Not really related to the OP's original problem . . .

I have been able to get under 3 millisconds accuracy using a drift file in Ubuntu.

Some horologist posts:  (some are old, but mostly applicable)

[http://ubuntuforums.org/showthread.php?t=1793516&highlight=ntp+time](http://ubuntuforums.org/showthread.php?t=1793516&highlight=ntp+time)

[http://ubuntuforums.org/showthread.php?t=1423407&highlight=ntp+time](http://ubuntuforums.org/showthread.php?t=1423407&highlight=ntp+time)

[http://ubuntuforums.org/showthread.php?t=2185773&highlight=ntp+time](http://ubuntuforums.org/showthread.php?t=2185773&highlight=ntp+time)

Keeping accurate standard time on your system is very different than timing CPU processes.

---

### Post by lu333031 on 2014-09-25
tgalati4, thanks for your pointer for the RT kernel. I can experiment with the kernel but even if some RT kernel patch works, that is not an acceptable solution to us at this time as we cannot change the kernel of our sytems being used in the field. We can, however, provide an update to an application which will read the time more reliably.

The link you provided mentions 2.6.x version of the kernel. Our Ubuntu 12.04 LTS uses 3.2.0. Is there nothing in this kernel to satisfy real-time, low-latency needs that can be accomplished by a user application?

When we compare the timestamps obtd. with our Ubuntu application with those obtained with a DOS app (yes DOS :(, that could directly read the time values from a HW register) running on a PC, we see the time drift in 100s of microSec (200+) in several timestamps but more serious than that is the issue when two consecutive timestamps are more than about 10ms apart on the Ubuntu, and not so on DOS. This level of timedrift flags a false error since a good data stream is supposed to have data bytes come in faster than 10ms. So, being able to timestamp a byte read from the UART on our system accurately is very important. 

Thank you.

---

### Post by xb12x2 on 2014-09-25
Your application is running on a modern, multitasking (time-slicing) protected OS: the millisecond range of accuracy is about the best you can expect with the type of solution you are using.

Two suggestions:

1. Consider _directly_ reading the CPU's Time Stamp Counter register from your code (google 'rdtsc'). This register counts the cpu's clock cycles so is very accurate, assuming you're running on a reasonably current cpu with a Ghz clock. It's a 64-bit register so can count for several years without rolling over. It's very easy to read.

2. Consider if a driver of some sort could be used to do the actual reads of the Time Stamp Counter. A kernel-mode driver could get a much more accurate count of clock cycles consumed (because it's much closer to the hw, etc) and then pass its result on to your user-land application.

---

### Post by tgalati4 on 2014-09-25
I think the 3.2 kernel has some real-time hooks built in, but you will have to investigate.  My experience with embedded platforms was with 2.6 kernel which required a recompile with the real-time modules included in the kernel config.

And yes, xb12x2's suggestions may help your situation.  A desktop-linux distro is not optimized for data acquisition.  How many lines of code in DOS?  Can you have multiple users in DOS?  Can you run several, simultaneous threads in DOS?  If DOS works for your application, then use DOS.  If you are asking:  "How can I make Linux behave like DOS for my specific data-acquistion program?"  The simple answer is you can't.

---

### Post by lu333031 on 2014-09-26
xb12x2, thanks for "rdtsc'. However, as we suspect, if it's not the accuracy of the clock functions that is the issue but the kernel preempting our process to do some housekeeping task(s) (no other user processes are running) that causes the time measurement to be skewed from time to time, then what is to prevent the kernel from preempting our process when it is trying to get the rdtsc info to timestamp the aquired data byte?

tgalati4, yes I understand the differences between Linux and DOS. The app is implemented on Linux in order to remove the necessity for having a PC when everything else required for our purposes is being run successfully on the Linux system. So, going back to the DOS app is not a desirable move.

Anyway, I'll keep looking....

Thank you.

---

### Post by xb12x2 on 2014-09-26
> **lu333031 said:**
> 

xb12x2, thanks for "rdtsc'. However, as we suspect, if it's not the accuracy of the clock functions that is the issue but the kernel preempting our process to do some housekeeping task(s) (no other user processes are running) that causes the time measurement to be skewed from time to time, then what is to prevent the kernel from preempting our process when it is trying to get the rdtsc info to timestamp the aquired data byte?



That is why I suggested that you do the actual clock-counting from a kernel-mode driver which can be made to run at a priviledge-level which will not get preempted during the count. Similar to an interrupt routine, or maybe an actual interrupt routine.

---

