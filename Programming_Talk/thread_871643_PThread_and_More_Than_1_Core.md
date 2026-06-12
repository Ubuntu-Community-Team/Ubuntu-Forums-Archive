---
title: "PThread and More Than 1 Core"
date: 2008-07-27
forum: Programming Talk
---

### Post by LightRaven on 2008-07-27
Hello all.

I have made an application in C using pthreads. My problem is that my program seems to be only using 1 of my cores when I create multiple threads. I have 4 cores (Q9300). I am using Ubuntu 8.04.

I do believe the problem is that on linkage it's using a pthread emulation package rather than the real thing?

Either way how do I solve this problem?

Many thanks.

---

### Post by LightRaven on 2008-07-27
Any suggestions?

---

### Post by dribeas on 2008-07-27
> **LightRaven said:**
> Any suggestions?

Not really. Try to ckeck that you do have pthread dev packages installed, and try to figure which library you are actually linking against. I have never had such a problem.

---

### Post by dwhitney67 on 2008-07-27
I found a reference (after googling for a while) that under Linux, all pthreads that are created are by default system-bound (not process-bound).  Thus I do not understand why you are having an issue.

Just for grins, can you please insert these statements before you create your threads:
[PHP]pthread_attr_t *attr = malloc( sizeof(pthread_attr_t) );
phread_attr_init( attr );
pthread_attr_setscope( attr, PTHREAD_SYSTEM_SCOPE );
...
pthread_create( &tid, attr, threadProc, &arg );[/PHP]
When the thread terminates, make sure the memory for 'attr' is relinquished:
[PHP]pthread_attr_destroy( attr );
free( attr );[/PHP]

---

### Post by LightRaven on 2008-07-27
Tried it , didn't change the situation. Thanks though. I do belive it's connected to this emulation pthread package. I do not know how to solve that though.

---

### Post by LightRaven on 2008-07-27
up

---

### Post by slavik on 2008-07-27
> **dwhitney67 said:**
> I found a reference (after googling for a while) that under Linux, all pthreads that are created are by default system-bound (not process-bound).  Thus I do not understand why you are having an issue.

Just for grins, can you please insert these statements before you create your threads:
[PHP]pthread_attr_t *attr = malloc( sizeof(pthread_attr_t) );
phread_attr_init( attr );
pthread_attr_setscope( attr, PTHREAD_SYSTEM_SCOPE );
...
pthread_create( &tid, attr, threadProc, &arg );[/PHP]
When the thread terminates, make sure the memory for 'attr' is relinquished:
[PHP]pthread_attr_destroy( attr );
free( attr );[/PHP]
Linux has no distinction between processes and threads. Linux has a notion of tasks. In the Linux kernel, the pthread implementation uses NTPL which are kernel threads. Solaris' version of pthreads uses user level threads.

Also, make sure that your threads are not blocking each other ...

---

### Post by dribeas on 2008-07-27
> **LightRaven said:**
> My problem is that my program seems to be only using 1 of my cores

I do believe the problem is that on linkage it's using a pthread emulation package rather than the real thing?


I've been trying to figure this up, but I can only come back to 'seems' as in your sentence above (what does it mean that it 'seems to be only using 1 core'?) and 'pthread emulation package' (what are you linking against?) There is a libpthread-stubs0 package, but if you link agains libpthread (-lpthread) it does not kick in. I am assuming that you have not compiled your kernel with no SMP support... default kernels are SMP.

I would ask you for the code so that I can test it and try to figure, but my laptop has a single core, so in my case it will use only one core, obviously. I guess I can try to run it remotedly at work, but no guarantee on that.

   David

---

### Post by LightRaven on 2008-07-27
> **dribeas said:**
> I've been trying to figure this up, but I can only come back to 'seems' as in your sentence above (what does it mean that it 'seems to be only using 1 core'?) and 'pthread emulation package' (what are you linking against?) There is a libpthread-stubs0 package, but if you link agains libpthread (-lpthread) it does not kick in. I am assuming that you have not compiled your kernel with no SMP support... default kernels are SMP.

