---
title: "nybody uses qt on ubuntu??"
date: 2009-11-06
forum: Programming Talk
---

### Post by nbulchandani on 2009-11-06
hello...
i use qt on winxp..and i have a dulaboot sytem.i installed qt on ubuntu but the compile output is as:
 p, li { white-space: pre-wrap; }  Running build steps for project 1...
 [COLOR=#0000FF]Starting: /usr/bin/qmake-qt4 /home/nishant/1/1.pro -spec /usr/share/qt4/mkspecs/linux-g++ -r CONFIG+=debug[/COLOR] 
 [COLOR=#0000FF]Exited with code 0.[/COLOR]
 [COLOR=#0000FF]Starting: /usr/bin/make -w[/COLOR] 
 make: Entering directory `/home/nishant/1'
 g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -o 1.o 1.cpp
 make: Leaving directory `/home/nishant/1'
 [COLOR=#FF0000]make: g++: Command not found[/COLOR]
 [COLOR=#FF0000]make: *** [1.o] Error 127[/COLOR]
 [COLOR=#FF0000]Exited with code 2.[/COLOR]
 [COLOR=#FF0000]Error while building project 1[/COLOR]
 [COLOR=#FF0000]When executing build step 'Make'[/COLOR]

[COLOR=#FF0000][/COLOR]

[COLOR=#FF0000][/COLOR]
[COLOR=#FF0000]..any ideas nyone....
[/COLOR]

---

### Post by -grubby on 2009-11-06
Try this command:

```

sudo apt-get install build-essential

```

It installs several compilers and such things necessary for compiling.

---

### Post by samjh on 2009-11-06
You don't have the C++ compiler, g++, installed.

Use the command posted by Grubby above.  The build-essential package includes compilers for C, C++, and relevant headers.

---

### Post by nbulchandani on 2009-11-07
Thanks folks.......
VEry happy nw...no need to switch to winxp for qt.....
:p:p:p:p:D:D

---

### Post by CptPicard on 2009-11-07
Well, Kubuntu, the KDE-based Ubuntu derivative is the place to be if you're a Qt/KDE guy like me you know...

---

