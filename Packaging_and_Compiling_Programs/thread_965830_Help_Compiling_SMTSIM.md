---
title: "Help Compiling SMTSIM"
date: 2008-10-31
forum: Packaging and Compiling Programs
---

### Post by SMTSIM on 2008-10-31
Hello,
I am trying to compile this Simulator:
[SMTSIM](http://www-cse.ucsd.edu/users/tullsen/smtsim2a.html)


When I try compiling with: make -f makefile.linux smtsim
I get the following IMPORTANT ERRORS:
syscalls.c:544: warning: passing arg 1 of `lstat' makes pointer from integer without a cast
syscalls.c:546: warning: passing arg 1 of `stat' makes pointer from integer without a cast
syscalls.c:558: structure has no member named `st_atim'
syscalls.c:559: structure has no member named `st_mtim'
syscalls.c:560: structure has no member named `st_ctim'

I cant figure this out, all I know is those members are associated with :
[<sys/stat.h>](http://www.opengroup.org/onlinepubs/000095399/basedefs/sys/stat.h.html)

any help is appreciate, I am pretty much a huge linux newb.

---

