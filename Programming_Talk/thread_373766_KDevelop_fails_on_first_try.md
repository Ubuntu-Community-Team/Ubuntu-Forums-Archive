---
title: "KDevelop fails on first try"
date: 2007-03-01
forum: Programming Talk
---

### Post by glue on 2007-03-01
I'm trying KDevelop. I did what the documentation says...built an new project, select C++/Simple KDE, and filled out the rest of the app wizard. I try to execute the simple project, a dialog box appears and I get it to do whatever it does like the documentation says but instead of the program running it spits out...

cd '/media/windows/Kubuntu/CppWork/kdetest3' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/media/windows/Kubuntu/CppWork/kdetest3/debug' && cd '/media/windows/Kubuntu/CppWork/kdetest3/debug' && CXXFLAGS="-O0 -g3" "/media/windows/Kubuntu/CppWork/kdetest3/configure" --enable-debug=full && cd '/media/windows/Kubuntu/CppWork/kdetest3/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
This Makefile is only for the CVS repository
This will be deleted before making the distribution

*** Creating acinclude.m4
*** Creating list of subdirectories
*** Creating configure.in
*** Creating aclocal.m4
*** Creating configure
*** Creating config.h template
*** Creating Makefile templates
Makefile.am: required file `./INSTALL' not found
Makefile.am: required file `./NEWS' not found
Makefile.am: required file `./README' not found
Makefile.am: required file `./AUTHORS' not found
make[1]: *** [cvs] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

What's going on? I look in the directory and all those required files are there. How do I fix this?

---

