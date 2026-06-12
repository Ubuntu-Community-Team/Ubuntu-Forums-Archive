---
title: "Qbasic an ubuntu"
date: 2007-01-19
forum: Programming Talk
---

### Post by jerryroy on 2007-01-19
is there a way to run qbasic code in ubuntu becuase thats the only language i know so far and im doing a little project with it for school and wanted to know is there a way to to use gui with it in ubuntu?

---

### Post by Wybiral on 2007-01-19
Well, theres Basic4SDL (in my sig) and freeBASIC that I know of (that both work on linux)

(I plan to make a VGA version of Basic4SDL that will be much more like QBasic)

---

### Post by jerryroy on 2007-01-19
so what about gui is this possible? an how do i impliment it in my program

---

### Post by Wybiral on 2007-01-20
It's possible in both, but probably easier in freeBASIC since there are more libraries for it at the moment.

This does inspire me to get to work on the VGA version of Basic4SDL, which will make it VERY close to QBasic.

But, currently basic4SDL has OpenGL, so you CAN do GUI's in it... It's just a little harder (because it's meant for 3d)

---

### Post by derjames on 2007-01-20
If you have your old MS-DOS 6.22 disk you can install it in a virtual machine... 
i.e. QEMU+MS-DOS
if you have access to a computer with Win95 or 98 is possible that QBASIC is installed there, so you can grab the files from that computer (QBASIC.EXE and QBASIC.HLP) and install them in QEMU+FreeDOS...

However I would stick with Python and/or Ruby since they are easy to learn and very fun to code... even programs with GUIs

---

### Post by Wybiral on 2007-01-20
Yeah... Learning something like python probably wouldn't be all that hard after QBasic... You just have to get used to the style change.

---

### Post by amo-ej1 on 2007-01-22
```

root@lap:/home/edb# dpkg -s yabasic
Package: yabasic
Status: install ok installed
Priority: optional
Section: interpreters
Installed-Size: 836
Maintainer: Matej Vela <vela@debian.org>
Architecture: i386
Version: 2.763-2
Depends: libc6 (>= 2.4-1), libice6, libncurses5 (>= 5.4-5), libsm6, libx11-6
Description: Yet Another BASIC interpreter
 yabasic implements the most common and simple elements of the BASIC
 language; it comes with for-loops and goto with while-loops and
 procedures.  yabasic does monochrome line graphics, and printing
 comes with no extra effort.  yabasic runs under Unix and Windows;
 it is small (less than 200 KB) and free.

```

Yabasic is a basic interpreter ;-)

[http://gambas.sourceforge.net/](http://gambas.sourceforge.net/) (also available in through apt) is an open source visual basic alike implementation

---

