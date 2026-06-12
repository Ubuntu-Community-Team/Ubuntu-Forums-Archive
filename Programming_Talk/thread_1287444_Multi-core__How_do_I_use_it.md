---
title: "Multi-core : How do I use it ?"
date: 2009-10-10
forum: Programming Talk
---

### Post by ProgramErgoSum on 2009-10-10
Hi,
As a programmer, do I have control on how code is executed on what processor ? By extension, if I ran a downloaded software say, Apache Tomcat, can I (as an administrator deploying code) have control on how the code execution is (or not) distributed across processors ? Finally, is running a 32 bit application on a 64 bit machine under-utilization of the hardware ?

I did come across the concepts of [Embarassingly parallel problem]("http://en.wikipedia.org/wiki/Embarrassingly_parallel") and [Amdahl's law]("http://en.wikipedia.org/wiki/Amdahl%27s_law"). 

I have a desktop computer running AMD Phenom quad-core processor, 64-bit. I use it mainly to play games to do some video-editing once in a while. This is all in Windows. I am now thinking of dual booting with Linux for some programming (not in any particular language) practice.

---

### Post by napsy on 2009-10-10
> **ProgramErgoSum said:**
> Hi,
As a programmer, do I have control on how code is executed on what processor ? 


Yes you do but it's better to leave scheduling to the system.
> 
By extension, if I ran a downloaded software say, Apache Tomcat, can I (as an administrator deploying code) have control on how the code execution is (or not) distributed across processors ? 


You can specify the CPU on which the process should run but again it's better to leave that to the scheduler unless you have good reasons.
Parallel execution of the process is dependent on the implementation. Which means if the program isn't specially written to be distributed between CPUs, it won't. Parallelization is a real programming problem because most languages that the industry uses are not specially designed for parallel computing. There are some extensions to the languages but it remains an open issue.

> 
Finally, is running a 32 bit application on a 64 bit machine under-utilization of the hardware ?


Yes it is since the applications can address only 2^32 of memory and use 32-bit bus transfers between CPU and memory.

> 
I did come across the concepts of [Embarassingly parallel problem]("http://en.wikipedia.org/wiki/Embarrassingly_parallel") and [Amdahl's law]("http://en.wikipedia.org/wiki/Amdahl%27s_law"). 


I have a desktop computer running AMD Phenom quad-core processor, 64-bit. I use it mainly to play games to do some video-editing once in a while. This is all in Windows. I am now thinking of dual booting with Linux for some programming (not in any particular language) practice.

Amdahl's law tells you that the overall performance is dependent on the parts of your computer where you didn't do any optimizations. So you should focus on those parts which represent a bottleneck on your system.

---

### Post by ProgramErgoSum on 2009-10-10
> Parallelization is a real programming problem because most languages that the industry uses are not specially designed for parallel computing.
Thanks for confirming my hunch !

After some searching around, I came across [taskset]("http://www.cyberciti.biz/faq/taskset-cpu-affinity-command/"). Perhaps, you were referring to this when talking about controlling the execution on a core ?

---

### Post by cholericfun on 2009-10-10
openmp and mpi for c and fortran,

not sure bout other langs

---

### Post by mihnea.radulescu on 2009-10-10
> **napsy said:**
> Parallel execution of the process is dependent on the implementation. Which means if the program isn't specially written to be distributed between CPUs, it won't.
As long as your application spawns more than one process, or a single process containing more than one thread, the OS dispatcher may schedule your threads to run simultaneously on the processor cores you have available. You need not think in terms of how the OS maps your threads to physical processors besides your application scaling with the number of processor cores available, if necessary (see threads, thread pools, etc.).

> **napsy said:**
> Parallelization is a real programming problem because most languages that the industry uses are not specially designed for parallel computing. There are some extensions to the languages but it remains an open issue.
Most of the languages libraries have made parallelization available in the last 20 or so years, through the Process and Thread primitives. The fact that higher level parallelization abstractions (say, parallel for) are missing and largely available in 3rd-party libraries or language extensions is an entirely different matter.

> **napsy said:**
> Amdahl's law tells you that the overall performance is dependent on the parts of your computer where you didn't do any optimizations. So you should focus on those parts which represent a bottleneck on your system.
Amdahl's law says that the maximum achievable speed of an application containing parallel code is strictly limited by the sequential (non-parallelizable) portions of its code. In other words, you will not achieve a linear increase in application speed by increasing the number of processor cores in a program that is highly sequential. As an example, it doesn't really matter if you have a 16-core CPU if the target application is a compiler (almost completely sequential by nature).

---

