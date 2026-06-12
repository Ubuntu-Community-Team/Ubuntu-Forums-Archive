---
title: "dpkg-genchanges: error: cannot read files list file: No such file or directory"
date: 2009-11-03
forum: Packaging and Compiling Programs
---

### Post by DexterLB on 2009-11-03
THIS ERROR IS A KILLER!!!
I've been struggling to fix it for over a week, no success.
This is my first package using cdbs. Everything is fine, the configure, build and install phases go smoothly, the binary is placed where it should be (debian/<name>/usr/bin/), but dpkg-genchange fails.

```
 dpkg-buildpackage -rfakeroot -D -us -uc -sa
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package timelapse
dpkg-buildpackage: source version 0.0.1-0ubuntu1
dpkg-buildpackage: source changed by Angel Pavlov Angelov <dexterabc@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
test -x debian/rules
test "`id -u`" = 0
rmdir obj-i486-linux-gnu
rmdir: failed to remove `obj-i486-linux-gnu': No such file or directory
make: [cleanbuilddir] Error 1 (ignored)
/usr/bin/make  -C obj-i486-linux-gnu  -k clean
rm -f debian/stamp-makefile-build
rm -rf obj-i486-linux-gnu
 dpkg-source -b timelapse-0.0.1
dpkg-source: warning: Version number suggests Ubuntu changes, but Maintainer: does not have Ubuntu address
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: info: using source format `1.0'
dpkg-source: info: building timelapse using existing timelapse_0.0.1.orig.tar.gz
dpkg-source: info: building timelapse in timelapse_0.0.1-0ubuntu1.diff.gz
dpkg-source: info: building timelapse in timelapse_0.0.1-0ubuntu1.dsc
 debian/rules build
test -x debian/rules
mkdir -p "obj-i486-linux-gnu"
cd obj-i486-linux-gnu && cmake /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/. -DCMAKE_INSTALL_PREFIX="/usr" -DCMAKE_C_COMPILER:FILEPATH="cc" -DCMAKE_CXX_COMPILER:FILEPATH="g++" -DCMAKE_C_FLAGS="-g -O2 -g -Wall -O2" -DCMAKE_CXX_FLAGS="-g -O2 -g -Wall -O2" -DCMAKE_SKIP_RPATH=ON -DCMAKE_VERBOSE_MAKEFILE=ON 
-- The C compiler identification is GNU
-- The CXX compiler identification is GNU
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/g++
-- Check for working CXX compiler: /usr/bin/g++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt-Version 4.5.2
-- Configuring done
-- Generating done
-- Build files have been written to: /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu
/usr/bin/make  -C obj-i486-linux-gnu  
make[1]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -H/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -B/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu --check-build-system CMakeFiles/Makefile.cmake 0
/usr/bin/cmake -E cmake_progress_start /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles/progress.make
/usr/bin/make -f CMakeFiles/Makefile2 all
make[2]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/make -f CMakeFiles/timelapse.dir/build.make CMakeFiles/timelapse.dir/depend
make[3]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 8
[ 12%] Generating ui_mainwindow.h
/usr/bin/uic-qt4 -o /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/ui_mainwindow.h /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/mainwindow.ui
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 6
[ 25%] Generating moc_mainwindowimpl.cxx
/usr/bin/moc-qt4 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -o /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/moc_mainwindowimpl.cxx /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/mainwindowimpl.h
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 7
[ 37%] Generating moc_conversionthread.cxx
/usr/bin/moc-qt4 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -o /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/moc_conversionthread.cxx /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/conversionthread.h
cd /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu && /usr/bin/cmake -E cmake_depends "Unix Makefiles" /home/human/develop/kdevelop/timelapse/timelapse-0.0.1 /home/human/develop/kdevelop/timelapse/timelapse-0.0.1 /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles/timelapse.dir/DependInfo.cmake --color=
Scanning dependencies of target timelapse
make[3]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/make -f CMakeFiles/timelapse.dir/build.make CMakeFiles/timelapse.dir/build
make[3]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 1
[ 50%] Building CXX object CMakeFiles/timelapse.dir/main.o
/usr/bin/g++   -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -g -O2 -g -Wall -O2 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default   -o CMakeFiles/timelapse.dir/main.o -c /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/main.cpp
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 2
[ 62%] Building CXX object CMakeFiles/timelapse.dir/mainwindowimpl.o
/usr/bin/g++   -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -g -O2 -g -Wall -O2 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default   -o CMakeFiles/timelapse.dir/mainwindowimpl.o -c /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/mainwindowimpl.cpp
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 3
[ 75%] Building CXX object CMakeFiles/timelapse.dir/conversionthread.o
/usr/bin/g++   -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -g -O2 -g -Wall -O2 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default   -o CMakeFiles/timelapse.dir/conversionthread.o -c /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/conversionthread.cpp
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 4
[ 87%] Building CXX object CMakeFiles/timelapse.dir/moc_mainwindowimpl.o
/usr/bin/g++   -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -g -O2 -g -Wall -O2 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default   -o CMakeFiles/timelapse.dir/moc_mainwindowimpl.o -c /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/moc_mainwindowimpl.cxx
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 5
[100%] Building CXX object CMakeFiles/timelapse.dir/moc_conversionthread.o
/usr/bin/g++   -DQT_DLL -DQT_DLL -DQT_GUI_LIB -DQT_CORE_LIB -g -O2 -g -Wall -O2 -I/usr/include/qt4 -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtCore -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -I/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu -I/usr/include/qt4/QtXmlPatterns -I/usr/include/qt4/QtWebKit -I/usr/include/qt4/QtHelp -I/usr/include/qt4/QtAssistant -I/usr/include/qt4/QtDBus -I/usr/include/qt4/QtTest -I/usr/include/qt4/QtUiTools -I/usr/include/qt4/QtScript -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtXml -I/usr/include/qt4/QtSql -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtDesigner -I/usr/include/qt4/Qt3Support -I/usr/share/qt4/mkspecs/default   -o CMakeFiles/timelapse.dir/moc_conversionthread.o -c /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/moc_conversionthread.cxx
Linking CXX executable timelapse
/usr/bin/cmake -E cmake_link_script CMakeFiles/timelapse.dir/link.txt --verbose=1
/usr/bin/g++   -g -O2 -g -Wall -O2  -Wl,-Bsymbolic-functions CMakeFiles/timelapse.dir/main.o CMakeFiles/timelapse.dir/mainwindowimpl.o CMakeFiles/timelapse.dir/conversionthread.o CMakeFiles/timelapse.dir/moc_mainwindowimpl.o CMakeFiles/timelapse.dir/moc_conversionthread.o  -o timelapse -rdynamic -lQtGui -lXext -lX11 -lm -lQtCore -lpthread -ldl 
make[3]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles  1 2 3 4 5 6 7 8
[100%] Built target timelapse
make[2]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -E cmake_progress_start /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 0
make[1]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
touch debian/stamp-makefile-build
DEB_MAKE_CHECK_TARGET unset, not running checks
 fakeroot debian/rules binary
test -x debian/rules
test "`id -u`" = 0
mkdir -p "obj-i486-linux-gnu"
DEB_MAKE_CHECK_TARGET unset, not running checks
/usr/bin/make  -C obj-i486-linux-gnu  install DESTDIR=/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/debian/timelapse/
make[1]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -H/home/human/develop/kdevelop/timelapse/timelapse-0.0.1 -B/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu --check-build-system CMakeFiles/Makefile.cmake 0
/usr/bin/cmake -E cmake_progress_start /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles/progress.make
/usr/bin/make -f CMakeFiles/Makefile2 all
make[2]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/make -f CMakeFiles/timelapse.dir/build.make CMakeFiles/timelapse.dir/depend
make[3]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
cd /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu && /usr/bin/cmake -E cmake_depends "Unix Makefiles" /home/human/develop/kdevelop/timelapse/timelapse-0.0.1 /home/human/develop/kdevelop/timelapse/timelapse-0.0.1 /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles/timelapse.dir/DependInfo.cmake --color=
make[3]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/make -f CMakeFiles/timelapse.dir/build.make CMakeFiles/timelapse.dir/build
make[3]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
make[3]: Nothing to be done for `CMakeFiles/timelapse.dir/build'.
make[3]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -E cmake_progress_report /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles  1 2 3 4 5 6 7 8
[100%] Built target timelapse
make[2]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
/usr/bin/cmake -E cmake_progress_start /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu/CMakeFiles 0
/usr/bin/make -f CMakeFiles/Makefile2 preinstall
make[2]: Entering directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
make[2]: Nothing to be done for `preinstall'.
make[2]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
Install the project...
/usr/bin/cmake -P cmake_install.cmake
-- Install configuration: ""
-- Installing: /home/human/develop/kdevelop/timelapse/timelapse-0.0.1/debian/timelapse/usr/bin/timelapse
make[1]: Leaving directory `/home/human/develop/kdevelop/timelapse/timelapse-0.0.1/obj-i486-linux-gnu'
 dpkg-genchanges -sa >../timelapse_0.0.1-0ubuntu1_i386.changes
