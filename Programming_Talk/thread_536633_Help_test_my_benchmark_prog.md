---
title: "Help test my benchmark prog"
date: 2007-08-27
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-08-27
Hi all,

I am starting to develop a (hopefully) comprehensive benchmarking suite (will include multiple CPU tests, memory, disk, GFX, etc.)

I have implemented one benchmark test (an implementation of a Whetstone test, ie. floating point calculations) using both a single thread and multiple threads.  Unfortunately I don't have a multi-core CPU and would like to see if it works as expected, and would like to confirm this before moving on too far.

Can you please give this a quick test and post the output here- would be much appreciated!

The test should take around a minute or so, for single-thread and 1/(# cores) minutes for multiple CPUs

Thanks!  Look forward to seeing some results :)

// Help yourself to the code if your interested, always keen on feedback too (I know the code is a little rough at this stage, this program is approx 1 day old)

---

### Post by u-foka on 2007-08-28
Hy! this are my results:
```
------ CPU INFO --------
CPUs: 2 (2 physical cores)
Model: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
Speed: 1995.239 MHz
Cache: 4096 KB

------ RESULTS --------
Whetstone (Single-thread) finished.  Elapsed=71.480003s
Whetstone (Multi-thread) finished.  Elapsed=72.739998s
```

---

### Post by AlexThomson_NZ on 2007-08-28
Thanks matey! :)

Was hoping the multi-thread one would be lower than that, better check the code...

---

### Post by Wybiral on 2007-08-28
You should really cut down the amount of time it takes to run... I started it hoping it would only take a minute but I had to stop it so I could get back to other things. I may run it at some point later when my computer is idle, but I think people would be more apt to try it if they didn't have to wait so long (especially us with lesser power machines).

---

### Post by AlexThomson_NZ on 2007-08-28
Hmm thanks for the suggestion my computer must be faster than I thought.

Can anyone else with a Dual (or even better a Quad) core give this a try to see if it distributes properly?

---

### Post by kknd on 2007-08-28
I thinks thats something wrong. I made it in 13 sec, with a athlon 64 1.8. The other guy result should be far better than mine (I compiled with special flags and tested on Arch Linux).

---

### Post by u-foka on 2007-08-28
It is interesting, but notice, i using my cpu in 32bit mode...

---

### Post by kknd on 2007-08-28
I'm using a 32bit system too. And even without optimization (running the pre-compiled one) I made in less time.

I suggest that the pre-compiled binary should get at least a -O2 flag.

---

### Post by u-foka on 2007-08-28
i have tested it on a dual pentium 3 system... and looked the time with a stopwatch
the first run (single thread) was 1:32 , wich was right on the program
the multithread run was 48 seconds on the stopwatch and 92 seconds on your program... so the bug is in the time calculation.... 

Bests 

Thomas Martin Klein

---

### Post by u-foka on 2007-08-28
Hy! We found the BUGG in your code ;)
How the clock function's descriptrion says:
```
Returns the number of clock ticks elapsed since the program was launched.
```
I think it means the total tick count of all cpu's  ;) so clock returns the time that the CPU spent on the process and if there are 2 CPUs it it spends x secs on both cpus thats 2*x cputime. and thats what clock() returns

---

### Post by AlexThomson_NZ on 2007-08-28
> **kknd said:**
> I'm using a 32bit system too. And even without optimization (running the pre-compiled one) I made in less time.

I suggest that the pre-compiled binary should get at least a -O2 flag.

Yeah, that's something I will have to look at, but does open a can of worms when performing benchmarks (ie. we want to test the time of a known function, not how much we can optimize it).  Also, different compilers may have more or less effective optimizations, etc. so there definitely needs to be a standard, so for now will leave it as no optimizations during compiling.

---

### Post by AlexThomson_NZ on 2007-08-28
> **u-foka said:**
> i have tested it on a dual pentium 3 system... and looked the time with a stopwatch
the first run (single thread) was 1:32 , wich was right on the program
the multithread run was 48 seconds on the stopwatch and 92 seconds on your program... so the bug is in the time calculation.... 

Bests 

