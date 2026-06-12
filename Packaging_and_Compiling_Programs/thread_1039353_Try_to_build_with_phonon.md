---
title: "Try to build with phonon"
date: 2009-01-14
forum: Packaging and Compiling Programs
---

### Post by copiutzu on 2009-01-14
Hi

I'm a new user of UBUNTU. I've installed the QT application and I tried to use phonon class libraries to create some sound application.

I'm trying to compile this code:

    Phonon::MediaObject *mediaObject = new Phonon::MediaObject(this);
    mediaObject->setCurrentSource(Phonon::MediaSource("/mymusic/barbiegirl.wav"));
    Phonon::AudioOutput *audioOutput =
        new Phonon::AudioOutput(Phonon::MusicCategory, this);
    Phonon::Path path = Phonon::createPath(mediaObject, audioOutput);

but I get the following linker errors:

Build (make)...
/usr/bin/uic ui/dialog.ui -o build/ui_dialog.h
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_PHONON_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/phonon -I/usr/include/qt4/phonon -I/usr/include/qt4 -Ibuild -Ibuild -o build/dialogimpl.o src/dialogimpl.cpp
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_PHONON_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/phonon -I/usr/include/qt4/phonon -I/usr/include/qt4 -Ibuild -Ibuild -o build/main.o src/main.cpp
/usr/bin/moc -DQT_PHONON_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/phonon -I/usr/include/qt4/phonon -I/usr/include/qt4 -Ibuild -Ibuild src/dialogimpl.h -o build/moc_dialogimpl.cpp
g++ -c -m64 -pipe -g -Wall -W -D_REENTRANT -DQT_PHONON_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4/phonon -I/usr/include/qt4/phonon -I/usr/include/qt4 -Ibuild -Ibuild -o build/moc_dialogimpl.o build/moc_dialogimpl.cpp
g++ -m64 -Wl,-rpath,/usr/share/qt4/lib -o bin/AUDIO1 build/dialogimpl.o build/main.o build/moc_dialogimpl.o    -L/usr/lib -lphonon -lQtGui -L/usr/lib -L/usr/X11R6/lib -laudio -lXt -lpng -lSM -lICE -pthread -pthread -lXi -lXrender -lXrandr -lXfixes -lXcursor -lXinerama -lfreetype -lXext -lX11 -lQtCore -lfontconfig -lz -lm -pthread -lgthread-2.0 -lrt -lglib-2.0 -ldl -lpthread
/
usr/bin/ld: cannot find -lphonon
collect2: ld returned 1 exit status
make: *** [bin/AUDIO1] Error 1
---------------------- Build finished without error----------------------

Can someone give me some ideas?

---

### Post by cubeist on 2009-01-14
do you have libphonon-dev installed?
```
sudo apt-get install libphonon-dev
```

---

### Post by copiutzu on 2009-01-14
> **cubeist said:**
> do you have libphonon-dev installed?
```
sudo apt-get install libphonon-dev
```

Thank you for the advice.
Unfortunately, I had it installed and still not working.

---

### Post by ariismail on 2009-02-26
I had the same error when I wanted to use Creator with phonon. I've installed libphonon-dev and it worked. Thanks for the advice.

---

### Post by seyed on 2010-03-10
> **cubeist said:**
> do you have libphonon-dev installed?
```
sudo apt-get install libphonon-dev
```

Yeah!
Its worked :p:o

Thanks a lot

---

