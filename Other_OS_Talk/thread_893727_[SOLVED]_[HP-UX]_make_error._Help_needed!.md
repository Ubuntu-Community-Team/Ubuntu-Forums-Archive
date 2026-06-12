---
title: "[SOLVED] [HP-UX] make error. Help needed!"
date: 2008-08-18
forum: Other OS Talk
---

### Post by RebounD11 on 2008-08-18
Hi everybody,

I'm running HP-UX 11.00 with gcc 3.3.2 and I am trying to compile an application from source. Running "./configure" is succesful but when I run "make" I get the following error:

```
/usr/ccs/bin/ld: unsatisfied symbols: pwrite(code)
collect2: ld returned 1 exit status
```

Any help is appreciated. I will give more details if needed and if I can provide them.

---

### Post by fistfullofroses on 2008-08-19
First, it sounds like you may have a version conflict between bin-utils and GCC. I am not sure about the userland included in HPUX, but you ought to have an equivalent package somewhere.

Next make sure that you have autoconf, automake, make, bin-utils, and GCC with a compatible libc (glibc, uClibc, or whatever).

---

### Post by D-EJ915 on 2008-08-20
you using gmake? you should be if you're not

---

