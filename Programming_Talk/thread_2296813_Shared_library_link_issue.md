---
title: "Shared library link issue"
date: 2015-09-29
forum: Programming Talk
---

### Post by itxpert on 2015-09-29
[B]Dear All,

I am having an issue on compiling. The contents of link file are given below:[/B]

/usr/bin/g++      -O3 -DNDEBUG    CMakeFiles/move3d-qt-studio.dir/main.cpp.o CMakeFiles/move3d-qt-studio.dir/move3d.cpp.o CMakeFiles/move3d-qt-studio.dir/moc_main.cxx.o  -o move3d-qt-studio  -L/home/usman/openrobots/lib -rdynamic ../../lib/Release/libMove3D-Qt-Gui.so -lQtOpenGL -lQtGui -lQtCore -lSM -lICE -lX11 -lXext -lxml2 -lGLU -lGL -lSM -lICE -lX11 -lXext -lmove3d /home/usman/openrobots/lib/libmove3d-planners.so /home/usman/openrobots/lib/libsoftMotion.so /home/usman/openrobots/lib/libgb.so -lm -lxml2 -lGLU -lGL -lmove3d /home/usman/openrobots/lib/libmove3d-planners.so -lqwt /home/usman/openrobots/lib/libsoftMotion.so /home/usman/openrobots/lib/libgb.so -lm -Wl,-rpath,/home/usman/openrobots/lib:/home/usman/openrobots/src/robotpkg/wip/move3d-studio/work.usman-ThinkPad-X230/move3d-studio-1.2.1/lib/Release: 


**And the error i am getting is below:**

../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::metaObject() const'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `stringContainer::stringContainer(QString)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `stringContainer::get()'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::getObject(Env::boolParameter)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `EnumPlannerParameterObject'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::getObject(Env::stringParameter)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::getObject(Env::doubleParameter)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::getObject(Env::intParameter)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::getString(Env::stringParameter)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::getObject(Env::vectorParameter)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `Env::setString(Env::stringParameter, QString)'
../../lib/Release/libMove3D-Qt-Gui.so: undefined reference to `stringContainer::set(QString)'
collect2: error: ld returned 1 exit status
src/move3d-qt/CMakeFiles/move3d-qt-studio.dir/build.make:168: recipe for target 'src/move3d-qt/move3d-qt-studio' failed
make[2]: *** [src/move3d-qt/move3d-qt-studio] Error 1
make[2]: Leaving directory '/home/usman/openrobots/src/robotpkg/wip/move3d-studio/work.usman-ThinkPad-X230/move3d-studio-1.2.1'
CMakeFiles/Makefile2:146: recipe for target 'src/move3d-qt/CMakeFiles/move3d-qt-studio.dir/all' failed
make[1]: *** [src/move3d-qt/CMakeFiles/move3d-qt-studio.dir/all] Error 2
make: *** [all] Error 2
make[1]: Leaving directory '/home/usman/openrobots/src/robotpkg/wip/move3d-studio/work.usman-ThinkPad-X230/move3d-studio-1.2.1'
Makefile:116: recipe for target 'all' failed


**I have also attached complete build log and link file. Please advise how to resolve it.**

---

### Post by itxpert on 2015-10-01
Any help people?

---

### Post by steeldriver on 2015-10-01
Where did you get the source? What version of Qt (3,4,5?) does it require?

---

### Post by itxpert on 2015-10-01
> **steeldriver said:**
> Where did you get the source? What version of Qt (3,4,5?) does it require?

The source is from [FONT=courier][COLOR=#4a4c48]git clone git://trac.laas.fr/git/robots/move3d-studio[/COLOR][/FONT]
[COLOR=#4A4C48][FONT=courier]
In instructions they have mentioned like this:[/FONT][/COLOR]
[COLOR=#4A4C48][FONT=Aller]
[/FONT][/COLOR][COLOR=#4A4C48][FONT=Aller]5) Install the last version of qwt[/FONT][/COLOR]
[LIST]
[*]  sudo apt-get install libqwt-dev 'or' sudo yum install qwt
[/LIST]
[COLOR=#4A4C48][FONT=Aller]Now what they mean by last version i dont know so i installed latest version of QT.
Do you think its QT version issue?[/FONT][/COLOR]

---

### Post by steeldriver on 2015-10-01
I don't know - were you able to successfully build the subordinate libraries (libmove3d  libmove3d-hri  libmove3d-planners)?

I tried to do so but it seems to be looking for a "gbM" package - which apparently is not the same as libgbm-dev

---

### Post by itxpert on 2015-10-02
> **steeldriver said:**
> I don't know - were you able to successfully build the subordinate libraries (libmove3d  libmove3d-hri  libmove3d-planners)?

I tried to do so but it seems to be looking for a "gbM" package - which apparently is not the same as libgbm-dev

Yes all subordinate libraries were installed without any problem. Only issue in last one move3d-studio. I am doing it on ubuntu btw.

---

