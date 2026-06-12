---
title: "Preview my benchmarking tool"
date: 2007-09-19
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-09-19
Hi all,

For those that may remember, I've been working off-and-on on making a system benchmarking tool for Linux.  It's starting to take shape now, so I thought I might post it here if there is anybody interested in giving it a try.

So far the bits I've implemented are:
 * CPU Benchmarking (single and multithreaded Integer and Floating benchmarks)
 * Disk Benchmarks (reading, writing and access time for cached and non-cached data)
 * Gnome Benchmark (this part is still a bit rough)

The bits still to do:
 * OpenGL Benchmarking
 * RAM Benchmarking (still wondering how to implement this)

So please, give it a go and let me know how you find it, and if you could paste your results would be great!

There is an x86 32 bits executable already compiled, otherwise just compile with 'make' in the src/ directory (the dependancies for compiling are just the basics: libgnomeui-2.0, gtk+-2.0 and libglade-2.0)

I'll start the ball rolling...
```

SYSTEM INFO
OS
 * Version: Benchpress v0.0 (20070920)
 *  Kernel: Ubuntu 2.6.20-16.31-generic
CPU
 * Cores: 1
 * Model: Intel(R) Pentium(R) M processor 1.86GHz
 * Speed: 1862 MHz
 * Cache: 2048 KB
RAM
 * Size: 1011 MB
 * Free: 4%

RESULTS

Graphics
Gnome
  Score: 29.7

Disk
Read/Write
  Disk write score: 6.5
   Disk read score: 18.5
Seek
  Small-file score: 25.6
  Large-file score: 10.3

CPU
Floating Point
 Single-threaded score: 10.9
  Multi-threaded score: 11.6
Integer
 Single-threaded score: 8.9
  Multi-threaded score: 9.5

```

---

### Post by aidanr on 2007-09-19
```
command:make
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchpress.o -c benchpress.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-prefs.o -c benchmark-prefs.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-spec.o -c benchmark-spec.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-timer.o -c benchmark-timer.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-cpu-float.o -c benchmark-cpu-float.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-cpu-integer.o -c benchmark-cpu-integer.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-disk.o -c benchmark-disk.c
gcc `pkg-config --cflags libgnomeui-2.0 gtk+-2.0 libglade-2.0 ` -o benchmark-gui.o -c benchmark-gui.c
gcc benchpress.o benchmark-prefs.o benchmark-spec.o benchmark-timer.o benchmark-cpu-float.o benchmark-cpu-integer.o benchmark-disk.o benchmark-gui.o `pkg-config --libs gtk+-2.0 libglade-2.0 libgnomeui-2.0 ` -o benchpress -export-dynamic
command:./benchpress

(benchpress:11312): Gtk-WARNING **: Invalid text buffer iterator: either the iterator is uninitialized, or the characters/pixbufs/widgets in the buffer have been modified since the iterator was created.
You must use marks, character numbers, or line numbers to preserve a position across buffer modifications.
You can apply tags and insert marks without invalidating your iterators,
but any mutation that affects 'indexable' buffer contents (contents that can be referred to by character offset)
will invalidate all outstanding iterators
Segmentation fault (core dumped)
command:

```

works for a bit, then segfaults

---

### Post by AlexThomson_NZ on 2007-09-19
Hmm that is probably the Gnome benchmark failing, disabling this in the preferences screen will at least let you run the CPU and Disk benchmark.

I'll have to look into why it does this- it looks like Gnome does not play nicely with threaded apps (at least to the extent this that app abuses Gnome widgets when doing the benchtest!)

---

### Post by Wybiral on 2007-09-19
Yeah, I got:

```

(benchpress:4528): Gtk-CRITICAL **: gtk_text_attributes_ref: assertion `values != NULL' failed

(benchpress:4528): Gtk-CRITICAL **: gtk_text_attributes_ref: assertion `values != NULL' failed

(benchpress:4528): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed
Segmentation fault (core dumped)

```

(as soon as I hit "Start")

---

### Post by AlexThomson_NZ on 2007-09-19
Ok, I should have disabled the Gnome benchmarking by default, try disabling it in the preferences screen and starting again...

---

### Post by Wybiral on 2007-09-19
OK, it ran fine without the GUI tests.

