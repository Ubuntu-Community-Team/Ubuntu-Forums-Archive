---
title: "Running faster on new SMP processors by compiling applications from source"
date: 2006-07-10
forum: Other OS Talk
---

### Post by jerinjoy on 2006-07-10
A friend of mine bought one of those new Dual Core laptops. I got him to install the 686-smp version of ubuntu and there is a marked difference from the 386 kernel. 
I was thinking about a few things.
386 architecture has the standard set of assembly level instructions used by all pre-Pentium II class of machines. The newer architectures support these instructions and then some more. In some cases a few instructions are deprecated and the hardware traps to software to emulate these instructions which is slow.
This would mean that it is better to compile all your programs from source rather than using precompiled packages. This would allow the application to use the newer instruction set and better use the hardware. This is evident from swiftfox which is precompiled by someone for a particular type of machine (386, 686, amd-k7 etc..) and runs faster than firefox. My first question is does gcc (4.0.0+) compile programs to utilize the latest hardware?
Another consideration is threading and parallelism in the existing software. With the newer hardware going multicore with multiple threads on each core, its useless if the software is not threaded/parallel.
([See UltraSPARC T1]("http://www.sun.com/processors/UltraSPARC-T1/")) If the software is threaded, does the latest version of gcc allow for such parallelism? It makes sense to get all existing software to support multithreading if they don't do so already.

Just my two cents.

---

### Post by brentoboy on 2006-07-10
software doesnt use multithreading unless the developer built it to.

compilers dont compile code to be "better" than the original application, *unless* you tweek the compile options by hand...  this thread is currently on a quest to do exactly what you are talking about...


[http://ubuntuforums.org/showthread.php?t=208595](http://ubuntuforums.org/showthread.php?t=208595)

---

