---
title: "sleep(int) in C++?"
date: 2006-11-09
forum: Programming Talk
---

### Post by Lster on 2006-11-09
Is there any library that contains a sleep function. I really need to stop using 100% of the CPU.

Thanks,
Lster

---

### Post by Arndt on 2006-11-09
> **Lster said:**
> Is there any library that contains a sleep function. I really need to stop using 100% of the CPU.

Like this:

```
#inlcude <stdio.h>
#include <lib for sleep>

int main(){
    printf("3");
    sleep(1000);
    printf("2");
    sleep(1000);
    printf("1");
    sleep(1000);
    printf("Go!");
    sleep(1000);
    
    return 0;
}
```

Thanks,
Lster

```
$ man 3 sleep

NAME
       sleep - Sleep for the specified number of seconds

SYNOPSIS
       #include <unistd.h>

       unsigned int sleep(unsigned int seconds);

...

```

---

### Post by THaugland on 2006-11-09
You can use Posix threads (great for portability). I think the syntax is:

#inlcude <stdio.h>
#include <pthread.h>

int main(){
    printf("3");
    sleep(1);
    printf("2");
    sleep(1);
    printf("1");
    sleep(1);
    printf("Go!");
    sleep(1);
    
    return 0;
}

---

### Post by hod139 on 2006-11-09
There is not a c++ standard sleep (there is a posix standard shown above), but it is easy enough to write it yourself:

