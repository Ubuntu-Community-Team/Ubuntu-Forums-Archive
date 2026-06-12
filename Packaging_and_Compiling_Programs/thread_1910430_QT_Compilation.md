---
title: "QT Compilation"
date: 2012-01-17
forum: Packaging and Compiling Programs
---

### Post by oslbhavana on 2012-01-17
I am using ubuntu10.10 
i hav installed qt-sdk through synaptic package manager
whan i try to compile a basic helloworld program i am getting error like
oslbh@ubuntu:~$ qmake-qt4 -project
^C
oslbh@ubuntu:~$ qmake-qt4
oslbh@ubuntu:~$ make
Makefile:6511: warning: overriding commands for target `output.o'
Makefile:2354: warning: ignoring old commands for target `output.o'
Makefile:6799: warning: overriding commands for target `utils.o'
Makefile:3218: warning: ignoring old commands for target `utils.o'
Makefile:6950: warning: overriding commands for target `winfix.o'
Makefile:5094: warning: ignoring old commands for target `winfix.o'
Makefile:7712: warning: overriding commands for target `snprintf.o'
Makefile:5209: warning: ignoring old commands for target `snprintf.o'
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -IDownloads/nmap/nbase -IDownloads/nmap -IDownloads/nmap/mswin32 -IDownloads/nmap/libpcap -IDownloads/nmap/libpcap/pcap -IDownloads/nmap/mswin32/pcap-include -IDownloads/nmap/nsock/include -IDownloads/nmap/libnetutil -IDownloads/nmap/libdnet-stripped/include -IDownloads/nmap/libdnet-stripped/include/dnet -IDownloads/nmap/liblua -IDownloads/nmap/liblinear -IDownloads/nmap/libpcre -IDownloads/nmap/ncat -IDownloads/nmap/nping -IDownloads/nmap/libdnet-stripped/src -IDownloads/nmap/liblinear/blas -IDownloads/nmap/nsock/src -I. -o hello.o hello/hello.cpp
hello/hello.cpp: In function ‘int main(int, char**)’:
hello/hello.cpp:5:2: error: ‘QApllication’ was not declared in this scope
hello/hello.cpp:5:15: error: expected ‘;’ before ‘app’
hello/hello.cpp:6:22: error: expected type-specifier before ‘Qlabel’
hello/hello.cpp:6:22: error: cannot convert ‘int*’ to ‘QLabel*’ in initialization
hello/hello.cpp:6:22: error: expected ‘,’ or ‘;’ before ‘Qlabel’
hello/hello.cpp:7:13: error: statement cannot resolve address of overloaded function
hello/hello.cpp:8:9: error: ‘app’ was not declared in this scope
hello/hello.cpp: At global scope:
hello/hello.cpp:3:5: warning: unused parameter ‘argc’
hello/hello.cpp:3:5: warning: unused parameter ‘argv’
make: *** [hello.o] Error 1


Do i need to install any additional package
I am unable to understand what could be the problem

plz help

---

### Post by oldos2er on 2012-01-17
Moved to Packaging and Compiling Programs.

---

### Post by gmargo on 2012-01-17
> **oslbhavana said:**
> 
hello/hello.cpp:5:2: error: ‘QApllication’ was not declared in this scope
hello/hello.cpp:5:15: error: expected ‘;’ before ‘app’
hello/hello.cpp:6:22: error: expected type-specifier before ‘Qlabel’
hello/hello.cpp:6:22: error: cannot convert ‘int*’ to ‘QLabel*’ in initialization
hello/hello.cpp:6:22: error: expected ‘,’ or ‘;’ before ‘Qlabel’
hello/hello.cpp:7:13: error: statement cannot resolve address of overloaded function
hello/hello.cpp:8:9: error: ‘app’ was not declared in this scope


Pay attention to the error messages.  At the very least, "QApplication" is misspelled. You are probably missing some semi-colons.  You should be able to find the other problems.  If not, then post your code.

Here's a "Hello World" that should work fine.
It is from [http://doc.trolltech.com/4.3/tutorial-t1.html](http://doc.trolltech.com/4.3/tutorial-t1.html)
```

#include <QApplication>
#include <QPushButton>

int main(int argc, char *argv[])
{
    QApplication app(argc, argv);

    QPushButton hello("Hello world!");
    hello.resize(100, 30);

    hello.show();
    return app.exec();
}

```

---

