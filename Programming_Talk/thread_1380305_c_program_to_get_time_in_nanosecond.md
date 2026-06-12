---
title: "c program to get time in nanosecond?"
date: 2010-01-13
forum: Programming Talk
---

### Post by vksingh on 2010-01-13
Hi,

How to write a program to get time in nano second.

Thanks,

Vivek

---

### Post by leandromartinez98 on 2010-01-13
I don't think any available clock has that precision in a normal computer.

---

### Post by dwhitney67 on 2010-01-13
> **leandromartinez98 said:**
> I don't think any available clock has that precision in a normal computer.

Mine does.  To get nanosecond time, I use clock_gettime().  One should verify if their computer supports nanosecond time resolution; to do that, call clock_getres().

The man-pages have good write-ups on both of these C/C++ library calls.

---

### Post by leandromartinez98 on 2010-01-14
I'm surprised. Very interesting. If someone wants to read more about
that:

[http://www.ntp-servers.com/uk/nano/index.htm](http://www.ntp-servers.com/uk/nano/index.htm)

---

### Post by jabl on 2010-01-16
> **dwhitney67 said:**
> Mine does.  To get nanosecond time, I use clock_gettime().  One should verify if their computer supports nanosecond time resolution; to do that, call clock_getres().


According to some simplistic tests I did a while ago, two subsequent calls to clock_gettime() give times that differ by about 65 ns. This was 9.10 AMD64 with a 3 GHz CPU. So what is the "correct" timestamp going to be? I'd guess when the values are copied into the timespec struct, but presumably some non-zero portion of the ~65ns execution time still remains before the call returns.

Which, as such, is in no way a bad result per se. A nanosecond is a really really short time period. For instance, light in vacuum travels only about 30 cm during 1 ns.

Even this kind of accuracy is pretty new in Linux. It was enabled by the so-called "hrtimers" patches that were committed somewhere around the 2.6.21 kernel. Before that the "minimum measurable time"  for the realtime clock was limited to around 1 us.

---

### Post by mmix on 2010-01-17
RDTSC in asm

[http://en.wikipedia.org/wiki/Time_Stamp_Counter](http://en.wikipedia.org/wiki/Time_Stamp_Counter)

HTH

---

### Post by lostinxlation on 2010-01-17
> **mmix said:**
> RDTSC in asm
 
[http://en.wikipedia.org/wiki/Time_Stamp_Counter](http://en.wikipedia.org/wiki/Time_Stamp_Counter)
 
HTH
 
Well, if you read the article, it says RDTSC needs to be synced before execution(pre-sync). THat explains why the previous poster's experiment had 65ns gap(which is equivalent to 216 cycles) between 2 clock_gettime() executed back to back. Basically, this instruction has to wait for all the outstanding operations are done before issuance. By doing so, it gets accurate time stamp in the sense that it got the correct time stamp upon RDTSC's execution, but it may not be always what you are looking for, depending on the situation. 
 
For example, you got asm code like
 
add
div
sub
RDTSC
add
mult
 
Due to out-of-order execution, sub might be finished before div is completed(division takes very long) and RDTSC needs to wait for div to complete. In this case, the time stamp RDTSC gets is (the time stamp that div is completed)+(the time required for cpu to commit all the instructions and retire all the resources)+(the time required for RDTSC to reach the pipe stage to get the value from TIMER register). 
So, if you expect the time stamp that sub is completed, you maynot get it though you might get a time stamp close (within 100 - 300 cycles ?) to what you are looking for.
If you need the time stamp closer to sub's execution, you need to insert another sync instruction before sub instruction to isolate it from the instructions prior to that.

---

### Post by dwhitney67 on 2010-01-17
> **lostinxlation said:**
> ...
If you need the time stamp closer to sub's execution, you need to insert another sync instruction before sub instruction to isolate it from the instructions prior to that.

This may not necessarily yield any better results; one has to consider that there are other processes running on the system.  The process being monitored could (and probably will) be temporarily halted by the OS so as to allow another process its fair share of time to play with the CPU.

---

### Post by supershin on 2010-01-17
My lecturer once said "The api is your best friend". Download the C/C++ api and keep it handy.

---

### Post by Arndt on 2010-01-17
> **supershin said:**
> My lecturer once said "The api is your best friend". Download the C/C++ api and keep it handy.

What do you mean here? The API documentation?

---

### Post by supershin on 2010-01-18
I meant it as helpful advice. The TC already got numerous answers. I mean this [http://www.cppreference.com/wiki/]("http://www.cppreference.com/wiki/").

I think an interesting question is how does java support this feature, how does it 
implement getting the time in nanoseconds and can it be replicated in C?

---

