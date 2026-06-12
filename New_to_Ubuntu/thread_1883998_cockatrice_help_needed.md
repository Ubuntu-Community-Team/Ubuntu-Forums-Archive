---
title: "cockatrice help needed"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-11-20
ok so I have put cockatrice on my desk top and it has done completely fine. I am putting it on my lap top and not but a few codes in I ran in to some problems. here is what i have so far.

joshua@joshua-laptop:~$ cd Downloads/cockatrice*
joshua@joshua-laptop:~/Downloads/cockatrice-20111113$ sudo apt-get install libqt4-dev
[sudo] password for joshua: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fakeroot (1.14.4-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fakeroot (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot
E: Sub-process /usr/bin/dpkg returned an error code (1)
joshua@joshua-laptop:~/Downloads/cockatrice-20111113$ cd cockatrice
joshua@joshua-laptop:~/Downloads/cockatrice-20111113/cockatrice$ lrelease translations/*.ts && qmake && make
Updating 'translations/cockatrice_cs.qm'...
    Generated 639 translation(s) (504 finished and 135 unfinished)

    Ignored 93 untranslated source text(s)
Updating 'translations/cockatrice_de.qm'...
    Generated 722 translation(s) (721 finished and 1 unfinished)

    Ignored 10 untranslated source text(s)
Updating 'translations/cockatrice_en.qm'...
    Generated 7 translation(s) (1 finished and 6 unfinished)

    Ignored 725 untranslated source text(s)
Updating 'translations/cockatrice_es.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_fr.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_it.qm'...
    Generated 721 translation(s) (720 finished and 1 unfinished)

    Ignored 11 untranslated source text(s)
Updating 'translations/cockatrice_ja.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_pl.qm'...
    Generated 0 translation(s) (0 finished and 0 unfinished)

    Ignored 732 untranslated source text(s)
Updating 'translations/cockatrice_pt-br.qm'...
    Generated 629 translation(s) (487 finished and 142 unfinished)

    Ignored 103 untranslated source text(s)
Updating 'translations/cockatrice_pt.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_ru.qm'...
    Generated 720 translation(s) (719 finished and 1 unfinished)

    Ignored 12 untranslated source text(s)
Updating 'translations/cockatrice_sk.qm'...
    Generated 0 translation(s) (0 finished and 0 unfinished)

    Ignored 732 untranslated source text(s)
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_SCRIPT_LIB -DQT_SVG_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtSvg -I/usr/include/qt4/QtScript -I/usr/include/qt4 -I. -Isrc -I../common -Ibuild -o build/zoneviewwidget.o src/zoneviewwidget.cpp
src/zoneviewwidget.cpp: In constructor ‘ZoneViewWidget::ZoneViewWidget(Player*, CardZone*, int, bool, const QList<ServerInfo_Card*>&)’:
src/zoneviewwidget.cpp:63: error: ‘setAutoFillBackground’ was not declared in this scope
make: *** [build/zoneviewwidget.o] Error 1

so can anybody make any since of this?

---

