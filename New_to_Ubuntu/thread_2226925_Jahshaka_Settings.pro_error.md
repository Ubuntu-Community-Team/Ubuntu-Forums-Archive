---
title: "Jahshaka Settings.pro error"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by Aadi246 on 2014-05-29
Hi, Guys.

So, I'm getting this type of error. And I dunno what to do.

Here's the terminal output :


*********************************************************************************************************


>>Configuring build type for jahshaka

Project MESSAGE: Jahshaka 2.0 build system
Project MESSAGE: -----------------------------
Project MESSAGE: 
Project MESSAGE: Checking operating system and paths
Project MESSAGE: 
Project MESSAGE: DEBUG
Project MESSAGE: Operating System Type (Linux)
Project MESSAGE: Using linux presets...
Braces mismatch /home/aadi/jahshaka/Settings.pro:425
Project LOAD(): Feature Settings.pro cannot be found.
---------------------------------------
Jahshaka Configure Script User Commands
---------------------------------------

SYNOPSIS

     ./configure [ switches ]
     ./configure [ switches ] jahshaka
     ./configure [ switches ] jahplayer

DESCRIPTION

     Configures the jahshaka build process to build either jahshaka
     or jahplayer

     By default running configure with no arguments will activate the
     build for jahshaka

     You need to follow the configure command with the make command
     in order to actually build the software!

SWITCHES

     --prefix=path
          sets the path for the installation (default: /usr/local)

     --disable-debug
          sets debug mode off

     --disable-plugins
          disables the plugin build and install

     --enable-static
          disables the dynamic loading of various open libraries


*********************************************************************************************************

---

### Post by Aadi246 on 2014-05-29
Okay... So, I did somethings some told by some other websites. And then I was able to succesfully ./configure it...
But when it came to the 'make' section, I got this error...



*****************************************************************************************************


................
................

cd apollon/ && make -f Makefile 
make[2]: Entering directory `/home/aadi/jahshaka/source/AuxiliaryLibraries/apollon'
/usr/bin/qmake -o Makefile apollon.pro
make[2]: Leaving directory `/home/aadi/jahshaka/source/AuxiliaryLibraries/apollon'
make[2]: Entering directory `/home/aadi/jahshaka/source/AuxiliaryLibraries/apollon'
g++ -c -m64 -pipe -O2 -fPIC -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I../gift -I. -o apollonsearchlistview.o apollonsearchlistview.cpp
apollonsearchlistview.cpp:22:24: fatal error: qpopupmenu.h: No such file or directory
compilation terminated.
make[2]: *** [apollonsearchlistview.o] Error 1
make[2]: Leaving directory `/home/aadi/jahshaka/source/AuxiliaryLibraries/apollon'
make[1]: *** [sub-apollon-make_default] Error 2
make[1]: Leaving directory `/home/aadi/jahshaka/source/AuxiliaryLibraries'
make: *** [sub-source-AuxiliaryLibraries-make_default] Error 2


*****************************************************************************************************

---

