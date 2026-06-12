---
title: "Inconsistency in time(NULL)"
date: 2009-05-23
forum: Programming Talk
---

### Post by asbuntu on 2009-05-23
(Hardy Heron (8.04) running on i386 platform,
 fully updated as of 5/23/09
 libc.a timestamp = 2906374 2008-09-12 10:33)

Help.  I'm frustrated.  I'm getting inconsistent results from the time() function in an ordinary c program.  Program...

```

/* ttime.c */
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main() {
  time_t tt, tt2;
  struct timeval tv;
  struct timezone tz;
  for (;;) {
    for (;;) {
      tt2 = time(NULL);
      if (tt != tt2) {
        tt = tt2;
        gettimeofday(&tv, &tz);
        break;
      }
    }
    printf("%10d %6d %s", tv.tv_sec, tv.tv_usec, asctime(localtime(&tt))); 
  }
}

```

I'm expecting one line of output every one second, because I detect when time() changes.  Problem is that I get multiple lines, at random times, with the same time() value.  Sometimes, asctime() will actually go backwards and then forward.

(I added the call to gettimeofday() to try to get a handle on what was going on.)  Typical output...

1243116146    343 Sat May 23 18:02:26 2009
1243116146  66844 Sat May 23 18:02:25 2009
1243116146  66855 Sat May 23 18:02:26 2009
1243116146  90870 Sat May 23 18:02:25 2009
1243116146  90879 Sat May 23 18:02:26 2009
1243116146 124106 Sat May 23 18:02:25 2009
1243116146 124116 Sat May 23 18:02:26 2009
1243116146 135259 Sat May 23 18:02:25 2009
1243116146 135270 Sat May 23 18:02:26 2009
1243116147    342 Sat May 23 18:02:27 2009
1243116147 191585 Sat May 23 18:02:26 2009
1243116147 191593 Sat May 23 18:02:27 2009
1243116148    342 Sat May 23 18:02:28 2009
1243116149    342 Sat May 23 18:02:29 2009
1243116149 190849 Sat May 23 18:02:28 2009
1243116149 190859 Sat May 23 18:02:29 2009
1243116149 250847 Sat May 23 18:02:28 2009
1243116149 250856 Sat May 23 18:02:29 2009

Where each line with the same time() value is printed at the same time.

In the original (larger) program, the core issue was the snippet...

```

  for (;;) {
    while (tt==time(NULL)); // wait until next second - burn CPU time
    tt = time(NULL);        // update last value
    // do something once per second
  }

```

This alternate program works perfectly...

```

/* ttime2.c */
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main() {
  time_t tt;
  struct timeval tv;
  struct timezone tz;
  for (;;) {
    for (;;) {
      gettimeofday(&tv, &tz);
      if (tv.tv_sec != tt) {
        tt = tv.tv_sec;
        break;
      }
    } 
    printf("%10d %6d %s", tv.tv_sec, tv.tv_usec, asctime(localtime(&tt))); 
  }
}

```

Output...
1243116363 241413 Sat May 23 18:06:03 2009
1243116364      0 Sat May 23 18:06:04 2009
1243116365      0 Sat May 23 18:06:05 2009
1243116366      0 Sat May 23 18:06:06 2009
1243116367      0 Sat May 23 18:06:07 2009
1243116368      0 Sat May 23 18:06:08 2009
1243116369      0 Sat May 23 18:06:09 2009
1243116370      0 Sat May 23 18:06:10 2009
1243116371      0 Sat May 23 18:06:11 2009
1243116372      0 Sat May 23 18:06:12 2009

What bothers me is that, behind the scenes, time() and gettimeofday() should have the same behavior for the integer part, and worse, the program depends on a time_t changing - which it appears to not - yet the program detects that and outputs a line.

I thought time_t was defined as an arithmetic type representing the number of seconds since the epoch.  That sounds integral to me.

Even more interesting is that I get stable results on other systems.  Even more and more interesting is that in the actual (larger) program that I incorporating this into, I get different results when I move things around.  That sounds like memory damage or uninitialized memory, but I can't find it.

