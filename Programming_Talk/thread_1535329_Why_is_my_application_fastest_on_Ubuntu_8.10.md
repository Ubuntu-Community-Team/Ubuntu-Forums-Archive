---
title: "Why is my application fastest on Ubuntu 8.10?"
date: 2010-07-20
forum: Programming Talk
---

### Post by freaklamarsch on 2010-07-20
Hi,

I have a C++ application that is generating Ethernet packets using the pcap library. I originally wrote it when Ubuntu 8.10 was up to date.

On Ubuntu 8.10 it was not a problem to get 1 Gbit/s out of it. In the meanwhile I have updated that machine and now it is hard to get 100 Mbit/s out of it.

I have checked it with several machines. The program runs fastest on Ubuntu 8.10 and slows down if I upgrade to any other version. I also tried to recompile it on the newer Ubuntus, also 64bit, and experimented with some gcc optimization flags, but I can not achieve the 1 Gbit/s on newer versionsof Ubuntu.

Using gprof there is no obvious reason for this slow down, the application seems to run slower over all. 

Does any one have an idea what was changed after 8.10 and what might cause this slow down in C++ applications?

Thanks,
FReAK

---

### Post by Zugzwang on 2010-07-21
I would suggest that you examine the changelog of the pcap library and check if they have changed anything in between the releases included in the corresponding Ubuntu distribution versions. Perhaps they fixed a bug in a way that decreases performance? Other than that, check where your program spends the most time on both platforms and see which part causes the slowdown.

---

### Post by freaklamarsch on 2010-07-21
Using the profiler, I could not see any strange change, the parts where time is spent seem to be on all Ubuntu versions the same.

In the changelogs of libpcap and for the Ubuntu package there is no change reported that would require to touch the packet sending part. But I think libpcap is not the problem.

According to gprof most time is spent on reading processor ticks (I try to do accurate timing) and looping through the std::deque I am using for sending.

I am using pthread to use the four cores of the CPU. Could it be that the scheduler has been changed between 8.10 and 9.04 

FReAK

---

### Post by MadCow108 on 2010-07-21
you could use oprofile which can profile the whole system including the kernel
maybe it helps finding the cause.

Also looking at some major kernel changes between 8.10 and 9.04 is probably a good idea.

---

### Post by freaklamarsch on 2010-07-23
Ok using oprofile I can see that 30% of the time is spent in libpcap. Strange that gprof did not show me this (or show that my function with the libpcap calls is using that much time).

I will try an old version of pcap next.

---

### Post by freaklamarsch on 2010-08-10
Hmm, using the same libpcap as it was used in 8.10 also did not speed up my program.

Is it possible that the default gcc flags have changed since 8.10?

How can I get a list of the default ggc flags to compare them between my Ubuntu versions?

---

### Post by MadCow108 on 2010-08-10
gcc -v file.c

ubuntu uses e.g. FORTIFY_SOURCE and the stack protector.
but they should not have a very high effect on performance

---

### Post by freaklamarsch on 2010-08-15
finally I found the problem and it is libpcap related.
In newer versions libpcap makes use of memory mapped sockets. Actually this should improve performance, but if I compile the current libpcap 1.1.1 on my Ubuntu 10.04 machine with mmap support removed, capture performance is back to the level as it was on 8.10.

---

