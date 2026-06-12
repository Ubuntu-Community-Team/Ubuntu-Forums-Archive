---
title: "varargs.h &gt; stdarg.h"
date: 2007-06-08
forum: Programming Talk
---

### Post by haftan on 2007-06-08
I have some old code to compile with my fatal.c (and others) using varargs.h
When I make, it tells me to upgrade to stdarg.h
Is it possible for me to install(?) varargs.h and compile/run my old code ... as is.
Or do I have to revise EVERYTHING that used varargs.h to use the stdarg.h macros, etc.?

---

### Post by hod139 on 2007-06-16
varargs.h came before ANSI C and standards.  If you plan on distributing this code you should seriously consider upgrading to the standard header.  If it is just some old cold that you want for yourself only, you should be fine using varargs.h.

---