Thomas Martin Klein

Hey that's awesome, I don't know why I didn't think of that! :P

I have a hyper-threaded system and thought the multi-threaded test ran a bit faster, but though nah, couldn't be!

Cheers so much for your help guys!

---

### Post by kknd on 2007-08-28
Hey, I fixed your program. I just added a function to calculate the time based on the system time itself. I will attach it when I make some more tests.

---

### Post by nikin on 2007-08-28
.. bytheway i ame the one with the dual PIII system... and i was just thinking that the benchmark would be more precise if you rip out the grapics part of it... and write a console only program... so that the xservers settings, the window manager, and that kind of stuff would not affect the test.

---

### Post by nikin on 2007-08-28
kknd : i tested your fix. 

the whole calculation got way faster. 32 secs instead of 1:32 on single thread.
i get now 21 secs on  multithread itch seems to be ok. but the progress bar behaves strange.. it gets 2/3 the way in 1 second and the rest after that becoming slower and slower and slower. 

A longer testing time would be more accurate ... if it is 21 secs on a Dual P3 800, i dont want to imagine how fast it is on a Quad Athlon MP, or that kind of stuff... 3-4 secs ?  that is not accurate enough i think.

Bests

Thomas Marton Klein

---

### Post by AlexThomson_NZ on 2007-08-28
> **nikin said:**
> .. bytheway i ame the one with the dual PIII system... and i was just thinking that the benchmark would be more precise if you rip out the graphics part of it... and write a console only program... so that the xservers settings, the window manager, and that kind of stuff would not affect the test.

Yeah that would be more precise (I could write it in assembly, run it for 24 hours, etc. too), my intention though is simple GUI tool to measure more 'real world' speed (even though it is a synthetic benchmark, I plan it include a few real world tasks too ), as well as a gfx (GUI and OpenGL) benchmark (which wouldn't work very well in console mode).  I don't think console only would be a true representation of a typical desktop.  It's hard not to get dragged into this sort of detail though, so I'll just mention that these results are not to be taken too seriously, but is an just an indication of desktop performance.

---

### Post by AlexThomson_NZ on 2007-08-28
> **nikin said:**
> kknd : i tested your fix. 

the whole calculation got way faster. 32 secs instead of 1:32 on single thread.
i get now 21 secs on  multithread itch seems to be ok. but the progress bar behaves strange.. it gets 2/3 the way in 1 second and the rest after that becoming slower and slower and slower. 

A longer testing time would be more accurate ... if it is 21 secs on a Dual P3 800, i dont want to imagine how fast it is on a Quad Athlon MP, or that kind of stuff... 3-4 secs ?  that is not accurate enough i think.

Bests

Thomas Marton Klein

I can explain the progress bar issue: When threads are running together the progress ticks along, but as threads complete the contributed progress drop also.  I will later implement a better way of measuring progress (otherwise this will be even more pronounced when better weighting values are introduced, at the moment I weight them to complete as close together as I could be bothered at the time).  I will certainly be tweeking to running time as well, probably reworking it report work done in 60s or similar.

Thanks for the feedback- keen to hear other suggestions too if anyone has any!  (BTW if anyone has issues with the CPU reporting, can you please post the contents of /proc/cpuinfo)  Thanks!

---

### Post by AlexThomson_NZ on 2007-08-28
Oh yeah, the reason for it taking much shorter time is because it is compiled with the O2 (optimize) tag, it is probably recommended you don't use that, as we want to execute things as written (as it is written to simulate real-life code with carefully considered and calculated weightings).  Using compiler-time optimazations makes the 'actual implementation' of the critical loops a bit of an unknown.

---

### Post by kknd on 2007-08-28
Is the new timer working for more than one core?

---

### Post by AlexThomson_NZ on 2007-08-28
It seems to be- but I have only tried your pre-compiled one (your new code doesn't seem to compile.  Am just tracking down the issue now...)

---

### Post by nikin on 2007-08-28
about CPU info:

the program writes nothing about my CPU... that place is empty 

my cpuinfo is :

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 3
cpu MHz         : 864.522
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1730.41
clflush size    : 32

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Pentium III (Coppermine)
stepping        : 3
cpu MHz         : 864.522
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1729.07
clflush size    : 32

if you want to check desktop perormance than thats cool with the GUI.
i am not a C coder, so cant figure a whole lot out of your code. i try to make it without optimisations.
are you doing integer or floating point calculations?
some suggestions:
Real life tasks:
JPEG encoding, file moving, restarting :) , donloading. Starting times for some apps. maybe compiling. maybe Printing. 
2D animation. not only GL based but SW also

---

### Post by nikin on 2007-08-28
thats what i get from make

etime.c: In function ‘get_time’:
etime.c:12: error: invalid use of undefined type ‘struct timeval’
etime.c:12: error: invalid use of undefined type ‘struct timeval’
etime.c:12: error: invalid use of undefined type ‘struct timeval’
etime.c:12: error: invalid use of undefined type ‘struct timeval’
make: *** [etime.o] Error

---

### Post by AlexThomson_NZ on 2007-08-28
> **nikin said:**
> 
i am not a C coder, so cant figure a whole lot out of your code. i try to make it without optimisations.
are you doing integer or floating point calculations?
some suggestions:
Real life tasks:
JPEG encoding, file moving, restarting :) , donloading. Starting times for some apps. maybe compiling. maybe Printing. 
2D animation. not only GL based but SW also