```

SYSTEM INFO
OS
 * Version: Benchpress v0.0 (20070920)
 *  Kernel: Ubuntu 2.6.20-16.31-generic
CPU
 * Cores: 1
 * Model: Intel(R) Celeron(R) CPU 2.93GHz
 * Speed: 2926 MHz
 * Cache: 256 KB
RAM
 * Size: 487 MB
 * Free: 10%

RESULTS

Disk
Read/Write
  Disk write score: 4.6
   Disk read score: 17.3
Seek
  Small-file score: 20.3
  Large-file score: 8.0

CPU
Floating Point
 Single-threaded score: 6.7
  Multi-threaded score: 6.4
Integer
 Single-threaded score: 6.0
  Multi-threaded score: 5.8

```

---

### Post by aidanr on 2007-09-20
nope, it crashes out on the cpu bench for me
```
SYSTEM INFO
OS
 * Version: Benchpress v0.0 (20070920)
 *  Kernel: Ubuntu Unofficial
CPU
 * Cores: 2
 * Model: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
 * Speed: 2402 MHz
 * Cache: 4096 KB
RAM
 * Size: 2027 MB
 * Free: 3%

RESULTS

Graphics
Gnome
  Score: 128.2

Disk
Read/Write
  Disk write score: 8.4
   Disk read score: 32.1
Seek
  Small-file score: 35.8
  Large-file score: 15.7
```

---

### Post by AlexThomson_NZ on 2007-09-20
Damn the CPU part should be rock solid- cheers for the notice, will look into it

---

### Post by slavik on 2007-09-20
fpu score doesn't make sense to me, the multi-threaded version is over 5x faster ... is core2quad that good?

```

SYSTEM INFO
OS
 * Version: Benchpress v0.0 (20070920)
 *  Kernel: Ubuntu 2.6.22-11.33-generic
CPU
 * Cores: 4
 * Model: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
 * Speed: 1596 MHz
 * Cache: 4096 KB
RAM
 * Size: 7999 MB
 * Free: 3%

RESULTS

CPU
Floating Point
 Single-threaded score: 13.3
  Multi-threaded score: 73.4
Integer
 Single-threaded score: 14.5
  Multi-threaded score: 57.3

```

bug or w/e you want to think of this as, in the benchmark-cpu-float.c
```

// Integer arithmetic
void sub_float_e()
{
	int weight = 190*ITERATIONS;
	int val1 = 1;
	int val2 = 2;
	int val3 = 3;
	double e1[4];
	int i;
	for (i=0; i <= weight; i++)
	{
		val1 = val1*(val2-val1)*(val3-val2);
		val2 = val3*val2-(val3-val1)*val2;
		val3 = (val3-val2)*(val2+val1);
		e1[val3-2] = val1+val2+val3;
		e1[val2-2] = val1*val2*val3;
	}
}

```

---

### Post by AlexThomson_NZ on 2007-09-20
Doh!  Good spotting, looks like a cut + paste error I missed

Not too sure of what to make of the anomaly, I can't see why a Quad core would be more than 4x faster, my instinct would be that it is 4x minus a bit of overhead, so either something is going on I haven't accounted for (weird caching thing) or a bug (most likely), however, it's a pretty simple measure of work done, so not too sure, will look into it.

Impressive results though- definetly the score to beat so far! :)

---

### Post by aidanr on 2007-09-20
Ok, now it's working. Earlier it segfaulted (I tried about 3 times), I come back a few hours later without changing anything and now it's working properly for some reason. :confused:

```
SYSTEM INFO
OS
 * Version: Benchpress v0.0 (20070920)
 *  Kernel: Ubuntu Unofficial
CPU
 * Cores: 2
 * Model: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz
 * Speed: 2402 MHz
 * Cache: 4096 KB
RAM
 * Size: 2027 MB
 * Free: 15%

RESULTS

Graphics
Gnome
  Score: 190.5

Disk
Read/Write
  Disk write score: 7.9
   Disk read score: 28.9
Seek
  Small-file score: 28.1
  Large-file score: 14.1

CPU
Floating Point
 Single-threaded score: 16.8
  Multi-threaded score: 32.0
Integer
 Single-threaded score: 14.3
  Multi-threaded score: 26.3
```

---