I would ask you for the code so that I can test it and try to figure, but my laptop has a single core, so in my case it will use only one core, obviously. I guess I can try to run it remotedly at work, but no guarantee on that.

   David

I have used the word seems as I have tested my SMP version on a Win XP HE machine using Cygwin and monitored the running time vs the same sequential version. I observed my SMP version being 2-4 times as fast using 4 cores (as expected).

In the mean time I switched to Ubuntu 8.04 and what I observed now with the same code is that the running time is higher or about the same as the sequential version. I am aware of at least 1 other person that has had the same problem with the solution being linkage with the correct pthread package. However I am using the -lptread flag.

What I can see from the normal Ubuntu monitor tools is that the CPU utilization is from 50-60 on the 4 cores whilst running my program. My threads are built to the very CPU intensive (which I also observed on Win XP with a close to 100% util. on all 4 cores) hence i figured something must be wrong. It may be switching the thread(s) around alot? It's hard to see.

Thanks for your time.

---

### Post by LightRaven on 2008-07-28
up

---

### Post by dribeas on 2008-07-28
> **LightRaven said:**
> I have used the word seems as I have tested my SMP version on a Win XP HE machine using Cygwin and monitored the running time vs the same sequential version. I observed my SMP version being 2-4 times as fast using 4 cores (as expected).

In the mean time I switched to Ubuntu 8.04 and what I observed now with the same code is that the running time is higher or about the same as the sequential version. I am aware of at least 1 other person that has had the same problem with the solution being linkage with the correct pthread package. However I am using the -lptread flag.

What I can see from the normal Ubuntu monitor tools is that the CPU utilization is from 50-60 on the 4 cores whilst running my program. My threads are built to the very CPU intensive (which I also observed on Win XP with a close to 100% util. on all 4 cores) hence i figured something must be wrong. It may be switching the thread(s) around alot? It's hard to see.

Thanks for your time.

You can meassure your program with time to get a better estimate:
```

$ time ./program
real    0m0.180s
user    0m0.000s
sys     0m0.008s

```

