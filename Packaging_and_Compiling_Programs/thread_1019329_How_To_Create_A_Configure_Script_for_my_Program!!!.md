---
title: "How To Create A Configure Script for my Program!?!?!?"
date: 2008-12-23
forum: Packaging and Compiling Programs
---

### Post by DexterLB on 2008-12-23
I've got a program, "hello world", written in Qt4 with QDevelop. I have a "src" folder and a "ui" folder. Executing "Build" in QDevelop creates a makefile and executes "make", which creates a folder "build" with the .o files inside, and a folder "bin" with the binary file inside. And when I start the binary file, the program works perfectly.

So, now I want to make a standard tarball. Can someone tell me how to make the configure.ac, makefile.am, etc in order to run autoconf and automake?

---

### Post by DexterLB on 2008-12-24
Anyone? :confused:

---

### Post by DexterLB on 2008-12-25
Ah, come on! no one!? duh!

Please reply, even if you don't know the exact answer!

---

### Post by dannytatom on 2008-12-25
I haven't the slightest idea, but here's a christmas bump. ;)

---

### Post by DexterLB on 2008-12-25
BUMP
Merry christmas!

---

### Post by DexterLB on 2008-12-26
bump

---

### Post by DexterLB on 2008-12-27
Bump

---

### Post by moma on 2009-01-01
I would recommend to use CMake for source code configuration/installation.
[http://www.cmake.org](http://www.cmake.org)

I just release [gscreendump version 0.1]("http://ubuntuforums.org/showthread.php?t=1026504") and it uses [Automake/Autoconf tools]("http://www.gnu.org/software/automake/"), but CMake is touted to be easier and more modern, so I consider to move to CMake too.

Debian (.deb) package for Debian/Ubuntu has its own configuration files (eg. control and rules files) which are rather easy to set up. 
See
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)   (very quick guide that may work in your case) 

[https://help.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html](https://help.ubuntu.com/ubuntu/packagingguide/C/basic-scratch.html)
[http://www.linux.com/articles/60383](http://www.linux.com/articles/60383)

BTW: [gscreendump 0.1]("http://code.google.com/p/gscreendump/") is waiting for you. You must read the Install page on Wiki first.

---

### Post by monkeyking on 2009-01-02
automake is quite ok

---

### Post by DexterLB on 2009-01-03
I couldn't find any way to use cmake with a qt project. Making a regular cmakelists.txt with the c++ files doesn't work, of course, and I don't know how to make it use qt.

monkeyking: I know it's quite OK, but I don't know how to use it with a qt project!

---

### Post by monkeyking on 2009-01-03
I've never done gui programming, so I can't help you with the qt specific stuff.

But normally you should do it like this.

Have an Makefile.am in each directory of your project.
The syntax is not like a normal Makefile.
More like a list of source files, where to install the program and name of the program.


Then use autoscan to generate a configure.scan,
change the stuff you need to change and rename the file to configure.ac


You need 4 more files called Makefile.in,config.h.in,alocal.m4 and configure

you create those with alocal, automake -ac, autoheader and autoconf.

This is the way to use automake, I don't think you can use the object files deployed by qt directly.

btw,
the minimum you can get away with is,
make a subdir called src, move all your .c .cpp to this folder.
Make a Makefile.am in your src which contains 
```
bin_PROGRAMS = yoyo
yoyo_SOURCES = main.c
```
make a Makefile in your ../src that looks like

```

SUBDIRS = src
dist_doc_DATA = README

```
write a empty README in ../src
[PHP]
AC_INIT([lalala], [0.1], [contact@gnu.org])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_PROG_CC
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([
           Makefile
           src/Makefile
          ])
AC_OUTPUT
[/PHP]
You generate your scrip and create missing files with autoreconf --install
good luck

---

