---
title: "Cross Compiling for ARM: KARO - PXA270"
date: 2007-03-06
forum: Programming Talk
---

### Post by cptnkabuki on 2007-03-06
I've set up a cross compilation tool chain directed at ARM.  Everything seems to be going fine until i try and make a zImage.  I've tried mulitple kernels and multiple toolchains.  The problem is this:

root@mother:/home/build_2-6-13/linux-2.6.13.2# make zImage
  CHK     include/linux/version.h
  CC      scripts/mod/empty.o
Assembler messages:
Error: Invalid processor variant -mcpu=xscale
make[2]: *** [scripts/mod/empty.o] Error 1
make[1]: *** [scripts/mod] Error 2
make: *** [scripts] Error 2

I've read that -mcpu has been depreciated.  Does anybody have any ideas for working around this?  Is this a known issue?  What was done to support -mcpu depreciation?

Thanks.

---

### Post by gradedcheese on 2007-03-07
I think it's "-march" (for 'architecture') now...

this might help, but maybe not:
[http://www.arm.linux.org.uk/docs/kerncomp.php](http://www.arm.linux.org.uk/docs/kerncomp.php)

---

### Post by kuin on 2010-03-10
can someone help me?
I do not understand about this board. I can not use it.
see this link: [http://www.mobisensesystems.com/pages_en/xscale_boards.html](http://www.mobisensesystems.com/pages_en/xscale_boards.html)
how to run it?
pleas.....!!!

---

