---
title: "libgfortran.so.3  _gfortran_copy_string"
date: 2010-11-11
forum: Packaging and Compiling Programs
---

### Post by darius007 on 2010-11-11
Hi 

I am running a code that needs certain libgfortran libraries.  Unfortunately I get this error message that  libgfortran.so.1 is  missing:

 libgfortran.so.1: cannot open shared object file: No such file or directory

I linked the ligfortran library as follows: sudo ln -s /usr/lib/libgfortran.so.3 /usr/lib/libgfortran.so.1

and now I got this error:

symbol lookup errorsymbol lookup error: :  ../../program/main/liblapack.so.3../../program/main/liblapack.so.3: :  undefined symbol: _gfortran_copy_stringundefined symbol:  _gfortran_copy_string

Thanks for your help.
Darius

---

### Post by SevenMachines on 2010-11-12
Can you recompile this code against libgfortran3? if so, thats the easiest way.
the library and the gcc version tend to be closely linked so although you can install the libgfortran1package you will likely need to install the equivalent version of various gcc packages to satisfy dependencies.

---

