---
title: "Profiling C code containing CBLAS LAPACK functions"
date: 2010-07-31
forum: Programming Talk
---

### Post by Mszanetti on 2010-07-31
Hi

I am used to profile C code in Linux using gprof.

I need to optimize a C project ... I am wondering if I can replace some parts of the code by equivalent lapack/cblas routines ... Therefore I need to compare the timing of each approach ...

It seems that gprof does not profile the lapack/cblas routines ... it does not list them ... therefore what is the best way to profile C code mixed with lapack/cblas routines?

Thank you!

---

### Post by Mszanetti on 2010-07-31
Hi

I just found this answer in the net:

Q: How can I profile a code, using gprof or xprofiler, and include the calls to LAPACK?
A: You'll need to include the profile-enabled version of LAPACK, namely -llapack_profile which resides in /usr/local/lib 

It turns out I don't have this library in my computer ... How to install it in an Ubuntu machine?

Thank you.

---

### Post by Mszanetti on 2010-08-01
Which package ... I cannot find the right one ... thank you

---

