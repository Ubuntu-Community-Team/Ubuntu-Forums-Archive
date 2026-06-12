---
title: "compiling a fortran program"
date: 2005-06-16
forum: Programming Talk
---

### Post by andrewL on 2005-06-16
Hi,  I am attempting to compile a program but I am having trouble with my ubunto recognizing my compiler.  I think I need to make a symbolic link to the c compiler.    When I am at the command line I type in gcc and it says:

gcc: Command not found.

  Which leads me to think that the link to the c compiler is not working for me.  If I type in gcc-4.0 it says:

gcc-4.0: no input files

  Does someone know how to fix this?

  I am trying to install a program called cns which requires c and fortran.  This is how I found out that there was a problem with my c compiler and my fortran compiler.  The directions for the installation says:

# in the CNSsolve directory type:
    * make install

# before using CNSsolve:
    * source cns_solve_env

When I type make install I get errors that look like this:

making compiler-test directory in intel-i686-linux
testing Fortran and C compilers
compiling: cc -O -ffast-math -DCNS_ARCH_TYPE_LINUX
/bin/sh: cc: command not found
/bin/sh: ./test_c: No such file or directory
***** ERROR: problem with C compiler *****
make[3]: *** [c-test] Error 3
compiling: fort77 -w -Nn2000 -O3 -malign-double -funroll-loops -ffast-math
   MAIN hello:
/usr/bin/fort77: aborting compilation
linking: fort77
/bin/sh: ./test_f: No such file or directory
***** ERROR: problem with Fortran compiler *****
make[3]: *** [fortran-test] Error 2
make[2]: *** [compiler-test] Error 2
make[1]: *** [compiler-test] Error 2
compiler problems - stopping installation
please check compilers before retrying installation
make: *** [install] Error 1



Any help would be greatly appreciated.  

Thanks,
andrew

:-)

---

### Post by desdinova on 2005-06-16
[QUOTE=andrewL]Hi, I am attempting to compile a program but I am having trouble with my ubunto recognizing my compiler. I think I need to make a symbolic link to the c compiler. When I am at the command line I type in gcc and it says:

gcc: Command not found.

  Which leads me to think that the link to the c compiler is not working for me.  If I type in gcc-4.0 it says:

gcc-4.0: no input files

  Does someone know how to fix this?

 I am trying to install a program called cns which requires c and fortran. This is how I found out that there was a problem with my c compiler and my fortran compiler. The directions for the installation says:

# in the CNSsolve directory type:
    * make install

# before using CNSsolve:
    * source cns_solve_env

When I type make install I get errors that look like this:

making compiler-test directory in intel-i686-linux
testing Fortran and C compilers
compiling: cc -O -ffast-math -DCNS_ARCH_TYPE_LINUX
/bin/sh: cc: command not found
/bin/sh: ./test_c: No such file or directory
***** ERROR: problem with C compiler *****
make[3]: *** [c-test] Error 3
compiling: fort77 -w -Nn2000 -O3 -malign-double -funroll-loops -ffast-math
   MAIN hello:
/usr/bin/fort77: aborting compilation
linking: fort77
/bin/sh: ./test_f: No such file or directory
***** ERROR: problem with Fortran compiler *****
make[3]: *** [fortran-test] Error 2
make[2]: *** [compiler-test] Error 2
make[1]: *** [compiler-test] Error 2
compiler problems - stopping installation
please check compilers before retrying installation
make: *** [install] Error 1



Any help would be greatly appreciated.  

Thanks,
andrew

:-)[/QUOTE]

This may be a little off topic but you can register at Intel's website for a free copy of their fortran compiler...

---

### Post by andrewL on 2005-06-16
Thanks for info.  I'll try out the fortran compiler but I don't know if that'll fix my c compiler issue.

ciao,
 Andrew

:-)

---

### Post by az on 2005-06-16
Install build-essential and g77

(g77 is the fortran compiler)

---

### Post by andrewL on 2005-06-16
I've been fiddling around with this problem for weeks and nothing was working until today.  Your suggestion of getting build-essential seems to be working.  At least it's doing stuff and not telling me that it has to crash now.

thanks,
Andrew
:-)

---

