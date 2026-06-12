---
title: "qmake project setup - qtestlib scenario"
date: 2009-04-03
forum: Programming Talk
---

### Post by dusan.saiko on 2009-04-03
Hello all,

I am trying to setup some structured generic project skeleton and running into a problem separating qtlibtest into subproject, as those should not be built in as part of the application, and I am trying to use some structured project setup as I do not like all files just being in one folder (I am in general a Java developer).. I have spent a half day searching the internet have not found anything.

sampleapp-project.pro:
TEMPLATE = subdirs
CONFIG += ordered
SUBDIRS = sampleapp sampleapp-tests

sampleapp.pro
TEMPLATE = app
TARGET =
DEPENDPATH += . inc src
INCLUDEPATH += . inc src
HEADERS += painter.h
SOURCES += painter.cpp main.cpp

sampleapp-tests.pro
TEMPLATE = app
QT += testlib
TARGET =
DEPENDPATH += . inc src ../sampleapp/inc ../sampleapp/src
INCLUDEPATH += . inc src ../sampleapp/inc ../sampleapp/src

# Input
HEADERS += sampleapp-tests.h
SOURCES += sampleapp-tests.cpp

There exist painter.h and painter.cpp defining Painter object under sampleapp project.

My problem is trying to use this Painter object from class PainterTest which is under sampleapp-tests project, receiving "undefinied reference to 'Painter:Painter()' when building.

If I look at the compile output, the test is not linking against objects from the sampleapp:

g++ -o sampleapp-tests debug/sampleapp.o debug/moc_sampleapp.o -L/usr/lib -lQtTest -lQtGui -lQtCore -lpthread


I very appreciate any help on:

- how to make this scenario work
- is this the way project should be setup, are there any guidlines and may be tutorials on this ?

thank you in advance

---

### Post by jtourville on 2009-04-03
In your sampleapp-tests.pro file, you should add painter.cpp to your SOURCES definition.  As far as I can tell, that's all you're missing.

---

### Post by dusan.saiko on 2009-04-04
Thank you. I have tried that already before, the problem was It was not enough to add the painter.cpp into sampleapp-tests.pro, I was then getting "undefined reference to `vtable"  error. I found out this is because QT and MOC needed by using macro QT_OBJECT.

But it was solved then by incluidng painter.h as well in the headers section of sampleapp-tests.

Thanks :-)

---

### Post by jtourville on 2009-04-04
Ah, glad you got it working!  :)

---

