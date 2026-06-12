---
title: "Making a valid DEB package"
date: 2013-02-27
forum: Programming Talk
---

### Post by checoimg on 2013-02-27
Hi guys I have some questions, number one is how do I compile a program so that the program file can be used by any user and where should I put the program /bin or /usr/bin.

And of course ths steps for making a .deb package. And I don't know how to make compilations apart from the default I believe other architectures are needed.

Thank you in advance.

---

### Post by r-senior on 2013-02-27
You don't need to do anything special during compilation to make a file that can be executed by any user. It just needs to be in a place they can access it and have the appropriate permissions, usually world execute. For example, note the location, permissions and ownership of a typical shared program like bash.

```
$ ls -l /bin/bash
-rwxr-xr-[COLOR="Red"]x[/COLOR] 1 [COLOR="red"]root root[/COLOR] 955024 Apr  3  2012 [COLOR="Red"]/bin[/COLOR]/bash
```

It's not usually as simple as compiling and copying though (unless it's for your own machine only).  You as the developer might know what to do, but someone else installing the program needs a consistent install method.

Assuming you are talking about C/C++ here, applications are usually built using [make]("http://www.gnu.org/software/make/manual/") and an install target specified to install the program as root into the correct place.

You could create the makefiles manually, but it's more common for GNU software to be built with autotools ([autoconf]("http://www.gnu.org/software/autoconf/") and [automake]("http://www.gnu.org/software/automake/manual/")). These tools create a configure script that analyses the system on which the program is to be installed, checks pre-requisuites are present and generates makefiles based on system configuration so programs can be made more portable. It looks impossibly difficult at first but it's not too bad when you get into it and writes a much better build system than you would write by hand. The automake manual has a good overview and [this is a nice little beginner's tutorial]("http://markuskimius.wikidot.com/programming:tut:autotools").

The end result of GNU autotools is that the installation process is consistent across packages and looks something like this:

```
$ tar xzvf someprogram-1.0.tar.gz
$ cd someprogram-1.0
$ ./configure
$ make
$ sudo make install
```

Packaging into a .deb file is a large topic, but there is an [Ubuntu Packaging Guide]("http://developer.ubuntu.com/packaging/html/index.html") that covers the process in detail.

The Ubuntu forums also have a [Ubuntu: Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44") forum.

---

### Post by checoimg on 2013-02-27
Thank you for your response r-senior.

---

### Post by checoimg on 2013-03-01
Chapter 2 i get this error when I try "make clean all" : Makefile:6: *** missing separator.  Stop. I suppose is indicating this separator missing in line 6.

---

### Post by schragge on 2013-03-01
Ensure that you use TAB characters as opposite to spaces at the beginning of lines in your Makefile. BTW, what version of *make* are you using. Starting with version 3.78, GNU is a bit more specific about it:
```

Makefile:6: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

```

---

### Post by checoimg on 2013-03-01
> **schragge said:**
> Ensure that you use TAB characters as opposite to spaces at the begininng of lines in your Makefile. BTW, what version of *make* are you using. Starting with version 3.78, GNU is a bit more specific about it:
```

Makefile:6: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.

```

This is the version: make 3.81-8.2ubuntu2
It had three spaces instead of a TAB character, when I changed it the "rm" became bold and "make clean all" worked just fine. Thank you schragge.

---

### Post by checoimg on 2013-03-01
Chapter 4

user@user:~/clscr-1.0$ automake
configure.ac: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.ac: You should verify that configure.ac invokes AM_INIT_AUTOMAKE,
configure.ac: that aclocal.m4 is present in the top-level directory,
configure.ac: and that aclocal.m4 was recently regenerated (using aclocal).
Makefile.am: required file `./INSTALL' not found
Makefile.am:   `automake --add-missing' can install `INSTALL'
Makefile.am: required file `./NEWS' not found
Makefile.am: required file `./README' not found
Makefile.am: required file `./AUTHORS' not found
Makefile.am: required file `./ChangeLog' not found
Makefile.am: required file `./COPYING' not found
Makefile.am:   `automake --add-missing' can install `COPYING'
Makefile.am: required file `./depcomp' not found
Makefile.am:   `automake --add-missing' can install `depcomp'
/usr/share/automake-1.11/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.11/am/depend2.am:   The usual way to define `am__fastdepCC' is to add `AC_PROG_CC'
/usr/share/automake-1.11/am/depend2.am:   to `configure.ac' and run `aclocal' and `autoconf' again.
/usr/share/automake-1.11/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.11/am/depend2.am:   The usual way to define `AMDEP' is to add one of the compiler tests
/usr/share/automake-1.11/am/depend2.am:     AC_PROG_CC, AC_PROG_CXX, AC_PROG_CXX, AC_PROG_OBJC,
/usr/share/automake-1.11/am/depend2.am:     AM_PROG_AS, AM_PROG_GCJ, AM_PROG_UPC
/usr/share/automake-1.11/am/depend2.am:   to `configure.ac' and run `aclocal' and `autoconf' again.

---

### Post by schragge on 2013-03-01
I suppose you have AM_INIT_AUTOMAKE in your configure.ac. Then try

```

autoreconf --install
./configure

```

---

### Post by checoimg on 2013-03-01
> **schragge said:**
> I suppose you have AM_INIT_AUTOMAKE in your configure.ac. Then try

```

autoreconf --install
./configure

```

I still get the same error here is my Makefile :

# Makefile: A standard Makefile for clscr.c

all: clscr

clean:
    rm -f clscr *.o

---------------------------------------------------------------------------
maybe I need something for install.

---

### Post by r-senior on 2013-03-01
You are writing a Makefile but then using automake. That doesn't make sense. If you want to use automake, the input file is Makefile.am and probably looks something like this:

```
bin_PROGRAMS = clrscr

clrscr_SOURCES = clrscr.c

```

The configure script builds Makefile from Makefile.am via Makefile.in.

It would probably be a good idea to post the contents of your configure.ac file so that we can see what is going on.

---

### Post by checoimg on 2013-03-01
configure.ac :

#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([FULL-PACKAGE-NAME], [VERSION], [BUG-REPORT-ADDRESS])
AC_CONFIG_SRCDIR([clscr.c])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CC

# Checks for libraries.

# Checks for header files.

# Checks for typedefs, structures, and compiler characteristics.

# Checks for library functions.

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

---

### Post by r-senior on 2013-03-01
Good. Now add a line after the AC_CONFIG_HEADERS line that invokes automake:

```
AM_INIT_AUTOMAKE
```

I think you also need this line after AC_PROG_CC to allow automake to build object files:

```
AM_PROG_CC_C_O
```

Then run these commands and see how it goes:

```

autoreconf --force
automake --add-missing
./configure

```

If that works:

```
make
```

Then you should have a compiled clrscr program. Unless I forgot a step, in which case, post your error messages.

EDIT: You will also need the Makefile.am file that I showed above, so don't forget to create that.

---

### Post by checoimg on 2013-03-01
autoreconf --force :

user@user:~/clscr-1.0$ autoreconf --force
configure.ac:12: required file `./compile' not found
configure.ac:12:   `automake --add-missing' can install `compile'
configure.ac:11: required file `./install-sh' not found
configure.ac:11:   `automake --add-missing' can install `install-sh'
configure.ac:11: required file `./missing' not found
configure.ac:11:   `automake --add-missing' can install `missing'
Makefile.am: required file `./INSTALL' not found
Makefile.am:   `automake --add-missing' can install `INSTALL'
Makefile.am: required file `./NEWS' not found
Makefile.am: required file `./README' not found
Makefile.am: required file `./AUTHORS' not found
Makefile.am: required file `./ChangeLog' not found
Makefile.am: required file `./COPYING' not found
Makefile.am:   `automake --add-missing' can install `COPYING'
Makefile.am: required file `./depcomp' not found
Makefile.am:   `automake --add-missing' can install `depcomp'
autoreconf: automake failed with exit status: 1

---

### Post by checoimg on 2013-03-01
automake --add-missing :

user@user:~/clscr-1.0$ automake --add-missing
configure.ac:12: installing `./compile'
configure.ac:11: installing `./install-sh'
configure.ac:11: installing `./missing'
Makefile.am: installing `./INSTALL'
Makefile.am: required file `./NEWS' not found
Makefile.am: required file `./README' not found
Makefile.am: required file `./AUTHORS' not found
Makefile.am: required file `./ChangeLog' not found
Makefile.am: installing `./COPYING' using GNU General Public License v3 file
Makefile.am:     Consider adding the COPYING file to the version control system
Makefile.am:     for your code, to avoid questions about which license your project uses.
Makefile.am: installing `./depcomp'

---

### Post by r-senior on 2013-03-01
That's OK, you always get errors at that point. Do the next one:

```
automake --add-missing
```

---

### Post by r-senior on 2013-03-01
Ah, OK, I did forget a step. GNU programs expect some standard files. Run this to create empty ones:

```
touch AUTHORS ChangeLog NEWS README
```

---

### Post by checoimg on 2013-03-01
ok I will do that when back home, on a class now...

---

### Post by checoimg on 2013-03-01
still get this error :

#make: *** No rule to make target `install'.  Stop.

---

### Post by r-senior on 2013-03-01
Did you create the Makefile.am file?

Does 'make' work, i.e. does it build the program.

Could you post the output you get when you run configure?

Also a directory listing of your project, created using 'ls -R'.

---

### Post by checoimg on 2013-03-01
user@user:~/clscr-1.0$ ls -R
.:
aclocal.m4      clscr.c~       config.status    doc-pak       Makefile.in
AUTHORS         compile        configure        INSTALL       missing
autom4te.cache  config.h       configure.ac     install-sh    NEWS
autoscan.log    config.h.in    configure.ac~    Makefile      README
ChangeLog       config.h.in~   COPYING          Makefile~     stamp-h1
clscr           config.h.save  depcomp          Makefile.am
clscr.c         config.log     description-pak  Makefile.am~

./autom4te.cache:
output.0  output.1  output.2  requests  traces.0  traces.1  traces.2

./doc-pak:
AUTHORS  ChangeLog  COPYING  INSTALL  NEWS  README

---

### Post by checoimg on 2013-03-01
user@user:~/clscr-1.0$ ./configure
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands

---

### Post by checoimg on 2013-03-01
Makefile.am
```
bin_PROGRAMS=clscr
clscr_SOURCES=clscr.c
```

---

### Post by checoimg on 2013-03-01
Make works because there is a compiled program.

---

### Post by r-senior on 2013-03-01
The configure output looks fine. Does the program build properly with make? Can you clean and rebuild?

Check that your Makefile.am is using the correct names. I misread your earlier posts as 'clrscr', but Makefile.am should have references to 'clscr'.

---

### Post by checoimg on 2013-03-01
> **r-senior said:**
> The configure output looks fine. Does the program build properly with make? Can you clean and rebuild?

Check that your Makefile.am is using the correct names. I misread your earlier posts as 'clrscr', but Makefile.am should have references to 'clscr'.

Yes I just rebuilt

---

### Post by r-senior on 2013-03-01
Everything looks fine to me. If it builds and cleans, it looks as though autoconf and automake are set up correctly.

Are you saying make is building the program but there is no "make install" target? Are you running "make install" with sudo?

---

### Post by checoimg on 2013-03-01
> **r-senior said:**
> Everything looks fine to me. If it builds and cleans, it looks as though autoconf and automake are set up correctly.

Are you saying make is building the program but there is no "make install" target? Are you running "make install" with sudo?

I erased the program and did make; When I do ```
sudo make install
``` I get the error : make: *** No rule to make target `install'.  Stop.

---

### Post by r-senior on 2013-03-01
In that case I don't understand. The configure output clearly shows that automake is creating "Makefile" and this should definitely produce an install target.

Maybe you could try one of these targets and see if they work?

```
make dist
make distcheck

```

Or how about opening up Makefile with a text editor and seeing what targets it has. (It should be pretty long).

If none of that helps, I'd make a new project directory, copy in configure.ac, Makefile.am, clscr.c, plus the AUTHORS, NEWS, ChangeLog and README and start again:

```
autoreconf
automake --add-missing
./configure
make
sudo make install

```

---

### Post by checoimg on 2013-03-01
```

user@user:~/clscr-1.0$ ls
AUTHORS         autoscan.log  clscr.c    configure.ac  Makefile.in  README
autom4te.cache  ChangeLog     configure  Makefile.am   NEWS

```

Should I erase autom4te.cache ?

---

### Post by checoimg on 2013-03-01
```
user@user:~/clscr-1.0$ automake --add-missing
configure.ac: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.ac: You should verify that configure.ac invokes AM_INIT_AUTOMAKE,
configure.ac: that aclocal.m4 is present in the top-level directory,
configure.ac: and that aclocal.m4 was recently regenerated (using aclocal).
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING' using GNU General Public License v3 file
Makefile.am:     Consider adding the COPYING file to the version control system
Makefile.am:     for your code, to avoid questions about which license your project uses.
Makefile.am: installing `./depcomp'
/usr/share/automake-1.11/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.11/am/depend2.am:   The usual way to define `am__fastdepCC' is to add `AC_PROG_CC'
/usr/share/automake-1.11/am/depend2.am:   to `configure.ac' and run `aclocal' and `autoconf' again.
/usr/share/automake-1.11/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.11/am/depend2.am:   The usual way to define `AMDEP' is to add one of the compiler tests
/usr/share/automake-1.11/am/depend2.am:     AC_PROG_CC, AC_PROG_CXX, AC_PROG_CXX, AC_PROG_OBJC,
/usr/share/automake-1.11/am/depend2.am:     AM_PROG_AS, AM_PROG_GCJ, AM_PROG_UPC
/usr/share/automake-1.11/am/depend2.am:   to `configure.ac' and run `aclocal' and `autoconf' again.
```

---

### Post by r-senior on 2013-03-02
OK, let me try:

*configure.ac*
```
AC_PREREQ([2.69])
AC_INIT([FULL-PACKAGE-NAME], [VERSION], [BUG-REPORT-ADDRESS])
AC_CONFIG_SRCDIR([clscr.c])
AC_CONFIG_HEADERS([config.h])
AM_INIT_AUTOMAKE

AC_PROG_CC
AM_PROG_CC_C_O

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

```

*Makefile.am*
```
bin_PROGRAMS=clscr
clscr_SOURCES=clscr.c
```

*clscr.c*
```
#include <stdio.h>

int main()
{
	puts("clscr");
	return 0;
}

```

And here is the build and install:

```
$ ls
clscr.c  configure.ac  Makefile.am
$ touch AUTHORS ChangeLog NEWS README
$ autoreconf
configure.ac:12: required file `./compile' not found
configure.ac:12:   `automake --add-missing' can install `compile'
configure.ac:8: required file `./install-sh' not found
configure.ac:8:   `automake --add-missing' can install `install-sh'
configure.ac:8: required file `./missing' not found
configure.ac:8:   `automake --add-missing' can install `missing'
Makefile.am: required file `./INSTALL' not found
Makefile.am:   `automake --add-missing' can install `INSTALL'
Makefile.am: required file `./COPYING' not found
Makefile.am:   `automake --add-missing' can install `COPYING'
Makefile.am: required file `./depcomp' not found
Makefile.am:   `automake --add-missing' can install `depcomp'
autoreconf: automake failed with exit status: 1
$ automake --add-missing
configure.ac:12: installing `./compile'
configure.ac:8: installing `./install-sh'
configure.ac:8: installing `./missing'
Makefile.am: installing `./INSTALL'
Makefile.am: installing `./COPYING' using GNU General Public License v3 file
Makefile.am:     Consider adding the COPYING file to the version control system
Makefile.am:     for your code, to avoid questions about which license your project uses.
Makefile.am: installing `./depcomp'
$ ls
aclocal.m4  autom4te.cache  clscr.c  config.h.in  configure.ac  depcomp  install-sh   Makefile.in  NEWS
AUTHORS     ChangeLog       compile  configure    COPYING       INSTALL  Makefile.am  missing      README
$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands
$ make
make  all-am
gcc -DHAVE_CONFIG_H -I.     -g -O2 -MT clscr.o -MD -MP -MF .deps/clscr.Tpo -c -o clscr.o clscr.c
mv -f .deps/clscr.Tpo .deps/clscr.Po
gcc  -g -O2   -o clscr clscr.o  
$ sudo make install
 /bin/mkdir -p '/usr/local/bin'
  /usr/bin/install -c clscr '/usr/local/bin'
$ clscr
clscr
```

If you start with the files as listed above, including the AUTHORS, NEWS, etc, you should get the same results. Then you need to do some reading about automake and autoconf so that you are more self-sufficient when something goes wrong.

---

### Post by checoimg on 2013-03-10
I was able to fix the error : ```
make: *** No rule to make target `install'.  Stop.
```

And made a .DEB package with checkintall

The package is working but I still get the "too bad quality" message while installing.

---

