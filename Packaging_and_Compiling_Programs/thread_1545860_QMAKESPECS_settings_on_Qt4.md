---
title: "QMAKESPECS settings on Qt4"
date: 2010-08-04
forum: Packaging and Compiling Programs
---

### Post by porosity on 2010-08-04
Hello, 

I am trying to use qmake to build a simple .pro file, and have installed the proper qt4 libraries (libqt4-dev, -core, -gui, -opengl).  When I run qmake I get the following error:

> QMAKESPEC has not been set, so configuration cannot be deduced.

I know I need to try and point this environment variable to some sort of compiler (linux-g++), but whenever I try to do so it tries to look in /usr/share/qt4/mkspecs.  Am I missing some qt4 pacakge, with an mkspecs/linux-g++ directory?

Thanks

---

### Post by SevenMachines on 2010-08-06
you need qt4-qmake i'd think
> $ apt-file search /usr/share/qt4/mkspecs | grep linux-g++
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++-32/qmake.conf
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++-32/qplatformdefs.h
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++-64/qmake.conf
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++-64/qplatformdefs.h
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++-maemo/qmake.conf
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++-maemo/qplatformdefs.h
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++/qmake.conf
qt4-qmake: /usr/share/qt4/mkspecs/linux-g++/qplatformdefs.h


---

