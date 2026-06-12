---
title: "g++ compiling output"
date: 2006-08-12
forum: Programming Talk
---

### Post by Ziggurat on 2006-08-12
Hi, ive noticed that when i compile some apps, the compiler output is like this:

[CC] file.cpp

or something like this. I am developing an app and would like to get this kind of output when i compile instead of:

g++ -c -pipe -g -D_REENTRANT -Wall -W  -DQT_SQL_LIB -DQT_XML_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4 -Imoc -Iui -o obj/moc_DialogNuevoRecibo.o moc/moc_DialogNuevoRecibo.cpp


How can i do this?

Thanks.

---

### Post by cwaldbieser on 2006-08-12
> **Ziggurat said:**
> Hi, ive noticed that when i compile some apps, the compiler output is like this:

[CC] file.cpp

or something like this. I am developing an app and would like to get this kind of output when i compile instead of:

g++ -c -pipe -g -D_REENTRANT -Wall -W  -DQT_SQL_LIB -DQT_XML_LIB -DQT_GUI_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4 -Imoc -Iui -o obj/moc_DialogNuevoRecibo.o moc/moc_DialogNuevoRecibo.cpp


How can i do this?

Thanks.

I am not sure what your exact aim is, but you could just write a shell script that passed its arguments to g++ and piped its output through some sed or awk script to print out only what you wanted to see.  You would then compile using the script instead of the compiler directly.

---