### Post by AlexThomson_NZ on 2007-09-20
Cool thanks for the feedback aidanr, think I might have tracked down the issue, it's hard because it is so random.  It's obviously a thread contention issue though.  I put a couple of sleep(1) statements in the benchpress.c file to work around this issue on my work PC (if it's the same issue), clearly there's more to it though, I suspect it's the textview widget not playing nicely...

---

### Post by slavik on 2007-09-20
It would be nice if the report was more detailed such as the test run and the score for the particular test. I will also look at the code more thoroughly because I think you can optimize it a bit more.

---

### Post by AlexThomson_NZ on 2007-09-20
Ah-ha!  One step ahead of you there!  On the 'main' output screen, I want the summarised results, but intend to have a 'results' screen, where more details results are given, ie. average seek times, system comparisons, etc. this will probably be the last thing to do though.  I don't really see the benifit of reporting on things like floating point addition, floating point passing arrays as parameters, etc. though (if that was what you were meaning)

What optimzations were you thinking?  I don't think it's too bad.  Obviously you can't optimize the work loops, other than that it's noo bad I thought...

---

### Post by slavik on 2007-09-20
using pthreads instead of gdk threads? and have the threads time themselves (or the portion that needs to be timed).

I can also suggest another test ... 1000 by 1000 matrix multiplication. on a 2.3GHz single CPU system, this would take about 30-40 seconds ...

edit: another thing, any chance the GUI could be separated from the actual benchmarking code?

---

### Post by Unix_Wizard on 2007-09-21
I'm only interested in the CPU test. This is on a 3800 x2 undervolted and overclocked to 2.4.
```

CPU
Floating Point
 Single-threaded score: 14.4
  Multi-threaded score: 28.8
Integer
 Single-threaded score: 10.5
  Multi-threaded score: 20.4
```

Take another look at CPU test. Note the perfect scaling on the floating point test, that's not right. Also my CPU temp hardly changed during the test though that could be because it's too short.

Can you please explain more about how the CPU benchmark works?

---

### Post by mssever on 2007-09-21
Everything worked fine on my machine. But is there any chance that there could be some interpretation of the scores? For example, my Gnome score was 25.5. 25.5 what?

```
SYSTEM INFO
OS
 * Version: Benchpress v0.0 (20070920)
 *  Kernel: Ubuntu 2.6.20-16.31-generic
CPU
 * Cores: 1
 * Model: Intel(R) Pentium(R) 4 CPU 2.66GHz
 * Speed: 2658 MHz
 * Cache: 512 KB
RAM
 * Size: 439 MB
 * Free: 1%

RESULTS

Graphics
Gnome
  Score: 25.5

Disk
Read/Write
  Disk write score: 1.5
   Disk read score: 6.3
Seek
  Small-file score: 12.6
  Large-file score: 3.6

CPU
Floating Point
 Single-threaded score: 5.3
  Multi-threaded score: 5.8
Integer
 Single-threaded score: 3.3
  Multi-threaded score: 3.6

```

---

### Post by AlexThomson_NZ on 2007-09-21
msserver, the CPU values should just be considered an index, linearly proportional to work done.  I guess everything not a scalar has a unit, however in this case it would be too complex as to be meaningless.

unix_wizard: I don't have the code with me at the moment and I haven't touched the CPU code for a while, but it goes along the line of:
```

while (TIME_NOT_ELAPSED)
{
    spawn N threads of "test"
    wait for all threads to finish
}
Result = # of iterations / actual_time_elapsed

"test"
{
   spawn thread to do "floating point addition"
   spawn thread to do "coniditional loops using FPs"
   spawn thread to do "arrays using FPs"
   ...
   wait for all threads to finish
}

```

Is obviously a little more complex, but that's the basic shape of it from memory.  I can't see anything fundamentally wrong with it, can you?  But as you say, perfect efficiency for multiple CPUs is not right (somebody else has pointed this out too)

---

### Post by slavik on 2007-09-21
here is how I would do it with pthreads (rough C pseudo code)
```

#define JOBS
long int time_taken[JOBS];
int threads[JOBS]; //I forget the exact type for pthreads ...

void main() { //this is bad but this is pseudocode, also, this could be a single multithreaded test
 while (i<JOBS) {
  pthread_start(&test, NULL, something, i++);
 }
 while (i<JOBS) {
  pthread_join(NULL);
 }
 while(i<JOBS) print time_taken[i++];
}

void test(int whatever) {
 int start = get_time();
 //do stuff (this stuff should not be threaded)
 int end = get_time();
 time_taken = end-start;
 return;
}
```

whenever you make a thread, it takes CPU time (which shows up as system in the time utility).

if you look for my code, you can define number of threads, what I found when testing it on a single CPU is that no matter the number of threads, it still took up the same amount of "user" time (the actual calculations). I ran it with 100 threads and the amount of time the system took (to make the threads) outweighed the user time by a lot. When I say a lot, I mean A LOT!!!

Also, threads share the process' global data (same memory page). Notice that there are no mutex/semaphore usage. When you look at my matrix code (should be in the forum), it can be done with mutex, too. (but I didn't realise back then).