'Real' is wall clock, 'user' is the CPU time your program has used and 'sys' is the CPU time that the system took to exec all your system calls. In a multithreaded application user+sys > real (wall clock may be 1s, while if it was working on 2 CPUs you can have used up to 2s of CPU time.

---

### Post by LightRaven on 2008-07-28
> **dribeas said:**
> You can meassure your program with time to get a better estimate:
```

$ time ./program
real    0m0.180s
user    0m0.000s
sys     0m0.008s

```

'Real' is wall clock, 'user' is the CPU time your program has used and 'sys' is the CPU time that the system took to exec all your system calls. In a multithreaded application user+sys > real (wall clock may be 1s, while if it was working on 2 CPUs you can have used up to 2s of CPU time.

Indeed, but this wasn't the problem though ;-)

---

### Post by LightRaven on 2008-07-29
up

---

### Post by LightRaven on 2008-07-31
Still a problem

---

### Post by dwhitney67 on 2008-07-31
What tools are you using to monitor each individual thread as it runs?

Would it be possible to see your code?

---

### Post by LightRaven on 2008-07-31
> **dwhitney67 said:**
> What tools are you using to monitor each individual thread as it runs?

Would it be possible to see your code?

I can't show the code. I have used the standard monitor tool coming with Ubuntu 8.04. Monitored the load before and during - visually (same with XP). No exact science but at least it's self consistent.

---

### Post by dwhitney67 on 2008-07-31
Have you tried developing a simple multi-threaded application that mimics a producer and consumer, or something similar that you can test on your home system?

I've attached a simple application (written in C++) that you can test with.  I only have single-core systems, so I can't verify if these are properly setup to meet your needs.

Please let me know your results.


P.S.  After downloading the attachment:
```
1.  tar xzvf Thread.tar
2.  cd Thread
3.  make
4.  ./threaded <iterations>
```

where <iterations> is the number of times the two threads should perform their task.  The default is 5 if a command-line arg is not given.  Obviously, the greater the number the more time you will have to monitor the threads in "action".

---

### Post by Cygnus on 2008-07-31
Does cat /proc/cpuinfo actually show several cores ?

---

### Post by LightRaven on 2008-07-31
First: Is the file corrupt ? Can't seem to extract it...

Second: Indeed it does. All 4 of them.

---

### Post by dwhitney67 on 2008-07-31
> **LightRaven said:**
> First: Is the file corrupt ? Can't seem to extract it...

Second: Indeed it does. All 4 of them.
Yes the file is/was corrupt.  I just fixed it.  Please try again.

---

### Post by LightRaven on 2008-07-31
> **dwhitney67 said:**
> Yes the file is/was corrupt.  I just fixed it.  Please try again.

I ran your makefile. However it gives me some warnings about loss of precision and doesn't generate threaded

---

### Post by dwhitney67 on 2008-07-31
What system are you using?

I do not receive any warnings whatsoever on either my Fedora 9 or Ubuntu 8.04 systems.

On Fedora, I am using gcc version 4.3.0.
On Ubuntu, I have version 4.2.3.

Can you paste what the warning is, and more importantly from where it is occurring?

---

### Post by dwhitney67 on 2008-07-31
Btw, edit the Makefile and make changes to the CXXFLAGS so that they appear as follows:
```
CXXFLAGS    = -Wall -Werror -pedantic -O2
```
This will not resolve the issue you are having with the compiler, however it will report all warnings and treat them as errors.

The code I provided does not do anything fantastically special; I cannot fathom why there would be a "precision" problem with anything.

---

### Post by LightRaven on 2008-07-31
> **dwhitney67 said:**
> What system are you using?

I do not receive any warnings whatsoever on either my Fedora 9 or Ubuntu 8.04 systems.

On Fedora, I am using gcc version 4.3.0.
On Ubuntu, I have version 4.2.3.

Can you paste what the warning is, and more importantly from where it is occurring?

Main.cpp: In function ‘int main(int, char**)’:
Main.cpp:26: fejl: cast from ‘time_t*’ to ‘int’ loses precision
Main.cpp:27: fejl: cast from ‘time_t*’ to ‘int’ loses precision

There will be another in MyThread.cpp at:

const unsigned int iter = reinterpret_cast<const unsigned int>( arg );

I am using Ubuntu 8.04 64 bit GCC version 4.2.3

---

### Post by Cygnus on 2008-07-31
No warnings here. I am not sure what the best way to verify this is but I tried the code and instead of just letting the threads print the number I let them do some heavy work and used the kde system tray to plot both my cores. Starting only one thread only one core worked (although it switched a few times in between wich one that was in use), starting both threads showed 50% workload per core.

---

### Post by dwhitney67 on 2008-07-31
> **LightRaven said:**
> Main.cpp: In function &#8216;int main(int, char**)&#8217;:
Main.cpp:26: fejl: cast from &#8216;time_t*&#8217; to &#8216;int&#8217; loses precision
Main.cpp:27: fejl: cast from &#8216;time_t*&#8217; to &#8216;int&#8217; loses precision

There will be another in MyThread.cpp at:

const unsigned int iter = reinterpret_cast<const unsigned int>( arg );

I am using Ubuntu 8.04 64 bit GCC version 4.2.3
The warnings in Main.cpp are easy to fix; goto lines 26-27, and instead of casting to an int, replace with time_t, and use the reinterpret_cast (although the C-style cast can be used too).
[PHP]
const time_t t1EndTime = reinterpret_cast<time_t>(t1Status);
const time_t t2EndTime = reinterpret_cast<time_t>(t2Status);
[/PHP]
As for the warning in MyThread.cpp, just ignore it because the value that is being passed in is indeed an unsigned integer.  I have no idea why your compiler is complaining.

P.S.  To ignore the remaining warning, remove the -Werror (if you have added it) from the Makefile.

---

### Post by dribeas on 2008-07-31
> **LightRaven said:**
> Main.cpp: In function ‘int main(int, char**)’:
Main.cpp:26: fejl: cast from ‘time_t*’ to ‘int’ loses precision
Main.cpp:27: fejl: cast from ‘time_t*’ to ‘int’ loses precision


That might be due to 32/64 bit compiler. Change 'const unsigned int' to 'unsigned long long const' (which should be 64 bits, check its size). That will take care of the warning.

   David

---

### Post by LightRaven on 2008-07-31
> **dwhitney67 said:**
> The warnings in Main.cpp are easy to fix; goto lines 26-27, and instead of casting to an int, replace with time_t, and use the reinterpret_cast (although the C-style cast can be used too).
[PHP]
const time_t t1EndTime = reinterpret_cast<time_t>(t1Status);
const time_t t2EndTime = reinterpret_cast<time_t>(t2Status);
[/PHP]
As for the warning in MyThread.cpp, just ignore it because the value that is being passed in is indeed an unsigned integer.  I have no idea why your compiler is complaining.

P.S.  To ignore the remaining warning, remove the -Werror (if you have added it) from the Makefile.

Sorry to bust your chops. This is what I get now and removing the above flag didn't help:

Makefile - compiling MyThread.cpp
MyThread.cpp: In member function ‘virtual int MyThread::run(void*)’:
MyThread.cpp:25: fejl: cast from ‘void*’ to ‘const unsigned int’ loses precision
make: *** [MyThread.o] Fejl 1

---

### Post by dwhitney67 on 2008-07-31
> **LightRaven said:**
> 
There will be another in MyThread.cpp at:

const unsigned int iter = reinterpret_cast<const unsigned int>( arg );

This warning is probably due to the declaration of 'iter' in Main.cpp.  Change the declaration to be:
[PHP]const int iter = argc > 1 ? atoi(argv[1]) : 5;[/PHP]
and in MyThread.cpp, change lines 25 and 27 to:
[PHP]
const int iter = reinterpret_cast<int>( arg );

for ( int i = 0; i < iter; ++i )
...
[/PHP]

---

### Post by LightRaven on 2008-07-31
> **dwhitney67 said:**
> This warning is probably due to the declaration of 'iter' in Main.cpp.  Change the declaration to be:
[PHP]const int iter = argc > 1 ? atoi(argv[1]) : 5;[/PHP]
and in MyThread.cpp, change lines 25 and 27 to:
[PHP]
const int iter = reinterpret_cast<int>( arg );

for ( int i = 0; i < iter; ++i )
...
[/PHP]

Very many times thanks for spending your time on this. It gave me though a whole new range of hurt warnings. 

Saying that, what I prop really need is a program that is confirmed to give a load of near 100% on several cores on Ubuntu 8.04 on a machine other than mine. I guess; I could make a simple program that spawns some thread and just add integers in infinity.

---

### Post by Cygnus on 2008-07-31
> **LightRaven said:**
> Saying that, what I prop really need is a program that is confirmed to give a load of near 100% on several cores on Ubuntu 8.04 on a machine other than mine. I guess; I could make a simple program that spawns some thread and just add integers in infinity.

See my previous post, I am on Kubuntu 8.04.

---

### Post by dwhitney67 on 2008-07-31
> **LightRaven said:**
> Very many times thanks for spending your time on this. It gave me though a whole new range of hurt warnings. 

Saying that, what I prop really need is a program that is confirmed to give a load of near 100% on several cores on Ubuntu 8.04 on a machine other than mine. I guess; I could make a simple program that spawns some thread and just add integers in infinity.
No doubt that the "meat" within the thread I gave is not process intensive.  Hopefully the code will serve as a spring-board for developing a test application of your own that meets your specific needs.

I've attached another thread application as an example.  This one uses the C++ Boost library, which needs to be installed prior to building this application.

After downloading:
```
1.  tar xzvf ThreadBoost.tar.gz
2.  cd ThreadBoost
3.  make
4.  ./threadTest <num msgs> <idle cycles>
```
where the <num msgs> represents the number of messages the producer thread should provide the consumer thread, and the <idle cycles> is the number of periods the consumer should linger if production of messages stops.

---

