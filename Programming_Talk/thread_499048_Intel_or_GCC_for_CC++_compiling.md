---
title: "Intel or GCC for C/C++ compiling?"
date: 2007-07-12
forum: Programming Talk
---

### Post by kripkenstein on 2007-07-12
Some guy where I work says that we should use the Intel compiler for our C/C++ code,  which he assumes is the best-optimized for running code on Intel CPUs (which our company will be using for the near future at least). I, on the other hand, tend to use GCC, because (1) I am more familiar with it, (2) it gives decent results, and (3) we can easily switch to AMD CPUs without changing our compile processes.

Opinions?

---

### Post by HermanAB on 2007-07-12
Actually, the benchmarks that I have seen shows that the best C/C++ compiler (in terms of code size and speed) is the one by Microsoft.  However, GCC execution speed is within 10% of MS Visual C++ and since everything else on Linux is compiled with GCC, you should stick to it.  Having two different tools on the same system, will cause more bugs.

---

### Post by WebDrake on 2007-07-12
> **kripkenstein said:**
> Some guy where I work says that we should use the Intel compiler for our C/C++ code,  which he assumes is the best-optimized for running code on Intel CPUs (which our company will be using for the near future at least). I, on the other hand, tend to use GCC, because (1) I am more familiar with it, (2) it gives decent results, and (3) we can easily switch to AMD CPUs without changing our compile processes.

Opinions?

Well, in general what makes your code most efficient is not what you compile it with but that the algorithms and data structures it uses are the best ones for the purpose.

The question you need to ask is whether the compiler optimizations are relevant to your use-case.  If you're talking about a typical application it probably makes little odds and you might as well work with the standard toolchain.  If on the other hand you're talking about serious number-crunching work where every tiny optimization counts, icc might be worth thinking about---but test to make sure it really does produce faster code.  It might not, it depends on the particular task you're performing.

---

### Post by meatpan on 2007-07-12
Keep in mind the restrictive licensing for using the intel compiler:
[http://www.intel.com/cd/software/products/asmo-na/eng/219771.htm](http://www.intel.com/cd/software/products/asmo-na/eng/219771.htm)

A while back there was a nice how-to (on the ubuntu 'how-to' board) about using the intel compiler.  I can't find it atm, but it's about 1-2 months old.

---

### Post by kripkenstein on 2007-07-12
Thanks for the comments so far. I guess I might do some benchmarks on our specific code and see what's what. But first I'll try to convince people here to use GCC and not spend time on that testing. In particular because of the licensing issue that meatpan correctly pointed out.

---

### Post by nrs on 2007-07-12
The Gentoo argument applies IMO. 

It just isn't worh the hassle.

---

