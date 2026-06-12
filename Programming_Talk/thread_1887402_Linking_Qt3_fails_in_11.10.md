---
title: "Linking Qt3 fails in 11.10"
date: 2011-11-26
forum: Programming Talk
---

### Post by jsedwards on 2011-11-26
I have a program that uses the Qt3 libraries.  It built with no problems on 11.04, but on 11.10 the ./configure fails when trying to link the test program:

```

g++ -lqt-mt  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi   -o bnv_qt_main bnv_qt_main.o moc_bnv_qt_test.o
bnv_qt_main.o: In function `main':
/pub/rivendell/rivendell-2.0.2/bnv_qt_main.cc:5: undefined reference to `QApplication::QApplication(int&, char**)'
bnv_qt_main.o: In function `Test':
/pub/rivendell/rivendell-2.0.2/bnv_qt_test.h:6: undefined reference to `QObject::QObject(QObject*, char const*)'
bnv_qt_main.o: In function `main':
/pub/rivendell/rivendell-2.0.2/bnv_qt_main.cc:7: undefined reference to `QObject::connect(QObject const*, char const*, QObject const*, char const*)'
bnv_qt_main.o: In function `~Test':
/pub/rivendell/rivendell-2.0.2/bnv_qt_test.h:7: undefined reference to `QObject::~QObject()'
bnv_qt_main.o: In function `main':
/pub/rivendell/rivendell-2.0.2/bnv_qt_main.cc:5: undefined reference to `QApplication::~QApplication()'
/pub/rivendell/rivendell-2.0.2/bnv_qt_main.cc:5: undefined reference to `QApplication::~QApplication()'
bnv_qt_main.o: In function `~Test':
/pub/rivendell/rivendell-2.0.2/bnv_qt_test.h:7: undefined reference to `QObject::~QObject()'
...

```

I have the same qt3 packages installed that I used in 11.04 and the libraries appear to be where they should be:



$ ls -l /usr/lib/*qt*
-rw-r--r-- 1 root root     835 2011-05-05 10:00 /usr/lib/libqt-mt.la
-rw-r--r-- 1 root root     861 2011-05-05 10:00 /usr/lib/libqt-mt.prl
lrwxrwxrwx 1 root root      17 2011-05-05 10:03 /usr/lib/libqt-mt.so -> libqt-mt.so.3.3.8
lrwxrwxrwx 1 root root      17 2011-05-05 10:03 /usr/lib/libqt-mt.so.3 -> libqt-mt.so.3.3.8
lrwxrwxrwx 1 root root      17 2011-05-05 10:03 /usr/lib/libqt-mt.so.3.3 -> libqt-mt.so.3.3.8
-rw-r--r-- 1 root root 7734748 2011-05-05 10:05 /usr/lib/libqt-mt.so.3.3.8

/usr/lib/qt3:
total 4
drwxr-xr-x 5 root root 4096 2011-11-26 15:13 plugins


Is there some other package I am missing?

Thanks,
   -Scott

---

### Post by Bachstelze on 2011-11-26
You're doing it wrong, the correct command is

```
g++ -o bnv_qt_main bnv_qt_main.o moc_bnv_qt_test.o  -lqt-mt  -lSM -lICE  -lX11 -lXext -lXmu -lXt -lXi  
```

---

### Post by jsedwards on 2011-11-27
Fascinating, that indeed fixes the problem.  I went in and reversed them in the ./configure script and now that works too.

So I guess the real problem is in autoconf?

Anyway, thanks!!

---

### Post by Bachstelze on 2011-11-27
Probably not in autoconf *per se* but rather in the templates your package uses.

---

