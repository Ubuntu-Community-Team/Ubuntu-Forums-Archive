---
title: "Having trouble including Phonon?"
date: 2009-11-14
forum: Programming Talk
---

### Post by mickbuntu on 2009-11-14
Hello,

  I'm doing a tutorial for qt4 programming. I can't get includes for Phonon here is the error output:

Running build steps for project sampleproj...
Starting: /usr/bin/qmake-qt4 /home/myhome/projects/sampleproj/sampleproj/sampleproj.pro -spec /usr/share/qt4/mkspecs/linux-g++ -r CONFIG+=debug 
Exited with code 0.
Starting: /usr/bin/make -w 
make: Entering directory `/home/myhome/projects/sampleproj/sampleproj'
g++ -c -pipe -g -Wall -W -D_REENTRANT -DQT_PHONON_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/phonon -I/usr/include/qt4 -I. -I. -o main.o main.cpp
In file included from main.cpp:2:
mainwindow.h:8:18: error: Phonon: No such file or directory
make: Leaving directory `/home/myhome/projects/sampleproj/sampleproj'
make: *** [main.o] Error 1
Exited with code 2.
Error while building project sampleproj
When executing build step 'Make'

what to do? thanks * cat on keyboard lol


Ask me questions if needed for more info.

---

### Post by januzi on 2009-11-14
Take a look at the /usr/include/qt4/. Is there "phonon" or "Phonon" ? And what's at the 8th line of the mainwindow.h ?

---

### Post by Joe Ker1086 on 2009-11-14
Quick phonon question....how do i access it from terminal? sorry to be a pest.

---

### Post by mickbuntu on 2009-11-23
> **januzi said:**
> Take a look at the /usr/include/qt4/. Is there "phonon" or "Phonon" ? And what's at the 8th line of the mainwindow.h ?


I got it resolved thank you, the problem was I needed to change the casing on phonon.

---

