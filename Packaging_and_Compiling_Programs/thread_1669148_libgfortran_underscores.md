---
title: "libgfortran underscores"
date: 2011-01-17
forum: Packaging and Compiling Programs
---

### Post by wari on 2011-01-17
Hi everyone!

Last friday I was trying to compile a mathematical model, which called some functions like "system_" and "unlink_" (notice the underscores). After some googling I realized that these functions were provided by libgfortran, but the version I had provides them without the trailing underscore ("system" and "unlink").

If I try to compile the model using the "-fno-underscoring" flag, it breaks the compatibility with netCDF library.

After some grepping into gcc source code, I found that libgfortran was compiled with the flag (AM_FCFLAGS) "-fno-underscoring" (gcc-4.4-4.4.4/src/libgfortran/configure, line 3415), that made me think of  recompiling the library without that flag to make it usable for my model.

Is it a good idea to make it work?? Which file should I modify? In this folder at least there are 2 that look as candidates (configure and configure.ac)

Any advice on this would be great.

---

### Post by gmargo on 2011-01-17
Can you provide an additional source file that will translate the underscored system calls to the appropriate names?  That's what the C programmer in me would do; I can't speak for Fortran though.  Recompiling a shared library seems like a drastic first step.  Plus it would break all of your other Fortran programs.

---

### Post by wari on 2011-01-17
The problem is that in the fortran source code of my model, the calls are made to the "system" and "unlink" functions, and the compiler changes them to "system_" and "unlink_" in the compiled code, so it fails in the linking stage, it does not find the underscored functions in libgfortran.

It seems that there is no other way to overcome this issue.

---

### Post by MadCow108 on 2011-01-18
have you tried -fno-second-underscore?

---