```

[COLOR=#339900]#include <time.h>[/COLOR]
 
[COLOR=#0000ff]void[/COLOR] sleep[COLOR=#000000]([/COLOR][COLOR=#0000ff]unsigned[/COLOR] [COLOR=#0000ff]int[/COLOR] mseconds[COLOR=#000000])[/COLOR]
[COLOR=#000000]{[/COLOR]
    [COLOR=#0000ff]clock_t[/COLOR] goal = mseconds + [COLOR=#0000dd]clock[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
    [COLOR=#0000ff]while[/COLOR] [COLOR=#000000]([/COLOR]goal > [COLOR=#0000dd]clock[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000])[/COLOR];
[COLOR=#000000]}[/COLOR]

```Not my code, credit goes to: [http://www.dreamincode.net/code/snippet38.htm](http://www.dreamincode.net/code/snippet38.htm)

---

### Post by Arndt on 2006-11-09
> **hod139 said:**
> There is not a c++ standard sleep (there is a posix standard shown above), but it is easy enough to write it yourself:

```

[COLOR=#339900]#include <time.h>[/COLOR]
 
[COLOR=#0000ff]void[/COLOR] sleep[COLOR=#000000]([/COLOR][COLOR=#0000ff]unsigned[/COLOR] [COLOR=#0000ff]int[/COLOR] mseconds[COLOR=#000000])[/COLOR]
[COLOR=#000000]{[/COLOR]
    [COLOR=#0000ff]clock_t[/COLOR] goal = mseconds + [COLOR=#0000dd]clock[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
    [COLOR=#0000ff]while[/COLOR] [COLOR=#000000]([/COLOR]goal > [COLOR=#0000dd]clock[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000])[/COLOR];
[COLOR=#000000]}[/COLOR]

```Not my code, credit goes to: [http://www.dreamincode.net/code/snippet38.htm](http://www.dreamincode.net/code/snippet38.htm)

The original poster did say that he "need[s] to stop using 100% of the CPU". Busy-looping is seldom a good idea.

---

### Post by hod139 on 2006-11-09
> **Arndt said:**
> The original poster did say that he "need[s] to stop using 100% of the CPU". Busy-looping is seldom a good idea.
Oops, good point :oops:

---

### Post by ansi on 2006-11-09
If you wouldn't like to make portable program (read: Windows), you can use "select()" to achieve similarity to the  "sleep()" function.

---

### Post by amo-ej1 on 2006-11-09
you could use hod139 's solution if you entered a 'sched_yield()' in the while() loop but that isn't portable either ;-)

---

### Post by Kopachris on 2008-08-13
I hate to resurrect what looks like a dead thread, but I'm trying to make a simple flight sim, so I need a portable sleep function that works in milliseconds or with a float seconds so I can accurately update speed and position.  Would nanosleep(1e6); work for one millisecond?  Thx!

Man page for nanosleep:
> 
NANOSLEEP(2)                BSD System Calls Manual               NANOSLEEP(2)

NAME
     nanosleep -- suspend thread execution for an interval measured in
     nanoseconds

LIBRARY
     Standard C Library (libc, -lc)

SYNOPSIS
     #include <time.h>

     int
     nanosleep(const struct timespec *rqtp, struct timespec *rmtp);

DESCRIPTION
     Nanosleep() causes the calling thread to sleep for the specified time
     (the actual time slept may be longer, due to system latencies and possi-
     ble limitations in the timer resolution of the hardware).  An unmasked
     signal will cause it to terminate the sleep early, regardless of the
     SA_RESTART value on the interrupting signal.


---

### Post by dwhitney67 on 2008-08-13
Of course it will work; just do the math correctly to compute the number of nanoseconds (1000000??)

An easier approach is perhaps to use usleep().  This functions accepts units in microseconds; thus if my math is correct, one millisecond is equivalent to 1000 microseconds.

---

### Post by Lster on 2008-08-13
Well, if you're using SDL, you could try SDL_Delay:

[http://www.libsdl.org/cgi/docwiki.cgi/SDL_Delay](http://www.libsdl.org/cgi/docwiki.cgi/SDL_Delay)

If you use nanosleep, be careful with resources (I've removed my code as it encourages poor use of this function):

[QUOTE=LibC]This function is a cancellation point in multi-threaded programs. This is a problem if the thread allocates some resources (like memory, file descriptors, semaphores or whatever) at the time nanosleep is called. If the thread gets canceled these resources stay allocated until the program ends. To avoid this calls to nanosleep should be protected using cancellation handlers.[/QUOTE]

[http://www.gnu.org/software/libc/manual/html_node/Sleeping.html#Sleeping](http://www.gnu.org/software/libc/manual/html_node/Sleeping.html#Sleeping)

---

### Post by Reiger on 2008-08-13
Would there be anything wrong with using the Linux API? I thought there were C functions built into the OS for this kind of trick? wait([args]) ?

Yep, sure looks like it:

[http://linux.about.com/od/commands/l/blcmdl2_wait.htm](http://linux.about.com/od/commands/l/blcmdl2_wait.htm)
[http://www.computerhope.com/unix/uwait.htm](http://www.computerhope.com/unix/uwait.htm)

---

### Post by Kopachris on 2008-08-13
Thanks.  I just wanted to make sure that it was a standard library function since I don't have a Windows machine to test it on since my PC's monitor died.

EDIT:  The sleep() function in "time.h" takes float values!  But I'm not sure whether or not that's just Xcode...

---

### Post by dwhitney67 on 2008-08-14
> **Lster said:**
> Well, if you're using SDL, you could try SDL_Delay:

[http://www.libsdl.org/cgi/docwiki.cgi/SDL_Delay](http://www.libsdl.org/cgi/docwiki.cgi/SDL_Delay)

If you use nanosleep, be careful with resources (I've removed my code as it encourages poor use of this function):



[http://www.gnu.org/software/libc/manual/html_node/Sleeping.html#Sleeping](http://www.gnu.org/software/libc/manual/html_node/Sleeping.html#Sleeping)
I'm sleepy and dehydrated... what causes that??  Hmmm??

Anyhow, Lster, are you answering your original question yourself?

---

### Post by dwhitney67 on 2008-08-14
> **Kopachris said:**
> Thanks.  I just wanted to make sure that it was a standard library function since I don't have a Windows machine to test it on since my PC's monitor died.

EDIT:  The sleep() function in "time.h" takes float values!  But I'm not sure whether or not that's just Xcode...
Thanks to who?  And for what?

If you want, you can pass a double into the sleep() function or whatever (see a bogus example below).  But seriously, it only takes unsigned integers, representing the number of seconds, as described in the API.  Any float or double will be rounded off (that is, down) to form an unsigned integer.  Thus 5.99999 will be 5 seconds.
[PHP]
#include <unistd.h>

int main()
{
  double val = 5.99999;
  sleep( val );
  return 0;
}
[/PHP]

---

### Post by Kopachris on 2008-08-14
It was originally thanks to anyone and everyone, I guess.  Who thought of accepting double values and rounding it down?  Why not just accept ints?  Nanosleep doesn't work, I looked at it and (in the Mac standard library, at least) it doesn't have much to do with "sleep" at all.  Hod139's sleep thing works pretty well, although it's dependent on how long the clock ticks are on the machine it runs on and takes longer depending on how fast your computer can decide whether or not "goal" is still grater than "clock()".  On my machine, this rounds out to about 1/100th of a second for one cycle (might have something to do with having iTunes running).  Ah, well, it should be good enough.

Boring, you-don't-care-about stuff:
[COLOR=White]But that sleep function is very similar to how you would make a TI 83-84+ graphing calculator sleep.  In TI BASIC, the calculator executes about 1 instruction per millisecond, so doing "FOR(x,0,1000):END" is a good way to get it to sleep for about a second.[/COLOR]

---

### Post by dwhitney67 on 2008-08-14
Below is an example program employing nanosleep().  If the program receives a signal, then nanosleep() will return before the time has expired (this is according to the API).  Thus in the program below I have demonstrated that nanosleep() can be called again after an expected signal has been received/processed.

[PHP]#define _POSIX_C_SOURCE 199309
#include <ctime>
#include <cerrno>
#include <csignal>
#include <cstring>
#include <cstdlib>

#include <iostream>

using namespace std;


void sigHandler( int signum )
{
  cout << "caught signal " << signum << endl;
}


void sleepFor( time_t seconds, long nsecs )
{
  timespec sleepPeriod = { seconds, nsecs };
  timespec unusedPeriod;

  for (;;)
  {
    if ( nanosleep( &sleepPeriod, &unusedPeriod ) == 0 )
    {
      break;
    }
    else if ( errno == EINTR )
    {
      cout << "sig detected... resuming timer." << endl;
      sleepPeriod = unusedPeriod;
    }
    else
    {
      cerr << "Error occurred with nanosleep; reason = " << strerror( errno ) << endl;
      break;
    }
  }
}


int main( int argc, char** argv )
{
  time_t seconds = 5;
  long   nsecs   = 0;

  if ( argc > 1 )
  {
    seconds = atoi( argv[1] );
  }
  if ( argc > 2 )
  {
    nsecs = atol( argv[2] );
  }

  signal( SIGUSR2, sigHandler );

  sleepFor( seconds, nsecs );

  cout << "time up!" << endl;

  return 0;
}
[/PHP]

P.S.  After compiling the program above, run it.  While it is running, send a USR2 signal to it to see the program output that the nanosleep (which was interrupted) is being resumed.
```

$ g++ nanosleep.cpp -o nanosleep
$ nanosleep 60 &
$ kill -s USR2 `pidof nanosleep`

```

---

### Post by KingTermite on 2008-08-14
> **hod139 said:**
> There is not a c++ standard sleep (there is a posix standard shown above), but it is easy enough to write it yourself:

```

[COLOR=#339900]#include <time.h>[/COLOR]
 
[COLOR=#0000ff]void[/COLOR] sleep[COLOR=#000000]([/COLOR][COLOR=#0000ff]unsigned[/COLOR] [COLOR=#0000ff]int[/COLOR] mseconds[COLOR=#000000])[/COLOR]
[COLOR=#000000]{[/COLOR]
    [COLOR=#0000ff]clock_t[/COLOR] goal = mseconds + [COLOR=#0000dd]clock[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR];
    [COLOR=#0000ff]while[/COLOR] [COLOR=#000000]([/COLOR]goal > [COLOR=#0000dd]clock[/COLOR][COLOR=#000000]([/COLOR][COLOR=#000000])[/COLOR][COLOR=#000000])[/COLOR];
[COLOR=#000000]}[/COLOR]

```Not my code, credit goes to: [http://www.dreamincode.net/code/snippet38.htm](http://www.dreamincode.net/code/snippet38.htm)

This is a busy loop and thankfully NOT how the real sleep() works. The real sleep uses signals and signal handlers.

---

### Post by KingTermite on 2008-08-14
Oops! dwhitney67 already beat me to it.

---

### Post by Kopachris on 2008-08-15
hod139's loop sleeper will be good enough.  I just need it to execute all it's instructions in a nice, even amount of time to make calculations consistent.  I don't necessarily need it to not use the CPU much since it's only going to be sleeping for probably a few hundredths of a second while it's not doing anything anyway.  Thanks for your help, everyone!

---

### Post by dwhitney67 on 2008-08-15
> **Kopachris said:**
> hod139's loop sleeper will be good enough.  I just need it to execute all it's instructions in a nice, even amount of time to make calculations consistent.  I don't necessarily need it to not use the CPU much since it's only going to be sleeping for probably a few hundredths of a second while it's not doing anything anyway.  Thanks for your help, everyone!
I disagree with your choice here; but do what you want.

Btw, here's another way to implement a delay in a program.  This code relies on select().
[PHP]#include <cstdlib>
#include <ctime>
#include <iostream>

int main( int argc, char **argv )
{
  const unsigned int sec  = argc > 1 ? atoi(argv[1]) : 5;
  const unsigned int usec = argc > 2 ? atoi(argv[2]) : 0;
  struct timeval     tv   = { sec, usec };

  std::cout << "Sleeping..." << std::endl;

  select( 0, 0, 0, 0, &tv );

  std::cout << "Yawn... time to get up!" << std::endl;

  return 0;
}[/PHP]

---

### Post by Orbital_sFear on 2008-09-06
Check out usleep.  That's what I use to get sub second sleeps

#include <unistd.h>

void msleep( int s )
{
  usleep( s * 1000 );
}

int main()
{
  usleep( 1000000 );  //Sleep for one second
  msleep( 1000 );     //Sleep for one second

  return 1;
}

---

### Post by DavidBell on 2008-09-06
Keep in mind that for non-deterministic OSs (like Linux and Windows) when you use functions like nanosleep, usleep, etc generally they mean sleep for *at least* the specified period, and there is no real upper limit. It's not unusual when you call these functions for the thread/process to lose CPU to other processes so a 1 usec delay can easily blow out to 10-100 msec.

Both OSs have realtime extentions that guarantee 1ms or less accuracy -  I haven't really gone into them but I think in both cases they have their own specialised sleep functions.

That was the status when I looked into this a year or so ago anyway.

HTH DB

---