Don't worry about not understanding my code, it's a bit of a mess (I literally hacked up that bit in a day, so haven't spent any time tidying it up- apologies to anyone who anybody that has to read it!)

Thanks for your suggestions re: real world applications.  I am probably not too concerned with networking speed (too many factors) and Printing.  I do intend to implement a disk performance benchmark, RAM, and 2D/3D graphics though.

The Whetstone is a floating point test, and I will also tackle a Dhrystone test too for integer calc, and maybe a few other standard 'mixture' tests (PI/prime calculation)

---

### Post by kknd on 2007-08-28
GCC 4.2 is crazy. Try changing the #include <linux/time.h> to #include <time.h>

---

### Post by nikin on 2007-08-28
Networkig speed is nowdays a serious point in average home and office PC use. downloading e-mail, uploading attachments. Browsing the web, updating the system, watching youTube, you name it. but if not, then not :D 

Printing is truly not close to be a realy curcial part. but i havent seen any good printing benchmarks. wich do some test like

prinitng pages with diferent amount of data
printing pages with different kind of data.
printing BW/Color.

on Lazers there is not much to this... their speed does not depend a lot on the data. but on Inkjets.. i think there can be about 1000% difference :D not to talk about my Matrix printer :D LOL

---

### Post by nikin on 2007-08-28
kknd
i did that before...
stil not working

---

### Post by AlexThomson_NZ on 2007-08-28
Try replacing:

#include <linux/time.h>

With:

#include <sys/time.h>

And the gettimeofday calls with:

gettimeofday(&start_time, 0);

I'll post up another version with I add some more bits and peices and have more of a 'proper' demo than this (this was just to see if the multi-thread timing worked, which obviously wasn't!)

Thanks for your help kknd!

---

### Post by nikin on 2007-08-28
Alex: 
that worked.. and now somehow i got CPU information also.

---

### Post by AlexThomson_NZ on 2007-08-28
Ahh ok, kknd must have taken that bit out for his test...

---

### Post by kknd on 2007-08-28
There was a bug in it: It doesn't closes itself when terminating the application.

I've fixed it and changed the UI, and tried to get this compiling on other machines (I see you posted this now too about <sys/time.h>).

To disable the optimization, edit just the Makefile.

If you agree, I would like to contribute more to your project =).

---

### Post by AlexThomson_NZ on 2007-08-28
Hell yeah- would be pleased to have you!

Give me a day or two to get the base of the code up to scratch, then we'll start on coding up some benchies! :)

---

### Post by kknd on 2007-08-29
> **AlexThomson_NZ said:**
> Hell yeah- would be pleased to have you!

Give me a day or two to get the base of the code up to scratch, then we'll start on coding up some benchies! :)

