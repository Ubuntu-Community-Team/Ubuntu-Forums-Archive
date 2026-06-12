---
title: "PowerPC cross-compiling"
date: 2007-03-22
forum: Programming Talk
---

### Post by wonko on 2007-03-22
I have a school-project where I'm supposed to  get Linux up and running on a development board based on the Freescale 8250 ("PowerPC") CPU.
You can read the whole assignment-text here: [http://www.itk.ntnu.no/fag/TTK4147/ovinger/oving9.php]("http://www.itk.ntnu.no/fag/TTK4147/ovinger/oving9.php")
I'm using ubuntu 6.06 on a Pentium4-machine.

So what I'm asking about is: where can I find the necessary software?
I seem to need some "linuxppc-2.6" kernel and "powerpc-linux-gcc". Minicom and build-essential I have. I can't seem to find this in the normal repositories (universe or multiverse). Are there any platform-specific powerpc repositories i need to enable, or will this screw up my system?

Please, if anyone knows *anything*, I'm real happy for any info!

---

### Post by pmasiar on 2007-03-22
I see - looks like you cannot use Ubuntu for PowerPC directly, and you want cross-compiling tools to **compile PowerPC code on Pentium**. Is that right?

I am no expert but my guess will be to read up GCC - should have switchces for that. IIRC build-essentials is the package, but I might be wrong.

---

### Post by wonko on 2007-03-22
Thanks for replying!
You understood me correctly. I can't install all of ubuntu, but need a small kernel to run on the development board (if I read the assignment correctly).
I also found [this thread]("http://www.ubuntuforums.org/showthread.php?t=360877"), where a similar problem is described, and a solution like what you described.
But now I'm told, by a senior student, that the software I need is not freely available, and I need to get it from some teachers at my school. So I guess I'll try that, and come back to you if I find out something more...
But thanks anyway! I really appreciate you trying to help :)

---

### Post by k0mpresd on 2007-03-22
does this help?

[http://penguinppc.org/dev/crosstool.php](http://penguinppc.org/dev/crosstool.php)

---

### Post by wonko on 2007-03-23
It looks promising. Thanks!
But still, I want to try the software available at my school first, so I'll wait for a reply from my teachers. But if that doesn't work, I sure will try out "crosstool".
I'll come back to you when I've heard from my teachers...

---

