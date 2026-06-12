---
title: "How to make your program spend less memory(RAM)? - C++"
date: 2010-12-03
forum: Programming Talk
---

### Post by hakermania on 2010-12-03
I am developing a GUI in C++ currently sixed 3.2 MB and I noticed that it spends at start around 11 MB RAM. When I have some action with it this spending can go up to 22-23 MB.
Can you tell me some tips in order to make the program less spender(e.g. avoid strings and prefer chars or avoid long and prefer int etc)? Thx in advance

---

### Post by Arndt on 2010-12-03
> **hakermania said:**
> I am developing a GUI in C++ currently sixed 3.2 MB and I noticed that it spends at start around 11 MB RAM. When I have some action with it this spending can go up to 22-23 MB.
Can you tell me some tips in order to make the program less spender(e.g. avoid strings and prefer chars or avoid long and prefer int etc)? Thx in advance

I suppose a lot depends on what toolkit you use.

Use valgrind and see if there is memory allocated but never freed, but which could be.

Try to identify points in the program where the memory usage suddenly rises.

Note that memory is never given back by programs, it can only be reused, so if you allocate 20 MB temporarily and then free 18 MB, looking at the program from the outside with 'top' or something similar will not show the freeing as such, but it may show how much of it is actually active. With bad enough locality, you will still use a lot more memory pages than necessary.

Not that 20 MB sounds acceptable, but it depends on much data you actually process.

Can you do some operations without opening any windows at all? Does that also use as much memory?

Sometimes it's useful to make the code temporarily do some action twice, in order to see if it takes a lot of time or memory, when it's impossible to just skip the action.

---

### Post by MadCow108 on 2010-12-03
20-30 mb is not really very much on modern systems.
how do you determine this number? e.g. top is not too good a measure due to it displaying also the memory in glibs freelist as used.

bluntly changing strings to char's and longs to ints can be a case of premature optimization.
Do not attempt it before profiling!

after the hunt for memory leaks with valgrind use massif (also in valgrind) to profile your heap usage and identify the big memory wasters and try to optimize them.

here is a (slightly outdated) guide:
[http://library.gnome.org/devel/optimization-guide/stable/optimization-massif-TBL-using-massif.html.en](http://library.gnome.org/devel/optimization-guide/stable/optimization-massif-TBL-using-massif.html.en)

how best to attack depends heavily on your program.
E.g. replace list's with deques, use flyweight pattern for small data sharing objects, freeing memory earlier, changing algorithms to in-place variants, structure packing, reduce library symbol exports ...

---

### Post by hakermania on 2010-12-03
Thx for the suggestions. btw I use Qt

---

### Post by hakermania on 2010-12-03
The output of valgrind (mecheck option) is:
```
==2377== HEAP SUMMARY:
==2377==     in use at exit: 2,908,599 bytes in 40,369 blocks
==2377==   total heap usage: 406,678 allocs, 366,309 frees, 58,952,345 bytes allocated
==2377== 
==2377== LEAK SUMMARY:
==2377==    definitely lost: 3,673 bytes in 78 blocks
==2377==    indirectly lost: 18,502 bytes in 702 blocks
==2377==      possibly lost: 2,161,310 bytes in 32,663 blocks
==2377==    still reachable: 725,114 bytes in 6,926 blocks
==2377==         suppressed: 0 bytes in 0 blocks
==2377== Rerun with --leak-check=full to see details of leaked memory

```

---

