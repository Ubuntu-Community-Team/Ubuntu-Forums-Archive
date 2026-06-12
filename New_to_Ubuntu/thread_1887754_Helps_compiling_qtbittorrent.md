---
title: "Helps compiling qtbittorrent"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by BlueFontBold on 2011-11-27
Hi, I'm trying to compile qbittorrent but have been unsuccessful with it.....
I installed build essentials and what I think are the proper qt libaries.

**This is what I get from the terminal-----**


Configuring qbittorrent ...
Verifying Qt 4 build environment ... fail

Reason: There was an error compiling 'conf'.  See conf.log for details.

Be sure you have a proper Qt 4.0 build environment set up.  This means not
just Qt, but also a C++ compiler, a make tool, and any other packages
necessary for compiling C++ programs.

If you are certain everything is installed, then it could be that Qt 4 is not
being recognized or that a different version of Qt is being detected by
mistake (for example, this could happen if $QTDIR is pointing to a Qt 3
installation).  At least one of the following conditions must be satisfied:

 1) --qtdir is set to the location of Qt
 2) $QTDIR is set to the location of Qt
 3) QtCore is in the pkg-config database
 4) qmake is in the $PATH

This script will use the first one it finds to be true, checked in the above
order.  #3 and #4 are the recommended options.  #1 and #2 are mainly for
overriding the system configuration.

And from the config file--- 


/usr/bin/moc-qt4 -DHAVE_MODULES -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. conf4.cpp -o conf4.moc
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DHAVE_MODULES -DQT_NO_DEBUG -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4 -I. -o conf4.o conf4.cpp
In file included from conf4.cpp:703:
libboost.qcm:8: fatal error: boost/version.hpp: No such file or directory
compilation terminated.
make: *** [conf4.o] Error 1

**Thank you in advance for any help you give me :)**

---

### Post by beew on 2011-11-27
I am not really experienced in this, but maybe you should install some libboost -dev files if they are not installed already and compile again.

---

### Post by dniMretsaM on 2011-11-27
Why do you need to compile? There are  PPA's for both the [stable]("https://launchpad.net/%7Ehydr0g3n/+archive/ppa") and [dev]("https://launchpad.net/%7Ehydr0g3n/+archive/qbittorrent-unstable") releases.

---

### Post by BlueFontBold on 2011-11-27
> **beew said:**
> I am not really experienced in this, but maybe you should install some libboost -dev files if they are not installed already and compile again.

I don't know which libboost dev files to install...when I search it on ubuntu software center there is a whole bunch to install...

Which ones do you think I should install?

---

### Post by BlueFontBold on 2011-11-27
> **dniMretsaM said:**
> Why do you need to compile? There are  PPA's for both the [stable]("https://launchpad.net/%7Ehydr0g3n/+archive/ppa") and [dev]("https://launchpad.net/%7Ehydr0g3n/+archive/qbittorrent-unstable") releases.

I think it would be really helpful for me if I learn how to compile programs....even though its kind of complicated....

---

### Post by beew on 2011-11-27
> **BlueFontBold said:**
> I don't know which libboost dev files to install...when I search it on ubuntu software center there is a whole bunch to install...

Which ones do you think I should install?

How about just libboost-dev?  Like I said I am not really experienced but from your output it appears that some libboost dev file is missing.

P.S. If you have to search often for dependencies use synaptic instead of the Software Center, it is slow and bloated, not very convenient. If you run 11.10 you need to install it yourself
```
sudo apt-get install synaptic
```

---

### Post by oldos2er on 2011-11-27
Dependencies are listed in the INSTALL file: ```
1) Compile and install qBittorrent with Qt4 Graphical Interface

  $ ./configure
  $ make && make install
  $ qbittorrent

  will install and execute qBittorrent hopefully without any problems.

  Dependencies:
    - Qt >= 4.5.0 (libqtgui, libqtcore, libqtnetwork, libqtxml, libqtdbus/optional)

    - pkg-config executable

    - libtorrent-rasterbar by Arvid Norberg (>= 0.14.4 REQUIRED, compatible with v0.15.x)
        -> http://www.libtorrent.net
        Be careful: another library (the one used by rTorrent) uses a similar name.

    - libboost 1.34.x (libboost-filesystem, libboost-date-time) + libasio
      or
    - libboost >= 1.35.x (libboost-system, libboost-filesystem, libboost-date-time)

    - python >= 2.3 && < 3.0 (needed by search engine)
        * Run time only dependency

    - geoip-database (optional)
        * If qBittorrent cannot find this database, it will try to resolve countries using the Internet but it will be a lot slower.
        * Run time only dependency

2) Compile and install qBittorrent without Qt4 Graphical interface

  $ ./configure --disable-gui
  $ make && make install
  $ qbittorrent

  will install and execute qBittorrent hopefully without any problems.

  Dependencies:
    - Qt >= 4.4.0 (libqt-devel, libqtcore, libqtnetwork)

    - pkg-config executable

    - libtorrent-rasterbar by Arvid Norberg (>= 0.14.4 REQUIRED, >= v0.15.0 ADVISED)
        -> http://www.libtorrent.net
        Be careful: another library (the one used by rTorrent) uses a similar name.

    - libboost: libboost-filesystem, libboost-date-time, libboost-thread, libboost-serialization


DOCUMENTATION:
Please note that there is a documentation with a "compiling howto" at http://wiki.qbittorrent.org.

------------------------------------------
Christophe Dumez <chris@qbittorrent.org>
```

---

### Post by andrew.46 on 2011-11-27
I am not terribly keen on this approach but a quick way of gathering the build dependencies would be::

```
sudo apt-get build-dep qbittorrent
```

I have not tested this while building qbittorrent though...

---

### Post by m0re0n on 2012-03-09
> **andrew.46 said:**
> I am not terribly keen on this approach but a quick way of gathering the build dependencies would be::

```
sudo apt-get build-dep qbittorrent
```

I have not tested this while building qbittorrent though...

Thank you thank you THANK you :)
been looking all over google for dependencies to compile this!
:popcorn:

---

