---
title: "Generating Fortran Documentation with Doxygen"
date: 2010-07-07
forum: Programming Talk
---

### Post by C-- on 2010-07-07
So I'm trying to generate Fortran documentation with Doxygen, but no matter what I do Doxygen won't display more than one subroutine for a given file. Even if I have no Doxygen comments in the source file, it only displays the first subroutine.

Does anyone know how to solve this?

Thanks.

---

### Post by C-- on 2010-07-12
OK nevermind; you have to explicitly specify that you want to EXTRACT_ALL methods in the doxygen config file, to inclue subroutines that are marked as private.

---

