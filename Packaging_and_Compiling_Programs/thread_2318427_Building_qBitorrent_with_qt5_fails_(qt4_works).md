---
title: "Building qBitorrent with qt5 fails (qt4 works)"
date: 2016-03-26
forum: Packaging and Compiling Programs
---

### Post by haraldnordgren on 2016-03-26
I want to build qBittorrent v3.4.0alpha with qt5, but I'm getting errors.

In this qBittorrent version qt5 is the default, but running [FONT=courier new]./configure --with-qt4 && make[/FONT] builds it using qt4, which is working fine. But I want qt5.

I have downloaded a bunch of qt5 packages, including [FONT=courier new]qtbase5-dev[/FONT] and [FONT=courier new]qttools5-dev-tools[/FONT] as suggested here ([https://github.com/qbittorrent/qBittorrent/wiki/Compiling-qBittorrent-on-Debian-and-Ubuntu](https://github.com/qbittorrent/qBittorrent/wiki/Compiling-qBittorrent-on-Debian-and-Ubuntu)). The configure script seems to be finding what it is looking for:

```
checking whether Qt4 should be enabled... no
checking for /usr/lib/x86_64-linux-gnu/qt5/bin/qmake... yes
checking for Qt5 qmake >= 5.2.0... /usr/lib/x86_64-linux-gnu/qt5/bin/qmake
checking whether QtDBus should be enabled... yes
checking for Qt5DBus >= 5.2.0... found
```

Still I am getting errors from the compilation process:

```
compiling base/utils/misc.cpp
base/utils/misc.cpp: In function ‘QString Utils::Misc::osName()’:
base/utils/misc.cpp:647:10: error: ‘prettyProductName’ is not a member of ‘QSysInfo’
     .arg(QSysInfo::prettyProductName())
          ^
base/utils/misc.cpp:648:10: error: ‘kernelVersion’ is not a member of ‘QSysInfo’
     .arg(QSysInfo::kernelVersion())
          ^
base/utils/misc.cpp:649:10: error: ‘currentCpuArchitecture’ is not a member of ‘QSysInfo’
     .arg(QSysInfo::currentCpuArchitecture());
          ^

```

Can anyone help me?

---

### Post by bernard-godard on 2016-03-28
According to [https://codereview.qt-project.org/#/c/88753/](https://codereview.qt-project.org/#/c/88753/)  [COLOR=#353535]**QSysInfo::currentCpuArchitecture()**[/COLOR]  was added in July 2014 so it cannot be in QT versions before version 5.3.2. If you are using 14.04, you have QT5.2. You might want to compile the latest version of QT.

---

