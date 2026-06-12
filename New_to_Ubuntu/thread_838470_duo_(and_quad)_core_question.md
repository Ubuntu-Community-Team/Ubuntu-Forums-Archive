---
title: "duo (and quad) core question"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Old Jimma on 2008-06-23
Dear Ubuntu Community:

I want to build a pretty fast computer for the purposes of doing scientific and statistical computing. I have a single processor AMD64 with Hardy now, and it works nicely.

I would like to build a system that uses duo (or quad) core AMD 64 bit processors... but my question is will the Ubuntu AMD64 operating system be able to use the two (or four) processors?? 

Thank you. I've greatly benefited replies I've gotten in the past from the forums. 

Sincerely,
Phil Smith
Duluth, GA

---

### Post by lswest on 2008-06-23
I run the 32bit version of Hardy (well, ran, it's now replaced by ArchLinux, but never mind that) on a dual core AMD turion 64x2 mobile TL-56 CPU and it ran both cores fine.  Definitely fine for quads too, friend of mine runs Fedora with a quad core.  Don't see why it wouldn't work on a 64bit version of Ubuntu, so I'd say it should all work out fine.

---

### Post by soxs on 2008-06-23
I am using an AMD Phenom with Ubuntu x86_64 8.04... and yes, ubuntu uses all 4 cores (like any other real linux distribution)

---

### Post by Pjotr123 on 2008-06-23
Absolutely. Let the cores come!  :-)

That's why Linux is being used widely in supercomputing, on universities and in research labs. The currently fastest supercomputer in the world, the Roadrunner from IBM, runs on Red Hat Linux.

Linux is the operating system of the pro's. Now available for your desktop as well. :-)

---

### Post by cespinal on 2008-06-23
Running Hardy on my dual cored laptop! everything works perfectly.

---

### Post by athowell on 2008-06-23
How do you determine if your system is using both cores?

When I first installed Ubuntu I recall "top" showing 2 CPU's.  However after several kernel updates from the Update Manager I don't see "top" listing two CPU's.

Please help me determine how to locate this information.

In older versions of Linux I'd always look for "SMP" but this is the first dual core vs dual processor machine I've ever had.

Thanks in advance.

---

### Post by Old Jimma on 2008-06-23
Athowell:

Good question! I'll look forward to learning how one knows this!!

Thanks,
Phil Smith
Duluth, GA

---

### Post by Vivaldi Gloria on 2008-06-23
> **Phil Smith said:**
> I want to build a pretty fast computer for the purposes of doing scientific and statistical computing. I have a single processor AMD64 with Hardy now, and it works nicely.

I would like to build a system that uses duo (or quad) core AMD 64 bit processors... but my question is will the Ubuntu AMD64 operating system be able to use the two (or four) processors?? 

Phil, ubuntu 8.04 works out of the box with duo (or quad) core processors and I have inter quad q6600 working nicely.

Are you aware of the fact that unless a program is written to use multi-processors then it can only use only one? Most programs out there are not multi-threaded so they cannot use multi-cores. So make sure that the programs you want work multi-threaded.

If they don't work multi-threaded then maybe it is better to buy a faster duo rather than a quad.

---

### Post by Old Jimma on 2008-06-24
Thanks, VIvaldi Gloria!

All the best,
Phil Smith
Duluth, GA

---

### Post by Cadmus on 2008-06-24
(just kidding here)

Real Programmers build their own beowulf clusters out of whatever machine they can find lying around (laptops, PS3s, washing machines).

---

### Post by Methuselah on 2008-06-24
q6600 here.
System monitor often shows all four cores cranking away.

---

### Post by gmc on 2008-06-24
A Quick and Easy way to tell if the Kernel see's all your cores is to open up a CLI terminal window and type "cat /proc/cpuinfo | less" (no quotes). This will list all the cores and their capabilities one after the other.

G.

---

