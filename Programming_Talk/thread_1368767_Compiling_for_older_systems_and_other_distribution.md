---
title: "Compiling for older systems and other distributions"
date: 2009-12-31
forum: Programming Talk
---

### Post by ThomasJ02 on 2009-12-31
I do most of my development work on a machine running Karmic on x86_64. However, I need to deploy my code to a machine running an old version of RedHat that has an old GLIBC. When I try to run programs that I've compiled locally, they of course complain about the GLIBC incompatibility. How can I fix this? Do I need to install the older GLIBC on my Karmic box, or is there some way around this issue? For various reasons I can't compile on the RH box.

---

### Post by wmcbrine on 2009-12-31
You could build with -static, but that makes huge binaries.

You might consider setting up an equivalent system in a virtual machine, and building/testing on that.

---

### Post by dwhitney67 on 2009-12-31
For starters, try compiling for the 32-bit architecture, which I presume is what you have for the RH system.  Give GCC the -m32 compiler option.  (Note, I do not expect much success with this course of action).

Barring success with that approach, consider cross-compiling.  You would build a cross-compiler on your x86-64 machine that builds code for the legacy RH machine.  Btw, this is not trivial.  You may want to reference documentation on Cross-Compiled Linux From Scratch (CLFS); it contains great information on how to build a cross-compiler.

> 
For various reasons I can't compile on the RH box.

Why is this?  Is it because it does not have a compiler installed?  Or is it because your source code is not portable?

---

### Post by LeifAndersen on 2009-12-31
dwhitney67 is right, you really should compile for 32 bit architectures.  You could try compiling it in a virtual machine, or compiling it on an online service, such as Amazon's, or I think Suse also has a build service which is free.

---

### Post by wmcbrine on 2009-12-31
> **dwhitney67 said:**
> For starters, try compiling for the 32-bit architecture, which I presume is what you have for the RH system.If he were trying to run a 64-bit binary on a 32-bit system, then I don't think the error message would refer to glibc, would it?

---

### Post by dwhitney67 on 2009-12-31
> **wmcbrine said:**
> If he were trying to run a 64-bit binary on a 32-bit system, then I don't think the error message would refer to glibc, would it?

You're probably right.  I would probably indicate that the file could not be executed.

However, if he were to compile the app with the -m32 option, it would run successfully.

---

