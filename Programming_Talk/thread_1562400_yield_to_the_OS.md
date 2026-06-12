---
title: "yield to the OS"
date: 2010-08-27
forum: Programming Talk
---

### Post by rockom on 2010-08-27
Hello,

What the best way (best practice) for yielding to the OS/processor in a tight while(1) loop?

Thanks,
-Rocko

---

### Post by schauerlich on 2010-08-27
What do you mean by "yielding"? Exiting the program? And what language?

---

### Post by CptPicard on 2010-08-27
It's hopefully a pre-emptive scheduler, that knows when it wants to keep your CPU-hogging process off the processor...

---

### Post by StephenF on 2010-08-27
That said you don't want your process appearing to take all the CPU idle time. I use either blocking IO or nanosleep when expecting on a buffer.

---

### Post by worksofcraft on 2010-08-27
This is a very good question: Preemptive schedulers can't tell the difference between running tight loops that do nothing and tight loops that massage data. Far too many processes hog the processor when they have nothing to do. It would be much more efficient to relinquish the remainder of their time slice and try again next turn round. That way other things can progress.

Doing a nano sleep might not be a good idea, because nano seconds quite short and might be handled with calibrated iteration loop. OTOH a proper sleep with time of zero might just work... 

IDK I'm going to lurk on this thread to see what others say ;)

---

### Post by worksofcraft on 2010-08-28
...
For all on this thread here, I put together this little experiment that is supposed to test lapsed processor time to actual time ratio with or without a call to sched_yield().

However it appears to make no difference. I'm not sure if I did the fcntl thingy right to set it into non blocking test if key press mode and I also don't know if perhaps read might do some kind of yield implicitly... so my test is inconclusive... perhaps someone else can make sense of it ;)

```

#include <sched.h>
#include <stdio.h>
#include <sys/times.h>

int main(int argc, char **argv) {
	struct tms timeRecord;
	clock_t actual_time = times(&timeRecord);
	clock_t used_time = timeRecord.tms_utime;
	unsigned long iterations = 0;
	printf("using sched_yield=%s\n", (argc <= 1)? "No": "Yes");

	while (argc <= 1 || !sched_yield()) {
		if (++iterations > 60000000) break;
	}

	actual_time = times(&timeRecord) - actual_time; // elapsed time 
	used_time = timeRecord.tms_utime - used_time;
	printf(
		"iterations=%ld, actual_time = %ld, used_time = %ld, ratio= %f%%\n",
		iterations, actual_time, used_time, (float) used_time * 100.0/ (float) actual_time
	);
}

```

Update: Removed the key press and have a conclusion now:
Without the sched_yield, nearly 100% of the actual time is spent in the process.
With sched_yield only about 10%. That's on a system that has nothing much else to do.

Evidently the non blocking read() was still doing some kind of yielding before.

---

### Post by StephenF on 2010-08-29
What would your results be when running "stress -c 10" as a different process? That's simulating a system under heavy load versus one that's otherwise idling.

---

### Post by NovaAesa on 2010-08-29
Just let the process scheduler handle it, it knows what it's doing. If your tight loop happens to be busy-waiting, then think of another algorithm. If your tight loop is doing useful calculations, then there is no problem with it not yielding to the OS - the OS will take its time slice whenever it's its turn.

---

### Post by worksofcraft on 2010-08-29
> **NovaAesa said:**
> Just let the process scheduler handle it, it knows what it's doing. If your tight loop happens to be busy-waiting, then think of another algorithm. If your tight loop is doing useful calculations, then there is no problem with it not yielding to the OS - the OS will take its time slice whenever it's its turn.

Sadly that is not true. e.g. If you are a Windows consumer you may have heard of ASIO drivers? Well Linux has exactly the same problems... the musically talented are extremely sensitive to bad timing of audio! These primitive general purpose schedulers and some of the other processes they host simply aren't good enough company for musically proficient applications :shock:

p.s. see answer below... what would you rather have running on your desktop.. a program that when the processor is really heavy loaded, still consumes 30% of your processor time on it's idle loops, or one that using only 0.3%?

Yet both giving same performance!

