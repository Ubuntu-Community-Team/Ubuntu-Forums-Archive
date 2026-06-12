---
title: "check for memory leaks C"
date: 2009-03-01
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-03-01
I want to check for memory leaks in a program I wrote in C. But I don't want a complicated system to do so.

EDIT: Sorry I found Valgrind

Does this mean my program in leak free
> $ valgrind --leak-check=full ./test
==16031== Memcheck, a memory error detector.
==16031== Copyright (C) 2002-2007, and GNU GPL'd, by Julian Seward et al.
==16031== Using LibVEX rev 1854, a library for dynamic binary translation.
==16031== Copyright (C) 2004-2007, and GNU GPL'd, by OpenWorks LLP.
==16031== Using valgrind-3.3.1-Debian, a dynamic binary instrumentation framework.
==16031== Copyright (C) 2000-2007, and GNU GPL'd, by Julian Seward et al.
==16031== For more details, rerun with: -v
==16031== 
8 7 6 5 4 3 2 1 0 
==16031== 
==16031== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 11 from 1)
==16031== malloc/free: in use at exit: 0 bytes in 0 blocks.
==16031== malloc/free: 36 allocs, 36 frees, 180 bytes allocated.
==16031== For counts of detected errors, rerun with: -v
==16031== All heap blocks were freed -- no leaks are possible.


---

### Post by ebichete on 2009-03-01
Yes, it is. The relevant line is:

==16031== All heap blocks were freed -- no leaks are possible.

---

### Post by monkeyking on 2009-03-01
No it doesn't your program is leak free.
It means that the time you ran the program it was leak free.

You need to make sure that your run path has been to every outskirts of you program.

---

