---
title: "timer interupt"
date: 2010-02-24
forum: Programming Talk
---

### Post by rockom on 2010-02-24
Hello,

The majority of my recent programming experience is with 8 and 16bit micro-controllers where hardware timer interrupts are simple to implement.  I have a few ideas on how to create a software timer interrupt but I'd like some input before I get too far.

What methods would you suggest to trigger a software interrupt after a variable amount of time has elapsed.  I must be able to service other functions during that time.  For example, I have 5 tasks that are serviced in my main program loop but every 500 milliseconds I want to service a 6th task and maybe every 5 seconds I service a 7th task.

In the 8 bit micro world I would just setup a free running timer to interrupt every 1 to 10 microseconds.  On interrupt decrement a counter, compare it to zero.  If Zero, set a 'service' flag and reset the counter.  Quick and simple.  I my main loop, service the functions whose flags are set. 

Thanks,
-Rocko

---

### Post by mdurham on 2010-02-24
It would probably help if you state which language are you using.

---

### Post by dwhitney67 on 2010-02-24
> **rockom said:**
> Hello,

The majority of my recent programming experience is with 8 and 16bit micro-controllers where hardware timer interrupts are simple to implement.  I have a few ideas on how to create a software timer interrupt but I'd like some input before I get too far.

What methods would you suggest to trigger a software interrupt after a variable amount of time has elapsed.  I must be able to service other functions during that time.  For example, I have 5 tasks that are serviced in my main program loop but every 500 milliseconds I want to service a 6th task and maybe every 5 seconds I service a 7th task.

In the 8 bit micro world I would just setup a free running timer to interrupt every 1 to 10 microseconds.  On interrupt decrement a counter, compare it to zero.  If Zero, set a 'service' flag and reset the counter.  Quick and simple.  I my main loop, service the functions whose flags are set. 

Thanks,
-Rocko

If you are developing in C/C++, you can use the timer_create() and timer_settime() to setup the real-time timer.  Your thoughts of using a semaphore in the interrupt (signal) handler will work just fine.  Your main loop will poll for the state of the semaphore as needed.

You can use usleep() to delay your main loop if it is running too fast; when the timer expires, _it will interrupt_ the usleep(), thus ensuring timely delivery of the semaphore's change of state.  I recommend that you setup usleep() for the same period that you setup the timer to expire.  The timer will expire before usleep() ever finishes, providing of course you have a load (ie. your main loop does something constructive).

To summarize in pseudocode:
```

1.  set up signal handler

2.  create timer

3.  configure timer with timeout period

4.  Enter main loop

    a. Check semaphore; if set

        - clear semaphore
        - do something

    b. Do other stuff

    c. Sleep for a minuscule period (optional)

    d. Return to step a.

```
The signal handler would merely have to do something like:
```

1.  Set semaphore

```

---

### Post by not_a_phd on 2010-02-24
I have a couple of applications that are doing same thing with a slight variation to dwhitney's theme. Instead of using usleep in the main loop, I use the sigsuspend(&emptyset). Also, I do all my synchronous stuff in the timer signal handler. 

To summarize in dwhitney's pseudocode:
 	Code:
 	1.  set up signal handler

2.  create timer

3.  configure timer with interval time period

4.  Spin off various other threads to do stuff like wait for 
    data on asynchronous serial or udp ports. 

4.  Enter main loop:

    sigemptyset(&set);
    while(true) {
       sigsuspend(&set);
       
       // Drops into this area after executing signal handler
       // every time period.

       // I normally leave this loop empty.

    }

I  set up all of my synchronous operations inside my timer signal handler:
 	Code:
 	1.  Increment a Counter
2.  Sample analog ports
...


I will readily admit, I do not fully understand all of the implications of the program structure above, and I welcome comment. My questions are:

- Are there issues with executing code inside the timer handler, so long as there is sufficient time within the defined interval?

- What is actually happening when we sigsuspend on the empty set? I know that the process stops until I get the timer signal, but I don't know why I wouldn't include the timer signal in the set of the sigsuspend argument.

---

### Post by rockom on 2010-02-24
> **mdurham said:**
> It would probably help if you state which language are you using.

I'm using C.  C++ is an option but C is preferred.
I'm using code:blocks to create a simple gcc console application.  The final app will be headless.

-Rocko

---

### Post by rockom on 2010-03-01
Thanks for the replies. 
I've think I'm set using timer_create() and timer_settime() as described.

Thanks again,
-Rocko

---

### Post by rockom on 2010-03-08
OK...this has been working great but now I have a new question.  Maybe I should post a new thread....let me know what you think.

Here is my code:

```

void initialize_timerA(int msec)
{
   struct sigaction timerA_sigact;
   struct sigevent  timerA_sigev;
   struct itimerspec timerA_itimer; 
   int timerA_rtn;
   timer_t timerA;

    // setup the signal
    sigemptyset(&timerA_sigact.sa_mask);

    timerA_sigact.sa_flags   = SA_SIGINFO;
    timerA_sigact.sa_handler = timerA_handler;

    sigaction(SIGRTMAX, &timerA_sigact, 0);

    // setup the timer
    memset(&timerA_sigev, 0, sizeof(timerA_sigev));

    timerA_sigev.sigev_notify          = SIGEV_SIGNAL;
    timerA_sigev.sigev_signo           = SIGRTMAX;
    timerA_sigev.sigev_value.sival_int = 1;

    timerA_rtn = timer_create(CLOCK_REALTIME, &timerA_sigev, &timerA);
    assert(timerA_rtn == 0);

    // start the timer
    timerA_itimer.it_interval.tv_sec = msec / 1000;
    timerA_itimer.it_interval.tv_nsec = (msec % 1000) * (1000 * 1000);
    timerA_itimer.it_value.tv_sec = msec / 1000;
    timerA_itimer.it_value.tv_nsec = (msec % 1000) * (1000 * 1000);

    timerA_rtn = timer_settime(timerA, 0, &timerA_itimer, 0);
    assert(timerA_rtn == 0);
}

void timerA_handler(int signo)
{
    if (signo == SIGRTMAX)
    {
        //set some flags
    }
}

void main(void)
{
     while(1){
     // poll for flags
     // look busy
     // sleep() if necessary
     }
}

```And for my question.
I had assumed I could just copy my timerA code and change timerA to timerB everywhere necessary allowing me to have two separate timers with their own time base. TimerA interrupts every 100ms and timerB maybe every 5 seconds.  But, it does not do that.  The handler for timerB fires on the timebase of timerA.  Anyway around this?

Thanks,
-Rocko

---

### Post by dwhitney67 on 2010-03-08
> **rockom said:**
> And for my question.
I had assumed I could just copy my timerA code and change timerA to timerB everywhere necessary allowing me to have two separate timers with their own time base. TimerA interrupts every 100ms and timerB maybe every 5 seconds.  But, it does not do that.  The handler for timerB fires on the timebase of timerA.  Anyway around this?

Thanks,
-Rocko
Assuming that you are using CLOCK_REALTIME for timer's A and B, AFAIK, the answer is no.  CLOCK_REALTIME represents a single timer.

If you need to perform special processing, say every 5 seconds, then consider incrementing a counter every time the 100ms timer expires.  When this counter reaches 50, then you can assume 5 seconds have elapsed.

---

### Post by rockom on 2010-03-08
*Update*

When I add a timerB, it trumps the timerA handler.  The timerB handler is triggered but at the period of timerA. 

-Rocko

---

### Post by rockom on 2010-03-08
> **dwhitney67 said:**
> Assuming that you are using CLOCK_REALTIME for timer's A and B, AFAIK, the answer is no.  CLOCK_REALTIME represents a single timer.


I'm using CLOCK_REALTIME and yes, I agree it's one single timer.

> **dwhitney67 said:**
> 
If you need to perform special processing, say every 5 seconds, then  consider incrementing a counter every time the 100ms timer expires.   When this counter reaches 50, then you can assume 5 seconds have  elapsed.

Exactly.  I use my 100ms timer for several counters. Some are 300ms, one is one seconds and another is 5 seconds so yes, that works fine.

In my post above, I used 100ms and 5sec just to try and keep it simple.  The point I guess is to make two or more timers with different periods.  In my actual app, the second timer needs to trigger an event that is much much longer than 5 seconds out.  It may be anywhere from several hours to several days out.  It's for scheduling automatic firmware updates to devices attached to USB ports.  I'll read a time and day from a configuration file, and then I'll know when the next 'automatic update' should occur.  If I use a counter with timerA and it's incrementing every 100ms, I'll have a huge number if my next update is 7 days from now.  However, if I setup a second timer (timerB) to expire every second or maybe even once a minute, my counter is more manageable.

I've found I can do the following.

In my initialize_timer routine I used the same signal number for both timerA and timerB.  So both handlers were setup to trigger on the same event: 

```
timerA_sigev.sigev_signo = SIGRTMAX
```I changed this in timerA to:
```
timerA_sigev.sigev_signo = TIMER_A_SIGNO
```And in timerB to:
```
timerB_sigev.sigev_signo = TIMER_B_SIGNO
```where:
```
#define TIMER_A_SIGNO    13
#define TIMER_B_SIGNO    14
```Now they trigger independently as they should.
The numbers I chose are arbitrary....I just picked something to make them different from each other.  Doing so allows me to have two timers from one real-time-clock.  I'm just not sure what the long term implications are.

I'd still like recommendations on a better way (if one exists) to use the signal.h library or a source for information on how to better understand the signal libraries and what the possibilities are.

An additional note, I chose not us use alarm() because only one alarm event is available.  With timers I can use multiple counters...

-Rocko

---

### Post by rockom on 2010-03-08
I've changed my signal numbers to be greater than 34 but less than 64.  That's the range of SIGRTMIN to SIGRTMAX.  Numbers 1~32 are defined in signum.h

This suggests I can't have more than 30 'user defined' signals.  I find that interesting.
However, it looks like within each signal number, I can filter for a signal value of type int.

-Rocko

---

### Post by dwhitney67 on 2010-03-08
Thanks for posting back your solution; it seems sound.  I cannot fathom why any application would ever need more than 30 timers.

---

### Post by rockom on 2010-03-09
I hope I never need more than a few timers.  Anymore would get out of hand real quick.  For the most part, one is plenty.

If I come up with anything worth posting as I continue to develop my solution, I'll be sure to post an update.

Thanks,
-Rocko

---

