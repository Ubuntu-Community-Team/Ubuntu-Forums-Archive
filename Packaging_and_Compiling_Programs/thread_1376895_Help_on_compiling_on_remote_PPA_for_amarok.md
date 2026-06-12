---
title: "Help on compiling on remote PPA for amarok"
date: 2010-01-09
forum: Packaging and Compiling Programs
---

### Post by dentaku65 on 2010-01-09
Hi all,
I hope to find some help by someone here, to understand what goes wrong when I trying to compile a package on my PPA; I'm trying to create a repo with the version 1.4.10 of amarok with all necessary patches (cover, wikipedia, etc..), but the remote compiling on PPA goes to error ( [http://yep.it/25nukf](http://yep.it/25nukf) ); I think that the error resides in my debian/rules file (here attached), after about twenty retry I'm asking here some help, I'm not so experienced with the DEB operations and for sure I've write something silly in the debian/rules file... I've configured and compiled correctly from sources this amarok 1.4.10 version on my box which is run really fine, but I have a lot of trouble to create the deb version.
Thx.

---

### Post by SevenMachines on 2010-01-10
looking at your debian/control file you have 3 entries on one line, this means that you are only building one package with the problematic title of "amarok1410, amarok1410-common, amarok1410-engine-xine"!

Package: amarok1410, amarok1410-common, amarok1410-engine-xine

you need to separate these packages out into individual package entries 

At the moment your actually building one package and hence once build directory in debian/ called 'amarok1410, amarok1410-common, amarok1410-engine-xine' !! which is why the build fails since it cant find the directory amarok1410

---

### Post by dentaku65 on 2010-01-10
> **SevenMachines said:**
> looking at your debian/control file you have 3 entries on one line, this means that you are only building one package with the problematic title of "amarok1410, amarok1410-common, amarok1410-engine-xine"!

Package: amarok1410, amarok1410-common, amarok1410-engine-xine

you need to separate these packages out into individual package entries 

At the moment your actually building one package and hence once build directory in debian/ called 'amarok1410, amarok1410-common, amarok1410-engine-xine' !! which is why the build fails since it cant find the directory amarok1410

