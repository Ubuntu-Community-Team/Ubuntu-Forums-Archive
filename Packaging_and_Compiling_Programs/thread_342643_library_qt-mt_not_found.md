---
title: "library qt-mt not found"
date: 2007-01-20
forum: Packaging and Compiling Programs
---

### Post by YourFriendlyGopher on 2007-01-20
Hi all,

I've been having this problem when running ./configure on all qt based programs. All of them complain about library qt-mt not being found:

```

checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

```

Where the error occurs in config.log:

```

configure:31904: checking for perl
configure:31964: result: /usr/bin/perl
configure:32100: checking for Qt
configure: 32165: /usr/share/qt3/include/qstyle.h
taking that
tried NO
configure:32282: rm -rf SunWS_cache; g++ -o conftest -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -L/usr/lib -L/usr/lib -Wl,--as-needed   conftest.cpp  -lqt-mt -lpng -lz -lm -ljpeg -ldl  -lXext -lX11 -lSM -lICE  -lpthread 1>&5
In file included from conftest.cpp:2:
/usr/share/qt3/include/qglobal.h:773:21: error: qconfig.h: No such file or directory
/usr/share/qt3/include/qglobal.h:783:22: error: qmodules.h: No such file or directory
configure:32285: $? = 1
configure: failed program was:
#include "confdefs.h"
#include <qglobal.h>
#include <qapplication.h>
#include <qcursor.h>
#include <qstylefactory.h>
#include <private/qucomextra_p.h>
#if ! (QT_VERSION >= 0x030100)
#error 1
#endif

int main() {
    (void)QStyleFactory::create(QString::null);
    QCursor c(Qt::WhatsThisCursor);
    return 0;
}
configure:32325: error: Qt (>= Qt 3.1 (20021021)) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

```

I've been trying to figure this out for ages, it's been a REAL pain. I've tried setting the environment variables QTDIR (/usr/share/qt3), QTLIB (/usr/lib) and QMAKESPEC (/usr/share/qt3/mkspecs/linux-g++). Also I've tried configuring by:

./configure --with-qt-dir=/usr/share/qt3 --with-qt-includes=/usr/include/qt3 --with-qt-libraries=/usr/lib/

But still nothing works.. so, if anyone has any ideas it'd be appreciated, thanks.

---

### Post by rhb on 2007-01-20
I am having other problems with qt, but I checked my system to verify that those headers work on it.  I do have them:

/usr/include/qt3/qconfig.h

Then I used apt-cache search to find likely candidate packages that you might be missing.  My conclusion is that the most likely one is libqt3-headers, but I suggest you make sure you have qt3-dev-tools also.

apt-cache show <package> will give you some information about the package.  To install, you can use:

apt-get install <package>

Generally, when you build from source there will be one or more -dev packages that are needed to provide headers and/or libraries.

---

### Post by hod139 on 2007-01-20
Have you installed the libqt3-mt-dev package?

---

### Post by YourFriendlyGopher on 2007-01-21
I have all the packages you suggested rhb, however I don't think I have the header file qconfig.h for some reason. Also running apt-get for the package libqt3-mt-dev gives:

```

$ sudo apt-get install libqt3-mt-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libqt3-mt-dev: Depends: libgl1-mesa-dev but it is not going to be installed or
                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Broken packages

```

And trying to get the package libgl1-mesa-dev gives:

```

The following packages have unmet dependencies:
  libgl1-mesa-dev: Depends: mesa-common-dev (= 6.5.1~20060817-0ubuntu3) but 6.5.1+cvs20060824 is to be installed
E: Broken packages

```

Any ideas?

---

### Post by hod139 on 2007-01-21
Have you put any unofficial sources in your /etc/apt/sources.list file?  In any case, you can try aptitude instead of apt, which is smarter and may automagically downgrade certain packages to allow the install of qt.

```

sudo aptitude install libqt3-mt-dev

```

---

### Post by YourFriendlyGopher on 2007-01-22
Using aptitude worked! I didn't think there was much of a difference between them.  Thanks for the help!

---

