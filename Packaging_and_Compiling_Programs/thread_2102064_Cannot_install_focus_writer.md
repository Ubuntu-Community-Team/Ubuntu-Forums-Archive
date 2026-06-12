---
title: "Cannot install focus writer"
date: 2013-01-06
forum: Packaging and Compiling Programs
---

### Post by bui89 on 2013-01-06
Cannot install [http://gottcode.org/focuswriter/](http://gottcode.org/focuswriter/)
I already did this:
```
apt-get install qt4-qmake
```
```
sudo apt-get install libenchant-dev
```
```
sudo apt-get install libzip-dev
```
```
sudo apt-get install build-essential
```
then as given in INSTALL did this
```
qmake
```
then:
```
make
```
and received:
```
g++ -c -pipe -O2 -pthread -Wall -W -D_REENTRANT -DVERSIONSTR=\"1.4.1\" -DDATADIR=\"/usr/local/share/focuswriter\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -Isrc/qtsingleapplication -Isrc/enchant -I/usr/include/glib-2.0 -I/usr/lib/i386-linux-gnu/glib-2.0/include -I/usr/include/enchant -I/usr/lib/libzip/include -Ibuild -o build/qtsingleapplication.o src/qtsingleapplication/qtsingleapplication.cpp
In file included from src/qtsingleapplication/qtsingleapplication.cpp:41:0:
src/qtsingleapplication/qtsingleapplication.h:43:24: fatal error: QApplication: No such file or directory
compilation terminated.
make: *** [build/qtsingleapplication.o] Error 1

```
I don't understand what error is this. Can anyone help me?:confused:

---

### Post by xno on 2013-01-19
you need

```
apt-get install libqt4-dev
```

xno

---

