---
title: "ppa source prepare"
date: 2011-05-03
forum: Packaging and Compiling Programs
---

### Post by marmistrz on 2011-05-03
hi
i've written my own program and want to upload it to a ppa
i've read the ubuntu guide about the packaging but still don't know how should I prepare my .cpp and .hpp to this structure so that it would make orig.tar.gz and configure and so on, so that i could upload it to a ppa
if you could make a tutorial how to get from cpp and hpp based program a ppa-uploadable version
can you help?

---

### Post by Ibidem on 2011-05-05
configure is usually nice; if it breaks, it's chaos.
It comes from autotools, so read the autoconf/libtool/... docs

But you'll need at least this much:

1. Have a makefile/configure/configure.in script
It and the source should be in the same directory, named <programname>-<version>
2. run dh_make  with the right flags, and edit debian/control
dh_make can create the source archive; I'd suggest choosing "debian source native" for your own programs.

---

### Post by marmistrz on 2011-05-07
i don't have this
I use netbeans and I have files ```
.cpp, .hpp, Makefile, dep.inc
```
and in folder ```
nbproject
```
```
configurations.xml
Makefile-Debug.mk
Makefile-impl.mk
Makefile-Release.mk
Makefile-variables.mk
Package-Debug.bash
Package-Release.bash
project.properties
project.xml

```
in subfolder ```
private
```
```
configurations.xml
Makefile-variables.mk
private.properties
private.xml

```

in folder ```
build/Debug/GNU-Linux-x86
``` ```
.o .o.d
``` files

what should i do?

---

### Post by marrabld on 2011-05-08
Packaging code can be tricky.  But if you have a simple program you are trying to upload then it shouldn't be too difficult

I think that your first step is to use autoconf to generate a 

```
./configure 
make 
sudo make install
```

type installation.  Start here

[http://www.gnu.org/software/autoconf/](http://www.gnu.org/software/autoconf/)

You do that so it can build across many different machines and have the autotools sort out the dependencies for you.  Just because it compiles on your machine doesn't mean it will on mine.  autoconf is designed to take care of that.

Once you have that working on your machine then you need to package it, to make the .deb 

start here

[https://wiki.ubuntu.com/PackagingGuide/Complete](https://wiki.ubuntu.com/PackagingGuide/Complete) 

basically you need to set up the rules for installing in a debian folder inside your source folder of your application.  But if you have the typical aforementioned install, then its very little work.  dh_build can do that for you.  If you have 'tricky' rules or special steps for building then you have to set up those rules in your /debian/rules file.

once you can get pbuilder to auto build your application then you can upload the source to your ppa and the ppa will follow the same steps as pbuilder to make the binary available to all.

I found the whole process tricky to get my head around to begin with but once the penny drops its not so bad.

I would start with those links and post specific questions.

Good luck

---

### Post by marmistrz on 2011-05-08
i found a tutorial on autotools but i can't create Makefile.am
I have an error:

```
configure.ac:6: error: possibly undefined macro: AM_INIT_AUTOMAKE
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.

```

while running autoconf

when i've inserted 
```
m4_pattern_allow
```
on start, i have this error too

---

### Post by marmistrz on 2011-05-09
could you post a working tutorial on this?
whichever i try i got errors...

---

### Post by alenn on 2012-08-12
this is an old tread, but I need this tutorial too.

---

