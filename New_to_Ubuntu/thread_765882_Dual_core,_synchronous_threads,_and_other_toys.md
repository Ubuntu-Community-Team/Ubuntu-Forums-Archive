---
title: "Dual core, synchronous threads, and other toys"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by kvk on 2008-04-24
I'm a wee bit confused by the applicability of dual core machines to general software applications as they are now written. As I understand it, dual core machines make possible simultaneous thread processing provided that the software is written to take advantage of it; otherwise, there is no reduction in computing speed. This is exactly the same as trying to run a cluster. Is that correct? Or is there some difference between cluster processing and dual core processing that eludes me? There is also the difference between an improvement in OS speed (as the OS may be able to use synchronous processing) and improvement in a given application.

I use an older computer (about six years) and might purchase a "new" refurbished one, as I need additional speed and memory for some research applications. BUT...all machines are now dual core, and I have no idea if Ubuntu can take advantage of this, nor do I know if, despite all the hype, the applications need to be specifically written to use dual core architecture, in which case a P4 with a 4 gH processor would be much better than a dual core with a pair of 2 gH processors, since only one at a time would be used.

Thank you!

---

### Post by chewearn on 2008-04-25
As far as I know, very few applications take advantage of the dual core.

One thing that can be beneficial is e.g. h.264 1080p decoding.  Unfortunately, the ffmpeg codec in ubuntu right now is not making use of dual core, resulting in insufficient processing power to decode this video format.

Fortunately, linux kernel is supporting dual core.  What this mean is running different applications at the same time will make use of both cores.  For example, if I am running a CPU intensive application which consume 100% of one core, the linux GUI is still responsive by making use of the second core.  Other application running will also be less likely to hang.  This is the advantage of dual core vs single core.

Due to CPU architecture improvement, one core of the Intel Core Duo 2GHz is as fast or faster than a Pentium 4 3.8GHz.  With two cores, you really get up to twice the CPU power of P4 4GHz.

Consider this:
AMD Atlon 64 3800+ is equivalent to a P4 3.8GHz.  This AMD CPU is running at 2GHz.
(AMD Atlon 64 X2 is the dual core version).

Core2Duo 2GHz is faster than AMD 64 X2 3800+ (2GHz clock).
It follows that a single core of Core2Duo 2GHz is faster than P4 3.8GHz.

This is not just theoretical, but in practice, I have run Folding@Home in these CPUs, and I can really say it's quite true.

---

### Post by 3rdalbum on 2008-04-25
I have a 3GHz Core 2 Duo, and it's an excellent processor.

For ordinary computing, you won't notice a difference between single and dual core, because you're not putting your processor up anywhere near capacity. But any video encoding you do will see a big improvement (including video DVDs and videos for an MP3 player). Compiling software can be faster when you tell the compiler to multithread (assuming you find the need to compile a lot, which I don't).

I have two DVD burners in my computer, and I often rip two CDs to MP3 at the same time. As each CD is being ripped by a different process (a different instance of the same program), each process gets put onto a different core. So multiple, single-threaded programs will see an improvement too.

Even if you run one single-threaded intensive program at a time, the rest of the operating system will go onto the other core, making the intensive job finish quicker. Even on a single-core processor, Linux is very good at keeping your foreground tasks responsive while something goes on in the background, but this ability is enhanced with multiple cores.

I don't agree with Intel making octo-core processors with Hyperthreading; I believe that's a waste as no normal programs will be able to utilise even eight threads at a time. And you'll notice that I have the beefiest dual-core processor I could find :-)  But believe me, dual-core is a better idea than finding an old hot 3.8GHz Pentium 4. Even a slower clock speed Core 2 is going to be at least comparable in speed in one core, due to the more efficient microarchitecture.

Note: I'm not sure about the previous poster saying that ffmpeg doesn't use multiple threads when decoding 1080p h.264 video. The attached screenshot will show that ffmpeg is using both cores, but only around 50% per core. This is probably because my processor is fast enough to decode it without any trouble.

---

### Post by chewearn on 2008-04-25
> **3rdalbum said:**
> Note: I'm not sure about the previous poster saying that ffmpeg doesn't use multiple threads when decoding 1080p h.264 video. The attached screenshot will show that ffmpeg is using both cores, but only around 50% per core. This is probably because my processor is fast enough to decode it without any trouble.

You should check your process monitor; it's likely the media player/ffmpeg only take up one core, while compiz is consuming the other core.

Ref:
[https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/194226](https://bugs.launchpad.net/ubuntu/+source/ffmpeg/+bug/194226)

---

### Post by kvk on 2008-04-25
Most excellent!! Thanks to both of you- that makes a few things much clearer! :)

---