Nice =). If you want, I can put in on a CVS and publish it under to [http://oproj.tuxfamily.org](http://oproj.tuxfamily.org).

---

### Post by bluehue on 2007-08-31
```

------ CPU INFO --------
CPUs: 2 (1 physical cores)
Model: Intel(R) Pentium(R) 4 CPU 3.20GHz
Speed: 3192.205 MHz
Cache: 512 KB

------ RESULTS --------
Whetstone (Single-thread) finished.  Elapsed=12.960955s
Whetstone (Multi-thread) finished.  Elapsed=9.023141s
```
Edit: This is based on kknd's release of the prog.

---

### Post by Amazona aestiva on 2007-08-31
------ CPU INFO --------
CPUs: 2 (2 physical cores)
Model: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Speed: 2600.000 MHz
Cache: 1024 KB

------ RESULTS --------
Whetstone (Single-thread) finished.  Elapsed=31,500000s
Whetstone (Multi-thread) finished.  Elapsed=31,700001s

--------------------------------------------------------------------------------

------ CPU INFO --------
CPUs: 2 (2 physical cores)
Model: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
Speed: 2600.000 MHz
Cache: 1024 KB

------ RESULTS --------
Whetstone (Single-thread) finished.  Elapsed=31,680000s
Whetstone (Multi-thread) finished.  Elapsed=31,680000s


At second I got the same results for the test. Is it good?

---

### Post by kknd on 2007-08-31
I don't know if multi cores are correctly used in the current test, because the parallelism must be threaded by the programmer in this case (fork() + synchronization and etc).

---

### Post by AlexThomson_NZ on 2007-08-31
Hi kknd, I have done some pretty big changes to the prog, will post it up when I get back to work on monday.

---

### Post by nikin on 2007-09-01
it would be nice if you could write down the dependencies of your program... to compile :D

---

### Post by AlexThomson_NZ on 2007-09-01
> **kknd said:**
> I don't know if multi cores are correctly used in the current test, because the parallelism must be threaded by the programmer in this case (fork() + synchronization and etc).

Ummm why would I use a process in this context?

---

### Post by kknd on 2007-09-02
> **AlexThomson_NZ said:**
> Ummm why would I use a process in this context?

You must explicit code for parallelisms :(, to get a good use of it.

---

### Post by AlexThomson_NZ on 2007-09-02
Like forks, threads are time-sliced by the kernel (and if there are multiple CPUs they will get used automatically).  Threads, though are much more efficient and can share data without using IPCs, so in this case is more practical.

I have attached what I have done so far with the code, It should compile cleanly, and does a time-limited floating point and integer test, both threaded and non-threaded, so give it a go, and let me know what you think.

A couple of issues I know are outstanding are the About dialog decorations missing, and threads to being tidied up if quit while running...

My results:
```

SYSTEM INFO
CPU
 * Cores: 2 (1 physical)
 * Model: Intel(R) Pentium(R) 4 CPU 3.20GHz
 * Speed: 3215 MHz
 * Cache: 1024 MB
RAM
 * Size: 2027 MB
 * Free: 55%

RESULTS
CPU
Floating Point
 Single-threaded score: 10.0
  Multi-threaded score: 15.9
Integer
 Single-threaded score: 10.1
  Multi-threaded score: 13.4

```

---

### Post by nonewmsgs on 2007-09-02
can you make it in debs? one for 32 and one for 64 and ill test it on a couple machines.

---

### Post by AlexThomson_NZ on 2007-09-02
Yep, I'll try to find time this arvo to do it... give this one a go though if you can, there is a 32bit compiled binary in there if I remember rightly.

BTW anyone that does try compiling it, don't use the optimize flags, or it might appear you are running it on a cray! :)

---

### Post by u-foka on 2007-09-03
Hy! There are the results ;)

With original binary:
```
SYSTEM INFO
CPU
 * Cores: 2 (2 physical)
 * Model: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
 * Speed: 1995 MHz
 * Cache: 4096 MB
RAM
 * Size: 1962 MB
 * Free: 8%

RESULTS
CPU
Floating Point
 Single-threaded score: 6.7
  Multi-threaded score: 10.7
Integer
 Single-threaded score: 5.9
  Multi-threaded score: 9.8
```

With a recompiled one:
```
SYSTEM INFO
CPU
 * Cores: 2 (2 physical)
 * Model: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
 * Speed: 1995 MHz
 * Cache: 4096 MB
RAM
 * Size: 1962 MB
 * Free: 7%

RESULTS
CPU
Floating Point
 Single-threaded score: 6.6
  Multi-threaded score: 12.7
Integer
 Single-threaded score: 5.9
  Multi-threaded score: 10.7
```

And you still have the bug: when i close the gtk window (after the test ran successfully) your code does not exit.

---

### Post by u-foka on 2007-09-03
Hy alex!

I think, you may like this app: [http://debcreator.cmsoft.net/](http://debcreator.cmsoft.net/) :)
A gui driven deb package creator ;)

---

### Post by AlexThomson_NZ on 2007-09-03
> **u-foka said:**
> Hy alex!

I think, you may like this app: [http://debcreator.cmsoft.net/](http://debcreator.cmsoft.net/) :)
A gui driven deb package creator ;)

Hey that's cool!  Thanks for the heads up re the not closing properly, I'll have to have a look at that...

---

### Post by AlexThomson_NZ on 2007-09-03
My laptop...

```

SYSTEM INFO
CPU
 * Cores: 2 (2048 physical) <--- this can't be right!
 * Model: Intel(R) Pentium(R) M processor 1.86GHz
 * Speed: 1862 MHz
 * Cache: 2048 MB
RAM
 * Size: 1011 MB
 * Free: 32%

RESULTS
CPU
Floating Point
 Single-threaded score: 11.6
  Multi-threaded score: 11.6
Integer
 Single-threaded score: 9.3
  Multi-threaded score: 8.8


```

---

### Post by kknd on 2007-09-03
Hey **AlexThomson_NZ**, about the paralellism:

Why multi-core cpus don't do better in the multi-thread test? I still think that it must be hand-optimized to use it.

The info now works 75% here, just some info are wrong (like 512mb cache, 40% used (only 13% where used without caching) and 512 cores), but its nice now :)

