---
title: "Timing how long a function takes (C++)"
date: 2009-11-04
forum: Programming Talk
---

### Post by kachofool on 2009-11-04
Hey all

This is a general question... I'm trying to time how long some functions in my program take (some are I/O dependant, I want to see the latency introduced). Is it safe to use "gettimeofday" to 'time' how long these functions take? Or is there a better method?

ie.

```

gettimeofday(&time1, &tz);
MyIOFunction();
gettimeofday(&time2, &tz);

std::cout << "My IO Function took: " << time1.tv_usec - time2.tv_usec;


```

I just want an estimate.

Regards,

-Preet

---

### Post by Vernünftiger Verbrecher on 2009-11-04
It depends on how accurate you want your answer to be. The method you have there would give you a rough idea I imagine. Also, you'd want to say time2 - time1. ;)

---

### Post by MadCow108 on 2009-11-04
for a better estimate you could use the cycle counter which is available on some cpu's
on this page you find headers for it (under cycle counter):
[http://www.fftw.org/download.html](http://www.fftw.org/download.html)

I don't know how accurate that really is, but it is probably better than gettimeofday

it is mostly more interesting to know how much time is spent in which portion of the code instead of absolute times
for this purpuse callgrind is very useful (integrated in valgrind, call with valgrind --tool=callgrind)
use kcachegrind to get very nice display of the result

---

### Post by grayrainbow on 2009-11-04
Usually what is used are profile tools (as MadCow108 pointed [http://valgrind.org/](http://valgrind.org/) is quite good, best open source I know). Profiler will allow you to see not only time your program need to do some job, but more likely where this time is actually spend(it's better if you can tell most of this before even run the program :) ).
That's all really good...but! Well, quite frankly, profiling is not one day learning task. And if you don't want to fill your head with "useless at that time stuff" simple markers are just enough. Just remember that when you put markers before and after some function call you actually measure funcall overhead + the job of the function(which if it's not private function will involve and safety checks), so just put markers inside the function where from yours program point of view I/O really happen.

---

### Post by MindSz on 2009-11-04
When I want to easily time my programs, I use the clock() function, which returns the number of clock cycles since the beginning of your program.

Here's a little program that measures the time it takes to execute a 'for' loop from 0 to 1000000000 ...big number, but I'm just trying to make a point ;)

```
#include <stdio.h>
#include <time.h>
#include<string.h>

clock_t clk1;
clock_t clk2;
clock_t clk3;

int i;

int main(int argc, char *argv[])
{
  clk1 = clock();

  while(1){
    clk2 = clock();
    for (i = 0; i<1000000000; i++){}
    clk3 = clock();

    printf("LOOP:%f TOTAL:%f\n",
	   (float)(clk3-clk2)/CLOCKS_PER_SEC,
	   (float)(clk3-clk1)/CLOCKS_PER_SEC);
  }

  //Terminado OK  
  return 0;
}
```

It runs forever, so when u get tired use CTRL-C

I forgot: The reason I use this and not the other time functions is because of resolution. Most of the time functions only show u to the second, while using the actual machine clock can give u several more levels of precision.

---

### Post by dwhitney67 on 2009-11-04
> **MindSz said:**
> ...
I forgot: The reason I use this and not the other time functions is because of resolution. Most of the time functions only show u to the second, while using the actual machine clock can give u several more levels of precision.

gettimeofday() returns a time value (struct timeval) with a timing resolution in microseconds (1 E-06 seconds).  With clock_gettime(), one can get timing resolution in nanoseconds (1 E-09 seconds).

To be sure what time resolution one's system provides, calling clock_getres() should prove helpful.

---

### Post by Arndt on 2009-11-05
> **kachofool said:**
> Hey all

This is a general question... I'm trying to time how long some functions in my program take (some are I/O dependant, I want to see the latency introduced). Is it safe to use "gettimeofday" to 'time' how long these functions take? Or is there a better method?

ie.

```

gettimeofday(&time1, &tz);
MyIOFunction();
gettimeofday(&time2, &tz);

std::cout << "My IO Function took: " << time1.tv_usec - time2.tv_usec;


```

I just want an estimate.

Regards,

-Preet

There were several good answers. Note also that you must make a decision whether to measure real (wall clock) time or CPU time.

A trick that's sometimes useful and convenient is to modify the code so that the part you want to measure is done twice. Then you don't need to add any measurement code in the program, just run it. This assumes that the to-be-measured part can be called twice without changing the behaviour of the program, but that's often the case. It also assumes that the program runs to completion so its run time can be measured, so for daemons it's less useful (though you can look at the used runtime with 'ps' or 'top').

---

