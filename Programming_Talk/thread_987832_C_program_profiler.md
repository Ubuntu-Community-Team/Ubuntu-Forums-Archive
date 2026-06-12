---
title: "C program profiler"
date: 2008-11-19
forum: Programming Talk
---

### Post by kvorion on 2008-11-19
Hi All,

I need to be able to profile a C program to analyze its memory access patterns and things like that at the processor level. I tried using the simplescalar simulator for this purpose but apparently the gcc module that comes with the simplescalar kit has a lot of errors. Could somebody suggest me a typical program that is used to profile native applications on the linux platform?

---

### Post by elctb on 2008-11-19
Take a look at gprof.

I believe it does what you're looking for.

---

### Post by kvorion on 2008-11-19
Thanks for the suggestion. What I need is at a lower level of abstraction than what gprof provides. I need to be able to get processor level information like memory accesses, cache accesses, hits misses and that kind of stuff. That is normally done by running it on a target platform (usually provided by a simulator).

---

### Post by PandaGoat on 2008-11-20
Try looking at [valgrind]("http://valgrind.org/").  I am not sure if this does what you are wanting, but it appears to have more detailed profiling than gprof.  Anyway, just go to [http://valgrind.org/docs/manual/manual.html](http://valgrind.org/docs/manual/manual.html) and search around to see if it does what you want.


[After reading about it some more, I saw that valgrind's manual recommends [OProfile]("http://oprofile.sourceforge.net/news/").]

---

