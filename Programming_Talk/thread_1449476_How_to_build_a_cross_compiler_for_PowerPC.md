---
title: "How to build a cross compiler for PowerPC?"
date: 2010-04-07
forum: Programming Talk
---

### Post by anhvuitinh on 2010-04-07
Hi,
 
Is there a free PowerPC Cross Compiler somewhere?
If not, can someone show me how to build one?
 
I need to create a simple hello world executable that runs on a powerpc board using Ubuntu 9.10 (x86 platform). I think the GCC version is 4.4.1.
 
Thanks.

---

### Post by dominiquec on 2010-04-07
Er...doesn't GCC already cross-compile to PowerPC?

---

### Post by anhvuitinh on 2010-04-08
I don't think so.

---

### Post by Dayofswords on 2010-04-08
found this, hope it helps
[http://gcc.gnu.org/onlinedocs/gcc/RS_002f6000-and-PowerPC-Options.html](http://gcc.gnu.org/onlinedocs/gcc/RS_002f6000-and-PowerPC-Options.html)

---

### Post by anhvuitinh on 2010-04-08
I tried but got this error:
gcc -g -Wall -mtune=powerpc ./hello.c -o hello.o
./hello.c:1: error: bad value (powerpc) for -mtune= switch

I am stuck.

---

### Post by Tony Flury on 2010-04-08
the web site suggested by DayOfSwords suggests using the -mpowerpc option as in :

gcc -g -Wall -mpowerpc ./hello.c -o hello.o

Try that ?

---

### Post by anhvuitinh on 2010-04-08
I tried -mpowerpc, -march=powerpc, -mcpu=powerpc and none of them worked.

---

### Post by dominiquec on 2010-04-09
A quick check of the forums reveals this past post:

[http://ubuntuforums.org/showthread.php?t=390645](http://ubuntuforums.org/showthread.php?t=390645)

---

### Post by not_a_phd on 2010-04-09
I don't think that thread had this link: [http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/) 

I would highly recommend that you check this site out, as Dan Kegel has put together some highly reliable scripts for downloading and building the necessary tools to cross compile for multiple powerpc (and arm, and sparcs, and...) platforms.

---

### Post by mmix on 2010-04-09
[http://wiki.openembedded.net/index.php/Main_Page](http://wiki.openembedded.net/index.php/Main_Page)

---