Is there something wrong with my system, or with my implementation?

I have been over this for several weeks now, and I just can't see it.

Thanks for very much.
Alex

---

### Post by asbuntu on 2009-05-23
FYI - In case anyone wonders why I don't just use the working alternate, its because I'm bothered by what looks like strange behavior in time(NULL) or (more probably) a bug in my own code.  :-)

---

### Post by Ackowa on 2009-05-25
If I remember correctly there are some optimisations in the kernel for time(NULL), so is doesn't always look at the clock but rather uses some estimative calculation that returns value close to true clock second but is much faster then looking for the exact real time.
And time has code so it reads the real time in between to correct it self.

So what probably happens is that this estimate value is returned some of the times and the real value some times with might leave you with estimated switching sec before the real time and then getting corrected causing multiple printouts.

---

### Post by asbuntu on 2009-05-25
I thought about that as well, but the inconsistency of the inconsistent results :-) made me change my mind.

Originally this was to have been a simple demo showing the difference in performance between different platforms, such as virtual vs real.  The core loop, `while (tt == time(NULL)));` would have contained some code, a counter at its simplest, that I would report once each second.  The original version was ..

```

#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main() {
  time_t tt; 
  int loops;
  for (;;) {
    for (loops=0, tt=time(NULL); tt==time(NULL); loops++);
  printf("%d %s", loops, asctime(localtime(&tt)));
  }
}

```

Now the problem has evolved into finding out why the platform, compiler, library or program is not doing what I expected.

The idea of internal optimizations is interesting, but does that explain how asctime() is returning results that appear to jump **backwards** in time?

The core concern, however, is that i break out of my inner loop when the time_t value of time(NULL) changes.  It changes, I break out of the loop, but then I break out of the loop again and again **without** time_t changing, and that is mystifying me?  Thanks.

Alex

---

### Post by asbuntu on 2009-06-13
I was talking to a friend, who is a main-stream physicist working with supercomputers.  He said something about "global optimizations" in gcc that might account for the behavior I'm experiencing.  I'm not quite sure I agree, because one of the steps I used was to make sure all optimizations were turned off.

To make matters worse, the program is not acting up right now, and I certainly did not recompile it.  Odd???

Anyway, does anyone know about this topic of "global optimizations" with gcc, or have any insight into the problem at hand?  What about the possibility of a kernel bug that got fixed when I updated the system?  Thank you.

---

