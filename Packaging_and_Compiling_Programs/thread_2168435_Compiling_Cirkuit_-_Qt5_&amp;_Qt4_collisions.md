---
title: "Compiling Cirkuit - Qt5 &amp; Qt4 collisions"
date: 2013-08-17
forum: Packaging and Compiling Programs
---

### Post by jacob-block on 2013-08-17
Hi all,

I'm having trouble building the program [Cirkuit]("http://wwwu.uni-klu.ac.at/magostin/cirkuit.html") and thought someone here might understand the issue.

Here are the steps from my build scripts:

```
sudo apt-get install texlive-latex-base texlive-latex-recommended texlive-pstricks texlive-base-bin texlive-extra-utils preview-latex-style m4 ghostscript pdf2svg
sudo apt-get install cmake kdelibs5-dev libqt4-dev libpoppler-qt4-dev
sudo apt-get install oxygen-icon-theme plasma-desktop gettext
cd ~
curl http://wwwu.uni-klu.ac.at/magostin/src/cirkuit-0.4.3.tar.bz2 | tar xj
mv cirk* cirkuit
cd cirkuit
mkdir build
cd build
cmake .. -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`


```

Here are my steps installing dpic, but I don't think (not sure) you need this to reproduce the error:
```

cd ~
curl https://ece.uwaterloo.ca/~aplevich/dpic/dpic.tar.gz | tar xz
cd dpic
make
sudo mv dpic /usr/local/bin
cd ~
rm -rf dpic

```

Once I get to the cmake command for building Cirkuit, I get the following error:

> -- The C compiler identification is GNU 4.7.3-- The CXX compiler identification is GNU 4.7.3
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - not found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found
-- Found Qt-Version 5.0.1 (using /usr/bin/qmake)
-- Looking for include file pthread.h
-- Looking for include file pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Found Automoc4: /usr/bin/automoc4  
-- Found Perl: /usr/bin/perl (found version "5.14.2") 
-- Found Phonon: /usr/include (Required is at least version "4.3.80") 
-- Performing Test _OFFT_IS_64BIT
-- Performing Test _OFFT_IS_64BIT - Success
-- Performing Test HAVE_FPIE_SUPPORT
-- Performing Test HAVE_FPIE_SUPPORT - Success
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL
-- Performing Test __KDE_HAVE_W_OVERLOADED_VIRTUAL - Success
-- Performing Test __KDE_HAVE_GCC_VISIBILITY
-- Performing Test __KDE_HAVE_GCC_VISIBILITY - Success
-- Configuring incomplete, errors occurred!

> CMake Error: The following variables are used in this project, but they are set to NOTFOUND.Please set them or make sure they are set and tested correctly in the CMake files:
QT_QT_INCLUDE_DIR
   used as include directory in directory /home/jacob/cirkuit/build/CMakeFiles/CMakeTmp


CMake Error: Internal CMake error, TryCompile configure of cmake failed


CMake Error at /usr/share/kde4/apps/cmake/modules/FindKDE4Internal.cmake:1297 (message):
  Qt compiled without support for -fvisibility=hidden.  This will break
  plugins and linking of some applications.  Please fix your Qt installation
  (try passing --reduce-exports to configure).
Call Stack (most recent call first):
  /usr/share/cmake-2.8/Modules/FindKDE4.cmake:95 (find_package)
  CMakeLists.txt:5 (find_package)

Clearly it is running into Qt5 compiling issues. Finding Qt5 instead of Qt4 libraries/header files. I am not sure how to fix it. I suspect the CMakeLists.txt file needs to be modified for forcing a Qt4 build, or I need to pass some parameters to define where the qt4-dev include/libs are.

Any help would be greatly appreciated! Thanks!

---

### Post by steeldriver on 2013-08-17
I had the same issue recently, and found this (the '-DQT_QMAKE_EXECUTABLE' option to cmake worked for me)

> 
How to force Cmake to use Qt4 when both Qt4 and Qt5 are installed on the same system
------------------------------------------------------------------------------------

On systems where both qt4 and qt5-base are installed, `qmake` refers to the 5.x version, so force cmake to use Qt4 this way:

export QT_SELECT=4

or using this option in cmake:

-DQT_QMAKE_EXECUTABLE=/usr/bin/qmake-qt4


SOURCE: [https://wiki.archlinux.org/index.php/KDE_Package_Guidelines](https://wiki.archlinux.org/index.php/KDE_Package_Guidelines)

---

### Post by oldos2er on 2013-08-17
Moved to Packaging & Compiling Programs.

---

### Post by jacob-block on 2013-08-17
Thanks! Worked perfectly.

---

