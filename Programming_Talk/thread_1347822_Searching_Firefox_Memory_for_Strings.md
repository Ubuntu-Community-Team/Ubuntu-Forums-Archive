---
title: "Searching Firefox Memory for Strings?"
date: 2009-12-06
forum: Programming Talk
---

### Post by mocha on 2009-12-06
I think I'm on the right track here but need some help.

I'm trying to figure out how to dump the memory of Firefox to a hex file and then grep it for strings.  Specifically I want to search the memory for embedded URL strings.  I use gdb "dump xxx memory <filename> <start_mem> <end_mem>"

I look at /proc/<PID>/maps which apparently gives me the memory mapping of firefox along with all of the libraries in use.  This is where I need help.  What range of memory do I need to look at?  I've tried the [stack] area which didn't seem to produce any results.

---

