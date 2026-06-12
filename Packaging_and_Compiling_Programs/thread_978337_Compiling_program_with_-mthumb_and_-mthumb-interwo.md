---
title: "Compiling program with -mthumb and -mthumb-interwork instruction"
date: 2008-11-11
forum: Packaging and Compiling Programs
---

### Post by gauravmittal on 2008-11-11
**I want to reduce size of binary.**
The one way is to strip it and the other way is to compile it with -mthumb and -mthumb-interwork instruction which conver **32 bit** code to **16 bit** code.

But when i am compiling it with this instruction, it is giving errors given below. 

  first occurrence: ../../bin-arm/libdisplay.a(ui_appln.o): thumb call to arm
../../bin-arm/libdisplay.a(ui_appln.o): In function `uiLogicalKeyValues':
../../module/display/src/ui_appln.c:199: warning: internal error: dangerous error
/usr/local/arm/3.4/lib/gcc/arm-linux-uclibc/3.4.3/../../../../arm-linux-uclibc/bin/ld: /usr/local/arm/3.4/lib/gcc/arm-linux-uclibc/3.4.3/libgcc.a(_modsi3.oS)(__modsi3): warning: **interworking not enabled**.

What i have to do to enable interworking or compile my program with this command.
Can some body help me.

---

### Post by Embedded Linux Guy on 2011-04-25
Try gcc --target-help and see if thumb-interwork is listed under target-specific options. If not your compiler doesn't support it.

---

