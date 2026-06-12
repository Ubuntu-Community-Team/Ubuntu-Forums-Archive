---
title: "Anjuta - RANLIB is undefined"
date: 2007-12-02
forum: Programming Talk
---

### Post by stodge on 2007-12-02
I'm trying to create a static library in Anjuta 2.20 but when I run autogen I get the error: 
 
libary used but RANLIB is undefined 
 
Any ideas how to fix this? 
 
Thanks

---

### Post by melopsittacus on 2009-07-09
Open configure.ac and add the line
```
AC_PROG_LIBTOOL
``` where you see the other AC_PROG* lines

(yes, I know it is a *very* old post, however as it came up among the first Google results when looking for this problem, I thought it might be useful to add the solution :))

---

