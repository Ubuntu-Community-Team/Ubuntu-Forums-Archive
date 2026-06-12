---
title: "AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body"
date: 2012-05-01
forum: Packaging and Compiling Programs
---

### Post by shahinab123 on 2012-05-01
Hi,

When I run configure -isf command, I get this warning:
configure.in:189: warning: AC_LANG_CONFTEST: no AC_LANG_SOURCE call detected in body.

In line 189 I have: GLD_GET_NPROCS

and in gld_get_nprocs.m4 I have:

AC_DEFUN([GLD_GET_NPROCS],[ 
  AC_MSG_CHECKING([for get_nprocs]) 
  AC_COMPILE_IFELSE([#include <sys/sysinfo.h> 
      int main() { get_nprocs(); return 0; }], 
    AC_MSG_RESULT([yes]); AC_DEFINE(HAVE_GET_NPROCS, 1, [Define this if get_nprocs is available]), 
    AC_MSG_RESULT([no])) 
]) 
What do you think is generating that warning?

---

### Post by oldos2er on 2012-05-01
Moved to Packaging and Compiling Programs.

---

