---
title: "[SOLVED] valgrind cryptic log"
date: 2008-06-12
forum: Programming Talk
---

### Post by kung fu buntu on 2008-06-12
```
$ valgrind --leak-check=full --show-reachable=yes --tool=memcheck   ./app.exe arg1 arg2

==1223== Memcheck, a memory error detector.
==1223== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==1223== Using LibVEX rev 1804, a library for dynamic binary translation.
==1223== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==1223== Using valgrind-3.3.0-Debian, a dynamic binary instrumentation framework.
==1223== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==1223== For more details, rerun with: -v
==1223==
==1223==
==1223== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 10 from 1)
==1223== malloc/free: in use at exit: 88 bytes in 2 blocks.
==1223== malloc/free: 67 allocs, 65 frees, 474,917 bytes allocated.
==1223== For counts of detected errors, rerun with: -v
==1223== searching for pointers to 2 not-freed blocks.
==1223== checked 3,345,936 bytes.
==1223==
==1223== 32 bytes in 1 blocks are still reachable in loss record 1 of 2
==1223==    at 0x4C210BC: calloc (vg_replace_malloc.c:397)
==1223==    by 0x729C54A: (within /lib/libdl-2.7.so)
==1223==    by 0x729BEF0: dlopen (in /lib/libdl-2.7.so)
==1223==    by 0x7CC3F7C: (within /usr/lib/libGL.so.100.14.11)
==1223==    by 0x7CDBB34: _init (in /usr/lib/libGL.so.100.14.11)
==1223==    by 0x400E165: (within /lib/ld-2.7.so)
==1223==    by 0x400E28D: (within /lib/ld-2.7.so)
==1223==    by 0x4000A99: (within /lib/ld-2.7.so)
==1223==    by 0x5: ???
==1223==    by 0x7FF000602: ???
==1223==    by 0x7FF000610: ???
==1223==    by 0x7FF000615: ???
==1223==
==1223==
==1223== 56 bytes in 1 blocks are still reachable in loss record 2 of 2
==1223==    at 0x4C210BC: calloc (vg_replace_malloc.c:397)
==1223==    by 0x7CC4E49: (within /usr/lib/libGL.so.100.14.11)
==1223==    by 0x7CDB69A: (within /usr/lib/libGL.so.100.14.11)
==1223==    by 0x7CDBB20: _init (in /usr/lib/libGL.so.100.14.11)
==1223==    by 0x400E165: (within /lib/ld-2.7.so)
==1223==    by 0x400E28D: (within /lib/ld-2.7.so)
==1223==    by 0x4000A99: (within /lib/ld-2.7.so)
==1223==    by 0x5: ???
==1223==    by 0x7FF000602: ???
==1223==    by 0x7FF000610: ???
==1223==    by 0x7FF000615: ???
==1223==    by 0x7FF00062F: ???
==1223==
==1223== LEAK SUMMARY:
==1223==    definitely lost: 0 bytes in 0 blocks.
==1223==      possibly lost: 0 bytes in 0 blocks.
==1223==    still reachable: 88 bytes in 2 blocks.
==1223==         suppressed: 0 bytes in 0 blocks.

```

What do I make of this?
It seems the leak is in a library that my application is linked (dynamically) with, but how can I be sure of this?
And how can I ignore it; assuming that this isn't a bug in my application but with the library instead.
The trace log is full of question marks...

My C++ application had returned 0 bytes leaked in the past, but I have lost track of it :(
Besides that, a simple hello in C++ has no leaks reported by valgrind.

Thank you.





EDIT:

The problem was with a library (ILUT) that I was linking the code with. And since I really didn't need it, by removing it I solved the problem.



EDIT 2 (for future reference): about the question marks:
[http://valgrind.org/docs/manual/faq.html#faq.unhelpful](http://valgrind.org/docs/manual/faq.html#faq.unhelpful)

---

