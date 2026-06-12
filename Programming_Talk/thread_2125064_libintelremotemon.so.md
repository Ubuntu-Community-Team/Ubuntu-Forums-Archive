---
title: "libintelremotemon.so"
date: 2013-03-12
forum: Programming Talk
---

### Post by cmoo1010 on 2013-03-12
Hi there... I just installed INTEL FORTRAN COMPILLER XE 2011 in my desktop. First than all, i had a problem with IFORT command, i fixed it. But now when i'm trying to compilate i see this message:

[I]ifort: error while loading shared libraries: libintelremotemon.so: cannot open shared object file: No such file or directory

[/I]What i'm suposse to do?

Thanks for your help.

---

### Post by sanguinoso on 2013-03-13
Does > locate libintelremotemon.so return anything? You could just not have your LD_LIBRARY_PATH set properly.

---