### Post by soltanis on 2009-06-13
Maybe you should turn optimizations off (gcc -O0, that's "minus oh zero"), and see if that helps.

And look into these functions:
[http://linux.die.net/man/3/clock_gettime](http://linux.die.net/man/3/clock_gettime)

Which may not do the so-called "optimizations" which are screwing you up.

---

### Post by asbuntu on 2009-06-13
> **soltanis said:**
> Maybe you should turn optimizations off (gcc -O0, that's "minus oh zero"), and see if that helps.


Been there.  Done that.  No help.

> 
And look into these functions:
[http://linux.die.net/man/3/clock_gettime](http://linux.die.net/man/3/clock_gettime)

Which may not do the so-called "optimizations" which are screwing you up.

Problem there is that **time_t time(&time_t)** is a very well defined _base library function_ that should work _exactly the same_ everywhere.

Yes, I can solve (and have solved) this issue using other calls, such as GetSystemTime, but the real issue is that I'm trying to find out why a basic system call is operating inconsistently.

I am not so egotistic that I consider that my code to be perfect.  Far from it.  I have done what I think is a reasonable job of looking at all the possibilities.  I even treated the time_t value as opaque, as it should be, and did not attempt to do anything with it, not even comparison, without using defined conversion routines.  I broke out each of the steps in the primary loop into single action steps, thinking I had a sequence problem.  Nothing helped.

One poster noted that the OS might be rounding things.  Well, if that's true, I would still expect consistent results.  The case where the result went backwards and then forward was most mystifying, as is the primary issue where I break out of the primary loops multiple times with the same value.

The biggest hint of something odd is that, in my original program, if I move things around, the results change.  That is a classic sign that something is not being initialized or that something is overrunning memory, but I just can not seem to find it.

Right now I have two systems that seem to work and one that does not.

My reason for pushing on this is that I consider the most likely explanation to be that I did something wrong, and if a find a "solution" that masks the issue, then I run the risk of having the problem pop up at the worst possible time, such as during the execution of a production, mission critical process.

Thank you.  Is this compiler?  OS?  Me?  Any other ideas?

---

### Post by soltanis on 2009-06-13
It is probably the system in this case. Though it is true that all systems have to reasonably implement the time() call, there is a lot of flexibility in the accuracy of the time (indeed, ANSI C warns that the resolution of time() may vary from system to system). It's likely that Linux devs, thinking (perhaps not incorrectly) that time() is only used for timestamping files/packets and that other functions will be used for time-critical tasks, implemented this shortcut.

You're just going to have to use a different function in this case. If you are that concerned about portability, wrap the OS-dependent call in an inline function and change just that function when you port to a different system.

Have you tried lint or valgrind against your code? I assume you've already run the compiler with all warnings turned on and it didn't tell you anything.

---

### Post by asbuntu on 2009-06-13
> **soltanis said:**
> You're just going to have to use a different function in this case. If you are that concerned about portability, wrap the OS-dependent call in an inline function and change just that function when you port to a different system.


I thought **time_t time(&time_t)** _was_ portable???


Besides, whenI say I have three systems, I'm talking about three ubuntu systems; one real, two virtual.  I'm trying to compare performance between native mode and virtual mode.  I'm not trying to compare, for instance, ubuntu against Windows.

> 
Have you tried lint or valgrind against your code? I assume you've already run the compiler with all warnings turned on and it didn't tell you anything.

I have not tried lint or valgrind.  I will look at them.

Yes, I tried all warnings, even up to pedantic, strict ANSI, etc.

Thank you.

---

### Post by soltanis on 2009-06-13
> 
time returns the current calendar time or -1 if the time is not available. If tp is not NULL, the return value is also assigned to *tp.


Either your code has a bug, or time() isn't meant to be used for implementing timers.

---

### Post by Lux Perpetua on 2009-06-14
For what it's worth, I ran your program, and here's what I got: ```
> a.out
1245005623 196829 Sun Jun 14 11:53:43 2009
1245005624   1070 Sun Jun 14 11:53:44 2009
1245005625   1070 Sun Jun 14 11:53:45 2009
1245005626   1070 Sun Jun 14 11:53:46 2009
1245005627   1070 Sun Jun 14 11:53:47 2009
1245005628   1070 Sun Jun 14 11:53:48 2009
1245005629   1070 Sun Jun 14 11:53:49 2009
1245005630   1070 Sun Jun 14 11:53:50 2009
1245005631   1070 Sun Jun 14 11:53:51 2009
1245005632   1085 Sun Jun 14 11:53:52 2009
1245005633   1069 Sun Jun 14 11:53:53 2009
1245005634   1070 Sun Jun 14 11:53:54 2009
1245005635   1069 Sun Jun 14 11:53:55 2009
1245005636   1070 Sun Jun 14 11:53:56 2009
1245005637   1069 Sun Jun 14 11:53:57 2009

```It seems to work over here. Compiler: ```
> gcc -v
Using built-in specs.
Target: i686-pc-linux-gnu
Configured with: ../configure --prefix=/usr --enable-shared --enable-languages=c,c++,fortran,objc,obj-c++ --enable-threads=posix --mandir=/usr/share/man --infodir=/usr/share/info --enable-__cxa_atexit --disable-multilib --libdir=/usr/lib --libexecdir=/usr/lib --enable-clocale=gnu --disable-libstdcxx-pch --with-tune=generic
Thread model: posix
gcc version 4.4.0 20090505 (prerelease) (GCC) 

```glibc is 2.10.1. 

In general, though, even if it works, that's not a good way to implement a timer: your program is eating CPU power constantly, even when it's just waiting for the second to change. Is there any particular reason you're not just using something like sleep(1)? That would free the processor for other tasks while your program waits.

---

### Post by asbuntu on 2009-06-14
> **soltanis said:**
> Either your code has a bug, or time() isn't meant to be used for implementing timers.

I'll go with the bug answer, though for the life of me I can not find it.  I have seen asctime print _two different values_ for the same _tt_.  Very odd.

As for "the current calendar time", the documentation actually says "an arithmetic type representing the seconds since the epoch".  Some people treat time_t as a long.  While workable, this is wrong.  A time_t value is to be treated as an opaque value, and converted _only_ using the defined functions, such as _asctime_.  Comparison, for example, is not defined.

Using the above argument, my code is clearly wrong.  In my defense, I have tried this every way possible, including formally using time_t correctly, and only calling time() one time, detecting its changed value, and then converting it properly.  All variations return the same insinsistent results, hence my simplification in the original post.

Thank you.  At this point, I'm, assuming some bug in my ubuntu system.  I intend to save it, and reinstall it.

---

### Post by asbuntu on 2009-06-14
> **Lux Perpetua said:**
> For what it's worth, I ran your program, and here's what I got: ```
> a.out
1245005623 196829 Sun Jun 14 11:53:43 2009
1245005624   1070 Sun Jun 14 11:53:44 2009
{snip}

```It seems to work over here. Compiler: ```
> gcc -v
Using built-in specs.
Target: i686-pc-linux-gnu
Configured with: ../configure --prefix=/usr --enable-shared --enable-languages=c,c++,fortran,objc,obj-c++ --enable-threads=posix --mandir=/usr/share/man --infodir=/usr/share/info --enable-__cxa_atexit --disable-multilib --libdir=/usr/lib --libexecdir=/usr/lib --enable-clocale=gnu --disable-libstdcxx-pch --with-tune=generic
Thread model: posix
gcc version 4.4.0 20090505 (prerelease) (GCC) 

```glibc is 2.10.1. 

In general, though, even if it works, that's not a good way to implement a timer: your program is eating CPU power constantly, even when it's just waiting for the second to change. Is there any particular reason you're not just using something like sleep(1)? That would free the processor for other tasks while your program waits.

I agree.  This is a horrible way to implement a timer.  I would never do this for a production system.  My intent was to answer the question/observation by an associate that running ubuntu in a VM was slow, because every instruction is emulated.  My suspicion is that only privileged instructions are emulated and that normal instructions are run natively.

The program is deliberately designed to burn CPU cycles.  In the bigger version (see earlier posts) I actually report how many times I go through that inner loop.  Thank you.

---

### Post by Lux Perpetua on 2009-06-14
Sorry, I apparently glossed over the part about demonstrating performance differences. > **asbuntu said:**
> I'll go with the bug answer, though for the life of me I can not find it.  I have seen asctime print _two different values_ for the same _tt_.  Very odd.That is very odd. Do you still have the program that produced that behavior? That might be the one we should be looking at. 

Some of the time functions return pointers to static data that multiple functions share, so conceivably that could cause apparently strange behavior. I don't know if that's the source of your trouble; right now, I can't see how it would make a difference in the code you've posted so far.

---

### Post by asbuntu on 2009-06-15
> **Lux Perpetua said:**
> Sorry, I apparently glossed over the part about demonstrating performance differences. That is very odd. Do you still have the program that produced that behavior? That might be the one we should be looking at.

No problem.  I even have trouble keeping track of this thread.  Here is the minimalist version of the code...

```

#include <stdlib.h>
#include <stdio.h>
#include <time.h>

int main() {
  time_t tt;
  for (;;) {
    while (tt == time(NULL));
    tt = time(NULL);
    printf("%10d %s", tt, asctime(localtime(&tt)));
  }
}

```

Thanks.

---

### Post by Lux Perpetua on 2009-06-16
Sorry, I've got nothing! I can't spot any bugs. Also, I ran it on two different Linux installations with completely normal results (one line every second). 

However, I did catch a small thing in some earlier posts: > 
...and worse, the program depends on a time_t changing - which it appears to not - yet the program detects that and outputs a line.The time_t variable (the value of time(NULL)) *is* changing; in your code, what you print out (the thing that isn't changing) is the tv_sec field of gettimeofday(). Apparently time(NULL) is returning unexpected results, but everything else seems to work as expected. To confirm that, you can print out the value of tt in your printf statement.

---

### Post by Zugzwang on 2009-06-16
The last code also works fine here. 

Note that in the first post, the author of the code assumes that "gettimeofday" and "time(NULL)" are using the same source for time values. However, the system has two clocks: One somewhere on the mainboard and one managed by the Linux kernel and updated after every so-and-so many clock cycles. There is no guarantee that "gettimeofday" and "time(NULL)" are using the same source, which may result in deviations.

---

### Post by Lux Perpetua on 2009-06-16
> **Zugzwang said:**
> The last code also works fine here. 

Note that in the first post, the author of the code assumes that "gettimeofday" and "time(NULL)" are using the same source for time values. However, the system has two clocks: One somewhere on the mainboard and one managed by the Linux kernel and updated after every so-and-so many clock cycles. There is no guarantee that "gettimeofday" and "time(NULL)" are using the same source, which may result in deviations.That would explain everything, but it's still strange that one of the clocks (the one used by time()) would behave so erratically.

---

### Post by asbuntu on 2009-06-16
> **Lux Perpetua said:**
> Sorry, I've got nothing! I can't spot any bugs. Also, I ran it on two different Linux installations with completely normal results (one line every second). 

However, I did catch a small thing in some earlier posts: The time_t variable (the value of time(NULL)) *is* changing; in your code, what you print out (the thing that isn't changing) is the tv_sec field of gettimeofday(). Apparently time(NULL) is returning unexpected results, but everything else seems to work as expected. To confirm that, you can print out the value of tt in your printf statement.

I am printing out tt.  I added tv_sec in an attempt to isolate the problem.  The interesting part of this is that it seems that I break out of the inner loop multiple times for the same value of tt, and I also sometimes get different results from asctime() for the same value of tt.  Also, if I use gettimeofday() instead of time(), my results are rock solid.  (The whole intent of this thread was to ask if there was any known issue with time().)  Doesn't that just beat all?

Anyway, thanks for looking at this.  Unless you or anyone else has any other ideas, I plan to chalk this up to some kind of corruption in my installation, save the installation, and reinstall from scratch.  Thanks, again.

---

### Post by asbuntu on 2009-06-16
For what its worth, i was searching google and found this VERY interesting post from several years ago...

> lkml.indiana.edu/hypermail/linux/kernel/0111.0/1465.html

The writer seems to be talking about an inconsistency between time() and gettimeofday().   Hmmmmm....

---

### Post by Lux Perpetua on 2009-06-16
> **asbuntu said:**
> I am printing out tt.  I added tv_sec in an attempt to isolate the problem.  The interesting part of this is that it seems that I break out of the inner loop multiple times for the same value of tt, and I also sometimes get different results from asctime() for the same value of tt.  Also, if I use gettimeofday() instead of time(), my results are rock solid.  (The whole intent of this thread was to ask if there was any known issue with time().)  Doesn't that just beat all?

Anyway, thanks for looking at this.  Unless you or anyone else has any other ideas, I plan to chalk this up to some kind of corruption in my installation, save the installation, and reinstall from scratch.  Thanks, again.I was referring mainly to this program: ```

/* ttime.c */
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <sys/time.h>

int main() {
  time_t tt, tt2;
  struct timeval tv;
  struct timezone tz;
  for (;;) {
    for (;;) {
      tt2 = time(NULL);
      if (tt != tt2) {
        tt = tt2;
        gettimeofday(&tv, &tz);
        break;
      }
    }
    printf("%10d %6d %s", tv.tv_sec, tv.tv_usec, asctime(localtime(&tt))); 
  }
}
```This program does not print out tt. This is the one you said gave you these results: > 
1243116146 343 Sat May 23 18:02:26 2009
1243116146 66844 Sat May 23 18:02:25 2009
1243116146 66855 Sat May 23 18:02:26 2009
1243116146 90870 Sat May 23 18:02:25 2009
1243116146 90879 Sat May 23 18:02:26 2009
1243116146 124106 Sat May 23 18:02:25 2009
1243116146 124116 Sat May 23 18:02:26 2009
1243116146 135259 Sat May 23 18:02:25 2009
1243116146 135270 Sat May 23 18:02:26 2009
1243116147 342 Sat May 23 18:02:27 2009
1243116147 191585 Sat May 23 18:02:26 2009
1243116147 191593 Sat May 23 18:02:27 2009
1243116148 342 Sat May 23 18:02:28 2009
1243116149 342 Sat May 23 18:02:29 2009
1243116149 190849 Sat May 23 18:02:28 2009
1243116149 190859 Sat May 23 18:02:29 2009
1243116149 250847 Sat May 23 18:02:28 2009
1243116149 250856 Sat May 23 18:02:29 2009Some of your programs do print out tt, but you didn't post the output of those programs. At least in this program, it's not the same value of tt causing the loop to break multiple times. It's the same value of tv.tv_sec, which just means tt and tv.tv_sec aren't in agreement, i. e., that time() and gettimeofday() are not in agreement with one another. If you changed that program to print out tt, you'd see different values, presumably jumping back and forth just like asctime is telling you. 

I understand that time() and gettimeofday() might be looking at different clocks, so there's no surprise that they don't agree exactly. However, one of the clocks is clearly broken (it counts backwards sometimes), which is a serious problem no matter how you look at it. I don't know enough about the implementation of time() to suggest what would cause that. If you want to dig deeper before reinstalling, you should probably find out how time() and gettimeofday() differ internally.

---

### Post by asbuntu on 2009-06-21
> **Lux Perpetua said:**
> ... I understand that time() and gettimeofday() might be looking at different clocks, so there's no surprise that they don't agree exactly. However, one of the clocks is clearly broken (it counts backwards sometimes), which is a serious problem no matter how you look at it. I don't know enough about the implementation of time() to suggest what would cause that. If you want to dig deeper before reinstalling, you should probably find out how time() and gettimeofday() differ internally.

I have been trying to do that.  I went to [www.kernel.org](www.kernel.org) and downloaded the version I have, but finding things in that source is proving hard.  I tried to find the source for the library containing time() and gettimeofday(), but that seemed to also be difficult.

Any suggestions, please, on how to find the source?  Thanks.

---

### Post by Lux Perpetua on 2009-06-22
> **asbuntu said:**
> I was talking to a friend, who is a main-stream physicist working with supercomputers.  He said something about "global optimizations" in gcc that might account for the behavior I'm experiencing.  I'm not quite sure I agree, because one of the steps I used was to make sure all optimizations were turned off.

To make matters worse, the program is not acting up right now, and I certainly did not recompile it.  Odd???

Anyway, does anyone know about this topic of "global optimizations" with gcc, or have any insight into the problem at hand?  What about the possibility of a kernel bug that got fixed when I updated the system?  Thank you.I think that's quite possible. In fact, if your kernel was updated at that time, then I would assume it was a kernel bug that got fixed. > **asbuntu said:**
> I have been trying to do that.  I went to [www.kernel.org](www.kernel.org) and downloaded the version I have, but finding things in that source is proving hard.  I tried to find the source for the library containing time() and gettimeofday(), but that seemed to also be difficult.

Any suggestions, please, on how to find the source?  Thanks.I just took a look myself. I picked up 2.6.30 since I didn't know which version you had. I think the sys_time() and sys_gettimeofday() syscalls (for which time() and gettimeofday(), respectively, seem to be wrappers) are defined in /kernel/time.c, and they in turn wrap functions in /kernel/time/timekeeping.c. I didn't study it thoroughly, but they do appear to be different, yet not completely independent. 

Interestingly, there's a comment in the code pointing out that sys_time() can be implemented in user space using sys_gettimeofday(). :-)

---

