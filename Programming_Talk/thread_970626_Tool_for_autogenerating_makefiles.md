---
title: "Tool for autogenerating makefiles?"
date: 2008-11-04
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-04
I'm looking for a easy-to-use tool to create makefiles.

Like I just select files and the program makes me the makefile.

---

### Post by JupiterV2 on 2008-11-04
I suppose that would be the GNU auto tools collection: automake, autoconf, libtools...etc...

You need to write some basic rules for the auto-tools to follow but they generate an appropriate Makefile for you. They are available through [www.gnu.org]("http://www.gnu.org") or the Ubuntu/Debian repositories.

---

### Post by Zugzwang on 2008-11-04
I would vote for "qmake". This is a quite restricted make-tool, but it is also quite simple.

You just create some ".pro" file in your project directory and put something like the following content there:
```

TEMPLATE = app console
CONFIG  += debug
CONFIG  -= qt
QT -= gui core

HEADERS += FirstHeader.h AndSoOn.h
SOURCES += FirstSourceFile.cpp AndSoOn.cpp
TARGET = release
LIBS += -lxml2 -lboost_iostreams

```

Adapt this file to your needs. The first line sets the "template" of the project. "app console" is normally what you need. In the second line, you can either put "debug" or "release" to get your executable either with debug symbols or optimized. Just copy the third and fourth line to avoid automatic linking against the QT libraries.

The lines 5-8 (Headers,Sources,Target,Libs) are self-explaining. Additionally, you can add lines like the following:

```

INCLUDEPATH = /home/you/customLibs/myLib
DEFINES += YOUR_DEBUG_SYMBOLS
PKGCONFIG += glib-2.0

```

These should also be self-explaining.

Then you can simply run "qmake-qt4 <YourPROFile>" and get a Makefile.

---

### Post by dribeas on 2008-11-05
> **crazyfuturamanoob said:**
> I'm looking for a easy-to-use tool to create makefiles.

Like I just select files and the program makes me the makefile.

CMake (even QT has moved out of qmake and into CMake :P)

---

### Post by loell on 2008-11-05
install anjuta and it will also install autotools/automake, import or make a c/c++ project. and it automatically add the am and ac files necessary for generating make files, basically up to the compilation or building process, all of it are automated.

---

### Post by Delever on 2008-11-05
[http://www.lrde.epita.fr/~adl/autotools.html](http://www.lrde.epita.fr/~adl/autotools.html)

Those pdf slides there were clearest explanation how to get autotools going.

---

