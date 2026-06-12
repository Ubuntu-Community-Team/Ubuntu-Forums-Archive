---
title: "A problem with free()   (C)"
date: 2008-04-21
forum: Programming Talk
---

### Post by POW R TOC H on 2008-04-21
I'm using malloc, to allocate memory,, and it does this fine... But when I try to free the memory, I get this :

```

*** glibc detected *** /home/fingerprint/Documents/CTESTGTK/combinations/bin/Debug/combinations: munmap_chunk(): invalid pointer: 0x0804a008 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb7d8592b]
/home/fingerprint/Documents/CTESTGTK/combinations/bin/Debug/combinations[0x8048648]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb7d2e050]
/home/fingerprint/Documents/CTESTGTK/combinations/bin/Debug/combinations[0x80484e1]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:03 20529201   /home/fingerprint/Documents/CTESTGTK/combinations/bin/Debug/combinations
08049000-0804a000 rw-p 00000000 08:03 20529201   /home/fingerprint/Documents/CTESTGTK/combinations/bin/Debug/combinations
0804a000-0806b000 rw-p 0804a000 00:00 0          [heap]
b7d17000-b7d18000 rw-p b7d17000 00:00 0 
b7d18000-b7e5c000 r-xp 00000000 08:02 17163      /lib/tls/i686/cmov/libc-2.6.1.so
b7e5c000-b7e5d000 r--p 00143000 08:02 17163      /lib/tls/i686/cmov/libc-2.6.1.so
b7e5d000-b7e5f000 rw-p 00144000 08:02 17163      /lib/tls/i686/cmov/libc-2.6.1.so
b7e5f000-b7e62000 rw-p b7e5f000 00:00 0 
b7e62000-b7e6c000 r-xp 00000000 08:02 928483     /lib/libgcc_s.so.1
b7e6c000-b7e6d000 rw-p 0000a000 08:02 928483     /lib/libgcc_s.so.1
b7e6d000-b7e6e000 rw-p b7e6d000 00:00 0 
b7e6e000-b7e91000 r-xp 00000000 08:02 17167      /lib/tls/i686/cmov/libm-2.6.1.so
b7e91000-b7e93000 rw-p 00023000 08:02 17167      /lib/tls/i686/cmov/libm-2.6.1.so
b7e93000-b7f7b000 r-xp 00000000 08:02 604684     /usr/lib/libstdc++.so.6.0.9
b7f7b000-b7f7e000 r--p 000e8000 08:02 604684     /usr/lib/libstdc++.so.6.0.9
b7f7e000-b7f80000 rw-p 000eb000 08:02 604684     /usr/lib/libstdc++.so.6.0.9
b7f80000-b7f86000 rw-p b7f80000 00:00 0 
b7f9d000-b7fa1000 rw-p b7f9d000 00:00 0 
b7fa1000-b7fbb000 r-xp 00000000 08:02 928484     /lib/ld-2.6.1.so
b7fbb000-b7fbd000 rw-p 00019000 08:02 928484     /lib/ld-2.6.1.so
bf81c000-bf832000 rw-p bf81c000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

Press ENTER to continue.

```

Can you please tell me what is this all about :( ?

---

### Post by Jessehk on 2008-04-21
My guess would be that you're freeing the same location in memory more than once.

It would be helpful to us if you could post the code that is causing this (the snippet should be as small as possible while still including the code causing the error).

---

### Post by sq377 on 2008-04-21
The backtrace should show a double free error if that was the case.  At first glance I would have to guess it is an invalid pointer being passed to free.  I've got to agree that we need to see some code to really understand what's going on.  If you dont want to hand that out, create a test case that shows the problem for us.

---

### Post by Joeb454 on 2008-04-21
Make sure your variable/pointer names are the same & correct

Remember that *pointer and *Pointer are 2 totally different pointers in C :)

---

