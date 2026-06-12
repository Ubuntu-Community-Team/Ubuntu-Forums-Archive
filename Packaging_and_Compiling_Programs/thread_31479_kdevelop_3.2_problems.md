---
title: "kdevelop 3.2 problems"
date: 2005-05-03
forum: Packaging and Compiling Programs
---

### Post by philstovell on 2005-05-03
I've installed all the kdevelop3 packages, fired it up and tried to compile a simple hello world program, from the automatically generated source code. When I click build, a dialog asks me to run automake & friends and configure first. I click yes, and it then comes up with the error: aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library.

Here's the whole contents of the output:

cd '/home/phil/src/hello' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/phil/src/hello/debug' && cd '/home/phil/src/hello/debug' && CXXFLAGS="-O0 -g3" "/home/phil/src/hello/configure" --enable-debug=full && cd '/home/phil/src/hello/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
make: *** [all] Error 1
*** Exited with status: 2 ***


Anybody any ideas?

Cheers, Phil.

---

### Post by rhys on 2005-05-03
[QUOTE=philstovell]I've installed all the kdevelop3 packages, fired it up and tried to compile a simple hello world program, from the automatically generated source code. When I click build, a dialog asks me to run automake & friends and configure first. I click yes, and it then comes up with the error: aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library.

Here's the whole contents of the output:

cd '/home/phil/src/hello' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/phil/src/hello/debug' && cd '/home/phil/src/hello/debug' && CXXFLAGS="-O0 -g3" "/home/phil/src/hello/configure" --enable-debug=full && cd '/home/phil/src/hello/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
make: *** [all] Error 1
*** Exited with status: 2 ***


Anybody any ideas?

Cheers, Phil.[/QUOTE]
 Go into Synaptic and download libtool :)

---

### Post by philstovell on 2005-05-04
[QUOTE=rhys]Go into Synaptic and download libtool :)[/QUOTE]
 Yes, installing libtool was the solution. Thanks very much for your help.

---

### Post by Lord Illidan on 2005-07-09
Thanks, this worked for me too!!

---

### Post by matomem on 2005-07-17
\\:D/  under construction

---

### Post by Biased turkey on 2005-09-26
Thanks a lot for the info rhys, installing libtool worked for me too.
Shouldn't apt-get install automatically install libtool when required to install kdevelop3.2 ?
I thought that by installing Ubuntu I would be free forever of packages dependency hell :)

---

### Post by mpx on 2005-10-31
I'm facing the same problem after upgrading to Breezy Badger.

Using syaptic update manager, when I try to mark libtool for installation, a dialog  comes up with the following error:

libtool: 
Depends: libc6-dev but it is not going to be installed or libc-dev

And when I try to install libc I get the following error:

libc6-dev:
  Depends: libc6 (=2.3.5-1ubuntu12) but 2.3.5-4 is to be installed

Please help. Thanks.

---

