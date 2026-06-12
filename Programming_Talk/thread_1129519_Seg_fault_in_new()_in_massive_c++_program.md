---
title: "Seg fault in new() in massive c++ program"
date: 2009-04-18
forum: Programming Talk
---

### Post by night_fox on 2009-04-18
I've been working on a fun project for a while, and it's got quite big. Halfway through, I realised (derr) that you have to delete/delete[] things that you allocate otherwise you leak memory. I implemented some of this. After doing some more coding, my program segfaults in completely random unexpected places and whenever I do something that might have plugged a memory leak or might have checked for something dodgy before allocating or whatever, It seems to segfault in an even more bizarre place.

Pretty much every time I get a segfault, I use my minimal knowledge of gdb to find out what the problem is. The backtraces often show that the segfault happens in the new() function, yet when I ret from all these functions, back to my program, there does not seem to be anything wrong with the offending dynamic allocation, I.E the size of an array to be allocated with new is finite and small. Why on earth would new crash? Could memory from another part of my program be leaking and causing these problems? If so how would I find this?

for instance

part of the backtrace
```
#0  0xb7255998 in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0xb72578c5 in malloc () from /lib/tls/i686/cmov/libc.so.6
#2  0xb740bdc7 in operator new () from /usr/lib/libstdc++.so.6
#3  0xb740bf0d in operator new[] () from /usr/lib/libstdc++.so.6
....
....
```

after returning to the function (#4 in backtrace)
```
300	    return_string=new char[length+1];
(gdb) print length
$1 = 20
```

AARGH!](*,) *Tears hair out*

Please can you give me some tips on debugging large programs?

---

### Post by Cygnus on 2009-04-18
You can try to run your program under [Valgrind]("http://valgrind.org/"), it can point out trouble for you before the crash happens.

---

### Post by night_fox on 2009-04-18
Thanks, installing it now.

---

### Post by night_fox on 2009-04-18
```
==11355== ERROR SUMMARY: 3826 errors from 22 contexts (suppressed: 107 from 1)
==11355== malloc/free: in use at exit: 10,094 bytes in 706 blocks.
==11355== malloc/free: 8,704 allocs, 7,999 frees, 1,072,354 bytes allocated.
==11355== For counts of detected errors, rerun with: -v
==11355== searching for pointers to 706 not-freed blocks.
==11355== checked 572,468 bytes.
==11355== 
==11355== LEAK SUMMARY:
==11355==    definitely lost: 9,742 bytes in 705 blocks.
==11355==      possibly lost: 0 bytes in 0 blocks.
==11355==    still reachable: 352 bytes in 1 blocks.
==11355==         suppressed: 0 bytes in 0 blocks.
==11355== Rerun with --leak-check=full to see details of leaked memory.

```

It ran the program to the end surpressing errors!.
I love this program! It's so easy to use.

OMG this is good!


Thankyou Cygnus!

:popcorn:

---

### Post by Sockerdrickan on 2009-04-18
valgrind rocks, indeed. :popcorn:

---

### Post by monkeyking on 2009-04-18
Yes valgrind is very nice indeed.

But for simple seg faults,
I mostly use gdb.

---

