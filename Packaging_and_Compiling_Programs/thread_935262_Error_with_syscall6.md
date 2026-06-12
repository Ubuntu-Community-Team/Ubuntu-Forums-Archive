---
title: "Error with syscall6"
date: 2008-10-01
forum: Packaging and Compiling Programs
---

### Post by mitch1710 on 2008-10-01
syscall6 error
I have the following error when compiling the syscall.c file

syscall.c:639: error: syntax error before "mmap2"
syscall.c:639: warning: type defaults to `int' in declaration of `_syscall6'
syscall.c:639: warning: data definition has no type or storage class
syscall.c:640: error: syntax error before "getdents"
syscall.c:640: warning: type defaults to `int' in declaration of `_syscall3'
syscall.c:640: warning: data definition has no type or storage class
syscall.c:641: error: syntax error before "getdents64"
syscall.c:641: warning: type defaults to `int' in declaration of `_syscall3'
syscall.c:641: warning: data definition has no type or storage class
syscall.c:666: error: syntax error before "_llseek"
syscall.c:674: warning: return type defaults to `int'
syscall.c: In function `_syscall5':

I'm using ubuntu and the kernel version is
kl2305-04:/media/sdb1/zesto> uname -a
Linux kl2305-04 2.6.22-15-generic #1 SMP Wed Aug 20 18:39:13 UTC 2008 i686 GNU/Linux

---

