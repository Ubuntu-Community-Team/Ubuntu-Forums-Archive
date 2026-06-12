---
title: "kdevelop+ifort"
date: 2008-06-23
forum: Programming Talk
---

### Post by luisadeias on 2008-06-23
Hello,
I'm a newbie of Ubuntu/Linux and I've been trying in the last few days to get the Intel Fortran Compiler working with Kdevelop.

I installed the Intel Fortan Compiler 10.1.015 and it works (even in the konsole window inside kdevelop).
I installed Kdevelop and did as suggested in:
[http://www.kdevelop.org/mediawiki/index.php/how_to_use_Intel_fortran_compiler](http://www.kdevelop.org/mediawiki/index.php/how_to_use_Intel_fortran_compiler)

and I cannot figure out why it's not working.
I have automake, build-essential, libtool, autoconf.

this is what I get when I run "Run Automake & friends":

cd '/home/luisa/Scrivania/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -f Makefile.cvs
aclocal
autoheader
automake
src/Makefile.am: Fortran 77 source seen but `F77' is undefined
src/Makefile.am: The usual way to define `F77' is to add `AC_PROG_F77'
src/Makefile.am: to `configure.in' and run `autoconf' again.
make: *** [all] Error 1
*** Exited with status: 2 ***


while when I run "Run configure" I get:

cd '/home/luisa/Scrivania/helloworld' && F77=ifort "/home/luisa/Scrivania/helloworld/configure"
installing -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for ifort... no
checking for ifc... no
checking for Fortran compiler default output file name... 
configure: error: Fortran compiler cannot create executables
See `config.log' for more details.
*** Exited with status: 77 ***


It seems to me that it's not finding ifort!

my configure.in file inside the helloworld folder is the following:

AC_INIT(configure.in)

AM_INIT_AUTOMAKE(helloworld, 0.1)
AM_CONFIG_HEADER(config.h)

AC_PROG_FC([ifort ifc])

AC_OUTPUT(Makefile src/Makefile)


Thanks in advance for any help!!!!

Luisa.

---

### Post by jmk123 on 2008-07-17
i had the same issue and the webpage that everyone points to is wrong (i think!).  i just followed the instructions kdevelop gives:

The usual way to define `F77' is to add `AC_PROG_F77'
to `configure.in' and run `autoconf' again.

so here is my configure.in file:
AC_INIT(configure.in)

AM_INIT_AUTOMAKE(helloworld, 0.1)
AM_CONFIG_HEADER(config.h)

AC_PROG_FC([ifort ifc])
AC_PROG_F77

AC_OUTPUT(Makefile src/Makefile)

and this is the output i get:

cd '/{}/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" LC_MESSAGES="C" LC_CTYPE="C" make -k 
cd . && /bin/bash /{}/helloworld/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make all-recursive
Making all in src
ifort -O2 -c -o helloworld.o helloworld.f
ifort -O2 -o helloworld helloworld.o 
*** Success ***

so basically, just add AC_PROG_FC([ifort ifc]) and remove AC_LANG_FORTRAN77, AC_F77_LIBRARY_LDFLAGS

i don't know if this is the correct way to do things, but it compiles at least!

---

