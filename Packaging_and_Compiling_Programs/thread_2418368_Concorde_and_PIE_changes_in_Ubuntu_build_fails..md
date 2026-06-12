---
title: "Concorde and PIE changes in Ubuntu: build fails."
date: 2019-05-06
forum: Packaging and Compiling Programs
---

### Post by Andrew_McLean on 2019-05-06
For some years I have been building and using the well-known 'concorde TSP' package for the Travelling Salesman Problem. This package is delivered (I believe) as a conventional 'autoconf' package with '.configure' and 'makefile.in' etc etc. Previously running '.configure' and 'make' has built the programs successfully, on earlier versions of Ubuntu.

On the latest OS Mint 19.1 (based on Ubuntu 18.04) the 'make' process fails with errors like this:

"relocation R_X86_64_32S against `.rodata' can not be used when making a PIE object; recompile with -fPIC"

I believe that this is caused by this change in Ubuntu 18.04: "gcc is now set to default to compile as PIE"

I have tried adding "-fPIC" to the gcc options in concorde's 'makefile.in', but that doesn't fix the problem.

Any suggestions as to the best way to address this ? Can I change something in the OS defaults ? Or would I have to change something else in the concorde package ?

---

### Post by Andrew_McLean on 2019-05-06
I got the solution to this by contacting the 'concorde' originator. The solution is to replace the downloaded 'qsopt' components (3 files) with the set labelled as:
Red Hat Linux, gcc 4.4.7,
 -fPIC (Intel 64-bit)

then rename 'qsopt.PIC.a' as 'qsopt.a', run make distclean, rerun the .configure script, and run make.

---

