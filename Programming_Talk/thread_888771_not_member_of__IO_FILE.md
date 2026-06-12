---
title: "not member of _IO_FILE"
date: 2008-08-13
forum: Programming Talk
---

### Post by unoodles on 2008-08-13
I am trying to port a program that creates a FILE* pointer then tries to access a part of it called _cnt and _ptr. In stdio.h the _IO_FILE struct only defines these on windows. What are the equivalents on Linux? And where can I read about what they do?

---

### Post by era86 on 2008-08-13
I don't know what the equivalences are, but a Google search found me this.

[http://homepages.cwi.nl/~daybuild/daily-docs/sdf-library/d0/d57/struct__IO__FILE.html](http://homepages.cwi.nl/~daybuild/daily-docs/sdf-library/d0/d57/struct__IO__FILE.html)

I remember accessing the different members of this struct in a previous problem I had.  Try debugging your program through DDD (based on GDB) and read the contents of it to understand it.

---

