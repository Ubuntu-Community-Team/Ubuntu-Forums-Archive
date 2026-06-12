---
title: "how to check how many unrolled loops"
date: 2014-07-22
forum: Programming Talk
---

### Post by zerop2 on 2014-07-22
If memory access were 100 cycles, and the unrolled loops are two cycles apart, LookAhead could be set to 50


it seems prefetch lookahead is (memory access)/(unrolled loops)


1. how to check how many cycles in memory access in ubuntu?
2. how to check how many unrolled loops in ubuntu?

---

### Post by tgalati4 on 2014-07-26
It's a little more complicated than that.  Unrolling loops gives the CPU the opportunity to process those loops with data in the local cache--saving CPU cycles from going out to RAM for each and every loop.  Depending on your code (and how deterministic it is) prefetch can help or hurt.  If you load too much into cache and your algorithm doesn't need it, then that can hurt performance.

The way to tell what values to use is to instrument your code and profile it--determine where the CPU cycles are being consumed and then examine those routines for time savings.  Unrolling loops is just one method.  You will want to spend some time with [strace]("http://manpages.ubuntu.com/manpages/trusty/man1/strace.1.html") and [profiling]("http://manpages.ubuntu.com/manpages/trusty/man1/readprofile.1.html").  Don't forget [gprof]("http://www.ibm.com/developerworks/library/l-gnuprof.html").

Of course you could run your code with different values of readahead and see if there is an optimum value.

To answer your specific questions:

1. Use the tools above to determine how long your code bothers the CPU.
2. The number of unrolled loops for your code depend on how deterministic it is.  The compiler's optimizer settings will get more aggressive depending on the optimization level selected during compilation.  Coding techniques can help or hinder unrolling.  You can also unroll manually in your code--breaking up loops in groups of 4 or 8 or 16:

Pseudo-code:

For i from 1 to 16, increment by 4
  array(i)=function(i)
  array(i+1)=function(i+1)
  array(i+2)=function(i+2)
  array(i+3)=function(i+3)
Return

This unrolling is deterministic.  You know how many total loops (16 in this case), you know the function can be computed independently of previous computations (function(i+1) does not depend on function(i)).  If your loop in not deterministic, you don't know the upper loop count, you don't know the relationship between function computations, then unrolling may not help.

---

