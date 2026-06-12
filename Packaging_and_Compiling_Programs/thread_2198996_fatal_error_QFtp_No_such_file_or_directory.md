---
title: "fatal error: QFtp: No such file or directory"
date: 2014-01-11
forum: Packaging and Compiling Programs
---

### Post by cdb10 on 2014-01-11
My system is:
```

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise

```
My code is:
```

cat main.cpp 
#include <QCoreApplication>
#include <QDebug>
#include <QFtp>
 
class Ftp : public QFtp
{
        Q_OBJECT
 
public:
        Ftp(QObject* parent = 0)
        {
                connect(this, SIGNAL(listInfo(QUrlInfo)), this, SLOT(doListInfo(QUrlInfo)));
                connect(this, SIGNAL(done(bool)), QCoreApplication::instance(), SLOT(quit()));
        }
 
protected slots:
        void doListInfo(const QUrlInfo& info)
        {
                qDebug() << info.name();
        }
};
 
int main(int argc, char* argv[])
{
        QCoreApplication app(argc, argv);
 
        Ftp ftp;
        ftp.connectToHost("ftp.trolltech.com");
        ftp.login();
        ftp.list();
        ftp.close();
 
        return app.exec();
}
 

```
During compilation error occurs.
```

$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
main.cpp:3:16: fatal error: QFtp: No such file or directory
compilation terminated.
make: *** [main.o] Error 1

```

---

### Post by steeldriver on 2014-01-11
Have you tried adding -I/usr/include/qt4/QtNetwork? That's where the QFtp header seems to be located on my system. Alternatively you could change #include <QFtp> to #include <QtNetwork/QFtp>

---

### Post by cdb10 on 2014-01-12
> **steeldriver said:**
> Have you tried adding -I/usr/include/qt4/QtNetwork? That's where the QFtp header seems to be located on my system. Alternatively you could change #include <QFtp> to #include <QtNetwork/QFtp>
I use "make" to build. How would I be able to use  -I/usr/include/qt4/QtNetwork?
I changed the "<QFtp>" to "<QtNetwork/QFtp>".
Compiler displays:
```

$ make
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
main.cpp:11:2: warning: unused parameter ‘parent’ [-Wunused-parameter]
g++ -Wl,-O1 -o qtftp main.o    -L/usr/lib/i386-linux-gnu -lQtGui -lQtCore -lpthread 
main.o: In function `main':
main.cpp:(.text.startup+0x3e): undefined reference to `QFtp::QFtp(QObject*)'
main.cpp:(.text.startup+0x46): undefined reference to `vtable for Ftp'
main.cpp:(.text.startup+0xc3): undefined reference to `QFtp::connectToHost(QString const&, unsigned short)'
main.cpp:(.text.startup+0x107): undefined reference to `QFtp::login(QString const&, QString const&)'
main.cpp:(.text.startup+0x139): undefined reference to `QFtp::list(QString const&)'
main.cpp:(.text.startup+0x149): undefined reference to `QFtp::close()'
main.cpp:(.text.startup+0x158): undefined reference to `vtable for Ftp'
main.cpp:(.text.startup+0x160): undefined reference to `QFtp::~QFtp()'
main.cpp:(.text.startup+0x1a0): undefined reference to `vtable for Ftp'
main.cpp:(.text.startup+0x1a8): undefined reference to `QFtp::~QFtp()'
main.cpp:(.text.startup+0x1e6): undefined reference to `QFtp::~QFtp()'
collect2: ld returned 1 exit status
make: *** [qtftp] Error 1



```

---

### Post by steeldriver on 2014-01-12
You will need to add the corresponding **-lQtNetwork** to the list of libs - easiest way would be to edit the Makefile and add both that and the -I/usr/include/qt4/QtNetwork include directive

---

### Post by cdb10 on 2014-01-12
I redrafted file "Makefile":
```

CC            = gcc
CXX           = g++
DEFINES       = -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED
CFLAGS        = -pipe -O2 -Wall -W -D_REENTRANT $(DEFINES)
CXXFLAGS      = -pipe -O2 -Wall -W -D_REENTRANT $(DEFINES)
INCPATH       = -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I/usr/include/qt4/QtNetwork
LINK          = g++
LFLAGS        = -Wl,-O1
LIBS          = $(SUBLIBS)  -L/usr/lib/i386-linux-gnu -lQtGui -lQtCore -lpthread -lQtNetwork  
AR            = ar cqs
RANLIB        = 
QMAKE         = /usr/bin/qmake
TAR           = tar -cf
COMPRESS      = gzip -9f
COPY          = cp -f
SED           = sed
COPY_FILE     = $(COPY)
COPY_DIR      = $(COPY) -r

```
[COLOR=#000000]During compilation error occurs:
[/COLOR]```

$ make
g++ -Wl,-O1 -o qtftp main.o    -L/usr/lib/i386-linux-gnu -lQtGui -lQtCore -lpthread -lQtNetwork  
main.o: In function `main':
main.cpp:(.text.startup+0x46): undefined reference to `vtable for Ftp'
main.cpp:(.text.startup+0x158): undefined reference to `vtable for Ftp'
main.cpp:(.text.startup+0x1a0): undefined reference to `vtable for Ftp'
collect2: ld returned 1 exit status
make: *** [qtftp] Error 1
 
```[COLOR=#000000]
[/COLOR]

---

### Post by steeldriver on 2014-01-12
The order in which you specify libraries matters - I don't know for sure, but I'd guess you want

```

-lQtNetwork -lQtGui -lQtCore -lpthread 

```

You basically need to go from highest 'level' to lowest i.e. assuming libQtNetwork uses objects from libQtCore it needs to go to the left of it

---

