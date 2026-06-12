---
title: "Compiling with distcc on dual core processor?"
date: 2006-04-20
forum: Programming Talk
---

### Post by hajk on 2006-04-20
As I understand it, a single executable will always run on a single core, although the job may be handed from one core to another at regular intervals. When I run a large optimization, for example, one of the cores of my dual core Opteron processor is 100% busy, while the other one is hardly busy at all -- so my other work doesn't have to wait until the optimization has completed.

But how can I use both cores simultaneously when compiling a great many different routines to object code? Is it possible to use distcc for that? What differences are there from using distcc on physically separated computers?

I would appreciate some help on this.

---

### Post by nagilum on 2006-04-20
Distcc is AFAIK only for use with multiple computers in a network, i.e. it does all the handling of copying source code / compiled files from and to the machines. To compile source on multiple processors you don't need any special software, make can handle this. Just specify the -j argument with the number of processors, e.g. "make -j 2" for your dual core.

---

### Post by engla on 2006-04-20
[QUOTE=hajk]As I understand it, a single executable will always run on a single core, although the job may be handed from one core to another at regular intervals.[/QUOTE]
Not really. Execution is parted into **threads**, where the simplest case is one thread per process. This is the simplest thing to develop and run in many ways, and gcc is probably not threaded since it's simple to provide multiple threads per build job on the higher level -- with more processes. Other tools, like GIMP or firefox or  other heavy data processors typically have many threads per process.

---

### Post by hajk on 2006-04-20
OK, I stand to be corrected on executing threads... 

I've tried to use make with the -j 2 or -j 4 option, doesn't seem to make any difference when compiling, for example, a Fortran "donlp2" optimization job: System Monitor shows just one of the cores shooting up to 100% for a while, the other staying at 4% or so.

And yes, I used to compile Gentoo on several of my networked computers with distcc, so it was just a thought whether this could or couldn't also be done across different cores...

---

### Post by nagilum on 2006-04-21
So far I used make -j only on a P4 with Hyperthreading. There it worked fine, both processors were busy and the source compiled about 20-30% faster. Maybe it's different with dual core processors, never worked with one of those.

---

### Post by LordHunter317 on 2006-04-21
[QUOTE=hajk]As I understand it, a single executable will always run on a single core,[/quote]No.  

> although the job may be handed from one core to another at regular intervals. Not if the kernel can avoid it.

> But how can I use both cores simultaneously when compiling a great many different routines to object code?A correctly written makefile that supports paralleization.

>  Is it possible to use distcc for that? What differences are there from using distcc on physically separated computers?Yes, but that's killing a fly with an elephant gun, and still requires what I said above.

[quote=engla]This is the simplest thing to develop and run in many ways, and gcc is probably not threaded since it's simple to provide multiple threads per build job on the higher level -- with more processes.[/quote]It's not multithreaded because there would be no gain for GCC.  Optimization of code can't really be parallelized and everything else is strongly I/O bound, frequently on other processes.

[quote=nailgum] 	So far I used make -j only on a P4 with Hyperthreading. There it worked fine, both processors were busy and the source compiled about 20-30% faster. Maybe it's different with dual core processors, never worked with one of those.[/quote]No, why would it be?  The kernel sees both in the same manner.

You won't see any single process in a compiler toolchain use more than one core/CPU/whatever at a time.  What make -j does is run multiple instances of the toolchain on multiple files at once.  So if you have 3 .f files, make -j3 will compile all of them to .o simultaneously, assuming you have rules written that allow for that.  It'll then run a single process when all of those complete that combines them into the final executable.

Obviously, the way your makefile is written influences this greatly.  There are books and many tutorials on google about how to take advantage of this, so doing some research should help here.

---