---

### Post by Yes on 2007-09-22
It looks good, but it runs the GNOME and Disk tests, and then exits without doing any of the CPU or RAM tests.  I have both of those tests checked under preferences.  Any idea what's going wrong?

Edit:  If I don't run the disk tests, I can run the CPU and GNOME tests.  The program doesn't exit when it's done anymore, but it still won't run the RAM test.  Any idea why the multi-threaded test was slower than the single threaded test?  I have a hyper-threaded CPU, so it should simulate two CPUs, which I thought made multi-threaded programs faster.

---

### Post by AlexThomson_NZ on 2007-09-23
> **Yes said:**
> It looks good, but it runs the GNOME and Disk tests, and then exits without doing any of the CPU or RAM tests.  I have both of those tests checked under preferences.  Any idea what's going wrong?
It is probably crashing.  If you run it from a terminal you will probably see some error messages (it seems to crash out mostly doing the Gnome test)

> Edit:  If I don't run the disk tests, I can run the CPU and GNOME tests.  The program doesn't exit when it's done anymore, but it still won't run the RAM test.  Any idea why the multi-threaded test was slower than the single threaded test? I have a hyper-threaded CPU, so it should simulate two CPUs, which I thought made multi-threaded programs faster.
That should definitely no happen, and you're the first to encounter this.  I haven't made it very clear, but the numbers are an indication of work done, so the higher the better.  Try disabling the Gnome test and pasting in the results.  Thanks very much for trying it though- it does look like I need to do more work on this than I thought...

---

### Post by slavik on 2007-09-23
another thing, may I suggest that you look up some file system comparisons and use the same test? (such as creating a 1GB file, deleting it, copying it, creating 1000 files with touch, removing them, etc).

---

### Post by AlexThomson_NZ on 2007-09-23
Well that is kinda what I done, in that it tests both large files (too big to be cached) and small files (that fit inside the cache).  I used 100Mb as my big file though, so that it doesn't take too long (100Mb is already pretty borderline on my PC when running on a USB drive).  I do like your idea though of including time taken to create and remove inodes though, as this will likely vary between filesystems.

---

### Post by slavik on 2007-09-23
> **AlexThomson_NZ said:**
> Well that is kinda what I done, in that it tests both large files (too big to be cached) and small files (that fit inside the cache).  I used 100Mb as my big file though, so that it doesn't take too long (100Mb is already pretty borderline on my PC when running on a USB drive).  I do like your idea though of including time taken to create and remove inodes though, as this will likely vary between filesystems.
exactly :) basically make your benchmarking tool something that can be used to compare filesystem/kernel combinations and such :)

May I suggest being able to run benchmarks from the command line?

---

### Post by AlexThomson_NZ on 2007-09-23
This is definitely something I will be adding, but probably later.  Might require big code changes, as I am already moving away from pthreads to gthreads, so *hopefully* get around all the errors that are popping up.  Making it command-line, will obviously not support gthreads (working on the assumption that gnome is not present) and will probably require a rewrite, so will probably end up being a seperate app (will do the same tests though, so results should be comparable)

---

### Post by slavik on 2007-09-23
that's why I suggested separating the app from the gui a bit before ... because kde users have to install extra stuff ...

---

### Post by AlexThomson_NZ on 2007-09-23
Dammit you might be right Slavik, I think I will probably have to get started on this....

---

### Post by Unix_Wizard on 2007-09-25
For the RAM benchmarking part could you make use of RAMspeed tests calculated into some sort of a comparable score (like the cpu test)?
**_[RAMspeed homepage]("http://www.alasir.com/software/ramspeed/index.html")_**

---

### Post by slavik on 2007-09-25
> **AlexThomson_NZ said:**
> Dammit you might be right Slavik, I think I will probably have to get started on this....
"I'm infallable, you should already know that."

Guess who I am quoting :)

---

### Post by kknd on 2007-09-25
Hi,

It crashes (the precompiled one and build from the source) before the GUI is show.

---

### Post by AlexThomson_NZ on 2007-09-26
> **slavik said:**
> "I'm infallable, you should already know that."

Guess who I am quoting :)

I'm not too sure, sounds like a Bush-ism(?)  who was it?

kknd, I'm re-doing from scratch (again), going to make it a command-line program, and have a seperate GUI app to act as a front-end as per Slavik's suggestion.  This  modularity will hopefully make it easier to trouble-shoot...

---

