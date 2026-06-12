---
title: "Installing PyQt4 for Python3.1"
date: 2010-03-12
forum: Packaging and Compiling Programs
---

### Post by eranga1988 on 2010-03-12
Hello guyz I tried to install PyQt4 after installing SIP-4.10.
When running configure.py in the PyQt4 folder I got the following ERROR message.
```

senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ python3.1 configure.py
Error: Make sure you have a working Qt v4 qmake on your PATH or use the -q
argument to explicitly specify a working Qt v4 qmake.
senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ 

```

Please help me to solve this!!!

---

### Post by eranga1988 on 2010-03-12
Updated

I installed qt4-qmake. Then after I run the configure.py I got the following Error.

```
senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ python3.1 configure.py
Determining the layout of your Qt installation...
Error: Failed to determine the layout of your Qt installation. Try again using
the --verbose flag to see more detail about the problem.
```

Please help me to solve this....

---

### Post by eranga1988 on 2010-03-12
Pls help me!!!

---

### Post by eranga1988 on 2010-03-12
Here which I got with --verbose flag

> senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ python3.1 configure.py --verbose flag
Determining the layout of your Qt installation...
/usr/bin/qmake -o qtdirs.mk qtdirs.pro
make -f qtdirs.mk
Error: Failed to determine the layout of your Qt installation. Try again using
the --verbose flag to see more detail about the problem.
b'g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_CORE_LIB -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. -o qtdirs.o qtdirs.cpp\n'b'qtdirs.cpp:1:17: error: QFile: No such file or directory\n'b'qtdirs.cpp:2:24: error: QLibraryInfo: No such file or directory\n'b'qtdirs.cpp:3:23: error: QTextStream: No such file or directory\n'b'qtdirs.cpp: In function \xe2\x80\x98int main(int, char**)\xe2\x80\x99:\n'b'qtdirs.cpp:7: error: \xe2\x80\x98QFile\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:7: error: expected \xe2\x80\x98;\xe2\x80\x99 before \xe2\x80\x98outf\xe2\x80\x99\n'b'qtdirs.cpp:9: error: \xe2\x80\x98outf\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:9: error: \xe2\x80\x98QIODevice\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:9: error: \xe2\x80\x98QIODevice\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:9: error: \xe2\x80\x98QIODevice\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:12: error: \xe2\x80\x98QTextStream\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:12: error: expected \xe2\x80\x98;\xe2\x80\x99 before \xe2\x80\x98out\xe2\x80\x99\n'b'qtdirs.cpp:14: error: \xe2\x80\x98out\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:14: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:14: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:15: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:15: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:16: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:16: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:17: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:17: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:18: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:18: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:19: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:19: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:21: error: \xe2\x80\x98QT_VERSION\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:22: error: \xe2\x80\x98QT_EDITION\xe2\x80\x99 was not declared in this scope\n'b'qtdirs.cpp:24: error: \xe2\x80\x98QLibraryInfo\xe2\x80\x99 has not been declared\n'b'qtdirs.cpp:86: error: \xe2\x80\x98qreal\xe2\x80\x99 was not declared in this scope\n'b'make: *** [qtdirs.o] Error 1\n'senzeh@senzeh-laptop:~/Python/PyQt-x11-gpl-4.7$ 


---

### Post by SevenMachines on 2010-03-13
are you sure you have the qt4 development files installed?

$sudo apt-get install libqt4-dev

---

### Post by CoBrA2168 on 2010-04-10
> **SevenMachines said:**
> are you sure you have the qt4 development files installed?

$sudo apt-get install libqt4-dev

Thank you thank you thank you thank you!!!  I've run into the same problems as the member above, and have been stumped for the last two hours.  I ran into this link on google, put that command in, and BAM it worked.  

For those wondering how exactly I installed PyQt4 on my Ubuntu 9.10 machine, this is how I did it:

I had to download both SIP and PyQt4 from the official website. I then had to install qmake, python-qt4, gcc-c++ (for the g++ command), and the libqt4-dev.

I then was able to manually install SIP and PyQt4 for Python 3.1 using the following commands for each:

python3.1 configure.py
make
sudo make install

Works like a charm now! Thanks.

---

### Post by Thomas Oliveira on 2010-07-07
I needed also to install python3.1-dev before 'making' SIP.

---

### Post by shameeram on 2010-08-31
Hello,

locate qmake

then use it after configure.py for eg :

python configure.py -q /usr/lib/qt4/bin/qmake

Good luck. :)

---

