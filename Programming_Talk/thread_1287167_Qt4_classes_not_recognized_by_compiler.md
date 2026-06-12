---
title: "Qt4 classes not recognized by compiler"
date: 2009-10-09
forum: Programming Talk
---

### Post by junderbr on 2009-10-09
I have recently installed qt4 and for some reason when I execute make, some classes, i.e., header files are not found and I get and error like:

    error: QHttp: No such file or directory

I figured out that the header file is located in "/usr/share/qt4/include/QtNetwork".  It appears as though the compiler has no trouble locating header files in the QtGui directory, for instance, but It doesn't seem to recognize header files in the QtNetwork directory and perhaps others.  Does anyone know why this might be and how I might fix it?

---

### Post by snova on 2009-10-09
When compiling, add **-I/usr/include/qt4/QtNetwork** to the command line. This has to be done for every Qt module you use.

---

### Post by Zugzwang on 2009-10-11
> **snova said:**
> When compiling, add **-I/usr/include/qt4/QtNetwork** to the command line. This has to be done for every Qt module you use.

It it normally a better idea to use the "qmake" utility. Then one can just list the modules needed and qmake will take care of setting the include directories *and* of linking against the correct libraries.

---