### Post by slavik on 2007-09-26
> **AlexThomson_NZ said:**
> I'm not too sure, sounds like a Bush-ism(?)  who was it?

kknd, I'm re-doing from scratch (again), going to make it a command-line program, and have a seperate GUI app to act as a front-end as per Slavik's suggestion.  This  modularity will hopefully make it easier to trouble-shoot...
Dogbert.

As for modularity, it is awesome. At work, I wrote a script that parses output of smbtree and only lists the info you want from the domain you want. Then I wrote another script that takes the list of names and outputs the name, the ip address and the mac address (wins server reports the mac address), then I wanted to learn how to make a gui and how to use a treeview, so I wrote a script that takes the stuff from the second script and puts it into a gui.

my suggestion for your case would be to use getopt (it's freaking awesome) for the cli program and have the gui "build" the command up, then run and catch the output.

catching the output you can do in like 4 ways (from the top of my head).

here's what I came up with:
- 1st gui to build the command and pipe the output to a second gui for display
- use popen and such from 1 gui program
- similar to the above, but create a permanent pipe instead (mkfifo) upon "install" or such
- temporary pipe

may I suggest using perl/python to write the gui? (perl::gtk is very similar to how you would use it in C)

---

### Post by AlexThomson_NZ on 2007-09-26
Ahh- Dogbert, the irony of the spelling mistake in 'infallable' threw me :)

I am handling the command-line arguments through the app itself (it's not very hard at all to do in C++).  The basic format will be:
benchpress <test_type> <test_options>
so will be called like:
benchpress cpu --float --integer --threads 32 --time 60
for example.
The GUI will probably be in C because I can whip this up very quickly (and because I like C)

---

### Post by slavik on 2007-09-26
but getopt can do more intelligent processing :)

hmm, the spell checker wasn't on I guess. I sometimes confuse when it's "able" and "ible"

---

### Post by kknd on 2007-09-26
> **AlexThomson_NZ said:**
> I'm not too sure, sounds like a Bush-ism(?)  who was it?

kknd, I'm re-doing from scratch (again), going to make it a command-line program, and have a seperate GUI app to act as a front-end as per Slavik's suggestion.  This  modularity will hopefully make it easier to trouble-shoot...

Nice =).  I will try to find good benchmarking methods for RAM and etc.  
I have a lot of work to do in the next weeks, sorry about my lack of participation.

---

### Post by AlexThomson_NZ on 2007-09-27
That would be good- RAM is the one grey area for me, and would like to steer away from inline assembly if I can (not that I'm uncomfortable with it- just don't really know what specifically to test, and how valuable the tests would be- to some extent this is already being done in the CPU tests anyway)...

No prob about the participation- probably just as well given the number of rewrites :)

---

### Post by Unix_Wizard on 2007-09-27
So I take it that using some code from the opensource RAMspeed test is not an option? I've seen phoronix use it for benchmarking RAM, it's very reliable.

---

### Post by AlexThomson_NZ on 2007-09-27
Ooo was hoping there was an opensource ram benchmarking tool out there... I'll definitely look into it.  Thanks for the pointer!

---

### Post by AlexThomson_NZ on 2007-09-27
Well I had a look, seems they are just doing a few simple tests, along the lines of what I was thinking: Reading/Writing blocks of ints/floats, etc.  Block additions, scales, etc.  Pretty simple stuff, but I'll have to look into why they chose to do things like scaled reads (isn't that just a integer/float read with the overhead of a multiplication?)

---

### Post by kknd on 2007-09-28
> **AlexThomson_NZ said:**
> Well I had a look, seems they are just doing a few simple tests, along the lines of what I was thinking: Reading/Writing blocks of ints/floats, etc.  Block additions, scales, etc.  Pretty simple stuff, but I'll have to look into why they chose to do things like scaled reads (isn't that just a integer/float read with the overhead of a multiplication?)

Maybe add some reallocations from a small size to a medium size of RAM multiple times, and / or creating a linked list and allocate / deallocate nodes until death?

I think it must stick with simples tests. The linked list one is also a real situation.

P.S.: I still can't get the program working, here is a poor debug that I made with gdb, as soon as the app starts (no gui yet)

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1226295616 (LWP 9537)]
0xb745ffa5 in fgets () from /lib/libc.so.6

---

### Post by dariusr on 2008-11-19
It's awesome! Keep up the great work! Every aspect of it works totally fine for me, but the only thing I'm having trouble with is translating the "score" on the Disk bench into something relative to like, megs or gigs per seconds on reading and writing

---

