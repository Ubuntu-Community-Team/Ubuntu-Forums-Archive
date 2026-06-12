---
title: "QT3 - Tutorial Issues"
date: 2007-11-14
forum: Programming Talk
---

### Post by iharrold on 2007-11-14
I'm relatively new to Linux programming and looking at using QT for creation of GUI's.  So I am following the QT tutorial located [here.]("http://doc.trolltech.com/4.0/tutorial-t1.html")

I get the following errors:
> iharrold@iharrold-Ubuntubox:~/QTTest$ make all
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:30:28: error: QApplication: No such file or directory
main.cpp:31:27: error: QPushButton: No such file or directory
main.cpp: In function ‘int main(int, char**)’:
main.cpp:35: error: ‘QApplication’ was not declared in this scope
main.cpp:35: error: expected `;' before ‘app’
main.cpp:37: error: ‘QPushButton’ was not declared in this scope
main.cpp:37: error: expected `;' before ‘hello’
main.cpp:38: error: ‘hello’ was not declared in this scope
main.cpp:41: error: ‘app’ was not declared in this scope
main.cpp: At global scope:
main.cpp:33: warning: unused parameter ‘argc’
main.cpp:33: warning: unused parameter ‘argv’
make: *** [main.o] Error 1


So I verified the QT3 includes are indeed at /usr/share/qt3/includes.  This still doesn't allow me to find the QApplication or QPushButton.  I forced the location with #include </usr/share/qt3/include/QApplication> and #include </usr/share/qt3/include/QPushButton>

> iharrold@iharrold-Ubuntubox:~/QTTest$ make all
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I/usr/include/qt3 -o main.o main.cpp
main.cpp:30:51: error: /usr/share/qt3/include/QApplication: No such file or directory
main.cpp:31:50: error: /usr/share/qt3/include/QPushButton: No such file or directory
main.cpp: In function ‘int main(int, char**)’:
main.cpp:35: error: ‘QApplication’ was not declared in this scope
main.cpp:35: error: expected `;' before ‘app’
main.cpp:37: error: ‘QPushButton’ was not declared in this scope
main.cpp:37: error: expected `;' before ‘hello’
main.cpp:38: error: ‘hello’ was not declared in this scope
main.cpp:41: error: ‘app’ was not declared in this scope
main.cpp: At global scope:
main.cpp:33: warning: unused parameter ‘argc’
main.cpp:33: warning: unused parameter ‘argv’
make: *** [main.o] Error 1

I get the following errors:


I am rather perplexed why the simple application in the very first tutorial won't compile.  What am I missing here?

---

### Post by wolfbone on 2007-11-14
Maybe you should be reading the QT3 tutorial not the QT4 tutorial :)

---

### Post by iharrold on 2007-11-14
> Maybe you should be reading the QT3 tutorial not the QT4 tutorial 

hah.. no it cannot be that simple ;)  I'll try tomorrow and set the includes to point to Qt4.

Anyone else have other suggestions?

Edit:  Oh looking at my second output, the line 30:51 and 30:50 shouldn't be displaying "no such file".  I copied the wrong output.

---

### Post by kvs on 2009-05-27
wolfbone is right. i was having the same problem. i was using qt3, but following the qt4 tutorial. in the tutorial, they include <QApplication> and  [FONT=monospace][/FONT]<QPushButton> files. i looked up in qt3 include folder, and instead they have files qapplication.h and qpushbutton.h . i tried including those, but still it gives me one error with the QPushButton hello("hello world ") part. i dont know, im still looking it up, but i think you should definitely change the header files.

---

