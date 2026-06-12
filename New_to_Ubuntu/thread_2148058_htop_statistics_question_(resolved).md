---
title: "htop statistics question (resolved)"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by grumpydaddy on 2013-05-23
Hi. First time poster and first time using command line only with Ubuntu 12.04.2 LTS (GNU/Linux 3.5.0-23-generic x86_64).

So, I look at the bar graphs for the cores running and think "running at 80-90% average that's good" then I look at the 1, 5, 15 Minute averages and these suggest that I am waaaay overloaded at upwards of 24 on a 4c/8t machine.

As a Windows refugee used to using GUI I have read about how this works but I am missing something I think ... what is it? Believe the graphical output or pay attention to the load averages?  Incidentally I like to run each machine at maximum then, if needs must, run another machine.... generally for research

 Please be gentle with me as I am also using putty for the first time to a remote machine ;)

---

### Post by tgalati4 on 2013-05-23
Load of 1.0 means one core is loaded to 100% of its CPU capacity and operations are waiting to be processed.  A 4-core machine would have a load of 4.0 when all four cores are loaded to 100%.  A load of 24 is quite high, perhaps 6x over the available 4-core throughput (4X6=24).  Why don't you cut and paste the output of:

```
top -d 5
```

It might look something like:

top - 17:30:39 up 34 days,  2:31,  3 users,  load average: 0.26, 0.20, 0.20
Tasks: 162 total,   1 running, 160 sleeping,   0 stopped,   1 zombie
%Cpu(s):  3.1 us,  **1.8 sy**,  0.0 ni, 94.9 id,  **0.2 wa**,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   2041992 total,  1263304 used,   778688 free,    44968 buffers
KiB Swap:  4094972 total,   253364 used,  3841608 free,   512620 cached

You want to pay attention to IOWaits (wa) and system use (sy) and stolen time (st) if this is a virtual machine.

---

### Post by grumpydaddy on 2013-05-24
From a graphical viewpoint I want to see this:

[[IMG]http://www.lakecityquietpills.com/photo/multihost/images/51822751512094218440.jpg[/IMG]]("http://www.lakecityquietpills.com/photo/multihost/")

your command produces this:

Tasks: 291 total,  22 running, 268 sleeping,   0 stopped,   1 zombie
Cpu(s): 74.7%us,  3.0%sy, 21.7%ni,  0.3%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:  16412744k total, 14864324k used,  1548420k free,    53104k buffers
Swap: 16752636k total,  1731100k used, 15021536k free,  6698224k cached

Not a virtual machine.

If I run the load averages around 8.0 then graphically I am seeing something more akin to a 33% load.... aaargh!

EDIT: looking deeper into this I found a comment that makes a little more sense to me: Average Load refers to processes that are *runnable* if the cpu were free to run them at that exact point in time. Sound about right?

From the top command then, what should I consider as critical cpu percentages re: user, system, nice etc?

---

### Post by landersohn on 2013-05-24
maybe running htop would be useful to find out what processes you have running and which are consuming CPU resources

---

### Post by tgalati4 on 2013-05-24
With no IOWaits and only 3% system overhead, your system appears to be running fine.  I'm not sure how you are setting your *nice* levels, but 30% of your cycles are being suppressed due to higher priority jobs.  So it is possible that your load figures are getting thrown off because of manual *nice* levels.  Remove any *nice* levels from your job scripts and see what the effect is.

*Nice* is helpful when you are competing against other users on a single machine, but for a single user with multiple jobs, let the scheduler do the scheduling.

The fact that you have 24 jobs running and only 4 cores means that you will get a load ~6.0 over time.  This assumes that each job is a CPU-muncher.  24 jobs divided by 4 cores leaves 6 jobs for each core not getting done--that translates to a load of about 6.0 for each core.  Or a total load of ~24.  Add the system overhead 3% and the overhead for swapping the *nice* levels and you are now looking at 27 to 35 which is what is shown in your *htop* output.  The *top* output shows CPU% which is a measure of CPU efficiency compared to real time.  In this case, only 74% of your CPU cycles are crunching your jobs and almost 22% is spent shuffling between 23 other jobs because of *nice* levels.

Not knowing anything about your jobs or how they are structured, you may want to write a script to run them in a serial fashion to better use the 4 cores.  You want the CPU% to be 97% and System to be 3%.  That is the best that you can do.

Spend some time profiling your code and you might gain significant time savings:

```
man strace
```

Oh, and welcome to the forums!

---

### Post by grumpydaddy on 2013-05-25
tgalati4: Many thanks for a decidedly clear overview of what I am looking at and for. Your explanation of nice is as clear to me now as it could ever be (Old guy here with slow head)

You are intimating that Ubuntu itself will make a better job of prioritising the work than the program would. When I consider that it was originally written for windows and here it runs mono, I suspect you may well be right.

Settings currently in use are those I used for windows and they do in fact adjust certain priorities upwards.

 The one thing that annoys me is when I just don't understand a what or a how. You have resolved my issue and my thinking. For that Sir (presumption), you have my thanks.

....and thanks too for the welcome ;)

---

### Post by tgalati4 on 2013-05-25
Mono is not known for its performance.  If you have the source code (in whatever language it was written in), you could recompile it and probably optimize it so that it would scream under linux.

I presumed that you set *nice* levels on your processes.  So it seems that the code itself is setting *nice* levels, which may not be helpful in a linux environment.  There are several schedulers that are used in linux and you can switch them to see if that increases your workload.  But first, recompile your code and try to remove as much mono as possible.

Some discussion on scheduling:  [http://askubuntu.com/questions/20705/is-the-bfs-scheduler-better-than-completely-fair-scheduler-for-desktop-computing](http://askubuntu.com/questions/20705/is-the-bfs-scheduler-better-than-completely-fair-scheduler-for-desktop-computing)

Ultimately, you want to maximize User-space computing.  Anything else is just wasting time.  Keeping your CPU's pegged at 100% is not efficient if there is a lot of IOWaits, or SYS time.  In fact keeping User CPU at 90% gives you 10% buffer so that housekeeping can be done and not cause other system problems.

I suspect that a good portion of your load is mono overhead, rather than number-crunching.

Post your optimization questions in the Programming forum and you will get lots of ideas.

---

### Post by grumpydaddy on 2013-05-27
I must admit that whilst I understand the concepts of what you are saying, what you propose is way beyond my capabilities.

I am, if you will, a ***user*** of this program and had no involvement in its development.

I can alter certain attributes within a menu so that is where I will start.

I do find it interesting that you say it may be possible to remove mono or elements of its use though.... Certainly food for thought and grounds for a discussion with those higher up the food chain than I.

---

### Post by tgalati4 on 2013-05-27
Mono has a long history that you can read here:  [http://en.wikipedia.org/wiki/Mono_programming_language](http://en.wikipedia.org/wiki/Mono_programming_language)

Because of its many compatibility layers it's not real fast.  Your *htop* graph shows the overhead in blue, which is I believe, the nice levels changing and overhead caused by mono.  So if you can isolate the number-crunching portions of your code and profile the rest, you might be able to make your code 20 to 50% faster.

---

