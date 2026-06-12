---
title: "Problem creating Library Debian Package"
date: 2014-12-21
forum: Packaging and Compiling Programs
---

### Post by MariusLinux on 2014-12-21
Hi,
I'm currently trying to create a Debian package of my library 'QTurtle' (written in C++, using Qt, providing 'turtle graphics for Qt's QGraphicsScene, made for a little project), including a -dev package. I've got a directory 'libqturtle-1.0', containing the source code (qturtle.cpp, qturtle.h, qturtle.pro, qturtle_global.h), nothing else. Here is the .pro file:

```
QT       += widgets

TARGET = qturtle
TEMPLATE = lib

DEFINES += QTURTLE_LIBRARY

SOURCES += qturtle.cpp

HEADERS += qturtle.h\
        qturtle_global.h

unix {
    headersf.files = $$HEADERS
    headersf.path = /usr/include
    target.path = /usr/lib
    INSTALLS += target
    INSTALLS += headersf
}


```

In this directory, I run:
```
dh_make --createorig
```

It produced the following output:
```
Currently there is no top level Makefile. This may require additional tuning.
Done. Please edit the files in the debian/ subdirectory now. You should also
check that the libqturtle Makefiles install into $DESTDIR and not in / .
Make sure you change the package name from libqturtleBROKEN to something
else, such as libqturtle1 in the debian/control file.
```

It created everything like it should. In the current's dir 'debian' subdir, I've removed all the unnecessary files, leaving only this:

changelog:
```
libqturtle (1.0-1) utopic; urgency=low

  * First QTurtle release

 -- Marius Steffen <marius.steffen@posteo.de>  Sun, 21 Dec 2014 02:35:20 +0100


```

compat:
```
9


```
control:
```
Source: libqturtle
Priority: optional
Maintainer: Marius Steffen <marius.steffen@posteo.de>
Build-Depends: debhelper (>= 9)
Standards-Version: 3.9.5
Section: libs

Package: libqturtle-dev
Section: libdevel
Architecture: any
Depends: libqturtle1 (= ${binary:Version}), ${misc:Depends}
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>
 
Package: libqturtle1
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: <insert up to 60 chars description>
 <insert long description, indented with spaces>


```

control:
```
Source: libqturtle
Priority: optional
Maintainer: Marius Steffen <marius.steffen@posteo.de>
Build-Depends: debhelper (>= 9)
Standards-Version: 3.9.5
Section: libs

Package: libqturtle-dev
Section: libdevel
Architecture: any
Depends: libqturtle1 (= ${binary:Version}), ${misc:Depends}
Description: Development package for libqturtle
 <insert long description, indented with spaces>
 
Package: libqturtle1
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: QTurtle Library
 <insert long description, indented with spaces>


```

libqturtle-dev.dirs:
```
usr/lib
usr/include
```

libqturtle-dev.install:
```
usr/include/*
usr/lib/lib*.a
usr/lib/lib*.so
usr/lib/pkgconfig/*
usr/share/pkgconfig/*


```

libqturtle1.dirs:
```
usr/lib
```

libqturtle1.install:
```
usr/lib/lib*.so.*


```

rules:
```
#!/usr/bin/make -f
# See debhelper(7) (uncomment to enable)
# output every command that modifies files on the build system.
#DH_VERBOSE = 1

# see EXAMPLES in dpkg-buildflags(1) and read /usr/share/dpkg/*
DPKG_EXPORT_BUILDFLAGS = 1
include /usr/share/dpkg/default.mk

# see FEATURE AREAS in dpkg-buildflags(1)
#export DEB_BUILD_MAINT_OPTIONS = hardening=+all

# see ENVIRONMENT in dpkg-buildflags(1)
# package maintainers to append CFLAGS
#export DEB_CFLAGS_MAINT_APPEND  = -Wall -pedantic
# package maintainers to append LDFLAGS
#export DEB_LDFLAGS_MAINT_APPEND = -Wl,--as-needed


# main packaging script based on dh7 syntax
%:
    dh $@ --buildsystem=qmake_qt4

# debmake generated override targets
# This is example for Cmake (See [http://bugs.debian.org/641051](http://bugs.debian.org/641051) )
#override_dh_auto_configure:
#    dh_auto_configure -- \
#    -DCMAKE_LIBRARY_PATH=$(DEB_HOST_MULTIARCH)





```

The 'debian/source' subdir contains format, containing:
```
3.0 (quilt)


```

copyright and docs remained unchanged, as I am just trying to build this package, only if this succeeds, I am going to think about this files;)

Next, ran:
```
dpkg-buildpackage -S -us -uc
```