dpkg-genchanges: error: cannot read files list file: No such file or directory
dpkg-buildpackage: error: dpkg-genchanges gave error exit status 2
debuild: fatal error at line 1334:
dpkg-buildpackage -rfakeroot -D -us -uc -sa failed
```

Please help, cdbs is so easy to use, just that error...
I can't find a solution...

The entire source archive is attached.

---

### Post by SevenMachines on 2009-11-03
I see you're using cmake in debian/rules, sadly I'm completely ignorant of all things cmake but I'm only half ignorant of debhelper, and luckily it knows this and makes things simple
so I'd recommend just letting that do the dirty work. Just add debhelper to rules so, 

debian/rules:
```
#!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk
include /usr/share/cdbs/1/class/cmake.mk #Cmake stuff
```

The package then builds fine, you can judge whether everything is installing to the right place (it looks ok), luckily debhelper will let you tweak that all happily too. Its already a build dependency so debian/control is fine

---

### Post by DexterLB on 2009-11-03
Thank you. This fixes it. :popcorn:

Marking thread as solved.

P.S. How do I do a "thanks" to an user? Before there was a "send thanks" button, now I can't find it.

---

### Post by SevenMachines on 2009-11-03
> **DexterLB said:**
> Thank you. This fixes it. :popcorn:

Marking thread as solved.

P.S. How do I do a "thanks" to an user? Before there was a "send thanks" button, now I can't find it.
I don't know how you add 'thanks' but a thanks message is just as good as far as I'm concerned :) Glad it helps

---

### Post by davide parise on 2013-02-19
Thank you. This fixes it for me too

---

