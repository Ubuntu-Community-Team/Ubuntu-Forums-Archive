---
title: "QT5 on wayland : qtwayland build is failing."
date: 2013-07-19
forum: Programming Talk
---

### Post by bhushanjcool on 2013-07-19
Hello,

I am trying to bring up qt5 on wayland on Ubuntu 12.04

I have checked out QT5 from here:
[http://qt.gitorious.org/qt/qt5/trees/stable](http://qt.gitorious.org/qt/qt5/trees/stable)

Compiled qtbase and trying to compile qtwayland module.

Below is the error I get:
abcd@ubuntu:~/qt_sources/qtwayland$ make
cd src/ && ( test -e Makefile || /usr/local/Qt-5.1.1/bin/qmake /home/bhushan/qt_sources/qtwayland/src/src.pro -o Makefile ) && make -f Makefile 
make[1]: Entering directory `/home/bhushan/qt_sources/qtwayland/src'
cd compositor/ && ( test -e Makefile || /usr/local/Qt-5.1.1/bin/qmake /home/bhushan/qt_sources/qtwayland/src/compositor/compositor.pro -o Makefile ) && make -f Makefile 
make[2]: Entering directory `/home/bhushan/qt_sources/qtwayland/src/compositor'
g++ -c -pipe -O2 -fvisibility=hidden -fvisibility-inlines-hidden -std=c++0x -fno-exceptions -Wall -W -D_REENTRANT -fPIC -DQT_BUILD_COMPOSITOR_LIB -DQT_BUILDING_QT -DQT_NO_CAST_TO_ASCII -DQT_ASCII_CAST_WARNINGS -DQT_MOC_COMPAT -DQT_USE_QSTRINGBUILDER -DQT_DEPRECATED_WARNINGS -DQT_DISABLE_DEPRECATED_BEFORE=0x050000 -DQT_WAYLAND_WINDOWMANAGER_SUPPORT -DQT_NO_WAYLAND_XKB -DQT_COMPOSITOR_WAYLAND_GL -DQT_NO_EXCEPTIONS -D_LARGEFILE64_SOURCE -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/local/Qt-5.1.1/mkspecs/linux-g++ -I. -I../../include -I../../include/QtCompositor -I/home/bhushan/qt_sources/qtwayland/include/QtCompositor/5.1.1 -I/home/bhushan/qt_sources/qtwayland/include/QtCompositor/5.1.1/QtCompositor -Iglobal -Iwayland_wrapper -I../shared -Icompositor_api -Iwindowmanagerprotocol -I/usr/local/Qt-5.1.1/include -I/usr/local/Qt-5.1.1/include/QtGui -I/usr/local/Qt-5.1.1/include/QtGui/5.1.1 -I/usr/local/Qt-5.1.1/include/QtGui/5.1.1/QtGui -I/usr/local/Qt-5.1.1/include/QtCore -I/usr/local/Qt-5.1.1/include/QtCore/5.1.1 -I/usr/local/Qt-5.1.1/include/QtCore/5.1.1/QtCore -I.moc/release-shared -o .obj/release-shared/wlcompositor.o wayland_wrapper/wlcompositor.cpp
In file included from wayland_wrapper/wlcompositor.cpp:49:0:
wayland_wrapper/wlextendedoutput.h:45:54: fatal error: wayland-output-extension-server-protocol.h: No such file or directory
compilation terminated.
make[2]: *** [.obj/release-shared/wlcompositor.o] Error 1
make[2]: Leaving directory `/home/bhushan/qt_sources/qtwayland/src/compositor'
make[1]: *** [sub-compositor-make_first] Error 2
make[1]: Leaving directory `/home/bhushan/qt_sources/qtwayland/src'
make: *** [sub-src-make_first] Error 2


-------------------------------------------------------------------------------------

Can anyone please help out here. Or probably any link that can guide me to install qt on wayland.!
Thanks in advance.

/BJ

---

### Post by Toz on 2013-07-19
*Moved to **Prgramming Talk***

---

### Post by www.rzr.online.fr on 2014-04-26
I just tried to rebuild devel branch for debian, you can test this at :

[https://qt.gitorious.org/qt/qtwayland-rzr/graph/sandbox/pcoval/snapshot](https://qt.gitorious.org/qt/qtwayland-rzr/graph/sandbox/pcoval/snapshot)

---

