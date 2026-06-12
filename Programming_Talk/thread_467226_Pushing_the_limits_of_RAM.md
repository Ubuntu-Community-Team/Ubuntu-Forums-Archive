---
title: "Pushing the limits of RAM"
date: 2007-06-07
forum: Programming Talk
---

### Post by Soybean on 2007-06-07
I'm working on a scientific simulation program that runs on a small cluster of computers (program is in C++, computers are running Dapper server). It's been going pretty well so far, but we've been working with relatively small data sets. Now we're looking to find out just how much our simulation can handle.

I think I understand the issues reasonably well on a "theoretical overview" sort of level, but I've never actually been in a situation before where I was (intentionally) going to fill up all available RAM. Does anyone have any advice?

Some of the things that I'm most concerned about:
1) Is there an easy way for my program to check how much memory it has allocated, or more importantly, how much is still available to it? Or do I just have to wait for an allocation to fail?
2) Thrashing. My understanding is that Linux will happily allocate more memory than it actually has available, because it's got all that swap space. But when active processes are collectively using more RAM than is available, everything can grind to a halt as the system does nothing but swap. Is there a way to detect this condition? I'd prefer it if I could detect it before it happened, but I'd be ok if there was just a way to auto-kill my program if it got into this sort of state.
3) Problems I don't even know about. Like I said, I've just got a theoretical overview of the issues that might come up when pushing a computer to its limits. That is, it was covered in a couple of my university courses. I find that the real world tends to work a bit differently than the more theory-based university courses, so I'm worried that things might go wrong that I've never heard of.

So... is there anyone out there who has some experience with big programs and can give me some pointers? That's 'pointers' as in 'tips or advice', not C pointers -- I've got plenty of those. 8-[

---

### Post by Ramses de Norre on 2007-06-07
I once managed to fill all my RAM and swap and everything stalled for like half a minute, then X crashed and took the application with him (or the other way around) and I could just log in again.
So it seems like the linux kernel can handle these situations, I think it uses a process called oom-killer which is the "out of memory process killer" for this.
And this is the end of my knowledge about this :)

---

### Post by escapee on 2007-06-07
My advice - let a Microsoft product run for a day or so, that should fill up the memory :)

What methods are you using now to drain the memory?

I'm no pro on utilizing other API's yet, but if there's away to pull the system's remaining memory info into the program, I would use that. 

Here's an idea in a crude form:

I'd have the program display the initial amount of RAM, then begin the cycles by starting a timer, create a set number of new pointers, then end the timer and print the timer results and remaining amount of RAM.  Rinse and repeat until it's full.  Then just keep track of how many cycles executed with a long counter and display at the end of each cycle as well.  When you run of out memory (assuming it doesn't crash) set a check to notify you and end the program once that point is reached.

The timers are there so you can see if the performance begins to hinder as the memory continues to get allocated.  


Sorry I just gave a crappy overview and didn't check grammar/spelling, but I'm sitting at work while I type this :)

Hope this helped out some.

---

### Post by meatpan on 2007-06-07
Some clustering tools, like SGE, Condor, and PBS, have useful built-in utilities that allow you to analyze the resource consumption of distributed processes.   Also, if configured, these tools can automatically assess the load on a given machine and allocate new jobs accordingly.  I currently use SGE, and it seems to do a fine job. 

If you want some fine-grained control of resource limits, take a look at the ulimit command.  This command allows you to specify 'soft' resource caps, such as cpu time and memory.

Is it possible to obtain a rough estimate of the memory requirements prior to running your program?  Sometimes you can do a 'quick & dirty' estimate by looking at the size of the input domain, and the associated algorithmic requirements.   This type of check can save a lot of headaches.  In some situations you can anticipate a resource problem and divide up the domain into multiple computing task.  

You can also approach this problem from an empirical perspective.  Try running your job a few times and seeing how much memory is required for various sizes of input.  Predict your future demand according to the patterns you observed.

---

### Post by Soybean on 2007-06-08
Thanks guys, this is great! :)

I wasn't aware of "oom killer." It's good to know that if I totally screw this up, the kernel has a way to fix it. I had been anticipating frequent trips to the server room to power-cycle all the nodes, but it sounds like they may be able to take care of themselves.

escapee and meatpan both gave me the good idea of just trying it with slowly increasing loads and some benchmarking. This probably should've been pretty obvious, but I had some sort of mental block where I could only conceive of two possibilities: 1) keep the data small, or 2) throw in the largest amount of data imaginable, and try to measure/record the point where things start to go horribly wrong. Somehow, "incrementally larger data sets" never crossed my mind. #-o

I looked up ulimit (and the related limits.conf), and that whole system looks pretty helpful too. I knew Linux had some quota settings, but I thought it mostly applied to disk use in a multi-user system, so I hadn't ever really looked at it. Being able to limit memory use or CPU time should be pretty handy, especially in the testing stage.

As for the clustering tools and dividing things up, I'm actually pretty comfortable with a variety of ways of dealing with resource problems once I've identified them. It's just that there are tradeoffs, of course. For example, if you can fit everything related to a particular data set into RAM on one system, it's going to go faster than if you split it up. Where I'm feeling a little out of my depth is in determining whether I can fit everything in RAM or not. Like, I've got 4Gb of physical memory. To simplify, let's say that's exactly 4 billion bytes. An integer is 4 bytes. Does that mean I can allocate an array of 1 billion integers? Well, probably not, at least not without some serious performance degradation, right? Well... how many integers *can* I safely allocate? The answer I seem to be getting is, "just try it and find out!" 

So, thank you all, I'm feeling more comfortable with the whole thing now. :) If anyone has any more ideas, though, please chime in! Even if they seem obvious, because it seems like those are the ideas I have the hardest time with. ;)

---

### Post by meatpan on 2007-06-08
Sounds good, Soybean. You definetely have the right attitude, too ;)

High performance computing can be a lot of fun and very rewarding.   If you learn any neat tricks about performance monitoring or resource optimization during your experiments, let us know!

---

### Post by Mr. C. on 2007-06-08
32-bit linux has process size limits; a process can not grow beyond these limits.

The virtual memory system does a fine job managing competing processes, but as has been mentioned, when you reach the limits of the system, the kernel will kill a process to free more memory.  You certainly want to ensure you have enough swap space to cover your simulation program.

Ps or top will show you the resident set size of the process - this will give you an idea of how much of your process is actually resident in ram.  Size is the total size of VM being used.

MrC

---

### Post by CptPicard on 2007-06-11
If the machines are dedicated to your simulation, why not turn swap off completely? If I were you, I wouldn't bother with swap at all and would prefer a good hard out of memory condition to the performance-destroying "soft landing" of swapping, which you might be seeing earlier than neccessary anyway...

Unless of course you're running a simulation on such a huge dataset that you simply can't fit it into RAM, but in that case I might look into coding my own filesystem access and buffering instead of using the OS as a middleman.

---

### Post by Mr. C. on 2007-06-12
Disabling swap is not a very good idea.  I doubt the OP wants to experience random daemon and application terminations due to lack of virtual memory.  The Unix/Linux VM systems are very efficient.

---

