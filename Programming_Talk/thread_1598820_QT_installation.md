---
title: "QT installation?"
date: 2010-10-17
forum: Programming Talk
---

### Post by worksofcraft on 2010-10-17
Besides Gtk there is a comprehensive GUI library called QT that's worth a look. I got [QT download]("http://qt.nokia.com/downloads") did a chmod +x on the .bin file and did a sudo ./*.bin which seems to have installed a load of files in /opt/qtsdk-2010.05, the default location.

However trying the simple [hello qt world! tutorial]("http://doc.trolltech.com/4.3/tutorial-t1.html") the qmake command wasn't found so I installed that with apt-get. Then I tried to run the make file it produced and clearly it is looking in the wrong place:
```

g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG
-DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++
-I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui
-I/usr/include/qt4 -I. -I. -o main.o main.cpp

```

Ah no I see I probably have to build it all first...
```

/opt/qtsdk-2010.05/qt$> sudo ./configure
# runs for quite some time and seems to complete OK :)

/opt/qtsdk-2010.05/qt$ make
# runs for quite some time then falls over :(
...
.obj/release-shared/qabstractsocket.o: In function `QAbstractSocket::abort()':
/opt/qtsdk-2010.05/qt/src/network/socket/qabstractsocket.cpp:2020: undefined reference to `QSslSocket::abort()'
.obj/release-shared/qabstractsocket.o: In function `QAbstractSocket::flush()':
/opt/qtsdk-2010.05/qt/src/network/socket/qabstractsocket.cpp:2081: undefined reference to `QSslSocket::flush()'
collect2: ld returned 1 exit status
make[1]: *** [../../lib/libQtNetwork.so.4.7.0] Error 1
make[1]: Leaving directory `/opt/qtsdk-2010.05/qt/src/network'
make: *** [sub-network-make_default-ordered] Error 2

```

so... question is... can anyone help me set this thing up properly?

---

### Post by krazyd on 2010-10-17
you don't need to install from the website - it's all in the repositories. try installing the 'qt4-dev-tools' package

---

### Post by worksofcraft on 2010-10-17
> **krazyd said:**
> you don't need to install from the website - it's all in the repositories. try installing the 'qt4-dev-tools' package

TYVM :)

that works... IDK why the 580Mbytes of download from the Nokia don't. So much for trying to get the very latest :confused:

---

### Post by CptPicard on 2010-10-17
> **worksofcraft said:**
> 
that works... IDK why the 580Mbytes of download from the Nokia don't. So much for trying to get the very latest :confused:

It's probably a good idea in general to write against the -dev package for the library version that actually comes with the distribution that one intends to write and run the code on; and there is rarely any benefit to pull in the latest and greatest especially with a mature toolkit such as Qt...

---

### Post by spjackson on 2010-10-17
> **CptPicard said:**
> It's probably a good idea in general to write against the -dev package for the library version that actually comes with the distribution that one intends to write and run the code on; and there is rarely any benefit to pull in the latest and greatest especially with a mature toolkit such as Qt...
I agree with this advice. However, if you do have a reason to experiment with the latest release, then Nokia's binary download for Linux works. At least it always has done for me, and I have rarely read reports of problems on the Qt-Interest mailing list. (By contrast, there are often reports of difficulties building the SDK from source.)

However, when using qmake, you must use the qmake that is in the download, not pick some bits from the repository and other bits from Nokia's download. That doesn't work; absolute paths are wired into qmake and other binaries (e.g. the shared libraries).

It is sufficient to specify the full path to qmake, e.g.
```

/opt/qtsdk-2010.05/qt/bin/qmake myproject.pro
make

```Or alternatively, you can set PATH.

---

### Post by worksofcraft on 2010-10-17
I'm looking at alternatives to developing from GObject based classes within the Gtk framework. Extending gtkmm classes doesn't seem to produce the desired effect and I suspect it is because the underlying GObject instances do not reflect my extended class hierarchy.

OTOH having to assimilate and reproduce all that "boiler plate" C code for new GObject based classes, or to learn the new "Vala" language is just going to put me right back to square one with everything. I just want to find out if teh C++ based QObject system is going to suit me better in the long run :)

---

### Post by nvteighen on 2010-10-18
> **worksofcraft said:**
> I'm looking at alternatives to developing from GObject based classes within the Gtk framework. Extending gtkmm classes doesn't seem to produce the desired effect and I suspect it is because the underlying GObject instances do not reflect my extended class hierarchy.

OTOH having to assimilate and reproduce all that "boiler plate" C code for new GObject based classes, or to learn the new "Vala" language is just going to put me right back to square one with everything. I just want to find out if teh C++ based QObject system is going to suit me better in the long run :)

Yeah, GObject feels weird, but it works... and teaches a lot of how C can be used to reproduce OOP. But weirdly enough, PyGtk is much better and saner than the original; the guys behind the Python binding have done a great job not just "porting" the library to Python but also "translating" it into more or less Pythonic ways (there are some quirks that remind you that you're using a binding for a C library, though).

All my little experience with Qt comes from PyQt... and I didn't like it too much, to be honest. But, again, I have very little experience with it in order to be able to compare both toolkits... All I can say is that I like GTK+'s look much better that Qt's and that's why I've done more GTK+ :P

(Then, try using GNUStep and feel the pain of the most ackward GUI toolkit!)

---

