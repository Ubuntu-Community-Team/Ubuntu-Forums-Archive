---
title: "help on using a library"
date: 2011-08-25
forum: Programming Talk
---

### Post by hadjimurad on 2011-08-25
I have a sparse matrix library libskit.a that I'm trying to use. When I compile with

gfortran -lskit test.o -o test.out

all of the calls to subroutines defined in the library give undefined references. However, when I instead use

gfortran libskit.a test.o -o test.out

then everything works fine. I have the .a file copied into /usr/lib and /usr/local/lib already; using other libraries like BLAS with the -l flag works just fine. Any ideas?

---

### Post by Bachstelze on 2011-08-25
-l flags go at the end of the command line. This should work:

```
gfortran -o test.out test.o -lskit
```

---

### Post by hadjimurad on 2011-08-27
Thanks, that worked. Man is that a silly mistake.

---

