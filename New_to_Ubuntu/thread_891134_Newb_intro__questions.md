---
title: "Newb intro / questions"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by aravel on 2008-08-15
Hi everyone!

I have just barely joined the forum community but this place has been a huge help to me for quite some time now.  I have just installed Ubuntu 8.04 and I like it a lot so far.  I have a couple of questions though that maybe some of you can answer:

1) I have an Intel quad core processor, does Ubuntu utilize the quad core efficiently?  Like I guess what I am asking is that I know that windows xp doesn't unless you have a graphics card that requires it then it starts to use it.  Does that make sense?

2) I currently have 2 gigs of memory, if I upgrade to 4 gigs will ubuntu recognize that much?

Any help would be appreciated!  Thanks!

---

### Post by Crafty Kisses on 2008-08-15
Yes usually Ubuntu detects hardware changes very good, so I don't see why you would have a problem.

---

### Post by cariboo on 2008-08-15
The answer to both your question is, The generic kernel is compiled with smp.

Quote from Wikipedia

> In computing, symmetric multiprocessing or SMP involves a multiprocessor computer-architecture where two or more identical processors can connect to a single shared main memory. Most common multiprocessor systems today use an SMP architecture. In case of multi-core processors, the SMP architecture applies to the cores, treating them as separate processors.

SMP systems allow any processor to work on any task no matter where the data for that task are located in memory; with proper operating system support, SMP systems can easily move tasks between processors to balance the workload efficiently.

Linux should see your upgraded ram, if not you may have to change a setting or two in your bios.

Jim

---

### Post by DGortze380 on 2008-08-15
> **aravel said:**
> Hi everyone!

I have just barely joined the forum community but this place has been a huge help to me for quite some time now.  I have just installed Ubuntu 8.04 and I like it a lot so far.  I have a couple of questions though that maybe some of you can answer:

1) I have an Intel quad core processor, does Ubuntu utilize the quad core efficiently?  Like I guess what I am asking is that I know that windows xp doesn't unless you have a graphics card that requires it then it starts to use it.  Does that make sense?

2) I currently have 2 gigs of memory, if I upgrade to 4 gigs will ubuntu recognize that much?

Any help would be appreciated!  Thanks!

1) Yes

2) Anything over 3GB will only be utilized on a 64bit OS.

---

