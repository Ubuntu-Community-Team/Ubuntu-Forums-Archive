---
title: "trouble configuring - going old and senile"
date: 2013-05-02
forum: Packaging and Compiling Programs
---

### Post by bouncingwilf on 2013-05-02
I'm just trying to compile and install tideEditor and it appears to be a fairly standard autoconfiguring package but fot the life of me I can't get it to find the relevant Qt modules.


The install readme gives the following instructions;

[HTML]tideEditor makes use of three Qt modules:  QtCore, QtGui, and Qt3Support.
To find the necessary headers and libraries, CPPFLAGS and LDFLAGS must be
set accordingly:

  bash-3.1$ ./configure \
    CPPFLAGS="-I$QT4DIR/include/QtCore -I$QT4DIR/include/QtGui -I$QT4DIR/include/Qt3Support" \
    LDFLAGS="-L$QT4DIR/lib"
  bash-3.1$ make
  bash-3.1$ su
  bash-3.1# make install
[/HTML]


Now on my system, these modules are located at /usr/include/qt4/ etc. but no amount of tinkering with the CPPFLAGS string seems to direct  configure to find the packages and hence configure aborts - where am I going wrong please?


Bouncingwilf.

---

