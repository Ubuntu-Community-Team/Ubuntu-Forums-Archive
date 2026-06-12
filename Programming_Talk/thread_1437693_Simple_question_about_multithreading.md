---
title: "Simple question about multithreading"
date: 2010-03-24
forum: Programming Talk
---

### Post by Ender985 on 2010-03-24
Hey all!

I've been writing some rudimentary c++ console programs that I need to execute in parallel, so that each instance deals with a different input file. I am using a i7 920 processor (4 cores and ability to handle 8 threads due to this Hyperthreading technology), and my idea was to use it to its full potential. However, this is proving more difficult than I expected.

Originally I used to write in gedit and then compile using gcc, and I could call the same program various times and each instance would use its own separated thread. But as the projects grew bigger and more complex, I moved to a more decent programming environment, CodeBlocks. Now however, irregardless of if I call the multiple instances of the binary via CodeBlocks, or if I execute it via various shells, no matter how many different instances I spawn they all only use one single thread, queueing as if the system was a single-processor computer. This also applies to completely different binaries compiled via CodeBlocks, if I execute 4 copies of program A as well as 4 copies of different program B, they all still use only one core.

I suspected this had to do with the way CodeBlocks builds the binaries, so I tried compiling them with Eclipse, obtaining the very same results. Finally I tried to go back to compile them myself using gcc, but it now gives me tons of warnings and errors and refuses alltogether to produce a binary file (when both CodeBlocks and Eclipse proceed just fine). 

So, any advice on how to solve this problem?


Thanks a lot

---

### Post by Xyro on 2010-03-24
> I moved to a more decent programming environment, CodeBlocks

I think you were better off in gedit, personally. vi/vim would be a better choice yet ;)

From what you've said, I think you mean multiprocessing. Multithreading would be accomplished by using a thread lib like pthreads or Qpthreads, and calling a function as a thread multiple times within a single process. See here: [http://www.linuxselfhelp.com/HOWTO/C++Programming-HOWTO-18.html](http://www.linuxselfhelp.com/HOWTO/C++Programming-HOWTO-18.html)

Also, I am not sure I follow the problem. You say if you execute your program numerous times, the don't run in parallel? I find this hard to believe, as the Linux kernel is set up to manage and spread all processes on a system across all CPUs, as well as context switch between all running processes on any given CPU fairly. Are you using a standard distro with an off-the-shelf kernel build? How do you know this is what is happening?

---

### Post by MadCow108 on 2010-03-24
it should have nothing to do with how code blocks builds the binary.

Probably your program tries to access some blocking resource like the harddisk.
When one process access that resource all other processes have to wait until it is finished or interrupted by the kernel scheduler.
So the processes probably do run in parallel but only one does work while the others sleep until they can access the blocking resource.

---

### Post by Ender985 on 2010-03-24
Thanks for the fast answers. Yeah probably the correct word is mutiprocessing instead of multithreading, forgive my term confusion, I'm not an IT specialist. Anyway thanks for the link, I do call multiple instances of the same binary as a way to take advantage of the multiple core processor, but learning how to directly program multithreading would probably be the optimal solution.

The way I can tell this is happening is by starring at the ubuntu system monitor screen, in the 'resources' tab usually the 7 threads sit more or less iddle while only one peaks, the 'processes' tab shows only one of the multiple instances over 0% cpu usage, and the waiting channel status for the other ones makes me think that they are actually waiting instead of processing (even though I know nothing about waiting channels). I'm using a standard Karmic x86-64 desktop distro, 2.6.31-20-generic kernel, fully updated. The system is fairly able to use the different cores, since when I run other software on top of my programs they do use the other processors without a problem. However I've been spotting this problematic behavior since when I switched over to CodeBlocks, so I don't think it is Ubuntu's problem, but me doing something wrong. 

All my programs are reading one line at a time from different input files and writting output to a handful of other files, so maybe the problem is the parallel HDD access creating a large bottleneck. I never thought this could be an issue though, my machine is fairly new (months old) so the HDD should be fast, the acces bus is a SATA. I'm not trying to read and write to a thousand files though, I would be simultaneously using around 20 tops.

Maybe I should just return to gedit and try to make gcc compile, and see if there is any performance change at all. But I don't really understand how can one program anything semi-complex with the only help of a handful of colors on the text (no brace collapse, no class members or function parameters lists..?). Everything I know about programming is self-taught, so I lack a lot of this kind of 'basic' knowledge I'm afraid.


Thanks a lot

---

### Post by Xyro on 2010-03-24
Unless you are messing with the process priorities or cpu affinities in your software, there really isn't anything in your code that would cause this behavior (that I can think of), besides being blocked by some I/O. Either way, your choice if IDE likely has nothing to do with this.

It doesn't matter how new your HDs are, they will never keep up with your CPU. I think that MadCow108 is correct.

> But I don't really understand how can one program anything semi-complex with the only help of a handful of colors on the text (no brace collapse, no class members or function parameters lists..?)

Ack! According to polls on this site, many Linux developers use vi/vim ;) Steep learning curve, but much more efficient in the long term. IDE = wasted time with hand on mouse.

---

### Post by MadCow108 on 2010-03-24
even fast harddisks are incredible slow compared to the cpu or the ram
ram has bandwidth of the order of gigabyte whereas disks have something in the megabytes, the latency of harddisks lies in the microseconds area, of ram in nanoseconds.
CPU caches are even a few orders of magnitude faster.

how often are your programs reading writing to the disk in the processes lifetime?
use the command iostat to check how much your processes are waiting for io.
If this is really the problem, try to reduce the writes to a few big blocks instead of many small ones.


changing back to gedit will not help you. code blocks probably also uses the gcc compiler and it for sure does not introduce some interprocess locks into your program for fun.
I would always use an IDE for big projects. I only use smaller editors like vim for very small projects.
There are better editors for coding than gedit. vim or emacs would be two examples. But they need similar if not longer time to learn than the most complex IDE.

---

### Post by Ender985 on 2010-03-26
I'm used to write a 'file_out <<' for each single line of output I need. And each of my scripts can easily produce several milion lines of output, so reading your answers probably this is causing the bottleneck. I wasn't even aware that writting to a file could be that much of a drag. So do you think that if I reduce the number of cout calls, and write large buffers instead of line to line, the speed should improve? I'll give it a try.

Thanks again!

---

### Post by MadCow108 on 2010-03-26
it may be enough just to replace endl with '\n' as endl also flushes the buffer the stream uses internally.

This is usually good when using a line buffered stream like stdout, but not so nice when using filestreams where the optimal buffer size is mostly around 4096KB, much larger then usual text lines.

If you aren't using endl or flushing the stream to often there is not much you can do except compressing your output somehow and only then save it to disk.
On very input/output heavy programs even very CPU expensive compression may lead to significant performance increase due to the reduced disk IO

---

