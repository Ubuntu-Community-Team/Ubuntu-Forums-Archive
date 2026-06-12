---
title: "compiling a simple program with qt"
date: 2006-01-17
forum: Programming Talk
---

### Post by fakie_flip on 2006-01-17
I followed the directions at [http://doc.trolltech.com/4.1/tutorial-t1.html](http://doc.trolltech.com/4.1/tutorial-t1.html) to try to compile the example there called main.cpp. I have libqt3-mt. I just installed libqt2-mt-dev and all of the dependencies it needs. I do not know why I am getting these errors. What should I do?

chris@ubuntu:~/qt$ qmake -project
chris@ubuntu:~/qt$ qmake
chris@ubuntu:~/qt$ make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/share/qt3/include -o main.o main.cpp
main.cpp:1:28: error: QApplication: No such file or directory
main.cpp:2:27: error: QPushButton: No such file or directory
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:6: error: &#8216;QApplication&#8217; was not declared in this scope
main.cpp:6: error: expected `;' before &#8216;app&#8217;
main.cpp:8: error: &#8216;QPushButton&#8217; was not declared in this scope
main.cpp:8: error: expected `;' before &#8216;hello&#8217;
main.cpp:9: error: &#8216;hello&#8217; was not declared in this scope
main.cpp:12: error: &#8216;app&#8217; was not declared in this scope
main.cpp: At global scope:
main.cpp:4: warning: unused parameter &#8216;argc&#8217;
main.cpp:4: warning: unused parameter &#8216;argv&#8217;
make: *** [main.o] Error 1
chris@ubuntu:~/qt$ ls
main.cpp Makefile qt.pro
chris@ubuntu:~/qt$

---

### Post by Neeko on 2006-01-18
Are you using QT 4 or QT 3? From the compiler message it looks like QT 3. The QT 4.1 tutorial wont work in QT 3.x

If QT 3.x you need to change the code a little:
```


#include <qapplication.h>
#include <qlabel.h>
int main(int argc, char *argv[])
{
QApplication myapp(argc, argv);
QLabel *mylabel = new QLabel("Hello World", 0);
mylabel->resize(120, 30);
myapp.setMainWidget(mylabel);
mylabel->show();
return myapp.exec();
}

```
If you have QT 4.1 installed, it's likely your paths aren't set up right, as QT cant find the headers it needs.

---

### Post by zir0n on 2008-03-27
I guess your trying to learn how to use QT also. I just ran into the same problem trying to follow the tutorial off the documentation at [http://doc.trolltech.com/4.2/tutorial-t1.html](http://doc.trolltech.com/4.2/tutorial-t1.html)

The problem was that i was using qmake which is a symlink to the qmake-qt3 bin when the tutorial is for qt4. To fix this you need to have the qt4-dev-tools installed and either point the symlink to qmake-qt4 or just call it instead. For example to compile the first tutorial go into the directory of the main.cpp and type:

```

qmake-qt4 -project
qmake-qt4
make

```

it should give you "basic_example" which you can just run.
:guitar:

---

