---
title: "QT-programs won't compile"
date: 2009-06-23
forum: Packaging and Compiling Programs
---

### Post by rakydude on 2009-06-23
Hi all,

I'm having problems compiling QT-programs on my Kubuntu 9.04.
qt4-dev-tools are installed.

The test-file I'm trying to compile looks like this:
```
#include <QThread>
int main() { return 0; }
```

When trying to compile:
```
~$ gcc -o test test.cpp
test.cpp:1:19: error: QThread: No such file or directory
~$ g++ -o test test.cpp
test.cpp:1:19: error: QThread: No such file or directory
```

Same problem if I try to include any other QT-files.

However, the files does exist:
```
~$ find /usr/include | grep QThread
/usr/include/qt4/QtCore/QThreadStorage
/usr/include/qt4/QtCore/QThread
/usr/include/qt4/QtCore/QThreadStorageData
/usr/include/qt4/QtCore/QThreadPool
~$ find /usr/include | grep qthread
/usr/include/qt4/Qt/qthreadstorage.h
/usr/include/qt4/Qt/qthread.h
/usr/include/qt4/Qt/qthreadpool.h
/usr/include/qt4/QtCore/qthreadstorage.h
/usr/include/qt4/QtCore/qthread.h
/usr/include/qt4/QtCore/qthreadpool.h
```

Does anyone have a clue as of what might be wrong?

---

### Post by lloyd_b on 2009-06-24
> **rakydude said:**
> Hi all,

I'm having problems compiling QT-programs on my Kubuntu 9.04.
qt4-dev-tools are installed.

The test-file I'm trying to compile looks like this:
```
#include <QThread>
int main() { return 0; }
```

When trying to compile:
```
~$ gcc -o test test.cpp
test.cpp:1:19: error: QThread: No such file or directory
~$ g++ -o test test.cpp
test.cpp:1:19: error: QThread: No such file or directory
```

Same problem if I try to include any other QT-files.

However, the files does exist:
```
~$ find /usr/include | grep QThread
/usr/include/qt4/QtCore/QThreadStorage
/usr/include/qt4/QtCore/QThread
/usr/include/qt4/QtCore/QThreadStorageData
/usr/include/qt4/QtCore/QThreadPool
~$ find /usr/include | grep qthread
/usr/include/qt4/Qt/qthreadstorage.h
/usr/include/qt4/Qt/qthread.h
/usr/include/qt4/Qt/qthreadpool.h
/usr/include/qt4/QtCore/qthreadstorage.h
/usr/include/qt4/QtCore/qthread.h
/usr/include/qt4/QtCore/qthreadpool.h
```

Does anyone have a clue as of what might be wrong?

The problem is that you aren't telling it where to find the file.  You can solve this one of two ways:

1.  Change it to "#include <qt4/QtCore/QThread>".
2.  Add "-I/usr/include/qt4/QtCore" to the gcc command.

I'm not familiar with QT, but I suspect it should be a combination of the two.  For instance, "#include <QtCore/QThread>", with "-I/usr/include/qt4" supplied on the gcc command line.

Lloyd B.

---

### Post by jithin1987 on 2009-06-25
> **rakydude said:**
> Hi all,

I'm having problems compiling QT-programs on my Kubuntu 9.04.
qt4-dev-tools are installed.

The test-file I'm trying to compile looks like this:
```
#include <QThread>
int main() { return 0; }
```

When trying to compile:
```
~$ gcc -o test test.cpp
test.cpp:1:19: error: QThread: No such file or directory
~$ g++ -o test test.cpp
test.cpp:1:19: error: QThread: No such file or directory
```

Same problem if I try to include any other QT-files.

However, the files does exist:
```
~$ find /usr/include | grep QThread
/usr/include/qt4/QtCore/QThreadStorage
/usr/include/qt4/QtCore/QThread
/usr/include/qt4/QtCore/QThreadStorageData
/usr/include/qt4/QtCore/QThreadPool
~$ find /usr/include | grep qthread
/usr/include/qt4/Qt/qthreadstorage.h
/usr/include/qt4/Qt/qthread.h
/usr/include/qt4/Qt/qthreadpool.h
/usr/include/qt4/QtCore/qthreadstorage.h
/usr/include/qt4/QtCore/qthread.h
/usr/include/qt4/QtCore/qthreadpool.h
```

Does anyone have a clue as of what might be wrong?

First let qmake handle things for you.
create a pro file like this
cat test_app.pro
TEMPLATE = app
SOURCES += test_file.cpp

then run qmake on the same directory which will create make file for you.
then just run make.

---

