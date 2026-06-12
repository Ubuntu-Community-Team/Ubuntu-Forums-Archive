---
title: "pthread C program - only uses one core!"
date: 2010-09-13
forum: Programming Talk
---

### Post by TiBaal89 on 2010-09-13
I've Google'd this to death and found many threads (some on this forum) but all of them seem to trail off without an answer being posted.

I am running a very small C program which uses pthreads.  It just does some matrix multiplication and is for the purpose of demonstrating the basic usage of pthreads.  The program's correctness is not in question - on Ubuntu 10.04 workstations at school, the program executes correctly and uses multiple cores.  On my home machine (quad core i5), it executes correctly - but ALWAYS schedules everything to a single core.

I'm including <pthread.h> and it is on my system in /usr/include/ where it should be...

I'm compiling with -l to link the library...

```
gcc myprog.c -o myprog -lpthread
```

And yet... every single time it schedules everything on a single core.  Clearly this is not what I envisioned when I purchased a quad core machine. :(

Any help is appreciated.  

I'm on 10.04 LTS... 'Linux xxxxxx 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux' specifically.

---------------

EDIT 9/16/10:  I've discovered that this only happens if the computer has been put to sleep since booting.  When the computer is first booted - it schedules concurrently across cores as you'd expect.  If I put the system to sleep and return - it runs only on a single core.  I had not noticed this behavior because I frequently use sleep (overnight, leaving the house, etc).

---

### Post by regala on 2010-09-13
> **TiBaal89 said:**
> 

```
gcc myprog.c -o myprog -lpthread
```

And yet... every single time it schedules everything on a single core.  Clearly this is not what I envisioned when I purchased a quad core machine. :(

Any help is appreciated.  



what makes you think that it runs on only one core ?

br,

ms

---

### Post by TiBaal89 on 2010-09-13
> **regala said:**
> what makes you think that it runs on only one core ?

br,

ms

Ah, good question - I forget to mention that.

I'm just watching 'top' while it runs, the process is only taking 100%.  Furthermore, if I hit '1' while top is going to view the loads on each core, it shows one loaded up at 100% and the others sort of putzing along doing whatever (maybe a few percent here and there).

---

### Post by regala on 2010-09-13
> **TiBaal89 said:**
> Ah, good question - I forget to mention that.

I'm just watching 'top' while it runs, the process is only taking 100%.  Furthermore, if I hit '1' while top is going to view the loads on each core, it shows one loaded up at 100% and the others sort of putzing along doing whatever (maybe a few percent here and there).

well, without reading the source, I can't see if there is any sync/lock issue that prevents 2 threads to run at the same time. But if you have actually several threads and only 1 CPU at 100%, I would look at the locking logic of your program

br,

mathieu

---

### Post by pbrane on 2010-09-13
If you want parallel or concurrent CPU usage you should make sure that your code is organized into independent tasks that can run concurrently. You might add **-Wall** to your command line to check for any warnings that come up.

Here are a couple of sources for info:
[https://computing.llnl.gov/tutorials/pthreads/]("https://computing.llnl.gov/tutorials/pthreads/")

[http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html]("http://www.yolinux.com/TUTORIALS/LinuxTutorialPosixThreads.html")

---

### Post by TiBaal89 on 2010-09-13
Thanks for the replies.  But, as I said the correctness of the program isn't in question.  It is a very simple matrix multiplication program written by my professor for demonstration purposes.  It divides the matrix into strips, and gives each to a worker function (allocates thread handles, calls pthread_create on the workers, pthread_join, etc).

On other machines the threads are scheduled across cores as you'd expect. The issue is definitely something with my machine...

---

### Post by MadCow108 on 2010-09-13
how many processors are listed when you do this:
cat /proc/cpuinfo

---

### Post by TiBaal89 on 2010-09-13
> **MadCow108 said:**
> how many processors are listed when you do this:
cat /proc/cpuinfo

All four of them... they also show up correctly in System Monitor and the like.

I should have mentioned - I also have basically the same short program implemented using MPI and that will execute on multiple cores.  So, it's something to do with pthreads specifically...

---

### Post by Simian Man on 2010-09-13
How long does this program run and how many threads do you have?

> **TiBaal89 said:**
> Thanks for the replies.  But, as I said the correctness of the program isn't in question.

Famous last words.

---

### Post by TiBaal89 on 2010-09-13
> **Simian Man said:**
> How long does this program run and how many threads do you have?

It takes as command line arguments the size of the problem and the number of threads... I've been using a problem size that takes about 30 seconds so I can watch it go, and have been setting the threads to something like 2, 4, or 8.

> **Simian Man said:**
> Famous last words.

I'm definitely aware of the peril in that statement... but truly, given the very specific situation here, I think it's fair.   ;)

---

### Post by pbrane on 2010-09-13
Do you know what version of pthreads you have?
**getconf GNU_LIBPTHREAD_VERSION** in a terminal should tell you. I'm not sure but maybe that has something to do with it.

How new is your i5? Does it have Turbo Boost (rev 2)? That may have something to do with this issue. I've read that turbo boost works by shutting down unused cores and raising the CPU multiplier of cores in use. By shutting down unused cores, the CPU doesn&#8217;t exceed its TDP or maximum power draw from the motherboard, so it&#8217;s a safe and power-efficient way to overclock on the fly.

---

### Post by TiBaal89 on 2010-09-15
> **pbrane said:**
> Do you know what version of pthreads you have?
**getconf GNU_LIBPTHREAD_VERSION** in a terminal should tell you. I'm not sure but maybe that has something to do with it.

```
$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.11.1
```


> **pbrane said:**
> How new is your i5? Does it have Turbo Boost (rev 2)? That may have something to do with this issue. I've read that turbo boost works by shutting down unused cores and raising the CPU multiplier of cores in use. By shutting down unused cores, the CPU doesn’t exceed its TDP or maximum power draw from the motherboard, so it’s a safe and power-efficient way to overclock on the fly.

Interesting... I put this machine together in late June this year.  I don't know much about what Intel has going on with that unfortunately.

---

### Post by TiBaal89 on 2010-09-15
Here's an interesting thing I tried... this program works and utilizes multiple cores on every other machine I've run it on - including a bunch of Ubuntu machines at school.

If I compile the program on the machine at school, copy the binary to mine, and run it - it runs correctly but only on a single core.

If I compile the program on my machine, copy the binary to the machines at school, and run it - it schedules to multiple cores.

---

### Post by radeon21 on 2010-09-15
I'm curious what would happen if you were to try to run it on the 10.10 beta.  The i5s are relatively new processors... perhaps the driver support is not quite mature?

What types of CPUs are in the machines at school?

---

### Post by TiBaal89 on 2010-09-15
The school machines are quad core i7 860's.  That's actually really interesting - whatever it is about those processors (some kind of dual hardware thread per core business), it shows up in the system as an 8-core machine.  Definitely something sexy about watching 8 threads of your program going at the same time in top. :D

I have a small extra partition laying around on this machine, I'll throw the 10.10 on there and see what happens.

---

### Post by radeon21 on 2010-09-15
The other thing you can try is to have gcc statically link the pthread libraries using the -static flag.  Just compiling and moving it between machines doesn't guarantee that the same code will run because libraries are dynamically loaded at runtime.  So if you're really curious, statically link on the school machine and bring it home and vice versa.  The results may (or may not) be interesting.

---

### Post by TiBaal89 on 2010-09-15
Thanks for the replies... but still, same deal.  Both versions run concurrently at school, both run single core at home.  Something definitely got included in the binary with the flag - went from 8K to about 950K. :lol:

---

### Post by TiBaal89 on 2010-09-16
Well, well... the plot thickens!  It schedules concurrently across cores as expected in the 10.10 release on my machine.  Now to figure what the difference is...

This is different in 10.10 from 10.04:

```
$ getconf GNU_LIBPTHREAD_VERSION
NPTL 2.12.1
```

Not sure if that's the issue...

---

### Post by slavik on 2010-09-16
NPTL are kernel threads (scheduled by kernel), what are the kernel version at home and school?

---

### Post by TiBaal89 on 2010-09-16
Home:

```
$ uname -a
Linux xxxxx 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
```

School (works on both):

```
$ uname -a
Linux xxxxx 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64 GNU/Linux
```
```
$ uname -a
Linux xxxxx 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:38:40 UTC 2010 x86_64 GNU/Linux
```

---

### Post by pbrane on 2010-09-16
> **TiBaal89 said:**
> The school machines are quad core i7 860's.  That's actually really interesting - whatever it is about those processors (some kind of dual hardware thread per core business), it shows up in the system as an 8-core machine.  Definitely something sexy about watching 8 threads of your program going at the same time in top. :D

I have a small extra partition laying around on this machine, I'll throw the 10.10 on there and see what happens.

An intel Hyper Threaded (HT) core shows up as 2 CPUs. Each core can perform two tasks simultaneously.

There are some differences between the i3, i5, and i7 procs that may be the cause of your observations. Still you would think the i5 would use more than one core  with pthreads.

---

### Post by radeon21 on 2010-09-16
Try running the statically compiled binary on 10.10.  That should tell you whether it was just the libpthread version that fixed the issue or whether it was a combination of kernel and driver.

---

### Post by TiBaal89 on 2010-09-16
OK, now this is hilarious... 

Last night no concurrency.  Right now - it works.  The only change I made to my system between these two events was installing Pingus.  :lol:

I don't know if something happened when I installed that or what... attached is my /var/log/dpkg.log for fun.

I think I'm going to do a fresh install of 10.04 on my extra partition to see if this problem is reproducible from the get go...

---

### Post by TiBaal89 on 2010-09-16
Well this just might be one of those mysteries for the ages... threads are running concurrently on a fresh 10.04 install, and after updating everything on that install.  They also continue to run concurrently on my original 10.04 install where this problem originated.

Thanks to all who replied.  It would have been nice to figure it out, but magically working again is nice too I guess. :eek:

---

### Post by TiBaal89 on 2010-09-17
AH HA!! :D

I just gained some much more specific info on what is going on here... it only doesn't work if the computer has been put to sleep since booting!

So, when I first boot up - it schedules concurrently.  Once I put the system to sleep and come back - it only runs on a single core.

Now THAT's weird.

It's very repeatable on my machine - both on my existing 10.04 install and a separate brand new 10.04 install.  I'm going to again put 10.10 on my extra partition to see if it happens there for fun...

---

### Post by kahumba on 2010-09-17
I think you should report this issue to the Linux kernel mailing lists especially if Ubuntu 10.10 (kernel 3.6.35) also doesn't work as expected after the system comes back from sleep.

---

### Post by TiBaal89 on 2010-09-17
Same problem in 10.10 with the 2.6.35 kernel...

```
$ uname -a
Linux xxxxx 2.6.35-22-generic #32-Ubuntu SMP Wed Sep 15 23:18:18 UTC 2010 x86_64 GNU/Linux
```

It's very repeatable on my machine in 10.10 and 10.04... I don't think the Ubuntu machines at school are put to sleep much, so can't say if I know of another machine this happens to.  I'll have to go in and try it, see what happens.

---

### Post by mkfeil on 2010-10-13
I am seeing this problem on my Dell E6510 on Ubuntu 10.04. Just running "make -j4" to try and use all cores will result in only one core being used if the machine has ever been put to sleep. Make probably uses pthreads().

---

### Post by TiBaal89 on 2010-10-15
I haven't really followed up with this... issue remains repeatable on my system, haven't yet experimented with others.

> **mkfeil said:**
> I am seeing this problem on my Dell E6510 on Ubuntu 10.04. Just running "make -j4" to try and use all cores will result in only one core being used if the machine has ever been put to sleep. Make probably uses pthreads().

That's interesting... though I can't really say much about it, I don't know anything about 'make' under the hood.  As a quick test, I compiled GraphViz with -j4 and it seemed to be using multiple cores.  That was while my machine was in a state where it does not run my sample pthreads problem concurrently.  Nothing I can add about that issue unfortunately...

---

### Post by slavik on 2010-10-15
> **pbrane said:**
> An intel Hyper Threaded (HT) core shows up as 2 CPUs. Each core can perform two tasks simultaneously.

There are some differences between the i3, i5, and i7 procs that may be the cause of your observations. Still you would think the i5 would use more than one core  with pthreads.
HT is not a separate core.

Single Core with HT (Pentium4) - single physical core, single physical CPU package
Dual Core without HT (Core Duo, etc.) - two physical cores, single physical CPU package

---

### Post by simonbp on 2010-10-27
Same deal with Perl "use threads" since upgrading to 10.10 after I wake from suspend on my ASUS A52J (Core i5). I had used the directions below to get suspend working, so that may have some effect...

[http://ubuntuforums.org/showthread.php?t=1460790](http://ubuntuforums.org/showthread.php?t=1460790)

---

### Post by mkfeil on 2010-10-30
More on my lack of concurrency problem on Dell Latitude E6510 and 10.04 LTS. It happens when coming out of suspend OR hibernate, and it's not only "make -j4" that has a problem. I wrote a tiny C program that just does a tight loop, and if I run 4 instances of this "loop" program from a bash shell using "loop &", they all get scheduled onto the same core!

This is verified using xosview. Before doing a sleep or hibernate, the problem is not there and all 4 instances of the "loop" program get scheduled onto different cores.

I tried comparing the output of "sysctl -a" before and after the problem happens, and there is no significant difference. This is really starting to annoy me.


> **TiBaal89 said:**
> I haven't really followed up with this... issue remains repeatable on my system, haven't yet experimented with others.



That's interesting... though I can't really say much about it, I don't know anything about 'make' under the hood.  As a quick test, I compiled GraphViz with -j4 and it seemed to be using multiple cores.  That was while my machine was in a state where it does not run my sample pthreads problem concurrently.  Nothing I can add about that issue unfortunately...

---

### Post by mkfeil on 2010-10-30
FIXED:

I updgraded my Dell E6510 to Ubuntu 10.10 and the problem was still there. But then I upgraded to the pre-release kernel, 2.6.35-23-generic x86_64, and the CPU load balancing problem after suspend/hibernate is fixed!

There are some other problems where resuming from suspend doesn't work anymore with my Nvidia graphics driver active, but I am ok with only using hibernate for now.

Max

---

