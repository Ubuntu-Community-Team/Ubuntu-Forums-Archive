---
title: "Power PC Cross Compiling"
date: 2012-09-06
forum: Programming Talk
---

### Post by IAMTubby on 2012-09-06
Hey,
I was trying to cross compile an application for the PowerPC.

This is the error log that make gives
```

ppc_4xx-gcc: lpower: No such file or directory
make[1]: *** [libmylib.so] Error 1
make[1]: Leaving directory `/home/projects/lib/linux'
make: *** [build] Error 2

```

What should I do ?
Is it because one of the Makefiles in the application is not using a ppc_4xx-gcc ?

Please advise.

---

### Post by durdenstationer on 2012-09-06
How would we know what the issue in your makefile is without seeing your makefile?

---

