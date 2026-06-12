---
title: "glibc development package is not installed"
date: 2011-06-19
forum: Packaging and Compiling Programs
---

### Post by navis13 on 2011-06-19
Hello,

I just installed on program called Dolphin Smash. The installation was successful, but when I'm trying to run simulation of some existing examples, it gives me follow error:
//-----------------------------------------------------------------------------------------------------
ERROR: failed to compile "/home/navis/eda/Dolphin/smash/examples/Verilog-Ams/OPAMP/opamp.vams"
ERROR: glibc development package is not installed (missing libc.so) 
//-----------------------------------------------------------------------------------------------------
How I can fix this issue?

Thanks,
BR

I start searching for the problem and I've seen follow
/usr/lib/crti.o: file not recognized: File format not recognized
collect2: ld returned 1 exit status

---

