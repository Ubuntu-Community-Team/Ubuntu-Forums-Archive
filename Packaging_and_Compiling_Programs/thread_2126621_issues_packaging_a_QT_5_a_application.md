---
title: "issues packaging a QT 5 a application"
date: 2013-03-17
forum: Packaging and Compiling Programs
---

### Post by iztok.jeras on 2013-03-17
Hi,

I am trying to package a QT 5.0.1 based application, and I have trouble with build dependencies and setting up a working QT 5 default environment. It would help if there was en example package I could use as reference.

If I understand it correctly, QT 4 and 5 build environments can coexist, but only one can be the default. I tried to add qt5-default to build dependencies, but it is not enough. I get the next error:

qmake Kactus2_Solution.pro
qmake: could not open config file '/usr/share/qtchooser//default.conf': No such file or directory
make[1]: *** [override_dh_auto_configure] Error 1

For the full build log please look at:
[https://launchpadlibrarian.net/134406778/buildlog_ubuntu-raring-amd64.kactus2_2.1.194-1~ppa5~raring1_FAILEDTOBUILD.txt.gz](https://launchpadlibrarian.net/134406778/buildlog_ubuntu-raring-amd64.kactus2_2.1.194-1~ppa5~raring1_FAILEDTOBUILD.txt.gz)

I also have some other issues compiling locally, but they are further in the process, and I contacted Kactus2 developers regarding it.

Regards,
Iztok Jeras

---