Output:
```
dpkg-buildpackage: Quellpaket libqturtle
dpkg-buildpackage: Quellversion 1.0-1
dpkg-buildpackage: Quelldistribution utopic
dpkg-buildpackage: Quellen geändert durch Marius Steffen <marius.steffen@posteo.de>
 dpkg-source --before-build libqturtle-1.0
 fakeroot debian/rules clean
dh clean --buildsystem=qmake_qt4
   dh_testdir -O--buildsystem=qmake_qt4
   dh_auto_clean -O--buildsystem=qmake_qt4
   dh_clean -O--buildsystem=qmake_qt4
 dpkg-source -b libqturtle-1.0
dpkg-source: Information: Quellformat »3.0 (quilt)« wird verwendet
dpkg-source: Information: libqturtle wird unter Benutzung des existierenden ./libqturtle_1.0.orig.tar.xz gebaut
dpkg-source: Information: libqturtle wird in libqturtle_1.0-1.debian.tar.xz gebaut
dpkg-source: Information: libqturtle wird in libqturtle_1.0-1.dsc gebaut
 dpkg-genchanges -S >../libqturtle_1.0-1_source.changes
dpkg-genchanges: kompletter Quellcode beim Hochladen hinzufügen
 dpkg-source --after-build libqturtle-1.0
dpkg-buildpackage: Alles hochzuladen (Originalquellen enthalten)


```
(if you need English output, just tell me, I will switch my system's language from German to English ;) )

Finally, I ran:
```
debuild -us -uc
```

Output:
```
dpkg-buildpackage -rfakeroot -D -us -uc
dpkg-buildpackage: Quellpaket libqturtle
dpkg-buildpackage: Quellversion 1.0-1
dpkg-buildpackage: Quelldistribution utopic
dpkg-buildpackage: Quellen geändert durch Marius Steffen <marius.steffen@posteo.de>
 dpkg-source --before-build libqturtle-1.0
dpkg-buildpackage: Host-Architektur amd64
 fakeroot debian/rules clean
dh clean --buildsystem=qmake_qt4
   dh_testdir -O--buildsystem=qmake_qt4
   dh_auto_clean -O--buildsystem=qmake_qt4
   dh_clean -O--buildsystem=qmake_qt4
 dpkg-source -b libqturtle-1.0
dpkg-source: Information: Quellformat »3.0 (quilt)« wird verwendet
dpkg-source: Information: libqturtle wird unter Benutzung des existierenden ./libqturtle_1.0.orig.tar.xz gebaut
dpkg-source: Information: libqturtle wird in libqturtle_1.0-1.debian.tar.xz gebaut
dpkg-source: Information: libqturtle wird in libqturtle_1.0-1.dsc gebaut
 debian/rules build
dh build --buildsystem=qmake_qt4
   dh_testdir -O--buildsystem=qmake_qt4
   dh_auto_configure -O--buildsystem=qmake_qt4
   dh_auto_build -O--buildsystem=qmake_qt4
make[1]: Entering directory '/media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0'
g++ -c -m64 -pipe -g -O2 -fstack-protector-strong -Wformat -Werror=format-security -D_FORTIFY_SOURCE=2 -Wall -W -D_REENTRANT -fPIC -DQTURTLE_LIBRARY -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -o qturtle.o qturtle.cpp
rm -f libqturtle.so.1.0.0 libqturtle.so libqturtle.so.1 libqturtle.so.1.0
g++ -m64 -Wl,-Bsymbolic-functions -Wl,-z,relro -shared -Wl,-soname,libqturtle.so.1 -o libqturtle.so.1.0.0 qturtle.o   -L/usr/lib/x86_64-linux-gnu -lQtGui -lQtCore -lpthread  
ln -s libqturtle.so.1.0.0 libqturtle.so
ln -s libqturtle.so.1.0.0 libqturtle.so.1
ln -s libqturtle.so.1.0.0 libqturtle.so.1.0
make[1]: Leaving directory '/media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0'
   dh_auto_test -O--buildsystem=qmake_qt4
 fakeroot debian/rules binary
dh binary --buildsystem=qmake_qt4
   dh_testroot -O--buildsystem=qmake_qt4
   dh_prep -O--buildsystem=qmake_qt4
   dh_installdirs -O--buildsystem=qmake_qt4
/media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs: 1: /media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs: usr/lib: not found
/media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs: 2: /media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs: usr/include: not found
dh_installdirs: problem reading debian/libqturtle-dev.dirs: 
debian/rules:22: recipe for target 'binary' failed
make: *** [binary] Error 127
dpkg-buildpackage: Fehler: Fehler-Exitstatus von fakeroot debian/rules binary war 2
debuild: fatal error at line 1364:
dpkg-buildpackage -rfakeroot -D -us -uc failed
```

The error seems to be:
```
/media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs:  1:  /media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs:  usr/lib: not found
/media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs:  2:  /media/Daten/Entwicklung/QTurtleLibDeb/libqturtle-1.0/debian/libqturtle-dev.dirs:  usr/include: not found
```

I don't have any clue why this happens, and I haven't found a solution yet, if anybody of you could help me, that would be really great :-)

THX in advance,
Marius

---

### Post by schragge on 2014-12-22
Any *.install, *.dirs, *.docs and so on under debian/ with executable bit set is considered a script and debhelper will try to execute them. With executable bit unset they are considered just file/directory lists. So try
```
chmod -x debian/libqturtle-dev.dirs
```

---

### Post by MariusLinux on 2014-12-22
> **schragge said:**
> Any *.install, *.dirs, *.docs and so on under debian/ with executable bit set is considered a script and debhelper will try to execute them. With executable bit unset they are considered just file/directory lists. So try
```
chmod -x debian/libqturtle-dev.dirs
```

Thank you very much :D
This finally solved my problem, but for somebody maybe having the same problem: '/media/Daten' is a NTFS partition on my harddisk :-/
So that's the reason why the executable bit wasn't set. Really stupid mistake. Don't try packaging on NTFS.

Greetings,
Marius

---

