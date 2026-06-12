---
title: "C++ and accurate timers under Linux?"
date: 2008-10-05
forum: Programming Talk
---

### Post by Calmatory on 2008-10-05
I need accurate timer, whith precision at least of 1/1000th of a second, in other words one ms.

However, C's own clock_t and clock() under time.h fluctuate way too much and can not be used for reliable time measurement.

In Windows, it is easy to use windows.h's GetTickCount(), but how could this be done under Linux? Is there a working library for it?

---

### Post by dwhitney67 on 2008-10-05
Consider using the C-library select() function.

[php]
#include <sys/time.h>
#include <unistd.h>

int main()
{
  struct timeval tv = { 0, 1000 };   // setup for 1 millisecond = 1000 microseconds

  select( 0, 0, 0, 0, &tv );         // delay

  return 0;
}
[/php]

P.S.  Sometimes I make mathematical errors; forgive me if 1000 microseconds does not equal 1 millisecond.

---

### Post by dwhitney67 on 2008-10-05
> **Calmatory said:**
> ...
However, C's own clock_t and clock() under time.h fluctuate way too much and can not be used for reliable time measurement.
...

I re-read your OP.  Can you back up the statement above with the source as to where you read about clock() being unreliable?  Was it the man-page or other source?

Btw, here's a simple program using clock().
[PHP]#include <unistd.h>
#include <limits>
#include <iostream>

void function()
{
  const unsigned int MAX = std::numeric_limits<unsigned int>::max() / 8;

  for ( unsigned int i = 0; i < MAX; ++i )
  {
    double value = ((i * 33.3) - 12.1) / 10.0;
    value += 1.0;
  }
}

int main()
{
  clock_t start  = clock();
  function();  // invoke something to create an artificial load on the program
  clock_t finish = clock();

  std::cout << "time delta (proc time) = " << (finish-start) << std::endl;
  std::cout << "time delta (seconds)   = " << ((finish-start)/CLOCKS_PER_SEC) << std::endl;

  return 0;
}[/PHP]

---

### Post by Npl on 2008-10-05
> **dwhitney67 said:**
> I re-read your OP.  Can you back up the statement above with the source as to where you read about clock() being unreliable?  Was it the man-page or other source?clock() uses the Realtime-Clock (RTC), which is a component on your motherboard. There are huge variations in granularity between different RTC, alot of them are nowhere near millisecond resolution.
Its unreliable as high-resolution measurement.

I know you could count ticks with assembler instructions (which have their own share of problems), but it would be best to find some crossplattform library. Dunno, maybe SDL has such functions.

---

### Post by Zugzwang on 2008-10-05
> **Npl said:**
> clock() uses the Realtime-Clock (RTC), which is a component on your motherboard. There are huge variations in granularity between different RTC, alot of them are nowhere near millisecond resolution.
Its unreliable as high-resolution measurement.

I know you could count ticks with assembler instructions (which have their own share of problems), but it would be best to find some crossplattform library. Dunno, maybe SDL has such functions.

What brought you to the conclusion that clock() uses RTC? According to [a man page for clock()]("http://opengroup.org/onlinepubs/007908799/xsh/clock.html"), the function measures time spent in the process with an accuracy dependent on the implementation of the function.

In SDL, You could use the [respective function]("http://www.libsdl.org/cgi/docwiki.cgi/SDL_GetTicks").

---

### Post by Calmatory on 2008-10-05
My own experience suggests that clock() is inaccurate. I once tried to make a program to benchmark the CPU by calculating primes. The results were VERY much off from each other. When the program said it took 40 seconds to calculate, in practice it took 30 seconds, measured with sport watch and a cell phone. After I used GetTickCount() in windows.h, the results were alot moer accurate and gave the real time it spent calculating.

---

### Post by dwhitney67 on 2008-10-05
> **Calmatory said:**
> My own experience suggests that clock() is inaccurate. I once tried to make a program to benchmark the CPU by calculating primes. The results were VERY much off from each other. When the program said it took 40 seconds to calculate, in practice it took 30 seconds, measured with sport watch and a cell phone. After I used GetTickCount() in windows.h, the results were alot moer accurate and gave the real time it spent calculating.
It seems that you applied the use of clock() incorrectly.  It does not measure real-time, that is the time-delta as derived from taking measurements from a stopwatch, mobile phone, etc.

