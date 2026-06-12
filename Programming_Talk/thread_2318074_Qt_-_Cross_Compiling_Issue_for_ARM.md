---
title: "Qt - Cross Compiling Issue for ARM"
date: 2016-03-22
forum: Programming Talk
---

### Post by Owen_Murphy on 2016-03-22
Hello,
I'm trying to write a simple GUI for an ARM processor running Debian linux (BeagleBone Black) using Qt, and I am having a very difficult time getting the code to compile.  I have compiled the same code using my host machine (x86_64 architecture, Ubuntu 14.04), and the resulting program runs properly (it is a big button that says "Hello world").  When I try to compile use an ARM compiler, it fails to compile.  Here is what I have so far:

project folder:
```
owen@Schwabuntu:~/qte-example$ ls
main.cpp  qte-example.pro
owen@Schwabuntu:~/qte-example$ cat main.cpp
#include <QApplication>
#include <QPushButton>
int main(int argc, char ** argv){
    QApplication app(argc, argv);

    QPushButton btn("Hello World");
    btn.show();
    btn.showMaximized();

    return app.exec();
}
owen@Schwabuntu:~/qte-example$ cat qte-example.pro
TEMPLATE=app
SOURCES = main.cpp
QT +=widgets

```

qmake information:
```
owen@Schwabuntu:~/qte-example$ qmake -version
QMake version 3.0
Using Qt version 5.2.1 in /usr/lib/x86_64-linux-gnu
owen@Schwabuntu:~/qte-example$ qmake -query
QT_SYSROOT:
QT_INSTALL_PREFIX:/usr
QT_INSTALL_ARCHDATA:/usr/lib/x86_64-linux-gnu/qt5
QT_INSTALL_DATA:/usr/share/qt5
QT_INSTALL_DOCS:/usr/share/qt5/doc
QT_INSTALL_HEADERS:/usr/include/qt5
QT_INSTALL_LIBS:/usr/lib/x86_64-linux-gnu
QT_INSTALL_LIBEXECS:/usr/lib/x86_64-linux-gnu/qt5/libexec
QT_INSTALL_BINS:/usr/lib/x86_64-linux-gnu/qt5/bin
QT_INSTALL_TESTS:/usr/tests
QT_INSTALL_PLUGINS:/usr/lib/x86_64-linux-gnu/qt5/plugins
QT_INSTALL_IMPORTS:/usr/lib/x86_64-linux-gnu/qt5/imports
QT_INSTALL_QML:/usr/lib/x86_64-linux-gnu/qt5/qml
QT_INSTALL_TRANSLATIONS:/usr/share/qt5/translations
QT_INSTALL_CONFIGURATION:/etc/xdg
QT_INSTALL_EXAMPLES:/usr/lib/x86_64-linux-gnu/qt5/examples
QT_INSTALL_DEMOS:/usr/lib/x86_64-linux-gnu/qt5/examples
QT_HOST_PREFIX:/usr
QT_HOST_DATA:/usr/lib/x86_64-linux-gnu/qt5
QT_HOST_BINS:/usr/lib/x86_64-linux-gnu/qt5/bin
QT_HOST_LIBS:/usr/lib/x86_64-linux-gnu
QMAKE_SPEC:linux-g++-64
QMAKE_XSPEC:linux-g++-64
QMAKE_VERSION:3.0
QT_VERSION:5.2.1
owen@Schwabuntu:~/qte-example$ cat /usr/lib/x86_64-linux-gnu/qt5/mkspecs/linux-arm-gnueabi-g++/qmake.conf
#
# qmake configuration for building with arm-linux-gnueabi-g++
#

MAKEFILE_GENERATOR      = UNIX
CONFIG                 += incremental gdb_dwarf_index
QMAKE_INCREMENTAL_STYLE = sublib

include(../common/linux.conf)
include(../common/gcc-base-unix.conf)
include(../common/g++-unix.conf)

# modifications to g++.conf
QMAKE_CC                = arm-linux-gnueabi-gcc
QMAKE_CXX               = arm-linux-gnueabi-g++
QMAKE_LINK              = arm-linux-gnueabi-g++
QMAKE_LINK_SHLIB        = arm-linux-gnueabi-g++

# modifications to linux.conf
QMAKE_AR                = arm-linux-gnueabi-ar cqs
QMAKE_OBJCOPY           = arm-linux-gnueabi-objcopy
QMAKE_NM                = arm-linux-gnueabi-nm -P
QMAKE_STRIP             = arm-linux-gnueabi-strip
load(qt_config)


```

When I compile for my desktop:
```
owen@Schwabuntu:~/qte-example$ qmake; make; ./qte-example
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -fPIE -DQT_NO_DEBUG -DQT_WIDGETS_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/lib/x86_64-linux-gnu/qt5/mkspecs/linux-g++-64 -I. -I/usr/include/qt5 -I/usr/include/qt5/QtWidgets -I/usr/include/qt5/QtGui -I/usr/include/qt5/QtCore -I. -o main.o main.cpp
g++ -m64 -Wl,-O1 -o qte-example main.o   -L/usr/X11R6/lib64 -lQt5Widgets -L/usr/lib/x86_64-linux-gnu -lQt5Gui -lQt5Core -lGL -lpthread 

```
...and a big button that says "Hello World" pops up

When I try to compile for ARM (after removing main.o, Makefile and qte-example)
```
owen@Schwabuntu:~/qte-example$ rm main.o Makefile qte-example
owen@Schwabuntu:~/qte-example$ ls
main.cpp  qte-example.pro
owen@Schwabuntu:~/qte-example$ qmake -spec linux-arm-gnueabi-g++
owen@Schwabuntu:~/qte-example$ make
arm-linux-gnueabi-g++ -c -pipe -O2 -Wall -W -D_REENTRANT -fPIE -DQT_NO_DEBUG -DQT_WIDGETS_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/lib/x86_64-linux-gnu/qt5/mkspecs/linux-arm-gnueabi-g++ -I. -I/usr/include/qt5 -I/usr/include/qt5/QtWidgets -I/usr/include/qt5/QtGui -I/usr/include/qt5/QtCore -I. -o main.o main.cpp
arm-linux-gnueabi-g++ -Wl,-O1 -o qte-example main.o   -lQt5Widgets -L/usr/X11R6/lib64 -L/usr/lib/x86_64-linux-gnu -lQt5Gui -lQt5Core -lGL -lpthread 
/usr/lib/x86_64-linux-gnu/libQt5Widgets.so: file not recognized: File format not recognized
collect2: error: ld returned 1 exit status
make: *** [qte-example] Error 1

```

I've been playing around with different versions of Qt, and I've gotten different error messages.  At work I have Qt 4.8.6, which tells me i'm using the wrong instructions, which leads me to believe that the code did not compile using ARM instructions or something like that.  I can update tomorrow morning when I have access to that computer.

I'm sure it's something simple, like I need to install something, or adjust a configuration file, but I'm having a lot of trouble figuring it out myself.

Thanks in advance!

Owen

---

