---
title: "which package required for gtk+ programming"
date: 2007-05-20
forum: Programming Talk
---

### Post by u04f061 on 2007-05-20
which packages are required for programming in gtk+ using c or c++.
there is problem for me in searching apt for gtk+. it displays a lot of softwares and i don't know which do i need.

second thing i have a problem with kdevelop. i want to use it as an ide for simple c programs which don't use gtk+ or any other library. when i write simple hello world c program and want to build project , it gives following error > /home/ejaz/cproj/check/debug
There is no Makefile in this directory
and no configure script for this project.
Run automake & friends and configure first?  
i installed automake and when again i pressed build project , it gave followiing error
> cd '/home/ejaz/cproj/check' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/ejaz/cproj/check/debug' && cd '/home/ejaz/cproj/check/debug' && CFLAGS="-O0 -g3 " "/home/ejaz/cproj/check/configure" --enable-debug=full && cd '/home/ejaz/cproj/check/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
configure.in:8: warning: macro `AM_PROG_LIBTOOL' not found in library
autoheader
automake
autoconf
configure.in:8: error: possibly undefined macro: AM_PROG_LIBTOOL If this token and others are legitimate, please use m4_pattern_allow. See the Autoconf documentation.
make: *** [all] Error 1
*** Exited with status: 2 ***


---

### Post by hod139 on 2007-05-20
For gtk development files, install libgtk2.0-dev.

To fix the kdevelop error you are seeing, try installing the package libtool.

---

### Post by u04f061 on 2007-05-20
thanks. my problem is solved
can you tell me is there any program for gtk+ like QT assistant?

---

### Post by kknd on 2007-05-20
For Cpp:

libgtkmm-dev.

It will download all other dependencies, but remember to update the library (ldconfig as root) and to include the headers and link againt the libs when compiling!

---

### Post by seamless on 2007-05-20
> **u04f061 said:**
> thanks. my problem is solved
can you tell me is there any program for gtk+ like QT assistant?
Glade is the equivalent for GTK+. Also remember that GTK+ is a C library if you want to develop with C++ you should use GTKmm (C++ bindings for GTK+).

---

### Post by u04f061 on 2007-05-20
can any body explain this > It will download all other dependencies, but remember to update the library (ldconfig as root) and to include the headers and link againt the libs when compiling!

i mean how to compile and include.
i am new to this

---

