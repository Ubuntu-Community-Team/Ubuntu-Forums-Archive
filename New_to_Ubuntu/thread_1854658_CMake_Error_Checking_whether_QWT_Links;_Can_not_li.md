---
title: "CMake Error: Checking whether QWT Links; Can not link to QWT libraries (Ubuntu10.04)"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by myashar on 2011-10-04
Hello,

I am trying to install, build, and compile a software package using cmake and, later,
'make' using Qt version 4.7 and Qwt version 5.2.x. It appears as if cmake is able to find all of the necessary QWT include and header files and, apparently, all of the QWT libraries, but it can't seem to link to the QWT libraries (?) Here is some of the output and error messages I get when running cmake:

    -- Found QWT: /usr/local/lib/libqwt.so
    -- Looking for QWT headers in /usr/local/qwt-5.2.3-svn/include
    -- Looking for QWT header qwt_global.h
    -- Looking for QWT header qwt_global.h -- /usr/local/qwt-5.2.3-svn/include/qwt_global.h
    -- Checking whether QWT headers compile
    -- Checking whether QWT headers compile -- TRUE
    -- Checking that QWT compile version is 5.2.0 or later
    -- Checking that QWT compile version is 5.2.0 or later -- found 5.2.0 -- ok
    -- Using QWT libraries /usr/local/qwt-5.2.3-svn/lib/libqwt.so.5.2.3
    -- Checking whether QWT links
    CMake Error at install/config.cmake:601 (message):
    Could not link to QWT libraries:
    Call Stack (most recent call first):
    CMakeLists.txt:934 (casa_find)
    etc...
    -- Configuring incomplete, errors occurred!

I have the qwt libraries installed in the directory /usr/local/qwt-5.2.3-svn/lib/, with
contents:

    libqwt.so -> libqwt.so.5.2.3
    libqwt.so.5 -> libqwt.so.5.2.3
    libqwt.so.5.2 -> libqwt.so.5.2.3
    libqwt.so.5.2.3

The QWT include directory is: /usr/local/qwt-5.2.3-svn/include/
Note that I have also installed libqwt5-qt4-dev and qt4-dev-tools on my Ubutnu 10.04 LTS
system (via sudo apt-get install) as well. This has resulted in the following libraries being created (in /usr/lib):

    libqwt.so -> /usr/lib/libqwt-qt4.so
    libqwt.so.5.2 -> /usr/lib/libqwt-qt4.so.5.2
    libqwt.so.5.2.0 -> /usr/lib/libqwt-qt4.so.5.2.0
    libqwt-qt4.so.5.0.2 -> /usr/lib/libqwt-qt4.so.5.2.0
    libqwt.so.5 -> /usr/lib/libqwt-qt4.so.5.0.2
    libqwt.so.5.0 -> /usr/lib/libqwt-qt4.so.5.0.2
    libqwt.so.5.0.2 -> /usr/lib/libqwt-qt4.so.5.0.2
    libqwt.so.4 -> libqwt.so.4.2.0
 libqwt.so.4.2 -> libqwt.so.4.2.0

(I've also created some symlinks, e.g.,
sudo ln -s /usr/lib/libqwt-qt4.so /usr/local/lib/libqwt.so)

Header files were also created and put in /usr/include/qwt-qt4/.
Note that since I need Qt 4.7 for the software package I'm trying to compile/build,
I needed to download, install and build Qt separately (because the Ubuntu qt4-dev-tools
package only provides an older version of Qt). On my system the Qt4.7 include and
library files are in /usr/local/Troltech/Qt-4.7.0/.

Finally, the cmake command that I'm issuing is as follows:

    sudo cmake -DBOOST_ROOT=/home/yashar/Downloads/boost_1_43_0 \
    -DBOOST_INCLUDEDIR=/home/yashar/Downloads/boost_1_43_0 \
    -DBOOST_LIBRARYDIR=/home/yashar/Downloads/boost_1_43_0/stage/lib \
    -DQT4_INCLUDE_DIRS=/usr/local/Trolltech/Qt-4.7.0/include \
    -DQT_QMAKE_EXECUTABLE=/home/yashar/Downloads/qt-everywhere-opensource-src-4.7.0/bin/qmake \
    -DQT4_LIBRARIES=/usr/local/Trolltech/Qt-4.7.0/lib \
    -DQWT_INCLUDE_DIRS=/usr/local/qwt-5.2.3-svn/include \
    -DQWT_LIBRARIES=/usr/local/qwt-5.2.3-svn/lib/libqwt.so.5.2.3 \
    -DCMAKE_BUILD_TYPE=Debug $CASAROOT/code \
    -DQWT_INCLUDE_DIRS=/usr/local/qwt-5.2.3-svn/include \
    -DQWT_LIBRARIES=/usr/local/qwt-5.2.3-svn/lib/libqwt.so.5.2.3 \
    -DCMAKE_BUILD_TYPE=Debug $CASAROOT/code \

I am baffled by the error message that I am getting. Do I need to make any modifications
to my CMakeLists.txt file (or any other file)? Note that, for some reason, the version
of cmake that I had (2.8) did not have a FindQwt.cmake or FindQwt5.cmake module, so I
downloaded (to /usr/share/cmake-2.8/Modules/) these from the internet. Are there any
modifications that I can make to these files to fix this problem? I have also tried
things like:

    export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/local/lib/libqwt.so
    export LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:/usr/lib
    export LD_LIBRARY_PATH=/usr/local/qwt-5.2.3-svn/lib:$LD_LIBRARY_PATH
    export LD_LIBRARY_PATH=/usr/local/qwt-5.2.3-svn

but none of this has helped either. If you have any ideas, tips, or suggestions, can
you please let me know?

Thank you.

mark

---

