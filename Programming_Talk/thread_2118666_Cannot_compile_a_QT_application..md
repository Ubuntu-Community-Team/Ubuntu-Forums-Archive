---
title: "Cannot compile a QT application."
date: 2013-02-21
forum: Programming Talk
---

### Post by blendmaster345 on 2013-02-21
First, I am very sorry if this is the wrong section. If it is, please let me know.

Hello,

     I am trying to compile a QT4 application, and qmake worked fine. When I ran make, I ended up with problems. The entire output is

```
denton@denton-Inspiron-570 ~/Software/qsstv_7.1.7 $ make
cd src/ && make -f Makefile 
make[1]: Entering directory `/home/denton/Software/qsstv_7.1.7/src'
/usr/bin/uic-qt4 configform.ui -o ui_configform.h
/usr/bin/uic-qt4 dirform.ui -o ui_dirform.h
/usr/bin/uic-qt4 freqform.ui -o ui_freqform.h
/usr/bin/uic-qt4 slantform.ui -o ui_slantform.h
/usr/bin/uic-qt4 soundcontrol.ui -o ui_soundcontrol.h
/usr/bin/uic-qt4 editor/editorform.ui -o ui_editorform.h
/usr/bin/uic-qt4 editor/gradientform.ui -o ui_gradientform.h
/usr/bin/uic-qt4 editor/textform.ui -o ui_textform.h
/usr/bin/uic-qt4 calibrationform.ui -o ui_calibrationform.h
/usr/bin/uic-qt4 loggingform.ui -o ui_loggingform.h
/usr/bin/uic-qt4 cameracontrol.ui -o ui_cameracontrol.h
/usr/bin/uic-qt4 mainwindow.ui -o ui_mainwindow.h
/usr/bin/uic-qt4 gallerywidget.ui -o ui_gallerywidget.h
/usr/bin/uic-qt4 rxwidget.ui -o ui_rxwidget.h
/usr/bin/uic-qt4 txwidget.ui -o ui_txwidget.h
/usr/bin/uic-qt4 sweepform.ui -o ui_sweepform.h
g++ -c -m64 -pipe -O2 -D_REENTRANT -Wall -W -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I../tmp -I. -o ../tmp/main.o main.cpp
Assembler messages:
Fatal error: can't create ../tmp/main.o: No such file or directory
main.cpp:22:24: fatal error: QApplication: No such file or directory
compilation terminated.
make[1]: *** [../tmp/main.o] Error 2
make[1]: Leaving directory `/home/denton/Software/qsstv_7.1.7/src'
make: *** [sub-src-make_default-ordered] Error 2

```

I am sorry if the answer is obvious, just a bit of a noob ;)

Any help is appreciated.

---

### Post by spjackson on 2013-02-22
The error message seems to be because the directory /home/denton/Software/qsstv_7.1.7/tmp does not exist, so you could create it.

However, I would normally expect qmake/make to result in the creation of the target directory.

Do you need to compile it? There seems to be a package for Ubuntu: [http://packages.ubuntu.com/search?keywords=qsstv]("http://packages.ubuntu.com/search?keywords=qsstv")

---