clock() can be used to measure the (approximate) _amount of processor time_ that a program consumes.  Thus if you have other processes running on your system, you cannot expect the results provided by clock() to equal that provided by a stopwatch.

A process only runs while it has control of the processor.  When a process exhausts its given time-slice period, another process will be run and the first process will lie dormant for a brief period.  At the end of the time-slice, the OS *may* give the first program another opportunity to use the processor.  But if the system is busy with many processes, then this may not be the case.

The "time" utility (in /usr/bin) seems to be able to measure the time (to a resolution of milliseconds) it takes a program to run, however it too may not be absolutely accurate.  Look at the source code for this utility to see how the authors were able to measure the real-time a program spent executing.

---

### Post by gnusci on 2008-10-07
I don't know whether there is a function or not, but this code can give you some ideas:

[PHP]#include <iostream>
#include <ctime>
#include <iomanip>

double mstimer(clock_t tstart, clock_t tstop){
  return 1000*(double)(tstop-tstart)/(double)(CLOCKS_PER_SEC);
}

int main(void){
  //
  clock_t tstart=0, tstop=0;
  //
  // the strart time counter
  tstart = clock();
  // the things you what to measure
  for(int i=0; i<10000; i++){
    for(int j=0; j<10000; j++){
      double di = (double)i*0.5+(double)j;
      double dj = di*di*di-di;
      di = dj*i/(dj+i);
    }
  }
  // the stop time counter
  tstop = clock();
  // time in (ms)
  std::cout<< mstimer(tstart,tstop)<< " (ms)" << std::endl;
  //
  return 0;
}
[/PHP]

---

### Post by jespdj on 2008-10-07
I'm not an expert in this, but as far as I know you need to install a [realtime kernel](https://wiki.ubuntu.com/RealTime/Hardy) if you need precise and high resolution timers on Linux.

For Ubuntu, you can install the package **linux-rt** which installs the realtime version of the current kernel for your Ubuntu version alongside the normal kernel; in the GRUB menu you can select to boot with the realtime kernel.

---

### Post by dwhitney67 on 2008-10-07
> **gnusci said:**
> I don't know whether there is a function or not, but this code can give you some ideas:

[PHP]#include <iostream>
#include <ctime>
#include <iomanip>

double mstimer(clock_t tstart, clock_t tstop){
  return 1000*(double)(tstop-tstart)/(double)(CLOCKS_PER_SEC);
}

int main(void){
  //
  clock_t tstart=0, tstop=0;
  //
  // the strart time counter
  tstart = clock();
  // the things you what to measure
  for(int i=0; i<10000; i++){
    for(int j=0; j<10000; j++){
      double di = (double)i*0.5+(double)j;
      double dj = di*di*di-di;
      di = dj*i/(dj+i);
    }
  }
  // the stop time counter
  tstop = clock();
  // time in (ms)
  std::cout<< mstimer(tstart,tstop)<< " (ms)" << std::endl;
  //
  return 0;
}
[/PHP]
Brilliant!  You took the number of seconds that a process executed and multiplied by a 1000 to yield milliseconds.  Now why didn't I think of that?

---

### Post by gnusci on 2008-10-07
> **dwhitney67 said:**
> Brilliant!  You took the number of seconds that a process executed and multiplied by a 1000 to yield milliseconds.  Now why didn't I think of that?

Thanks dwhitney67... I just wanted to give the correct output to the OP, but actually your solution was fine, since the OP can straight forward get the seconds.

---

### Post by Npl on 2008-10-07
> **Zugzwang said:**
> What brought you to the conclusion that clock() uses RTC? According to [a man page for clock()]("http://opengroup.org/onlinepubs/007908799/xsh/clock.html"), the function measures time spent in the process with an accuracy dependent on the implementation of the function.I somehow mixed it up with the time() function. My apologies.

---

### Post by MimeNarrator on 2010-07-09
I see that this thread is long dead, but for future googlers who come across it as I did in their search for an accurate way to compare execution times in C or C++, a very simple solution is provided by the cycle.h file included with the source code for FFTW, available at [http://www.fftw.org](http://www.fftw.org). It can be included in any program (subject to FFTW's license) independently from the rest of FFTW, and implements a tick counter using inline assembly provided for many different architectures.[URL="http://www.fftw.org/"]
[/URL]

---

