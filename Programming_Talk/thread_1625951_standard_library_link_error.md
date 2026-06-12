---
title: "standard library link error?"
date: 2010-11-19
forum: Programming Talk
---

### Post by worksofcraft on 2010-11-19
I really don't understand this :confused:
I add line of code that has nothing to do with any standard library functions and the function fopen isn't even called in the module where the line of code was added and I get this error message:

```

./a.out: relocation error: ./a.out: symbol fopen, version GLIBC_2.2.5 not defined in file libc.so.6 with link time reference

```

What on earth does it mean :confused:

---

### Post by worksofcraft on 2010-11-19
That was a run time error on shared library use, so I put all the code in one big source file and then it compiled linked and worked just fine... so I split it all up again into separate modules and mysteriously it's still working :D

---

### Post by Arndt on 2010-11-20
> **worksofcraft said:**
> That was a run time error on shared library use, so I put all the code in one big source file and then it compiled linked and worked just fine... so I split it all up again into separate modules and mysteriously it's still working :D

I would probably have done "make clean" and "make".

---

