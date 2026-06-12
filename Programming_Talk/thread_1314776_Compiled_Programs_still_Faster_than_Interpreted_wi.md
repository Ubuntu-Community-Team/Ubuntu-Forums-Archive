---
title: "Compiled Programs still Faster than Interpreted with SSD?"
date: 2009-11-04
forum: Programming Talk
---

### Post by jr226 on 2009-11-04
It's my understanding that the main benefit of a precompiled code (FORTRAN, C etc) is the preallocation of memory, so it takes less time to find the values when the code is running.  

With SSD, where there are no physical components that have to search for data, will there still be a huge difference in run times between a compiled and interpreted language (IE MATLAB)?

---

### Post by Can+~ on 2009-11-04
(Assuming SSD as in Solid State Drive)

When you run an application (double click something), the necessary compiled code will be uploaded into memory, wrapped inside a Process Control Block (or PCB), becoming a process. Once there, it's all between memory and CPU, and subsequent interruptions to I/O devices. (And assuming it isn't thrown into Swap space)

Interpreted languages work with the "Interpreter" running already as an application on memory, and parsing data as it comes in.

So the only noticeable difference would be on startup (ie. when moving from long-term storage to memory) and subsequent calls to hard disk (eg. open(filename)...).

> It's my understanding that the main benefit of a precompiled code (FORTRAN, C etc) is the preallocation of memory, so it takes less time to find the values when the code is running. 

The main benefit, is not having an interpreter running (memory usage), and having to parse on real time (processor), that's the reason why most interpreted languages, actually compile things before, and use the interpreter to handle memory addressing (between many other things).

So to answer your question. A compiled program (and interpreter-compiled) would start up faster because it's loaded into memory faster. On the other hand, a truly interpreted (matlab interactive prompt, as you mentioned) won't notice any difference at all.

But the true benefit of SSD, is that, when the application is running (either compiled or interpreted), when doing a request to load a file, it will probably be faster.

---

### Post by samjh on 2009-11-04
> **jr226 said:**
> It's my understanding that the main benefit of a precompiled code (FORTRAN, C etc) is the preallocation of memory, so it takes less time to find the values when the code is running.  

With SSD, where there are no physical components that have to search for data, will there still be a huge difference in run times between a compiled and interpreted language (IE MATLAB)?
Advantages of static compilation involves more than just preallocation of memory.  Statically-compiled programs are already in executable form native (or compatible) to the hardware and operating system that runs it, and does not need to be parsed by an interpreter or undergo any intermediate processing to run (eg. just-in-time compilation).

Interpreted programs will generally be slower than statically-compiled programs except:
[list][*]Where a function or a component is called multiple times.  Just-in-time compilers used by some interpreted languages can optimise the relevant code so that it can be executed potentially faster than the equivalent statically-compiled code.
[*]Where the statically compiled program was compiled without optimisation options for a particular hardware platform.  For example, a program statically compiled for i386 will not be optimised on a Core 2 Duo.  But a JIT compiler (eg. as used in Java and .NET) can optimise the code better for the specific hardware it is being executed on.[/list]
There are probably others, but those two are just from the top of my head.

As for your question about whether SSDs will make a huge difference in run time between compiled and interpreted languages, the answer is no.  While SSDs generally benefit from faster start-up and access times, this won't affect a program's performance if there is little or no hard disk I/O involved.  Even if the program performs a lot of hard disk I/O, SSDs are not necessarily faster than conventional hard disks: many have lower bandwidth than conventional hard disks, have different bandwidths for read and write operations, or suffer from degraded performance due to age.

---

