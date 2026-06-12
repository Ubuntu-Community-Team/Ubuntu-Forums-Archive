---
title: "For all those people who still think Java is slow"
date: 2007-03-21
forum: Programming Talk
---

### Post by munckfish on 2007-03-21
I found this article about Java today. It's an interview with a guy from Sun called Brian Goetz. He makes some pretty interesting observations about C and Java and their relative speed/performance. Particularly he says Java is now much faster than C at allocating and deallocating objects: "the cost now of allocating an object in the Java language is less expensive than in C by a factor of four or five"

[http://java.sun.com/developer/technicalArticles/Interviews/goetz_qa.html](http://java.sun.com/developer/technicalArticles/Interviews/goetz_qa.html)

Of couse I realise this guy is on Sun's payroll. :D

Cheers

---

### Post by Tomosaur on 2007-03-21
It's all pretty much redundant really. As Goetz himself pointed out - Java relies much more heavily on the environment it is being run on. While C will generally perform 'well' on any platform it is capable - Java relies on the environment not throwing anything in its way.

In **theory** Java is comparable to C performance-wise, but in practice it may or may not be. On Linux it is unlikely to be a problem, but for a platform such as Windows, for example, where the environment tends to get more clogged down and chuggy, then Java may experience a performance hit against C.

---

### Post by angustia on 2007-03-21
some time ago i was helping a friend to develop a simple multithreaded daemon in plain C.  In some part of this daemon many threads allocates a block of memory for themselves and later they free it. There was a bug in the code that made one thread to write out of the bound of its allocated memory block and write in the end of the other block of another thread. The error was not detected until the victim thread frees its block.

I couldn't get info about that feature but i suppose the libc memory manager put some 'canaries' before and after each memory block that malloc allocates, and these canaries was tested when the blocks where freed.  I'm not sure but i suppose those canaries must be 4 bytes long integers with a random number, so any malloc you make will be at least 8 byte bigger than you spect.

what i'm try to say: 

most of C speed is due the fact it creates code with most of the checks out. This lack of checks has forced to implements indirect ways to prevent overflows: the first one is hardware memory segmentation, and others like stack guards and malloc guards. These indirect forced checks are applied to any program the computer runs, independently if deserved or not. 

Also, most O.S. are designed to run primaryly C (or ASM) programs, and does some facilities for them: when two C programs uses the same shared library, the O.S. only load the .so file once. When two java programs uses the same .class file, at least the file is loaded once, but its compilation (JIT) has to be done twice and stored twice in memory.

At the end: 

to make a fair comparison between C and java (or any other 'compiled' higher level language), java must be run on a processor without memory protections and a libc without those consistency checks, because those checks are already done by the language itself.

(i do agree that java uses pornographic ammounts of memory to run)

excuse my english.

---

### Post by Wybiral on 2007-03-21
Actually, as far as memory allocation goes, you aren't stuff with malloc and free in C, those are just the standards. I've actually written faster memory allocation/freeing routines then malloc/free in C (it was just buffered memory but it ran sometimes at 2-3 times the speed of malloc/free).

But you can't just write your own memory management in Java.

Also, I posted these quotes on another thread, but I don't remember where so I'm going to post them here. These are from John Carmack (the guy who wrote the game engine for wolf3d, doom, and quake... A legend in the game industry where performance is of utter importance). He was talking about developing games for mobile phones and why he wasn't happy to work with Java...

> ...The biggest problem is that Java is really slow. On a pure cpu / memory / display / communications level, most modern cell phones should be considerably better gaming platforms than a Game Boy Advanced. With Java, on most phones you are left with about the CPU power of an original 4.77 mhz IBM PC, and lousy control over everything.

I spent a fair amount of time looking at java byte code disassembly while optimizing my little rendering engine. This is interesting fun like any other optimization problem, but it alternates with a bleak knowledge that even the most inspired java code is going to be a fraction the performance of pedestrian native C code.

Even compiled to completely native code, Java semantic requirements like range checking on every array access hobble it. One of the phones (Motorola i730) has an option that does some load time compiling to improve performance, which does help a lot, but you have no idea what it is doing, and innocuous code changes can cause the compilable heuristic to fail.

Write-once-run-anywhere. Ha. Hahahahaha. We are only testing on four platforms right now, and not a single pair has the exact same quirks. All the commercial games are tweaked and compiled individually for each (often 100+) platform. Portability is not a justification for the awful performance.

---

### Post by munckfish on 2007-03-21
I guess as usual, it's just about using the right tool for the job. You either want to ignore memory management and just concentrate on the features your producing. Or if you want that extra level of control you choose to use C or Assembler.

In fact although I started out programming in Java I love C. I picked up the K&R book recently and I've loved every moment of it so far. My inspiration is to be able to (eventually) write or improve drivers for odd bits of hardware that still don't run right with Linux yet.

---

### Post by Wybiral on 2007-03-21
> **munckfish said:**
> My inspiration is to be able to (eventually) write or improve drivers for odd bits of hardware that still don't run right with Linux yet.

Thats awesome, I really think that's one of the most productive things that can be done for the Linux community right now. It's hard for people to use Linux when their hardware isn't supported!

---

