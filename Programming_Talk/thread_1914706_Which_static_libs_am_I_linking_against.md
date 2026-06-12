---
title: "Which static libs am I linking against"
date: 2012-01-24
forum: Programming Talk
---

### Post by hwttdz on 2012-01-24
At the link stage of a build how can I tell which static libs I'm linking against?  I'm calling gfortran as my linker which I assume is invoking ld.  I have my own copy of the libs in my home dir, and I want to know if I'm linking against /usr/lib, /usr/local/lib or ~/lib.  ldd of course only tells me shared libs, and these are being linked in statically.

---

### Post by hwttdz on 2012-01-27
Answer: pass gfortran (when being called as the linker) the --trace flag.  In order to get it to go to the linker it needs to be preceded by -Wl, 

Example: gfortran -Wl,--trace -o hello_world.exe hello_world.o other_object_file.o -llapack -lblas

This will tell you not only which lapack and atlas you are using, but also which other libraries gfortran is linking in.

---