p.s. One of the chapters from what I mention in [http://ubuntuforums.org/showthread.php?t=1563342](http://ubuntuforums.org/showthread.php?t=1563342)
was a complete preemptive multi tasking scheduler for MSDOS all written in C++... with only a few lines of assembler to handle hardware interrupts. At the time people were much more interested in windows 95 and Microsoft didn't have a clue about how to do multi tasking so I actually just gave up :P

---

### Post by worksofcraft on 2010-08-29
> **StephenF said:**
> What would your results be when running "stress -c 10" as a different process? That's simulating a system under heavy load versus one that's otherwise idling.

Nice question :)
with stress -c 10 running in the background
The processor usage of my idle loop **without** a yield was 30%
with calls to yield it was 0.3%

I listed the code, so do have a go on your computer...
```

g++ sched.cc
stress -c 10&
./a.out
# or
./a.out use sched_yield tyvm

```

---

### Post by nvteighen on 2010-08-29
Lol... you've made this thread interesting... without knowing yet what the OP wanted! :P

---

### Post by MadCow108 on 2010-08-29
> **worksofcraft said:**
> 
p.s. see answer below... what would you rather have running on your desktop.. a program that when the processor is really heavy loaded, still consumes 30% of your processor time on it's idle loops, or one that using only 0.3%?

I would not use a program which uses busy waits on a system which requires interactivity ...

If you need to process to wait for something, let it sleep and wake it up when it occurs.

---

### Post by worksofcraft on 2010-08-29
> **MadCow108 said:**
> I would not use a program which uses busy waits on a system which requires interactivity ...

If you need to process to wait for something, let it sleep and wake it up when it occurs.

Yes that is very sound advice :)

Alas people who program certain popular GUI desktop operating systems seem to think that you need "message pumps" running in tight loops and that having reentrant calls and call-backs between OS and application constitutes *multi-tasking* :shock:

---

### Post by rockom on 2010-08-30
Sorry I have not got back to this thread sooner.  It was a GREAT weekend. 

So...
I'm programming in C.  No C++ here.
The main loop is polling several serial ports, polling interprocess message queues, updating LED's, and maintaining scheduled events.  The schedules events only occur every 24 hours.  So most of the time, it does nothing.

At the bottom of my loop I have.

```
msleep(25);
```where
```
void msleep (int ms)
{
    struct timespec time;
    struct timespec remain;
    time.tv_sec = ms / 1000;
    time.tv_nsec = (ms % 1000) * (1000 * 1000);

    //sleep
    while (nanosleep(&time, &remain) == -1)
        time = remain;
}
```the primary purpose of msleep() is to allow my timers interrupts to work during the sleep.

This seems to work fine.  Without the msleep my process uses 100% of CPU (per top).  When using msleep the CPU time is negligible.

-Rocko

---

### Post by Arndt on 2010-08-31
> **rockom said:**
> Hello,

What the best way (best practice) for yielding to the OS/processor in a tight while(1) loop?

Thanks,
-Rocko

Does one of 'pause', 'select' or 'poll' do what you want?

---

### Post by worksofcraft on 2010-08-31
> **rockom said:**
> Sorry I have not got back to this thread sooner.  It was a GREAT weekend. 

So...
I'm programming in C.  No C++ here.
The main loop is polling several serial ports, polling interprocess message queues, updating LED's, and maintaining scheduled events.  The schedules events only occur every 24 hours.  So most of the time, it does nothing.

At the bottom of my loop I have.

```
msleep(25);
```where
```
void msleep (int ms)
{
    struct timespec time;
    struct timespec remain;
    time.tv_sec = ms / 1000;
    time.tv_nsec = (ms % 1000) * (1000 * 1000);

    //sleep
    while (nanosleep(&time, &remain) == -1)
        time = remain;
}
```the primary purpose of msleep() is to allow my timers interrupts to work during the sleep.

This seems to work fine.  Without the msleep my process uses 100% of CPU (per top).  When using msleep the CPU time is negligible.

-Rocko

Disadvantage of using any kind of sleep is that you have a potential latency in responding to whatever you are waiting for that is equal to your sleep time. You then need to add to that the worst case delay in preempting the process that is active at the time when the sleep ends:

Because your process was sleeping there can be a priority inversion where a low priority process needs to finish something before your higher priority job can be resumed. However I don't know enough about Linux scheduler to know if it could be an issue.

---

### Post by worseisworser on 2010-08-31
> **Arndt said:**
> Does one of 'pause', 'select' or 'poll' do what you want?

Also see epoll.

---

