---
title: "c++ wait / delay"
date: 2010-03-08
forum: Programming Talk
---

### Post by cholericfun on 2010-03-08
Hi

i'm just getting to know c++
was wondering how to pause the process for a
set amount of time (say some hours) before resuming
execution. Basically i am trying to write some sort of alarm clock.
so far the solutions i found occupy ~100% of the processor and
that is certainly not what i intend. Is there a less power-consuming way?
thanks

---

### Post by pbrane on 2010-03-08
You should investigate timers. glib has them, Qt has them, GTK has them...

---

### Post by dwhitney67 on 2010-03-08
> **cholericfun said:**
> Hi

i'm just getting to know c++
was wondering how to pause the process for a
set amount of time (say some hours) before resuming
execution. Basically i am trying to write some sort of alarm clock.
so far the solutions i found occupy ~100% of the processor and
that is certainly not what i intend. Is there a less power-consuming way?
thanks

The most 'famous' timer in the C/C++ domain is conjured up using alarm().  It is not the best solution, but for basic purposes, such as an alarm clock, it is usable.

Here's a practical (err, basic) solution:
```

#include <csignal>
#include <iostream>

class AlarmClock
{
public:
   AlarmClock(const unsigned int hour, const unsigned int min)
   {
      // Ideally, this method should accept a wake-up time.
      // Compute the delta time period from the wake-up time vs. the current time.
      // For now, just assume 5 seconds.

      int deltaSeconds = 5;

      signal(SIGALRM, AlarmClock::sigHandler);

      alarm(deltaSeconds);
   }

   void enable() const
   {
      pause();
   }

   bool isTimeToWakeUp() const
   {
      return wakeUp;
   }

private:
   static void sigHandler(int signo)
   {
      if (signo == SIGALRM)
      {
         wakeUp = true;
      }
   }

   static bool wakeUp;
};

bool AlarmClock::wakeUp = false;


int main()
{
   AlarmClock ac(8, 15);

   ac.enable();

   // the check of the alarm status is not really necessary, but shown
   // for sake of "completeness".
   if (ac.isTimeToWakeUp())
   {
      std::cout << "Get up... now!" << std::endl;
   }
}

```

---

### Post by psusi on 2010-03-08
Or you can just call usleep() assuming this is on a unix system.  Windows has Sleep().

---

### Post by dwhitney67 on 2010-03-08
> **psusi said:**
> Or you can just call usleep() assuming this is on a unix system.  Windows has Sleep().
usleep() is available, however it has it's limitations.

For instance, if I wanted to set the alarm off in 23 hours, 59 minutes...
```

#include <unistd.h>

int main(void)
{
   // delay for 23 hours, 59 minutes... in microseconds
   // ((23 * 60) + 59) * 60 * 1000000
   //
   const useconds_t delay = 86340000000;    // GCC warning on 32-bit system!

   usleep(delay);;
}

```
... I get the following on an attempt to compile the code above:
```

g++ usleep.cpp 
usleep.cpp:8: warning: integer constant is too large for &#8216;long&#8217; type
usleep.cpp: In function &#8216;int main()&#8217;:
usleep.cpp:8: warning: large integer implicitly truncated to unsigned type

```

P.S.  sleep(), which accepts a parameter representing a delay in seconds, is more appropriate.

---

### Post by cholericfun on 2010-03-09
thanks for the replies,
alarm() works perfect so far (in not using excessive cpu)
will have to try out a bit more.
actually sleep() works fine as well, much easier to use as well.

---

### Post by psusi on 2010-03-09
That example alarm code will just return without printing anything or waiting at all since isTimeToWakeUp() will return false before the alarm fires.

You want something like sleep() if you want to stop for a certain period of time.  You want alarm() if you want to keep doing other processing while you wait for the alarm to fire.

---

### Post by dwhitney67 on 2010-03-09
> **psusi said:**
> That example alarm code will just return without printing anything or waiting at all since isTimeToWakeUp() will return false before the alarm fires.

You want something like sleep() if you want to stop for a certain period of time.  You want alarm() if you want to keep doing other processing while you wait for the alarm to fire.

I attempted to provide a hint that the call to isTimeToWakeUp() was superfluous because the AlarmClock's enable() method calls the C library's pause() function.

The only way pause() would return would be if a signal, that is expected by the application, is delivered, or if for some unlikely reason, it fails.  The application only expects one type of signal, and that is SIGALRM.

In conclusion, the call to enable() is a blocking call; no other instructions in the code will be executed until it returns.  Sending a signal that is not expected by the application will simply terminate the app.

I hope now that this is somewhat clearer.

---

### Post by psusi on 2010-03-09
Ahh, I missed the pause().

---

