---
title: "Help installing a non-repository program"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Leigen_Zero on 2008-05-27
Hello there, I am trying to install gnuitar 0.3.2
when I follow the readme and type ./configure in the directory i unzipped it to I get the following errors:
```

george@george-laptop:~/Desktop/gnuitar-0.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... missing
checking for working autoconf... missing
checking for working automake-1.4... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gawk... no
checking for mawk... mawk
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for glib-config... no
checking for GLIB - version >= 1.2.6... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.2.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Test for GLIB2 failed. See the file 'INSTALL' for help.

```

If anyone could help me it would be much appreciated

---

### Post by spiderbatdad on 2008-05-27
```
sudo apt-get install build-essential autoconf automake-1.4
```

---

### Post by osamaao on 2008-05-28
I have the same problem, tired to run: sudo apt-get install build-essential autoconf automake-1.4

output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
autoconf is already the newest version.
E: Couldn't find package automake-1.4

---

### Post by kpkeerthi on 2008-05-28
The package name is **automake1.4**.

See [http://packages.ubuntu.com/hardy/automake1.4](http://packages.ubuntu.com/hardy/automake1.4)

---

### Post by pedro_orange on 2008-05-28
```
sudo apt-get install automake
```

This is the list in the repo:

```
pedro@pedro-laptop:~$ apt-cache search automake
autoconf - automatic configure script builder
autoconf-doc - automatic configure script builder documentation
automake - A tool for generating GNU Standards-compliant Makefiles
automake1.4 - A tool for generating GNU Standards-compliant Makefiles
automake1.7 - A tool for generating GNU Standards-compliant Makefiles
automake1.8 - A tool for generating GNU Standards-compliant Makefiles
automake1.8-doc - A tool for generating GNU Standards-compliant Makefiles
automake1.9 - A tool for generating GNU Standards-compliant Makefiles
automake1.9-doc - A tool for generating GNU Standards-compliant Makefiles
autotools-dev - Update infrastructure for config.{guess,sub} files
gnome-common - common scripts and macros to develop with GNOME or GNOME 2.0
pkg-config - manage compile and link flags for libraries
qt3-designer - Qt3 Designer
autobook - GNU Autoconf, Automake and Libtool Book
autoproject - create a skeleton source package for a new program
ftjam - FreeType version of Jam, a replacement for make
jam - Software-build tool, replacement for make
kapptemplate - creates a framework to develop a KDE application
libticables2-dev - support library for Texas Instruments link cables [development files]
libticables3-dev - support library for Texas Instruments link cables [development files]
libticalcs2-dev - provides functions to communicate with TI calculators [development files]
libticalcs4-dev - provides functions to communicate with TI calculators [development files]

```

---

### Post by Leigen_Zero on 2008-05-28
ok I think we are getting somewhere, still not working though:
```
george@george-laptop:~/Desktop/gnuitar-0.3.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets $(MAKE)... yes
checking for working aclocal-1.4... found
checking for working autoconf... found
checking for working automake-1.4... found
checking for working autoheader... found
checking for working makeinfo... missing
checking for gawk... no
checking for mawk... mawk
checking whether ln -s works... yes
checking for gcc... gcc
checking for C compiler default output... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for a BSD-compatible install... /usr/bin/install -c
checking for glib-config... no
checking for GLIB - version >= 1.2.6... no
*** The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
checking for pkg-config... /usr/bin/pkg-config
checking for GLIB - version >= 2.2.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
configure: error: Test for GLIB2 failed. See the file 'INSTALL' for help.

```

not sure what that means

---

### Post by kpkeerthi on 2008-05-28
Refer to the README file that is the source folder of gnuitar. It should have the 'dependencies' required to compile the program.

```

sudo apt-get install libglib1.2-dev libgtk1.2-dev

```

Some help [here]("http://ubuntuforums.org/showthread.php?t=29029")

---

### Post by Leigen_Zero on 2008-05-28
thanks all installed fine now
in university library so will test when i get home

cheers again for all the help

---

