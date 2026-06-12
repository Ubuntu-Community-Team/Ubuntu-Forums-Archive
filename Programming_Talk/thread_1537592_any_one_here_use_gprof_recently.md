---
title: "any one here use gprof recently?"
date: 2010-07-23
forum: Programming Talk
---

### Post by mr.wu on 2010-07-23
I came across some google pages (one is on this forum) on using gprof to profile a c program.  I tested gprof usage by compiling a hello world program but when it comes to profiling my real program it seems to not work.  I say this because it does not produce gmon.out file.

To complicate things I had to manually link my program.

For hello world I do this

cc -pg a.c

For my program I have lots of objects file which I compile with the same -pg switch and I then make an archive .a file with command "ar".  Then I link like this

xld -o program lib_mine.a other_libs.so

A google search shows to use gcrt0.a just after program in above line as well as using -lc_p in above line.  Both does not work.  For a start, "locate gcrot0.a" gives nothing but there is "gcrot1.a".

Can someone give me some suggesstion?

Thanks

---

### Post by kheralalit on 2011-07-30
hii friend 
can u plz let me know how to work with gprof under ubuntu 11.04.

i have downloaded the steps of compilation from some website but unable to locate the exact thing what i want.

i am using this profiler for the first time.
please reply early i need to submit a assignment based on this profiler.

thnks

---

