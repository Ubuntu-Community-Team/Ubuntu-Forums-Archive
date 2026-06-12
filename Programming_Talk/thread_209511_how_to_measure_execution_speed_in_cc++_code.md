---
title: "how to measure execution speed in c/c++ code"
date: 2006-07-05
forum: Programming Talk
---

### Post by melquiades on 2006-07-05
hi guys,

             I've been trying to figure how to measure execution speed 
( cpu/processor time ) of programs i've written in c/c++. I've tried 
gnu's time but I can't get any coherent output. I have also looked at
the gnu libc manual and tried the functions clock ( clock_t clock() 
from time.h) and times ( clock_t times(struct tms*) from sys/times.h),
but it has only helped in increasing my befuddlement. Any sort of help
will be really appreciated.

cheers,
melqui

---

### Post by Ubuntist on 2006-07-05
What about just running your programs with the time command, e.g., if the executable is a.out, then do "time a.out".

---

### Post by pharcyde on 2006-07-05
Have you tried using gprof?  -> [http://www.gnu.org/software/binutils/manual/gprof-2.9.1/html_mono/gprof.html](http://www.gnu.org/software/binutils/manual/gprof-2.9.1/html_mono/gprof.html)

---

### Post by wr3cktangle on 2006-07-06
i've used the code from the 3rd post from here: [http://www.gamedev.net/community/forums/topic.asp?topic_id=318639](http://www.gamedev.net/community/forums/topic.asp?topic_id=318639)

it uses time.h, but i believe it works with ctime too.

here is the code from ju2wheels post:

#include <time.h>
#include <iostream>
using namespace std;

int main()
{
    clock_t start, end;

    start = clock();

    //perform calculations for which performance needs to be checked

    end = clock();

    cout << "Time required for execution: "
         << (double)(end-start)/CLOCKS_PER_SEC
         << " seconds." << "\n\n";
    return 0;
}

---

### Post by hod139 on 2006-07-06
If you are interested in the time of a particular method call instead of the entire program execution time, [this article]("http://www.cs.rpi.edu/%7Emusser/gp/timing.html") is really useful.

---

### Post by wmcbrine on 2006-07-06
Well, you didn't really explain why you find "time" incoherent or clock() befuddling, so it's difficult to answer. However, if your concern is to make your programs faster, then all you have to do is remember a few principles:

1. The slowest thing a program can do, by far, is disk access.

2. The second slowest thing a program can do is memory access.

Therefore, to make your program faster, you cut these down as much as possible. That can mean, for example, passing by reference instead of value whenever practical -- but only when the size of the data you're passing is significantly bigger than the size of a pointer!

Anything beyond these principles is just icing. Profiling won't help you nearly as much as they will.

And as Einstein said:

3. Everything should be made as simple as possible, but no simpler.

That means, don't do something in three steps when you can do it in one. Of course, figuring out what constitutes a "step" is sometimes not obvious. And there can be two meanings to "simple": One is "simple [for humans] to understand"; the other is "simple for the computer to do". Sometimes these aren't the same. But most of the time, they are (particularly in a lower-level language like C).

HTH.

---

### Post by melquiades on 2006-07-07
fellow ubuntu enthusiasts,

         i'm sorry, it was poor choice of words on my part. what i meant as incoherent output on /usr/bin/time was imprecise output, I was hoping for something as precise as cpu cycles if possible. I also tried the libc functions clock() but I was confused with the negative double output of clock(), when I expected it to produce an integral number indicative of number of clock ticks. Here is my sample code and it's output.

#include <time.h>
#include <stdio.h>

int main()
{
	int i;
	clock_t start, end;
	double cpu_time_used;
	start = clock();
	for(i = 0; i < 100; i++) {}
	end = clock();
	printf("start time: %2.16e\n",start);
	printf("end time: %2.16e\n",end);
	printf("CLOCKS_PER_SEC %d\n",CLOCKS_PER_SEC);
	return 0;
}

output:

start time: -1.9511318206787109e-01
end time: -1.9511318206787109e-01
CLOCKS_PER_SEC 1000000

I also tried gprof, but I still can't get any measure of execution speed.
Here's a sample.

1.) File : hello.C

#include <iostream>
using namespace std;

main()
{
	cout << "Hello World.\n";
}

2.) compilation and linking:
> g++ -g -pg hello.C -o hello

3.) snippet from gprof ./hello output

Flat profile:

Each sample counts as 0.01 seconds.
 no time accumulated

  %   cumulative   self              self     total           
 time   seconds   seconds    calls  Ts/call  Ts/call  name    
  0.00      0.00     0.00        1     0.00     0.00  global constructors keyed to main
  0.00      0.00     0.00        1     0.00     0.00  __static_initialization_and_destruction_0(int, int)


		     Call graph (explanation follows)


granularity: each sample hit covers 4 byte(s) no time propagated

index % time    self  children    called     name
                0.00    0.00       1/1           __do_global_ctors_aux [10]
[8]      0.0    0.00    0.00       1         global constructors keyed to main [8]
                0.00    0.00       1/1           __static_initialization_and_destruction_0(int, int) [9]
-----------------------------------------------
                0.00    0.00       1/1           global constructors keyed to main [8]
[9]      0.0    0.00    0.00       1         __static_initialization_and_destruction_0(int, int) [9]
-----------------------------------------------

there must be something wrong with my setup, or me, me probably since I'm
a novice c/c++ programmer, so it might just be some fundamental mishap. Please enlighten this befuddled newbie.

TIA,
melqui

---

### Post by thumper on 2006-07-07
Your program didn't take long to do anything, because it doesn't do anything.

Try to do something more complex to measure execution speed.

---

### Post by wmcbrine on 2006-07-07
> **melquiades said:**
> 
	printf("start time: %2.16e\n",start);
	printf("end time: %2.16e\n",end);

Well, the reason you got scientific notation is that you asked for it -- in printf(), nothing to do with clock(). It's that "%2.16e". If you want an integer, try "%lu".

P.S. And the numbers you're seeing appear to be a rounding error with the "%e" format -- anything else, and I just get "0" for both values. If I up the loop count from 100 to 10,000,000, I start to get results. Notice that the actual resolution is nowhere near a single "clock_t", much less a CPU cycle. There's no way you can get that.

If you really, really want to know how many cycles something takes: 1. Compile to assembly language; 2. Get an ASM book that has instruction timings; 3. Add them up manually. Well, that's what I did back in my Z80 and 8088 days; it won't work with current processors, which execute several instructions per cycle and utilize weird techniques like out-of-order execution.

---

