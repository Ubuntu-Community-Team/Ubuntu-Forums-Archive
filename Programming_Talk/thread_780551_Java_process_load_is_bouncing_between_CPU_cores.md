---
title: "Java process load is bouncing between CPU cores?"
date: 2008-05-03
forum: Programming Talk
---

### Post by kavon89 on 2008-05-03
I've never seen this happen on Windows. I'm writing a program to accurately calculate square roots of numbers in Java. While under load, the cores keep pushing the work between each other, here is a screenshot:

[http://i26.tinypic.com/2hzhgte.jpg](http://i26.tinypic.com/2hzhgte.jpg)

I guess this is because I haven't made use of threads yet? The process is only using 48% of my total CPU so I guess it's just passing around 1 thread between cores? Why would it do this?

---

### Post by Quikee on 2008-05-03
> **kavon89 said:**
> I've never seen this happen on Windows. I'm writing a program to accurately calculate square roots of numbers in Java. While under load, the cores keep pushing the work between each other, here is a screenshot:

[http://i26.tinypic.com/2hzhgte.jpg](http://i26.tinypic.com/2hzhgte.jpg)

I guess this is because I haven't made use of threads yet? The process is only using 48% of my total CPU so I guess it's just passing around 1 thread between cores? Why would it do this?

Actually this is normal (happens in windows and other OS also) as it is related to how process schedulers work. To achieve virtual multitasking/multiprocessing there needs to be a queue of processes, which are feeded to the CPU only for a limited amount of time (time slice). For example CPU cycles through processes and works on each one for example 1000 ns. 
Now in case you have 2 (or more) processors both take processes of the queue and work on them for a certain amount of time, so it can happen that the same process can one time be processed by CPU0 and another time by CPU1 (or CPUn) - from the view of the process this doesn't matter.

---

### Post by kavon89 on 2008-05-03
Ok thanks, I thought it was weird/inefficient of it doing this.

---

### Post by evymetal on 2008-05-04
If you renice the process to something appropriate (a strong negative number) then the process will tend to stick to a singe core.

- also on most systems I've used, 48% in top will correspond to 48% of a single CPU or core. I guess it's having to wait on something else (RAM or paging).

---

### Post by stroyan on 2008-05-04
When you use java there is always threading involved.
Even if you don't explicitly thread the JVM will use threads
for activities like garbage collection and input event handling.
You can get java to print a list of threads and their states by
typing <ctrl>-\ at the terminal that started java, (or otherwise
sending SIGQUIT to the java process).

The linux kernel is usually good about keeping a particular
thread on the same CPU as long as that CPU remains available.
That helps performance by maximizing reuse of cache lines that
can only be accessed by one CPU/core.

You may be seeing java running a garbage collection algorithm.
The CPU time in the shorter periods of the graph would be a GC thread.
That can be a substantial portion of the jvm activity if your
code is creating and releasing a lot of objects.  That used to
be a big performance problem for java.  Recent versions are much
improved by using generational garbage collection techniques to
optimize handling of short-lived objects.  But it is still worth
thinking about.  You could google for 'java heap churn' to learn more.
You might start at
[http://www.ibm.com/developerworks/java/library/j-perf05214.html](http://www.ibm.com/developerworks/java/library/j-perf05214.html)
or
[http://www.javaworld.com/javaworld/jw-11-1999/jw-11-performance.html](http://www.javaworld.com/javaworld/jw-11-1999/jw-11-performance.html)

P.S.
  The ubuntu top command actually shows the summary cpu usage as 50% for
one fully loaded CPU on a two CPU or two core system.  You can see the
cpu utilization of individual CPUs by press '1' when running top.

---

### Post by kavon89 on 2008-05-04
I'm working on getting it multi threaded. Running into a probably common error with synchronizing the threads/controlling them. Hopefully the Java forums help me out on this, if not I might try here. :D

---

