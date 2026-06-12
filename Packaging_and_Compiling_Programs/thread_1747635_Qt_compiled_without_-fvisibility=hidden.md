---
title: "Qt compiled without -fvisibility=hidden"
date: 2011-05-02
forum: Packaging and Compiling Programs
---

### Post by li-unix on 2011-05-02
For those who know about the Qt version offered in Kubuntu 11.04, when I compile my own program in KDevelop I get this error immediately:

CMake Error: Generator: execution of make failed. Make command was: /usr/bin/gmake "cmTryCompileExec/fast"
CMake Error at /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake:1300 (message):
[B]  Qt compiled without support for -fvisibility=hidden.  This will break
  plugins and linking of some applications.  Please fix your Qt installation.[/B]
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindKDE4.cmake:95 (FIND_PACKAGE)
  CMakeLists.txt:3 (find_package)

Any ideas how to fix this? I hope Kubuntu doesn't have a copy of Qt that is useless in development :(

---

### Post by MadCow108 on 2011-05-03
do you have libqt4-dev installed?
on my system the flag for visibility support (QT_VISIBILITY_AVAILABLE) is defined

---

### Post by li-unix on 2011-05-03
I have it installed. How do I check what the flag is defined to?

---

### Post by MadCow108 on 2011-05-03
compile this:
```
// compile with:
// g++ tmp.cpp -I /usr/include/qt4/

#include <QtCore/QtGlobal>
int main() {
#ifndef QT_VISIBILITY_AVAILABLE
#error QT_VISIBILITY_AVAILABLE is not available
#else
#warning ok
#endif
}
```

---

### Post by li-unix on 2011-05-03
I get #warning ok, so the flag is set! So why cmake complain about a missing flag?

At the same time, KDevelop also can't find my Qt libraries yet I have them installed (eg. libqt4-dev)

---

### Post by li-unix on 2011-05-03
I think it was a problem with some config files. I create a new KDevelop project and copied over all my source code and know everything works :)

Rule#1 in programming - keep your development environment the same!

---

