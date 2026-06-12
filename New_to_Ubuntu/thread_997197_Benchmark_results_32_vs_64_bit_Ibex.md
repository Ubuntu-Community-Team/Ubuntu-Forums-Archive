---
title: "Benchmark results 32 vs 64 bit Ibex"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by CaponeSA on 2008-11-29
Hi all.  I've been Window$ free now for 2 years (sounds like a Windows anonymous meeting!) and have converted quite a number of people to Linux. I have been using Kubuntu up to 8.04, but KDE 4 is still so buggy that I moved to Ubuntu.

Since my desktop (core 2 due 2.4GHz + 2Gb ram) supports 64 bit, I've always been tempted to try it, but I was under the impression that 64 bit Linux is for the real clever guys, with lots of memory since it's difficult to get 32 bit apps installed and it chews up a lot of memory and all that ... I however decided to try 64 bit.  I installed Ubuntu Ibex 32 bit and 64 bit for dual booting on the same machine, same hard drive and also using exactly the same swap partition - so everything should be compared on a 1 to 1 basis.

Well ... 64 bit ROCKS!  It's noticeably faster in the general desktop activity (although I found that the KDE desktop is still much more responsive than Gnome - will try KDE 4.5 again). I had no problem installing 32 bit apps (using getlibs) and everything works out of the box, just like the 32 bit version (even my Nvidia driver was installed automatically)

Now, the big test, is 64 bit really worth it.  I first used hardinfo to do a few benchmarks (both 32 and 64 bit Ibex installations are up to date and no tweaking done)

1 -  CPU Zlib - 32 bit =  19 570.68 KiB/s  == 64 bit = 41 535.58 KiB/s
2 -  CPU Fibonacci - 32 bit =  3.7 s  == 64 bit = 4.01s
3 -  CPU MD5 - 32 bit =  78.92 MiB/s  == 64 bit = 58.8 MiB/s
4 -  CPU SHA1 - 32 bit =  90.99 MiB/s  == 64 bit = 90.89 MiB/s
5 -  CPU Blowfish - 32 bit =  13.83 s  == 64 bit = 14.069 s
6 -  FPU Raytracing - 32 bit =  18.71 s  == 64 bit = 8.84 s

So, although there are some places that 32 bit is quicker than 64 bit, the 64 bit results are VERY impressive.  But how about a real word test?

I did a 5 GB mpeg video grab (Hauppage 150) and used AVIdemux to convert to DVD.  Once again, same machine, same hard drive, etc.

1 - Indexing the mpg - 32 bit = 1m 55s  == 64 bit = 1m 55s
2 - Convert to DVD - 32 bit = 44m (69.8 frames/s) ==  64 bit = 38m (77.5 frames/s)

I think the hard drive throughput speed is the determining factor for indexing, but by simply using a 64 bit distro, the DVD encoding is 11% faster!

All fine but how much memory will I loose if I use a 64 bit distro compared to 32 bit?  After a clean boot, I looked at the application memory usage (all results are with the latest updates for Ibex):

1 - Kubuntu - 32 bit = 16%   ==  64 bit = 15%
2 - Ubuntu - 32 bit = 12%   ==  64 bit = 12%
3 - Xubuntu - 32 bit = 12%   ==  64 bit = not tested

mmm, no difference between 32 and 64 bit memory usage and funny enough, Xubuntu uses the same amount of memory after a clean start as Ubuntu!

Now, how about with some apps running?  I repeated the test on Ubuntu with the following apps running: Krusader, Krusader root, Peazip, Adobe Acrobat, Konqueror and Open Office Writer 3.  I purposely loaded some KDE apps since I assume that they load a number of extra KDE libs which should push up the memory usage.  The results for % application memory used:

Ubuntu 8.10 - 32 bit = 20%   ==  64 bit = 20%

Thus, to make a long story short, in my opinion,_** if your processor supports 64 bit, us it, don't even think twice!**_  You will have a noticeably much snappier desktop, no problem in installing 32 bit apps, have a much faster processing power and no memory sacrifice - we'll that's my experience.

---

### Post by Xiong Chiamiov on 2008-11-29
The memory usage people talk about is hard drive space, rather than virtual memory.  This is due to the fact that each line of binary is twice as long (64-bits, rather than 32).

The thing that holds most people back from 64-bit (including myself) is the terrible support for Java, Flash and Wine.  For servers, it is fine, but most people use those daily on their desktop machines, and getting the 32-bit versions of them installed on a 64-bit machine is usually more of a pain than it's worth.

---

### Post by CaponeSA on 2008-12-01
It's the first time that I hear about reference to increased _hard drive_ space due to  a 64 bit installation vs 32 bit (anyway, even if this is true, what is a gig or two more on the large drives we have today?). 

Before I switched to 64 bit, I studied the Ubuntu 64 bit forums and people definitely talk about "*One disadvantage of 64-bit architectures compared to 32-bit architectures is that the same data will occupy more space in memory (due to larger pointers and possibly other types and alignment adding)*."  There is mention of up to 10% less available memory (hard drive space is not mentioned)  I have however found with empirical measurements that 64 bit and 32 bit uses the same amount of memory with the normal applications that I use.

Wine?  I installed via Synaptic and I use it - no problem.  I also found that the Java stuff that I use work standard without a problem (installed Ubuntu-restricted-extras).  There are one or two websites that does not function correctly with Firefox, but I've had the same problem with Ubuntu 32 bit and have always (also now with 64 bit), used KDE's Konqueror for these few sites and all works well.

Like I stated in the original post, If I install everything in 64 bit Ubuntu which I installed in the 32 bit version, I see no difference in operation, except that I quite literally have a much faster machine!

---

### Post by jenkinbr on 2008-12-01
Very nice!  I've been thinking about getting a laptop that has 64-bit architecure, but wasn't sure if I should try Ubuntu x64 or not.  If I get said laptop, I will definatly try it out.  Thanks.

---

### Post by hyper_ch on 2008-12-01
java - works fine on 64bit
flash - works fine with ia32lib (or even now you ahve a native linux 64bit flash client provided by adobe)
wine - works fine on 64bit

---

