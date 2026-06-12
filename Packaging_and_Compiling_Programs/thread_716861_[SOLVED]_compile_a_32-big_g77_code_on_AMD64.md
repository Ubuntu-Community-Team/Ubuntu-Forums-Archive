---
title: "[SOLVED] compile a 32-big g77 code on AMD64"
date: 2008-03-06
forum: Packaging and Compiling Programs
---

### Post by dimkal on 2008-03-06
is it possible to compile a 32-bit code (using g77) on an AMD64 processor running on an AMD64 Hardy?

---

### Post by dimkal on 2008-03-09
OK i figured this out on my own.  You must install the gcc-multilib package, and compile with the -m32 switch...


%> g77 -m32 -o test32 test.f

%> file test32
test32:  ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), not stripped

---

