---
title: "threading"
date: 2007-09-19
forum: Programming Talk
---

### Post by zanjabeel5 on 2007-09-19
Hi

I wanted to see how multi threading will improve performance, so I did the following demo program.

pseudo code:


int ARR[1,000,000]

main()
       run_test1()
       run_test2()


test1()
     iterate of the million cells in ARR
           increase each cell thousand times (using for loop, NOT +1000 :) )

test2()
   make 2 threads, each does what test1 does to other half of the ARR.


test1 finished in 4.06 seconds 
and test 2 in about 4.08 seconds ??

I expected test2 to finish in about 2 seconds
what I'm doing wrong ?
I've attached the full code, it's pretty simple ~ 60 lines.

---

### Post by psusi on 2007-09-19
Do you have two processors?

---

### Post by zanjabeel5 on 2007-09-19
yes.

in fact. I think the problem is the way I do the time measurement.
because when I run test2 I notice it takes less time.
so I ran from the command line
> date; test1; date;
and
> date; test2; date;

these gave the desired results. tests being 2 seconds only.
also while in test2 I see in the gnome system monitor both cpus peak

I didn't suspect the timer function cause I copied it from openssl :)

---

### Post by DMills on 2007-09-19
You are running on a single core machine. 

The CPU can only do one thing at any given time, and your job is totally CPU bound, threads offer no advantage in this situation. 

On a multicore box (either a straight SMP box or a core 2 Duo or the like), you would see an improvement as both cores could work the problem, but it would be less then a factor of 2 due to cache coherency overheads. 

Threads are a big win when you have multiple IO bound tasks that are blocking on different IO activities, so to give an example I am working on, I have one thread that drives a soundcard, with another that refills the disk IO ringbuffer and a third that handles network comunications. Total load is only about 1%, but the threads were a simpler way to organise things then a state machine would have been.

HTH.

Regards, Dan.

---

### Post by AlexThomson_NZ on 2007-09-19
I can't see any reason why the code wouldn't work as planned.  As DMills suggested, you are probably running a single core CPU. 

I have done a pretty decent benchmarking program that suppors multi-cores, I'll post it up soon...

---

### Post by zanjabeel5 on 2007-09-19
Thanks guys.
but I'm running on core due2.
and I CAN see both cpus peak.

running this gives good results :

> date; ./test2 ; date;

I see it took  2 seconds. while using test1 ( not threaded ) it takes 4 seconds. which is what you explained.

the problem is that i couldn't measure time elapsed "programmatically",  in test2 I  have something like:

start = clock();
 // create 2 threads;
 // join_threads
end = clock();
print diff(start, end)

this still prints 4 seconds

---

### Post by gnusci on 2007-09-19
try with:

**> time test2**

and also make sure that your threads are running in different processor, better force them to go to different processor than expect the OS do that for you, it happen that if the OS does not see a real needing to use the two processor, it will just run the two thread in one processor. This happen because the OS it is not thinking as we want, it is just trying to keep the performance of the whole system.

---

### Post by AlexThomson_NZ on 2007-09-19
Ahh have encountered this before.  Here's a timer I used to measure ELAPSED time rather than CPU time.  Gnusci, you don't need to 'force threads onto different processors', using pthreads, the kernel takes care of this for you.

```

void start_timer()
{
    gettimeofday(&start_time, 0);
}

int get_time()
{
    gettimeofday(&end_time, 0);
    return (end_time.tv_sec-start_time.tv_sec) * 10000000 + (end_time.tv_usec-start_time.tv_usec);
    //return 0;
}

```

---

