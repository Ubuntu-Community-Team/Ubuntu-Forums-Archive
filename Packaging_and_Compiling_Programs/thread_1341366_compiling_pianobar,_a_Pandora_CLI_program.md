---
title: "compiling pianobar, a Pandora CLI program"
date: 2009-11-29
forum: Packaging and Compiling Programs
---

### Post by gpapagni on 2009-11-29
Has anyone recently installed pianobar?  It is a CLI program for Pandora music service.  I have downloaded the tarballs for this but I can't figure out the dependencies since two of these are tarballs themselves.  Anyone have some suggestions?

BTW, I have never compiled binary or source code before.  The problem is in cmake . where the compiler is not seeing the 2 dependent files.  Thanks.

gpapagni

---

### Post by SevenMachines on 2009-12-01
if you post details of any errors you get, what steps you have actually gone through and so on someone might be able to help

---

### Post by gpapagni on 2009-12-01
I will do that as soon as I am able.  I should know better.  Thanks.

---

### Post by arthursucks on 2010-01-06
I found the dependencies were the libmad dev and libfaad dev files.  Easly grabbed from apt.  But when I run make...
```
$ make
Scanning dependencies of target ezxml
[  6%] Building C object libezxml/src/CMakeFiles/ezxml.dir/ezxml.o
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/libezxml/src/ezxml.c: In function ‘ezxml_internal_dtd’:
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/libezxml/src/ezxml.c:429: warning: operation on ‘s’ may be undefined
Linking C static library libezxml.a
[  6%] Built target ezxml
Scanning dependencies of target waitress
[ 13%] Building C object libwaitress/src/CMakeFiles/waitress.dir/waitress.o
Linking C static library libwaitress.a
[ 13%] Built target waitress
Scanning dependencies of target piano
[ 20%] Building C object libpiano/src/CMakeFiles/piano.dir/crypt.o
[ 26%] Building C object libpiano/src/CMakeFiles/piano.dir/http.o
[ 33%] Building C object libpiano/src/CMakeFiles/piano.dir/piano.o
[ 40%] Building C object libpiano/src/CMakeFiles/piano.dir/xml.o
Linking C static library libpiano.a
[ 40%] Built target piano
Scanning dependencies of target wardrobe
[ 46%] Building C object libwardrobe/src/CMakeFiles/wardrobe.dir/wardrobe.o
[ 53%] Building C object libwardrobe/src/CMakeFiles/wardrobe.dir/md5.o
Linking C static library libwardrobe.a
[ 53%] Built target wardrobe
Scanning dependencies of target pianobar
[ 60%] Building C object src/CMakeFiles/pianobar.dir/main.o
In file included from /home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c:50:
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/player.h:37:19: error: ao/ao.h: No such file or directory
In file included from /home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c:50:
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/player.h:86: error: expected specifier-qualifier-list before ‘ao_device’
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c: In function ‘main’:
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c:89: warning: implicit declaration of function ‘ao_initialize’
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c:275: error: ‘struct audioPlayer’ has no member named ‘waith’
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c:276: error: ‘struct audioPlayer’ has no member named ‘waith’
/home/arthursucks/Desktop/PromyLOPh-pianobar-6d63e2e/src/main.c:347: warning: implicit declaration of function ‘ao_shutdown’
make[2]: *** [src/CMakeFiles/pianobar.dir/main.o] Error 1
make[1]: *** [src/CMakeFiles/pianobar.dir/all] Error 2
make: *** [all] Error 2

```
Any help would be super appreciated.  I would like to run this in native 64bit.

---

### Post by SevenMachines on 2010-01-06
error: ao/ao.h: No such file or directory

means that a dependency on libao-dev is missing
$sudo apt-get install libao-dev

---

### Post by arthursucks on 2010-01-18
@SevenMachines

Thanks! That was it!

---

