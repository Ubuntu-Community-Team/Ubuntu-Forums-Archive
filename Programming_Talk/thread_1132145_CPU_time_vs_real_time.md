---
title: "CPU time vs real time"
date: 2009-04-21
forum: Programming Talk
---

### Post by geo909 on 2009-04-21
Hello all,

I was wondering how one can convert CPU time to approximate real time, depending to his machine, for example. Even vaguely, but just to get the rough idea. 

Thanks in advance..

EDIT: 
To be more specific: I'm using Maple, a computer algebra system. The "time" function shows the running CPU time in "seconds". So, for example, what does that mean? This is what the corresponding help page says:

> 
The time command returns the total CPU time used since the start of the Maple session. The units are in seconds and the value returned is a floating-point number.



---

### Post by cabalas on 2009-04-21
> **geo909 said:**
> To be more specific: I'm using Maple, a computer algebra system. The "time" function shows the running CPU time in "seconds". So, for example, what does that mean? This is what the corresponding help page says:

Due to the way multi-tasking operating systems work (on a single core machine) there is only ever one process running at once, for a minuscule amount of time - fast enough so to us it looks like there are multiple applications running at once.  That is what CPU time is, the amount of time the application is actually using the CPU rather than the total time that the application has been running.

Translating from CPU time to real time can be difficult as it depends on many different factors such as:

[LIST]
[*]The process scheduler that the kernel is using.
[*]How many other processes are running.
[*]The priority of all the process running
[*]The time slice given to each process (and whether this depends on priority).
[/LIST]

On thing that might be worth a look is the source for time (if you haven't come across it run 'man time' in a terminal).

---

### Post by geo909 on 2009-04-22
Thanks for the reply!

I think it is quite clear to me now..

---

