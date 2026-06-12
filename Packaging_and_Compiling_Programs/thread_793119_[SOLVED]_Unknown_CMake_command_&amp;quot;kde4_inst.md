---
title: "[SOLVED] Unknown CMake command &amp;quot;kde4_install_icons&amp;quot;"
date: 2008-05-13
forum: Packaging and Compiling Programs
---

### Post by happysmileman on 2008-05-13
I've gotten the latest source of KDiamond from SVN, and want to build it (I made a few tiny changes to it so don't want to use the packages), when I do a "cmake ." I get:

```
CMake Error: Error in cmake code at
/home/paul/kdiamond/kdiamond/src/pics/CMakeLists.txt:1:
Unknown CMake command "kde4_install_icons".
-- Configuring done
```

I have kdelibs5-dev, kdesdk-kde4, and kde4-devel installed so I would assume that I have all I need to build this.

Any ideas?

---

### Post by thotmos on 2008-05-22
Hi there
do you have libkdegames-dev-kde4? it did the trick for me
don't forget to set LibKDEGames_DIR
```

sameh@desktop:~/kdiamond-0.3$ export LibKDEGames_DIR=/usr/lib/kde4:$LibKDEGames_DIR
sameh@desktop:~/kdiamond-0.3$ cmake .
-- Found Qt-Version 4.4.0 (using /usr/bin/qmake-qt4)
-- Found X11: /usr/lib/libX11.so
-- Found KDE 4.0 include dir: /usr/lib/kde4/include
-- Found KDE 4 library dir: /usr/lib/kde4/lib
-- Found KDE4 kconfig_compiler preprocessor: /usr/lib/kde4/bin/kconfig_compiler
-- Found KDE4 automoc: /usr/lib/kde4/bin/kde4automoc
-- Found KDEGAMES: /usr/lib/kde4/include
-- Configuring done
-- Generating done
-- Build files have been written to: /home/sameh/kdiamond-0.3
sameh@desktop:~/kdiamond-0.3$ make
[  8%] Generating settings.h, settings.cpp
[ 16%] Generating kdiamond_automoc.cpp
Generating game.moc
Generating container.moc
Generating board.moc
Generating mainwindow.moc
Generating animator.moc
Generating diamond.moc
/home/sameh/kdiamond-0.3/src/container.h:0: Warning: No relevant classes found. No output generated.
Scanning dependencies of target kdiamond
[ 25%] Building CXX object src/CMakeFiles/kdiamond.dir/kdiamond_automoc.o
[ 33%] Building CXX object src/CMakeFiles/kdiamond.dir/animator.o
[ 41%] Building CXX object src/CMakeFiles/kdiamond.dir/board.o
[ 50%] Building CXX object src/CMakeFiles/kdiamond.dir/container.o
[ 58%] Building CXX object src/CMakeFiles/kdiamond.dir/diamond.o
[ 66%] Building CXX object src/CMakeFiles/kdiamond.dir/game.o
[ 75%] Building CXX object src/CMakeFiles/kdiamond.dir/main.o
[ 83%] Building CXX object src/CMakeFiles/kdiamond.dir/mainwindow.o
[ 91%] Building CXX object src/CMakeFiles/kdiamond.dir/renderer.o
[100%] Building CXX object src/CMakeFiles/kdiamond.dir/settings.o
Linking CXX executable kdiamond
[100%] Built target kdiamond
```

---

