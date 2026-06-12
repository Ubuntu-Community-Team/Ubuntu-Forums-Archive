---
title: "Compiler very weird error while trying to use libnotify libs"
date: 2011-07-07
forum: Programming Talk
---

### Post by hakermania on 2011-07-07
Hello, I am using QtCreator as a compiler for C++ and I have the following problem:

Firstly, I made a Qt console application as a sample for something that I would like to include to my main application.
The sample's project file looks like:
```

TEMPLATE = app
TARGET = 
DEPENDPATH += .
INCLUDEPATH += .
[B]CONFIG += link_pkgconfig
PKGCONFIG += libnotify[/B]
SOURCES += update-notifications.cpp

```The highlighted part is the important one. This part actually links to the libnotify libraries.
So, my original code in the update-notifications.cpp file starts with:
```

#include <libnotify/notify.h>
..code
..more code etc.

```So, I simply link to the libnotify libraries and I use the library I need to use.
This sample runs very well!

The problem is that when I do these steps to my GUI main program, which was the initial purpose of making this sample, I get too many errors!
I mean, I link the libraries by editing the project file, I include the libnotify/notify.h library and even if I don't include any of the code I get errors like:
```

/usr/include/glib-2.0/gio/gdbusintrospection.h:151: error: expected unqualified-id before &#8216;protected&#8217;

```So, as you see, the error isn't about my code#-o
How weird can this be? The compiler finds errors at the libraries of libnotify while the sample code runs OK?
i tried recompiling the program via terminal in case qtcreator didn't remake the Makefile and didn't include the linked libraries but I get the same errors from there too.

It is the first time I get an error like this so I really need your help here....
[U]
So, in short words the problem is:
I make a sample and runs OK by linking the libraries and running the code.
In my main program I do exactly the same thing but the compiler finds errors about the libraries[/U]

The .pro files of both of the projects (because there is the key I think) are:

Sample project file:
```

TEMPLATE = app
TARGET = 
DEPENDPATH += .
INCLUDEPATH += .
CONFIG += link_pkgconfig
PKGCONFIG += libnotify
SOURCES += update-notifications.cpp

```Main Project file:
```

TEMPLATE = app
TARGET = 
DEPENDPATH += .
INCLUDEPATH += .
QT += dbus
LIBS += -lcv -lhighgui[B]
CONFIG += link_pkgconfig[/B]
**PKGCONFIG += libnotify**

# Input
HEADERS += about.h \
           extras.h \
           glob.h \
           history.h \
           mainwindow.h \
           MyCameraWindow.h \
           preferences.h \
           properties.h \
           QOpenCVWidget.h \
           screenshot.h \
           statistics.h
FORMS += about.ui \
         extras.ui \
         history.ui \
         mainwindow.ui \
         preferences.ui \
         properties.ui \
         screenshot.ui \
         statistics.ui
SOURCES += about.cpp \
           extras.cpp \
           history.cpp \
           main.cpp \
           mainwindow.cpp \
           MyCameraWindow.cpp \
           preferences.cpp \
           properties.cpp \
           QOpenCVWidget.cpp \
           screenshot.cpp \
           statistics.cpp
RESOURCES += icons.qrc

```Thanks in advance for any answers...

---

### Post by hakermania on 2011-07-08
&#921; think that this BUMP is unavoidable...  :(

---

### Post by hakermania on 2011-07-13
Ok, I found a solution! The library I included used the word 'signals' to name something, but this is not permitted because this word is used by Qt. The solution is to type:
```
#define QT_NO_KEYWORDS
```
before including anything in the file you have the inclusion of the file...
Then replace the following:
```

SLOT() -> Q_SLOT()
slots: -> Q_SLOTS:
SIGNAL() -> Q_SIGNAL()
signals: -> Q_SIGNALS:
emit -> Q_EMIT


```

---

