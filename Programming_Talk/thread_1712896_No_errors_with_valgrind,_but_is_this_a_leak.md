---
title: "No errors with valgrind, but is this a leak?"
date: 2011-03-23
forum: Programming Talk
---

### Post by Pithikos on 2011-03-23
If I run from the terminal
```
valgrind ls
```I get
```
==2170== HEAP SUMMARY:
==2170==     in use at exit: 48,176 bytes in 123 blocks
==2170==   total heap usage: 651 allocs, 528 frees, 131,251 bytes allocated
==2170== 
==2170== LEAK SUMMARY:
==2170==    definitely lost: 120 bytes in 1 blocks
==2170==    indirectly lost: 0 bytes in 0 blocks
==2170==      possibly lost: 0 bytes in 0 blocks
==2170==    still reachable: 48,056 bytes in 122 blocks
==2170==         suppressed: 0 bytes in 0 blocks
==2170==
==2170== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)
```As you see there are no errors given but that puzzles me a bit. There are only 528 frees and 651 allocs so there must be something wrong?  Then it points out that 120 bytes are definitely lost and 48KB is still reachable. Isn't that synonym with LEAKAGE?

---

### Post by Arndt on 2011-03-23
> **Pithikos said:**
> If I run from the terminal
```
valgrind ls
```I get
```
==2170== HEAP SUMMARY:
==2170==     in use at exit: 48,176 bytes in 123 blocks
==2170==   total heap usage: 651 allocs, 528 frees, 131,251 bytes allocated
==2170== 
==2170== LEAK SUMMARY:
==2170==    definitely lost: 120 bytes in 1 blocks
==2170==    indirectly lost: 0 bytes in 0 blocks
==2170==      possibly lost: 0 bytes in 0 blocks
==2170==    still reachable: 48,056 bytes in 122 blocks
==2170==         suppressed: 0 bytes in 0 blocks
==2170==
==2170== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 4 from 4)
```As you see there are no errors given but that puzzles me a bit. There are only 528 frees and 651 allocs so there must be something wrong?  Then it points out that 120 bytes are definitely lost and 48KB is still reachable. Isn't that synonym with LEAKAGE?

It means the program doesn't bother with freeing everything when it is exiting anyway. Nothing strange or wrong with that.

When you are developing a program, you may want it to free everything at the end, so you can more easily catch whatever leaks there were before that point. The point is to avoid having the program grow and grow unnecessarily during execution, not to tidy everything up just before exiting.

---

### Post by slavik on 2011-03-23
> **Arndt said:**
> It means the program doesn't bother with freeing everything when it is exiting anyway. Nothing strange or wrong with that.

When you are developing a program, you may want it to free everything at the end, so you can more easily catch whatever leaks there were before that point. The point is to avoid having the program grow and grow unnecessarily during execution, not to tidy everything up just before exiting.
unless the kernel does not clean up afterwards (which is not true for Linux kernel 2.6.x)

---

### Post by Pithikos on 2011-03-23
> **Arndt said:**
> It means the program doesn't bother with freeing everything when it is exiting anyway. Nothing strange or wrong with that.

When you are developing a program, you may want it to free everything at the end, so you can more easily catch whatever leaks there were before that point. The point is to avoid having the program grow and grow unnecessarily during execution, not to tidy everything up just before exiting.

Oh so something like Firefox? :roll:
I had the missconception that leakage meant that a third person would be able to get access to memory addresses and read the values there to see what we did. I thought it was a security thing rather than a space thing.

---

### Post by MadCow108 on 2011-03-23
> **Pithikos said:**
> Oh so something like Firefox? :roll:
I had the missconception that leakage meant that a third person would be able to get access to memory addresses and read the values there to see what we did. I thought it was a security thing rather than a space thing.

what you probably thought of was information leakage.
This happens e.g. when you do not fully initialize data structures in the kernel and pass that structure to userspace.
The uninitialized parts of the structure may contain valuable information about stuff happening in the kernel.
e.g. this bug:
[http://lwn.net/Vulnerabilities/410813/](http://lwn.net/Vulnerabilities/410813/)

---

