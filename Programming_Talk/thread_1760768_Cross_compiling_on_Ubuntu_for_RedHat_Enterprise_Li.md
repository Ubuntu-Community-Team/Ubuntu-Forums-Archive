---
title: "Cross compiling on Ubuntu for RedHat Enterprise Linux"
date: 2011-05-17
forum: Programming Talk
---

### Post by dave.johnston on 2011-05-17
Hi,

I was wondering if anyone had managed to create a setup/build a toolchain that allowed them to compile C/C++ code on Ubuntu for a RedHat EL 5.5 / Cent OS 5.5 platform ? 
I'd like to use the GNU compiler for this purpose.

If you have, I would be interested to see how it was done.

Cheers

---

### Post by dwhitney67 on 2011-05-17
Why are you convinced that you require a cross-compiler?

I just developed/compiled a trivial C++ application on my Ubuntu 10.10 32-bit system, and ran it successfully on an RHEL 5.5 64-bit system.

I used GCC version 4.4.3 on my Ubuntu system.

---

### Post by dave.johnston on 2011-05-18
I'm trying to compile a fairly large software base, that currently compiles successfully on RH EL 5.5.

Compiling on Ubuntu fails at various points, I also think compiling on ubuntu and copying libraries onto the system to test, will give me issues when it comes to debugging.

Ideally I'd like to have complete binary compatibility.

---

### Post by dwhitney67 on 2011-05-18
> **dave.johnston said:**
> 
Compiling on Ubuntu fails at various points...

This is pretty vague; what do you mean by fails?

I've developed code in the past that compiled fine on one system, but when I brought it over to another system that had a later version of GCC, compiling the code would produce errors.

This had nothing to do with cross-compiling; it merely had to do with poor assumptions I made when I originally developed the code.

---

### Post by dave.johnston on 2011-05-19
The versions of gcc are the same, 4.4, but there are differences in some of the dependent libraries on the system.

In the past when you compiled applications on Ubuntu and ran them on Redhat, were all the debug symbols intact when you debugged on the RedHat system?

In the past I have found running binaries/libraries compiled on Ubuntu on another system such as RedHat5, the debugging info is mangled, which is part of the motivation for looking at cross compiling.

---

