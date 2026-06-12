---
title: "Application crashing on Intel but not Athlon processors"
date: 2013-02-14
forum: Programming Talk
---

### Post by bagpussnz on 2013-02-14
Hi,
This is a tricky one to describe. I know it's vague, but has anyone seen this behaviour...

We have a lot of legacy Fortran code which we translate to C using a translation tool. This tool is a C program - it's not large, but due to the nature of what it does, is relatively complex. (I am in discussion with the vendor on this, but frankly we are at our wits end).

I have installed a number of machines with Ubuntu 10.04. Every installation is identical using 10.04 64 bit. (with ia32-libs).

When we compile the tool in 32 bit (-m32), it crashes with random segmentation faults - But only on Intel architectures.
It works perfectly on Athlon architectures.

It works fine in 64 bit mode (-m64) on both Intel and Athlon.

I tried in desperation creating an Intel 32 bit machine - same configuration and compiled the tool natively - again it crashes.

Just to make it even more difficult, the tool works fine in every architecture on Centos.

Any ideas anyone? I know the obvious answer is to give it back to the vendor, but I've never seen anything like this before and wondef if anyone has any ideas - compilation options, package installs, etc

Regards,
Ian

---

### Post by Bachstelze on 2013-02-14
Just because it "works" does not mean it's okay. It is not at all uncommon for a program to have a bug that "shows itself" only in special circumstances, which can be a specific CPU architecture.

Your program has a bug, you have to find and fix it.

---

### Post by bagpussnz on 2013-02-14
Hi,
Thanks for the response - when I say the program does work - it's after tests to ensure the translated code is good.

The problem is that Intel and Athlon are meant to be binary compatible. Yes, there is probably a bug in the program or in it's compilation options or in the compiler....

---

### Post by ofnuts on 2013-02-14
> **bagpussnz said:**
> Hi,
This is a tricky one to describe. I know it's vague, but has anyone seen this behaviour...

We have a lot of legacy Fortran code which we translate to C using a translation tool. This tool is a C program - it's not large, but due to the nature of what it does, is relatively complex. (I am in discussion with the vendor on this, but frankly we are at our wits end).

I have installed a number of machines with Ubuntu 10.04. Every installation is identical using 10.04 64 bit. (with ia32-libs).

When we compile the tool in 32 bit (-m32), it crashes with random segmentation faults - But only on Intel architectures.
It works perfectly on Athlon architectures.

It works fine in 64 bit mode (-m64) on both Intel and Athlon.

I tried in desperation creating an Intel 32 bit machine - same configuration and compiled the tool natively - again it crashes.

Just to make it even more difficult, the tool works fine in every architecture on Centos.

Any ideas anyone? I know the obvious answer is to give it back to the vendor, but I've never seen anything like this before and wondef if anyone has any ideas - compilation options, package installs, etc

Regards,
Ian

First, "it crashes" is a bit terse... what is it doing exactly when it crashes? Any hint of using the more exotic instructions?

Second, did you try to compile it with less optimizations?

---

### Post by trent.josephsen on 2013-02-14
How many different processors have you tried?

"Binary compatible" only need apply as long as you are doing sensible things. Different processors have different ways of handling cache, different timing constraints, that kind of thing, and when your C code has undefined behavior, the compiler is allowed to generate code that does anything it feels like -- including code that may appear to work on some processors but crash on others.

For instance, it could be you're overwriting a buffer somewhere, and because of the difference in how the processors arrange memory in cache, it goes undetected on the AMD machine but causes a segfault on the other one. (You didn't specify what you meant by "crash", so I figure a segfault fits the bill.) That's only one possibility, and you should be glad it's crashing consistently on one kind of machine because you know for sure there's a bug in it, as opposed to finding out after two years of periodic and apparently random crashes.

One other question leaps to mind -- does it crash while processing input? Does it crash only on some inputs and not others? Those are questions you should ask yourself when looking in the code for the bug.

---

### Post by jwbrase on 2013-02-14
> **bagpussnz said:**
> Hi,
Thanks for the response - when I say the program does work - it's after tests to ensure the translated code is good.

The problem is that Intel and Athlon are meant to be binary compatible.

There are some differences in what instructions (sysenter/sysexit vs. syscall/sysret) are valid to use for making and returning from system calls in 32-bit programs. This may or may not be what you're running into.

---