Separating the tests in Floating point / Integer were a good idea too.

I've atached the fixed code (closes the program when the GUI are destroyed).

**My results with the original flags:**

SYSTEM INFO
CPU
 * Cores: 1 (512 physical)
 * Model: AMD Athlon(tm) 64 Processor 3000+
 * Speed: 1808 MHz
 * Cache: 512 MB
RAM
 * Size: 1011 MB
 * Free: 60%

RESULTS
CPU
Floating Point
 Single-threaded score: 9,7
  Multi-threaded score: 10,6
Integer
 Single-threaded score: 7,3
  Multi-threaded score: 7,4

**P.S** To prevent code overwrite, you could put your code into a SVN / CVS repo, so we could contribute to it in a more efficient manner!

---

### Post by AlexThomson_NZ on 2007-09-03
> **kknd said:**
> Hey **AlexThomson_NZ**, about the paralellism:

Why multi-core cpus don't do better in the multi-thread test? I still think that it must be hand-optimized to use it.

But it does work better with multiple cores!  My work PC with 2 virtual cores is about 60% faster, and someone posted here with a result that was pretty much doubled, so that is expected behaviour :)

> 
The info now works 75% here, just some info are wrong (like 512mb cache, 40% used (only 13% where used without caching) and 512 cores), but its nice now :)

yeah I just noticed this when I tried it at home with my single core CPU, should be an easy fix.

> 
**P.S** To prevent code overwrite, you could put your code into a SVN / CVS repo, so we could contribute to it in a more efficient manner!
Sure!  You suggested somewhere earlier, you want to do that?  Otherwise I'll look into it later today if I get a chance (I've just started a new job, so I don't have as much time now)...

Once we get it tidied up, I'd like to release it more officially, even if it is just the CPU tests for now.  Would also need to do the results screen as well (I will do a mock up GUI shortly, hopefully)

---

