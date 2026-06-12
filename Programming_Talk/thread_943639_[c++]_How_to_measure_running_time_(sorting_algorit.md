---
title: "[c++] How to measure running time? (sorting algorithms)"
date: 2008-10-10
forum: Programming Talk
---

### Post by lian1238 on 2008-10-10
Hi guys,

For my term project, I'm required to analyze the running times of 4 sorting algorithms. I have to find a way to measure 5 things:

[LIST=1]
[*]Number of Comparisons made
[*]Total Clock time spent in comparisons
[*]Number of Exchanges (Swapping of Elements) performed
[*]Total Clock time spent in Exchange of Elements
[*]Overall clock time spent in sorting a given sample data set
[/LIST]
For (1), I can increment the counter of comparisons inside the callback functor.
For (3), I guess I can add a similar line into the swap function.

For the rest, how can I measure the clock time without (significantly) increasing the clock time *because* of the measuring?

---

### Post by kknd on 2008-10-10
For the overal time, store the time that your program started, and in the end subtract the current time from the stored initial time.

---

### Post by dribeas on 2008-10-10
If you can make different executables, use 'time' command, as it will give you real processor time. If you take real time at the beginning and end of your algorithm then you will have some randomness out of the state of all other system processes (if some external process kicks in, it will influence your measurement). Also note that you should make various measurements and average results. Finally consider that even if it is probably small, you should take into account the fact that you are logging the number of comparisons and swap, and that measuring adds up a little more to your algorithm (unless you make different executables for counting iterations and times).

---

### Post by hod139 on 2008-10-10
Here's how one of the STL author's timed his sort function: [http://www.cs.rpi.edu/~musser/gp/timing.html]("http://www.cs.rpi.edu/%7Emusser/gp/timing.html").  His timer code is publicly available as well, [http://www.cs.rpi.edu/~musser/stl-book/source/timer.h]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/timer.h")

For an example of how to use it, I used his timing code in this post: [http://ubuntuforums.org/showpost.php?p=4303318&postcount=31](http://ubuntuforums.org/showpost.php?p=4303318&postcount=31)

He also uses it to time sort on a vector here: [http://www.cs.rpi.edu/~musser/stl-book/source/ex19-02.cpp](http://www.cs.rpi.edu/~musser/stl-book/source/ex19-02.cpp)

---

### Post by lian1238 on 2008-10-10
> **hod139 said:**
> Here's how one of the STL author's timed his sort function: [http://www.cs.rpi.edu/~musser/gp/timing.html]("http://www.cs.rpi.edu/%7Emusser/gp/timing.html").  His timer code is publicly available as well, [http://www.cs.rpi.edu/~musser/stl-book/source/timer.h]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/timer.h")

For an example of how to use it, I used his timing code in this post: [http://ubuntuforums.org/showpost.php?p=4303318&postcount=31](http://ubuntuforums.org/showpost.php?p=4303318&postcount=31)

He also uses it to time sort on a vector here: [http://www.cs.rpi.edu/~musser/stl-book/source/ex19-02.cpp]("http://www.cs.rpi.edu/%7Emusser/stl-book/source/ex19-02.cpp")

Thanks for these useful links. They appear to be exactly what I need. I'll read into them. :)

---

### Post by lian1238 on 2008-10-10
I think I can now time the whole sorting routine accurately, but I don't quite understand how just the comparisons were timed.

I was wondering if I could do this: Make a million comparisons in a loop, divide by a million to get the clock time for one comparison, and multiply by the total number of comparisons made? Just an idea.

---

### Post by lian1238 on 2008-10-12
Bump?

---

### Post by hod139 on 2008-10-14
To time the comparisons, you will add the timer code inside your sort function, and only around the part of the sort routine that moves elements.  You will have to write your own sort function, and not use an STL sort.

---

### Post by lian1238 on 2008-10-14
So you're saying I should start and stop, before and after each line of comparisons, and same for swaps? But you see, the time it takes for one line of code is too small to be measured accurately. I assume the timer code you're talking about is clock().

---

### Post by stroyan on 2008-10-14
You can use clock_gettime and clock_getres to make accurate measurements
of elapsed time.  But the assumption that the time in comparisons is
separated from the time in exchanges could be a problem.  The actual
time spent reading and writing memory locations varies dramatically
depending on whether they are in any of multiple levels of hardware
caches.  A recent comparison of a sorting key may reduce the time spent
exchanging the data record in memory locations near that key.
And the time to read or write a memory location will vary because of
differences in the access pattern effecting cache and TLB reuse.

You can learn much more about the performance of memory operations by
reading the "What every programmer should know about memory" articles at
[http://lwn.net/Articles/250967/](http://lwn.net/Articles/250967/) .  Part 2 is particularly interesting.
It is a really big, complicated topic.  But understanding it is worth it.

---

### Post by masumeh-- on 2010-04-16
> **stroyan said:**
> You can use clock_gettime and clock_getres to make accurate measurements
of elapsed time. But the assumption that the time in comparisons is
separated from the time in exchanges could be a problem. The actual
time spent reading and writing memory locations varies dramatically
depending on whether they are in any of multiple levels of hardware
caches. A recent comparison of a sorting key may reduce the time spent
exchanging the data record in memory locations near that key.
And the time to read or write a memory location will vary because of
differences in the access pattern effecting cache and TLB reuse.
 
You can learn much more about the performance of memory operations by
reading the "What every programmer should know about memory" articles at
[http://lwn.net/Articles/250967/](http://lwn.net/Articles/250967/) . Part 2 is particularly interesting.
It is a really big, complicated topic. But understanding it is worth it.
 helllo
i calculated the time of my program by clock instruction but the time of program for same inputs is different in each run. please help me

---

### Post by MadCow108 on 2010-04-16
there will always be a differences in multiple runs. A computer is no high precision time measurement instrument.

There are lots of sources of noise, some examples:
there are hundreds of processes running in an operating and the cpu is scheduled between them. how much cpu time a process gets is never the same
memory usage is different on every run, sometimes you may generate more page faults than on other times.
modern cpu's may have non-deterministic branch predictors so even hardware clock cycle counters can deviate
and many many more

if you want accurate samples let the algorithm do lots of work so the runtime is long compared to statistical fluctuations
and run the benchmark lots of times and average appropriately to reduce the statistical error

---

### Post by Jekshadow on 2010-04-16
```
time ./my-program
```

---

### Post by masumeh-- on 2010-05-01
there isn't any way to measure the run time of program pure without interfering the other processes or factors?????

---

### Post by MadCow108 on 2010-05-01
on a normal system only with a realtime kernel where you have certain time guarantees on scheduling, memory allocation etc.
(the linux kernel is not yet a realtime kernel, even when compiled with realtime options!)

what do you want to do that requires that precision?

why not measure multiple times on bigger problem sizes to reduce the effect of noise?
you can also give your process a higher absolute priority and low nice value to get bigger slices of the cpu time.

---

### Post by masumeh-- on 2010-05-02
I want to compare the run time of 4 programs like papers for a specific input and therefore i can't consider big inputs???

---

### Post by CptPicard on 2010-05-02
A theoretical Big-Oh style argument is not sufficient or otherwise viable?

---

### Post by MadCow108 on 2010-05-02
I doubt the usefulness of timings when the maximal input is so small that system noise destroys the measurement

---

### Post by vek on 2010-05-02
A more GUI approach would be to use kcachegrind and valgrind together.

run:

valgrind --tool=callgrind (your command line)

The program will run slowly, it is doing a lot of debug and output.  Once you quit the program, it will output a callgrind file in the current folder.

Feed that to kcachegrind and it will allow you to visually explore the tree of calls that your program made, and tell you exactly how much time each took, what they called, etc.

You could also run it with --tool=cachegrind and see if your instructions are causing cache misses or other issues.

You'll need to install valgrind and kcachegrind (but those are both in the repositories.).  They both have man pages and websites and tutorials.  I highly recommend going this path if you are serious about timing and optimizing.  

To get proper timing information your program must output debug information (note: it doesn't have to be debug compiled, it should be optimized - never profile debug code, it just has to write the debug info to a file that valgrind can read).

---

### Post by Cracauer on 2010-05-02
The C stuff I use goes like this. In C++ you would define an interface class that has a "run_for_benchmark()" method and then pass instances of objects of classes implementing that interface to a "Benchmark.run(such_an_object)" class. That run method would do timing and printing for you.

Here's the C stuff. I has automatic printing of symbols invoked.
```

volatile int stopit = 0;

const int usec_per_test = 500000;

void onsig(int sig)
{
  stopit = 1;
}

void runtest(void (*func)(void), const char *funcname)
{
  struct itimerval it;
  int n;
  struct timeval beginning;
  struct timeval end;

  timerclear(&it.it_interval);
  it.it_value.tv_sec = 0;
  it.it_value.tv_usec = usec_per_test;

  setitimer(ITIMER_REAL, &it, NULL);

  if (gettimeofday(&beginning, NULL) == -1) {
    perror("gettimeofday1");
    exit(2);
  }
  for (n = 0; !stopit; n++)
    (*func)();
  stopit = 0;
  if (gettimeofday(&end, NULL) == -1) {
    perror("gettimeofday2");
    exit(2);
  }

  double seconds_per_call = 
    (double)end.tv_sec + (double)end.tv_usec / 1000000
    - (double)beginning.tv_sec - (double)beginning.tv_usec / 1000000;
  
  seconds_per_call /= (double) n;

  if (seconds_per_call > 1.0 / 100000.0 ) {
    printf("%10.1f usec/call: '%s'\n", seconds_per_call * 1000000.0, funcname);
  } else {
    printf("%10.1f nsec/call: '%s'\n", seconds_per_call * 1000000000.0
           , funcname);
  }
}

#define call_stuff(_FUNCNAME_) \
  runtest(test_ ## _FUNCNAME_, #_FUNCNAME_)

void test_gettimeofday()
{
  struct timeval tv;
  if (gettimeofday(&tv, NULL) == -1) {
    perror("gettimofday");
    exit(2);
  }
}

int main(void)
{

  if (signal(SIGALRM, onsig) == SIG_ERR) {
    perror("signal");
    exit(2);
  }
  call_stuff(gettimeofday);
  return 0;
}



```

This is copy and pasted out of a bigger program and might be incomplete. Not compile tested.

---