Thx SevenMachines!,
I'll trying to create one package amarok1410 with my debian/control file;
 but if I take a look on the of Bogdan PPA of amarok [https://launchpad.net/~bogdanb/+archive/ppa](https://launchpad.net/~bogdanb/+archive/ppa) I see all the packages together (view package details)... this confused me in the creation of the package.

---

### Post by SevenMachines on 2010-01-10
if you look at the actual packaging source of the bogdan ppa you mention though you'll see whats actually been used to generate the packages, compare your debian/control file to the one used there, although you might not want to do it the same way you can see what i meant by separate Package: entries for each actual package

debian/control:
```
Source: amarok
Section: kde
Priority: optional
Maintainer: Bogdan Butnaru <bogdanb@gmail.com>
XSBC-Original-Maintainer: Modestas Vainius <modestas@vainius.eu>
Uploaders: Ana Beatriz Guerrero Lopez <ana@debian.org>
Build-Depends: cdbs, debhelper (>= 5.0.0), quilt, bzip2, automake, libtool,
 kdelibs4-dev,
 libxine-dev, libdbus-qt-1-dev,
 libtag1-dev, libsqlite3-dev, libtunepimp-dev,
 libmysqlclient15-dev, libpq-dev,
 libvisual-0.4-dev, libsdl1.2-dev,
 libifp-dev, libusb-dev, libgpod-nogtk-dev (>= 0.4.2), libnjb-dev, libmtp-dev,
 ruby, ruby1.8-dev
Standards-Version: 3.8.0
XS-VCS-Bzr: http://bazaar.launchpad.net/~kubuntu-members/amarok/debian
XS-Original-Vcs-Svn: svn://svn.debian.org/svn/pkg-kde/kde-extras/amarok/trunk/
Homepage: http://amarok.kde.org

Package: amarok14
Architecture: any
Depends:  amarok14-common (>= ${source:Version}), amarok14-engine-xine (= ${binary:Version}), unzip, ${shlibs:Depends}
Suggests: amarok14-engines, moodbar, konqueror | www-browser,
 python, python-qt3, libqt0-ruby1.8, libvisual-0.4-plugins
Conflicts: amarok
Description: Amarok 1.4 series
 This is the last version of Amarok in the 1.4 series that was published
 in the Ubuntu repositories, before those switched to Amarok 2.*.
 .
 I made a few packaging tweaks, though:
   - all binary packages are suffixed with '14'; this way aptitude 
   doesn't attempt to upgrade them to the 2.* series
   - packages conflict with their non-suffixed versions; note that it's
   not normally possible to install Amarok from both 1.4 and 2.* series.
   (It's probably technically possible, but would need much work to make
   sure settings aren't lost.)
   - version incremented

Package: amarok14-common
Architecture: all
Depends: ruby
Recommends: amarok14 (>= ${source:Version})
Suggests: libqt0-ruby1.8, python, python-qt3
Conflicts: amarok14 (<= 2:1.4.9.1-0ubuntu3), amarok, amarok-common
Description: architecture independent files for Amarok
 This package contains architecture independent files needed for Amarok to run
 properly. It also provides Amarok documentation. Therefore, unless you have
 'amarok14' package installed, you will hardly find this package useful.
 .
 See 'amarok14' for more info

Package: amarok14-engine-xine
Architecture: any
Depends: ${shlibs:Depends}
Recommends: amarok14 (= ${binary:Version}), libxine1-ffmpeg
Conflicts: amarok-xine, amarok-engine-xine
Replaces: amarok-xine
Description: xine engine for Amarok 1.4 series
 This package provides the xine engine for Amarok 1.4.
 .
 BB: This is the only one I bothered to compile, and I suspect the others
 might not be working anymore.

```

---

### Post by dentaku65 on 2010-01-10
Hi SevenMachines,
seems that things really getting better; now the creation of the deb goes perfect, except for one thing: amarok1410-common; this deb has not been created, here my debian/control file:

> Source: amarok
Section: kde
Priority: optional
Maintainer: Dentaku65 <dentaku65@gmail.com>
XSBC-Original-Maintainer: Modestas Vainius <modestas@vainius.eu>
Uploaders: Ana Beatriz Guerrero Lopez <ana@debian.org>
Build-Depends: cdbs, debhelper (>= 5.0.0), bzip2, automake, libtool, kdelibs4-dev, libxine-dev, libdbus-qt-1-dev, libtag1-dev, libsqlite3-dev, libtunepimp-dev, libmysqlclient15-dev, libpq-dev, libvisual-0.4-dev, libsdl1.2-dev, libifp-dev, libusb-dev, libgpod-nogtk-dev (>= 0.4.2), libnjb-dev, libmtp-dev, ruby, ruby1.8-dev
Standards-Version: 3.8.3
XS-VCS-Bzr: [http://bazaar.launchpad.net/~kubuntu-members/amarok/debian](http://bazaar.launchpad.net/~kubuntu-members/amarok/debian)
XS-Original-Vcs-Svn: svn://svn.debian.org/svn/pkg-kde/kde-extras/amarok/trunk/
Homepage: [http://amarok.kde.org](http://amarok.kde.org)

Package: amarok1410
Architecture: any
Depends:  amarok1410-common (>= ${source:Version}), amarok1410-engine-xine (= ${binary:Version}), unzip, ${shlibs:Depends}
Suggests: amarok1410-engines, moodbar, konqueror | www-browser, python, python-qt3, libqt0-ruby1.8, libvisual-0.4-plugins
Conflicts: amarok
Description: Amarok 1.4 series with patches
 This is the last version of Amarok in the 1.4 series that is available
 in the KDE repositories, before those switched to Amarok 2.*.
 .
 I made a few packaging tweaks, though:
   - all binary packages are suffixed with '1410'; this way aptitude 
   doesn't attempt to upgrade them to the 2.* series
   - packages conflict with their non-suffixed versions; note that it's
   not normally possible to install Amarok from both 1.4 and 2.* series.
   (It's probably technically possible, but would need much work to make
   sure settings aren't lost.)
   - version incremented, covermanager fix (last.fm), MTP fix, Wikipedia fix and GCC44 fix

Package: amarok1410-common
Architecture: all
Depends: ruby
Recommends: amarok1410 (>= ${source:Version})
Suggests: libqt0-ruby1.8, python, python-qt3
Conflicts: amarok, amarok-common
Description: architecture independent files for Amarok
 This package contains architecture independent files needed for Amarok to run
 properly. It also provides Amarok documentation. Therefore, unless you have
 'amarok1410' package installed, you will hardly find this package useful.
 .
 See 'amarok1410' for more info

Package: amarok1410-engine-xine
Architecture: any
Depends: ${shlibs:Depends}
Recommends: amarok1410 (= ${binary:Version}), libxine1-ffmpeg
Conflicts: amarok-xine, amarok-engine-xine
Replaces: amarok-xine
Description: xine engine for Amarok 1.4 series
 This package provides the xine engine for Amarok 1.4.


---

### Post by dentaku65 on 2010-01-11
... never mind, I discovered the error in the debian/rules file :o

---