### Post by Perfect Storm on 2007-09-03
Maybe there's something you could use from this project: [http://globs.sourceforge.net/](http://globs.sourceforge.net/)

---

### Post by AlexThomson_NZ on 2007-09-03
Globs loos like it has some serious implementation issues, besides the fact that it is written in Python (no flamewars please, I just mean that it is going to be far, far to CPU limited!), it gives the user too much control.  Hopefully this one will be a bit more robust.

---

### Post by kknd on 2007-09-03
Humm, then I was wrong :). Glad to see that is less work to do.

I can create a CVS repository, plus put the program info on my "project" website if you want.

**About GLOB**:

I don't think that the gap is the Python speed, since it only servers as a glue there, but it's Python, and converting it to C wouldn't be a speed saver at all (and just using it would be bad, since there will be a python dependency).

---

### Post by AlexThomson_NZ on 2007-09-03
I'm pretty comfortable with OpenGL, I don't expect any problems doing a pretty decent openGL benchmark using C only.

If you could create a CVS repo would be great!  Thanks for that! :)

---

### Post by kknd on 2007-09-03
> **AlexThomson_NZ said:**
> I'm pretty comfortable with OpenGL, I don't expect any problems doing a pretty decent openGL benchmark using C only.

If you could create a CVS repo would be great!  Thanks for that! :)

Nice ;).

I've created the CVS. I will try to p.m you the info.

---

### Post by bluehue on 2007-09-04
Again, used kknd's version.
```

SYSTEM INFO
CPU
 * Cores: 2 (1 physical)
 * Model: Intel(R) Pentium(R) 4 CPU 3.20GHz
 * Speed: 3192 MHz
 * Cache: 512 MB
RAM
 * Size: 1010 MB
 * Free: 19%

RESULTS
CPU
Floating Point
 Single-threaded score: 9.7
  Multi-threaded score: 15.9
Integer
 Single-threaded score: 5.8
  Multi-threaded score: 8.7
```

---

### Post by kcbnac on 2007-09-08
PERFECT TIMING!

I'm just getting started on the need to benchmark several dual Quad-Core servers, and Google'd for 'Ubuntu benchmark' - it will be a little bit until I get them running Linux, but I am DEFINITELY subscribing to the thread and will be able to test this for ya. :D

I'd recommend getting it into some sort of revision management system (CVS, git, etc) so people can come back and look at the code as it progresses - and it can gain more 'legitimacy' in the benchmarking world.  I'd recommend Sourceforge.

So Quad-Core testing is coming - hopefully that will help significantly.
:guitar:

---

### Post by AlexThomson_NZ on 2007-09-08
Hiya kcbnac!

Hey that's great news, look forward to seeing some results from ya :)

it is in CVS now, courtesy of kknd, I'm doing a little work now around the memory benchmarking, so that (hopefully) will be coming shortly, time permitting.  The CPU performance testing should be pretty finalised, and hasn't been touched since, so use the last one posted here for now...

---

### Post by AlexThomson_NZ on 2007-09-20
Hi thread-subscribers- I have made another pre-release of this app at this thread ([http://ubuntuforums.org/showthread.php?t=555247](http://ubuntuforums.org/showthread.php?t=555247))  If anyone's keep on trying this out would be appreciated (if you get errors, try disabling the Gnome benchmark for now)

---

### Post by kcbnac on 2007-10-01
Sadly, some things happened and I no longer have access to multiple quad+ core systems for the moment - but as time goes on, I'll keep coming back and using it.  (Moved, and working on setting up my server for my own personal use - including some benchmarking)

Don't worry - Quad-Cores are becoming more common - we'll find 'em sooner or later.

---

### Post by nutz on 2007-11-13
This is very interesting. Good for testing overclocking results.

Would be nice to have the option to make it run in loops for stability testing.

---

### Post by AlexThomson_NZ on 2007-11-13
Thanks for the feedback nutz.  I'm working on a new version of this, a command-line version with a GUi frontend.  This will have support for looping, etc., I just need to iron out some threading wrinkles and I'll put it up...

---

### Post by nutz on 2007-11-14
Looking forward to it.

---

