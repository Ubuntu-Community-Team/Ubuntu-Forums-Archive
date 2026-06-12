---
title: "[C] getpwuid leaky?"
date: 2009-01-25
forum: Programming Talk
---

### Post by Jesdisciple on 2009-01-25
I recently [started using **getpwuid(geteuid())** to find the user's profile directory]("http://ubuntuforums.org/showthread.php?t=1048468"), but it apparently has three memory leaks.  Should I report a bug, or maybe use another alternative?  (I can post the surrounding code, but **getpwuid(geteuid())** really is the entire input.)

I also don't understand why the line number in toolkit_init isn't shown.  Is that possibly related?

According to Memcheck:```
==18802== 156 (36 direct, 120 indirect) bytes in 1 blocks are definitely lost in loss record 1 of 3
==18802==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==18802==    by 0x4133C30: (within /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x4134565: __nss_database_lookup (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x459EF5B: ???
==18802==    by 0x45A100C: ???
==18802==    by 0x40DADA1: getpwuid_r (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x40DA716: getpwuid (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x804A863: toolkit_init (in /home/chris/NetBeansProjects/Outliner/outliner)
==18802==    by 0x8049167: outline_init (outline.c:22)
==18802==    by 0x8048BB8: main (main.c:46)
==18802== 
==18802== 
==18802== 40 bytes in 5 blocks are indirectly lost in loss record 2 of 3
==18802==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==18802==    by 0x413374B: __nss_lookup_function (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x459EF7B: ???
==18802==    by 0x45A100C: ???
==18802==    by 0x40DADA1: getpwuid_r (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x40DA716: getpwuid (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x804A863: toolkit_init (in /home/chris/NetBeansProjects/Outliner/outliner)
==18802==    by 0x8049167: outline_init (outline.c:22)
==18802==    by 0x8048BB8: main (main.c:46)
==18802== 
==18802== 
==18802== 80 bytes in 5 blocks are indirectly lost in loss record 3 of 3
==18802==    at 0x4025D2E: malloc (vg_replace_malloc.c:207)
==18802==    by 0x411EA5B: tsearch (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x413370D: __nss_lookup_function (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x459EF7B: ???
==18802==    by 0x45A100C: ???
==18802==    by 0x40DADA1: getpwuid_r (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x40DA716: getpwuid (in /lib/tls/i686/cmov/libc-2.8.90.so)
==18802==    by 0x804A863: toolkit_init (in /home/chris/NetBeansProjects/Outliner/outliner)
==18802==    by 0x8049167: outline_init (outline.c:22)
==18802==    by 0x8048BB8: main (main.c:46)
==18802== 
==18802== LEAK SUMMARY:
==18802==    definitely lost: 36 bytes in 1 blocks.
==18802==    indirectly lost: 120 bytes in 10 blocks.
==18802==      possibly lost: 0 bytes in 0 blocks.
==18802==    still reachable: 0 bytes in 0 blocks.
==18802==         suppressed: 0 bytes in 0 blocks.
```

Thanks!

---

### Post by CptPicard on 2009-01-25
Standard library functions don't just have spurious memory leaks all over the place so if I were you I'd just forget about it. As the man page doesn't explictly say that you're responsible for freeing the memory, what most likely happens is that the library does keep track of what is going on so that it can later return the same buffer on subsequent calls, but that memcheck is unable to see this...

EDIT: actually, what is most likely to happen is that there really is no need to release that buffer at all during program running time (you may want to read it again after all), so indeed it is not freed at all and that's perfectly fine...

---

### Post by Jesdisciple on 2009-01-26
Thanks, Picard.  Now I wonder what would persist through an entire program and occupy 156 bytes.  Anyway, the lurker may want to know that this shuts Memcheck up about the issue:```
{
    getpwuid
    memcheck:Leak
    fun:getpwuid
}
```See [http://valgrind.org/docs/manual/manual-core.html#manual-core.suppress](http://valgrind.org/docs/manual/manual-core.html#manual-core.suppress) for an explanation.

---

