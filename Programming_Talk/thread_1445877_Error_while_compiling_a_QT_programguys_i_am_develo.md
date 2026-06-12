---
title: "Error while compiling a QT programguys i am developing GUI application using QT  i us"
date: 2010-04-03
forum: Programming Talk
---

### Post by manojboopathi on 2010-04-03
guys i am developing GUI application using QT

i used the following code:

#include <QApplication>
#include <QLabel>
int main(int argc, char *argv[])
{
QApplication app(argc, argv);
QLabel *label = new QLabel("Hello Qt!");
label->show();
return app.exec();
}

and then used the following commands in terminal for compilation

qmake -project
qmake hello.pro

these two worked successfully
when i entered third command "make" i got the following error:

make

g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o hello.o hello.cpp
hello.cpp:1:24: error: QApplication: No such file or directory
hello.cpp:2:18: error: QLabel: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:5: error: ‘QApplication’ was not declared in this scope
hello.cpp:5: error: expected `;' before ‘app’
hello.cpp:6: error: ‘QLabel’ was not declared in this scope
hello.cpp:6: error: ‘label’ was not declared in this scope
hello.cpp:6: error: expected type-specifier before ‘QLabel’
hello.cpp:6: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:3: warning: unused parameter ‘argc’
hello.cpp:3: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1

plz say me how to rectify this error....

waiting for reply....

---

### Post by the_unforgiven on 2010-04-03
> **manojboopathi said:**
> guys i am developing GUI application using QT

i used the following code:

#include <QApplication>
#include <QLabel>
int main(int argc, char *argv[])
{
QApplication app(argc, argv);
QLabel *label = new QLabel("Hello Qt!");
label->show();
return app.exec();
}

and then used the following commands in terminal for compilation

qmake -project
qmake hello.pro

these two worked successfully
when i entered third command "make" i got the following error:

make

g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o hello.o hello.cpp
hello.cpp:1:24: error: QApplication: No such file or directory
hello.cpp:2:18: error: QLabel: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:5: error: ‘QApplication’ was not declared in this scope
hello.cpp:5: error: expected `;' before ‘app’
hello.cpp:6: error: ‘QLabel’ was not declared in this scope
hello.cpp:6: error: ‘label’ was not declared in this scope
hello.cpp:6: error: expected type-specifier before ‘QLabel’
hello.cpp:6: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:3: warning: unused parameter ‘argc’
hello.cpp:3: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1

plz say me how to rectify this error....

waiting for reply....
The QT3 header files are all in lowercase and with '.h' suffix.
[http://doc.trolltech.com/3.3/qapplication.html](http://doc.trolltech.com/3.3/qapplication.html)
[http://doc.trolltech.com/3.3/qlabel.html](http://doc.trolltech.com/3.3/qlabel.html)

---

### Post by manojboopathi on 2010-04-03
hey i changed as u said. still its showing error only ya

this is the error:

g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o hello.o hello.cpp
hello.cpp:1:26: error: qapplication.h: No such file or directory
hello.cpp:2:20: error: qlabel.h: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:5: error: ‘QApplication’ was not declared in this scope
hello.cpp:5: error: expected `;' before ‘app’
hello.cpp:6: error: ‘QLabel’ was not declared in this scope
hello.cpp:6: error: ‘label’ was not declared in this scope
hello.cpp:6: error: expected type-specifier before ‘QLabel’
hello.cpp:6: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:3: warning: unused parameter ‘argc’
hello.cpp:3: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1

---

### Post by the_unforgiven on 2010-04-03
> **manojboopathi said:**
> hey i changed as u said. still its showing error only ya

this is the error:

g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o hello.o hello.cpp
hello.cpp:1:26: error: qapplication.h: No such file or directory
hello.cpp:2:20: error: qlabel.h: No such file or directory
hello.cpp: In function ‘int main(int, char**)’:
hello.cpp:5: error: ‘QApplication’ was not declared in this scope
hello.cpp:5: error: expected `;' before ‘app’
hello.cpp:6: error: ‘QLabel’ was not declared in this scope
hello.cpp:6: error: ‘label’ was not declared in this scope
hello.cpp:6: error: expected type-specifier before ‘QLabel’
hello.cpp:6: error: expected `;' before ‘QLabel’
hello.cpp:8: error: ‘app’ was not declared in this scope
hello.cpp: At global scope:
hello.cpp:3: warning: unused parameter ‘argc’
hello.cpp:3: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1
Are you sure about the path /usr/share/qt3/include? 
On my system (karmic), they're installed at /usr/include/qt3 ..

Ok, on more digging, /usr/share/qt3/include is a symlink to /usr/include/qt3 anyway..
Is that broken in your system?
Do you have libqt3-headers package installed?
Pkg details:
[http://packages.ubuntu.com/karmic/libqt3-headers](http://packages.ubuntu.com/karmic/libqt3-headers)

File list:
[http://packages.ubuntu.com/karmic/i386/libqt3-headers/filelist](http://packages.ubuntu.com/karmic/i386/libqt3-headers/filelist)

---

