---
title: "gcc, glibc, strlen and seg faults"
date: 2010-11-09
forum: Programming Talk
---

### Post by xxwombatxx on 2010-11-09
I'm having a very odd problem compiling codes that use strlen in the standard library. I asked on stackoverflow to no avail, but I suspect it's something a bit more specific to ubuntu, and however apt has configured gcc/glibc on my machine.

gcc version 4.3.4 on ubuntu 10.04. Compiling this very simple code example:

[http://www.cplusplus.com/reference/clibrary/cstring/strlen/](http://www.cplusplus.com/reference/clibrary/cstring/strlen/)

with gcc and running gives a segfault when it hits the strlen line. gdb backtrace shows:  (gdb) backtrace
#0  0x0000000000801030 in strlen@@GLIBC_2.2.5 ()
#1  0x000000000040066d in main () at test.c:11
  Running gdb itself does output two warnings:
  warning: the debug information found in "/lib/ld-2.11.1.so" does not match "/lib/ld-linux-x86-64.so.2" (CRC mismatch).
warning: the debug information found in "/lib/libc-2.11.1.so" does not match "/lib/libc.so.6" (CRC mismatch).
  unsure if that's relevant. I'm also curious why glibc is on version  2.2.5, and how I'd go about updating that (apt-get update libc6* shows everything up to date). The same code compiled by the Intel C compiler icc works  just fine.


  Thanks in advance!

---

### Post by Some Penguin on 2010-11-09
What input did you provide?

---

### Post by spjackson on 2010-11-09
> **xxwombatxx said:**
> I'm having a very odd problem compiling codes that use strlen in the standard library. I asked on stackoverflow to no avail, but I suspect it's something a bit more specific to ubuntu, and however apt has configured gcc/glibc on my machine.

gcc version 4.3.4 on ubuntu 10.04. Compiling this very simple code example:

Is that not 4.4.3?

> 
[http://www.cplusplus.com/reference/clibrary/cstring/strlen/](http://www.cplusplus.com/reference/clibrary/cstring/strlen/)

with gcc and running gives a segfault when it hits the strlen line. gdb backtrace shows:  (gdb) backtrace
#0  0x0000000000801030 in strlen@@GLIBC_2.2.5 ()
#1  0x000000000040066d in main () at test.c:11
  Running gdb itself does output two warnings:
  warning: the debug information found in "/lib/ld-2.11.1.so" does not match "/lib/ld-linux-x86-64.so.2" (CRC mismatch).
warning: the debug information found in "/lib/libc-2.11.1.so" does not match "/lib/libc.so.6" (CRC mismatch).
  That CRC mismatch doesn't look good. You are on 64-bit Ubuntu, yes? Is your gcc 64-bit or have you built/installed a 32-bit version. Is your program 32-bit or 64-bit?

> 
unsure if that's relevant. I'm also curious why glibc is on version  2.2.5, and how I'd go about updating that (apt-get update libc6* shows everything up to date). The same code compiled by the Intel C compiler icc works  just fine.
  I only get a problem (as expected) if I input a string longer than 256 characters.
(gcc 4.4.3, 64-bit Ubuntu 10.04)

---

### Post by xxwombatxx on 2010-11-09
how often do we struggle with something for hours or days to the point of actually asking someone else, then figured it out a few minutes later?

the problem was with a very obscure proprietary compiler taking over the linker. sorry for the post, this can be deleted.

---

