---
title: "Debugging a Fortran Program"
date: 2010-02-06
forum: Programming Talk
---

### Post by CaKiwi on 2010-02-06
I have compiled a Fortran program by using

gfortran -ggdb file.f90

To try to step through it in the debugger, I enter

gdb a.out

but I cannot create a break point. I have tried a number of commands including

b <line number>
b <subroutine name>

What am I missing here?

---

### Post by croto on 2010-02-06
try indicating the file name. If for instance you want a breakpoint in line 10:
```

break file.f90:10

```

---

### Post by CaKiwi on 2010-02-06
Thanks for the response, Croto. For some reason

```
break <line number>
```

is working now.

---

