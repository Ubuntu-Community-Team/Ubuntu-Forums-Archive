---
title: "Qt headers not found!"
date: 2006-02-01
forum: Packaging and Compiling Programs
---

### Post by timmy666 on 2006-02-01
when i try to install programs and i use the ./configure, everything looks good until it gives back: 
Qt headers not found!.

so where can i get the Qt headers?

---

### Post by Lord Illidan on 2006-02-01
Have you done a search for qt headers in synaptic?
I guess not.

---

### Post by timmy666 on 2006-02-01
it din't work

---

### Post by Lord Illidan on 2006-02-01
What program are you trying to install?

---

### Post by timmy666 on 2006-02-01
dc-qt-0.1.2

but it happens with other programs to

---

### Post by Didjit on 2006-02-03
I'm having the same problem. I donwnloaded the QT3 dev kit. Changed my QTDIR to /usr/lib/qt3 and I still get: 

qdir.h: No such file or directory

On a Make. So, if you figure it out, plz share. 

Didjit

---

### Post by Hiew on 2006-04-12
*bump* 

**EDIT AT BOTTOM**

I'm using kde and trying to install kftpgrabber-0.7.0-beta1 

I've been getting a similar problem but the problem with me could be that i'm a noob to linux :p . I've never had any problems with ./configure until i reformatted my computer and installed ubuntu again.

If there's something i need to download, i have no clue what i would download and i tried downloading a few qt things in synaptic but they're most likely the wrong thing since it still doesn't work. ](*,) 

This is the error i get:
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!

***EDIT: i've installed qt lol :rolleyes: (stupid noob Hiew) and now i'm getting this error:
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

---

### Post by Mustard on 2006-04-12
I'm trying to follow the old adage of you can give a man fish and he will eat for a day, teach him to fish and he will eat every day. :)  So here goes...

Here is an example of how you might search for dependencies indicated by error messages at compilation.

```
mustard@slave:~$ apt-cache search libqt
libcppunit-dev - Unit Testing Library for C++
libguile-dev - Development headers and static library for libguile
libqt0-ruby1.8 - Qt bindings for Ruby
libqt3-i18n - i18n files for Qt3 library
libqt3-mt-dbg - debugging symbols for libqt3-mt
libqt3-mt-ibase - InterBase/FireBird database driver for Qt3 (Threaded)
libqt3-mt-mysql - MySQL database driver for Qt3 (Threaded)
libqt3-mt-odbc - ODBC database driver for Qt3 (Threaded)
libqt3-mt-psql - PostgreSQL database driver for Qt3 (Threaded)
libqt3-mt-sqlite - SQLite database driver for Qt3 (Threaded)
libqt4-core - Qt 4 core non-GUI functionality runtime library
libqt4-debug - Qt 4 debugging runtime libraries
libqt4-designer - Qt 4 Designer libraries
libqt4-dev - Qt 4 development files
libqt4-gui - Qt 4 core GUI functionality runtime library
libqt4-qt3support - Qt 3 compatibility library for Qt 4
libqt4-sql - Qt 4 SQL database module
libqttestrunner1c2 - Unit Testing Library for C++
qt3-assistant - The Qt3 assistant application
adept - package manager for KDE
libqt-perl - Perl bindings for the Qt library
libqt3-compat-headers - Qt 1.x and 2.x compatibility includes
libqt3-headers - Qt3 header files
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
libqt3-mt-dev - Qt development files (Threaded)
libqthreads-12 - QuickThreads library for Guile
```

With 20/20 hindsight I probably could have used the grep command which would have filtered the above list and produced a shorter list of candidates..

```
mustard@slave:~$ apt-cache search libqt | grep mt
libqt3-mt-dbg - debugging symbols for libqt3-mt
libqt3-mt-ibase - InterBase/FireBird database driver for Qt3 (Threaded)
libqt3-mt-mysql - MySQL database driver for Qt3 (Threaded)
libqt3-mt-odbc - ODBC database driver for Qt3 (Threaded)
libqt3-mt-psql - PostgreSQL database driver for Qt3 (Threaded)
libqt3-mt-sqlite - SQLite database driver for Qt3 (Threaded)
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
libqt3-mt-dev - Qt development files (Threaded)

```

This list a number of available packages that could indicate a possible choice.  In particular its looking for libqt-mt with a version number greater than 3.2, so that gives a hint that libqt3-mt might be the one you need.  So you look for the -dev package that might fill that dependency and then show the information on that package with the command below.


```
mustard@slave:~$ apt-cache show libqt3-mt-dev
Package: libqt3-mt-dev
Priority: optional
Section: libdevel
Installed-Size: 160
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: i386
Source: qt-x11-free
Version: 3:3.3.4-8ubuntu5
Replaces: libqt-mt-dev, libqt3-dev (>= 3.0.5-4), libqt3-helper, libqt3-headers (<= 3:3.1.1-3), libqt3-emb (<= 3:3.0.3-1)
Depends: xlibs-static-dev (>= 4.3.0.dfsg.1-4), libxext-dev (>= 4.3.0.dfsg.1-4), libxrandr-dev (>= 4.3.0.dfsg.1-4), x-dev (>= 4.3.0.dfsg.1-4), libsm-dev (>= 4.3.0.dfsg.1-4), libxmu-dev (>= 4.3.0.dfsg.1-4), libice-dev (>= 4.3.0.dfsg.1-4), libx11-dev (>= 4.3.0.dfsg.1-4), libxt-dev (>= 4.3.0.dfsg.1-4), libxrender-dev, libxcursor-dev, libxinerama-dev, libxi-dev, libmng-dev (>= 1.0.3), libpng12-0-dev, libjpeg62-dev, zlib1g-dev, libfreetype6-dev, libc6-dev, libqt3-mt (= 3:3.3.4-8ubuntu5), libqt3-headers (= 3:3.3.4-8ubuntu5), qt3-dev-tools (= 3:3.3.4-8ubuntu5), libgl1-mesa-dev | libgl-dev, libglu1-mesa-dev | libglu-dev, libxft-dev, libaudio-dev
Recommends: libqt3-compat-headers
Suggests: libqt3-i18n, qt3-doc
Conflicts: libqt-mt-dev, libqt3-emb (<= 3:3.0.3-1)
Filename: pool/main/q/qt-x11-free/libqt3-mt-dev_3.3.4-8ubuntu5_i386.deb
Size: 51054
MD5sum: 13546fed7b184e6cf7033429faa57e8b
Description: Qt development files (Threaded)
 Qt is a C++ class library optimized for graphical user interface
 development. This package contains the libqt-mt.so symlink, necessary
 for building threaded Qt applications as well as the libqui.so symlink
 and the necessary header files for libqui.so. (See README.Debian and
 the Qt Documentation for instructions on libqui.so)
 .
 WARNING: If you plan to build some older Qt3 applications, you will
 most probably have to install the libqt3-compat-headers package. It
 contains all the headers which are not part of the official Qt3 API
 anymore but which are still used by some programs. So if you encounter
 problems with missing header files, please install this package first
 before you send a bugreport.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
mustard@slave:~$


```

The above library seems to fall within the parameters for version numbers that your dependency error is showing.

Usually a liberal use of apt-cache search commands used in conjuction with the grep command as a filter can help to locate the correct package.

```
mustard@slave:~$ apt-cache search libqt | grep headers
libguile-dev - Development headers and static library for libguile
libqt3-compat-headers - Qt 1.x and 2.x compatibility includes
libqt3-headers - Qt3 header files

```

This search produces the headers package.

Of course if you do all this and come up with nothing, then it's quite possible that its not in the repositories for your version of Ubuntu.  Sometimes you might find them included in the development version.  Installing stuff outside of the repositories for your particular version of Ubuntu can be fraught with problems.  It's possible, but not always practical or wise to do so.

---

### Post by Hiew on 2006-04-12
hmm thanks for the info on how to use apt-cache search, it can be actually very usefull... i'll have to remember this one

However, how would i do this for something like the error i edited on my first post?

---

### Post by Mustard on 2006-04-12
[QUOTE=Hiew]hmm thanks for the info on how to use apt-cache search, it can be actually very usefull... i'll have to remember this one

However, how would i do this for something like the error i edited on my first post?[/QUOTE]

Did you read the last search in my example?

It contain a list of headers packages.

```
mustard@slave:~$ apt-cache search libqt | grep headers
libguile-dev - Development headers and static library for libguile
libqt3-compat-headers - Qt 1.x and 2.x compatibility includes
libqt3-headers - Qt3 header files
```

Have you installed, libqt3-headers and libqt3-compat-headers?

If you read the example of the apt-cache show command I used, you would see that the description of the file actually tells you what you need to install. :)

If you need the fish I can throw you the fish. :D

```
sudo apt-get install libqt3-headers libqt3-compat-headers
```

Then run ./configure again.

---

### Post by Hiew on 2006-04-12
Yeah i installed those, but it's giving me a different error now:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

lol i'm learning how to catch fish but slowly ;)

---

### Post by Mustard on 2006-04-12
[QUOTE=Hiew]Yeah i installed those, but it's giving me a different error now:

checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

lol i'm learning how to catch fish but slowly ;)[/QUOTE]

Hmmm..well this one is difficult.  I hadn't really thought about this before, but I notice you are installing a KDE application in a Gnome environment, which basically means its going to want to install a lot of KDE specific packages to work.  This 'configure:error' is due to it expecting you to be running KDE and again refers to some 'headers'.

/me thinks a lot

It took a bit of staring at the screen for a while for me to figure this one out (as well as some googling for the specifics about wha this application you are compiling does).  I thought we might have hit a dead-end for a second, but I've worked it out.

```
mustard@slave:~$ apt-cache search qt | grep kde
fireflier-client-kde - Interactive firewall rule creation tool - QT client
ggz-kde-game-data - GGZ Gaming Zone:  KDE based game front-end data
ggz-kde-games - GGZ Gaming Zone:  KDE based game front-ends
kde-devel - the K Desktop Environment development files and modules
kdesdk-kfile-plugins - KDE file dialog plugins for software development files
kdesdk-misc - various goodies from the KDE Software Development Kit
kdesdk-scripts - a set of useful development scripts for KDE
kdevelop3 - An IDE for Unix/X11 - development version
kdevelop3-data - An IDE for Unix/X11 - data
kdevelop3-dev - An IDE for Unix/X11 - development files
kdevelop3-doc - An IDE for Unix/X11 - documentation
kdevelop3-plugins - An IDE for Unix/X11 - development files
libsmokekde-dev - SMOKE Binding Library to KDE - Development Files
licq-plugin-kde - graphical user interface plug-in for Licq using Qt and KDE
openoffice.org-kde - KDE UI Plugin and KDE File Picker for OpenOffice.org
openoffice.org2-kde - KDE Integration for OpenOffice.org (Widgets, Dialogs, Addressbook)
ebook-dev-kde20 - [EBOOK-DEV] KDE 2.0 Development
```

```

mustard@slave:~$ apt-cache show kde-devel
Package: kde-devel
Priority: extra
Section: universe/kde
Installed-Size: 40
Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
Architecture: all
Source: meta-kde
Version: 5:44ubuntu2
Depends: kde-core, kdesdk, libartsc0-dev, libarts1-dev, kdelibs4-dev, kdebase-dev, libkonq4-dev, qt3-designer
Suggests: kde-i18n
Filename: pool/universe/m/meta-kde/kde-devel_44ubuntu2_all.deb
Size: 7500
MD5sum: a6e5b250e03210d3d0ad524df4b9acab
Description: the K Desktop Environment development files and modules
 KDE (the K Desktop Environment) is a powerful Open Source graphical
 desktop environment for Unix workstations. It combines ease of use,
 contemporary functionality, and outstanding graphical design with the
 technological superiority of the Unix operating system.
 .
 This metapackage includes official KDE modules that are useful to developers,
 including KDE's software development kit (SDK), Qt3's designer tool, and all
 core KDE header and development packages.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

mustard@slave:~$

```

---

### Post by Hiew on 2006-04-12
I actually have KDE installed o.O i installed it through the kubuntu packages in synaptic and i can run it without problem, and well now...one problem after another! make doesn't work, even though ./configure is perfect and even tells me it's good to use make. Where would i look for errors on make T_T 

I really appreciate all the help you're giving me! This has been something thats been bothering me for a while... anyways if there is anything you would like in return just pm me and i'll see what i can do.

**EDIT*** these are the last few lines of make:

```

/usr/bin/ld: cannot find -ldbus-1
collect2: ld returned 1 exit status
make[4]: *** [kftpgrabber] Error 1
make[4]: Leaving directory `/home/hiew/downloads/kftpgrabber-0.7.0-beta1/kftpgrabber-0.7.0-beta1/kftpgrabber/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/hiew/downloads/kftpgrabber-0.7.0-beta1/kftpgrabber-0.7.0-beta1/kftpgrabber/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/hiew/downloads/kftpgrabber-0.7.0-beta1/kftpgrabber-0.7.0-beta1/kftpgrabber'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hiew/downloads/kftpgrabber-0.7.0-beta1/kftpgrabber-0.7.0-beta1'
make: *** [all] Error 2

```

---

### Post by Mustard on 2006-04-12
[QUOTE=Hiew]I actually have KDE installed o.O i installed it through the kubuntu packages in synaptic and i can run it without problem, and well now...one problem after another! make doesn't work, even though ./configure is perfect and even tells me it's good to use make. Where would i look for errors on make T_T 

I really appreciate all the help you're giving me! This has been something thats been bothering me for a while... anyways if there is anything you would like in return just pm me and i'll see what i can do.[/QUOTE]

Ah ok, well if you have KDE installed, it was just a case of having to download the develoment files (which is pretty standard when compiling from source).  As for the 'make' problem, I would have preferred to see the specific error message but if I was to guess at the problem it would be that build-essential is not installed.

```
sudo apt-get install build-essential
```

If it's already installed, then the specific error messages you received when trying to make, is the clue to what the problem is.

-edit-

Ok, you posted the error messages while I was typing... I have to say I'm a bit stumped at this stage. :)  I'll keep looking but I'm not sure about the specifics of this error.

---

### Post by Hiew on 2006-04-12
It's greatly appreciated and yeah its really confusing me quite a bit...since i've used ./configure | make | sudo make install before easily without incident... and make sure you do this as a passtime and not regard it as a job hehe ;)

---

### Post by Mustard on 2006-04-12
[QUOTE=Hiew]It's greatly appreciated and yeah its really confusing me quite a bit...since i've used ./configure | make | sudo make install before easily without incident... and make sure you do this as a passtime and not regard it as a job hehe ;)[/QUOTE]

Hehe..yeah. I try to treat it as an opportunity for me to learn something myself. :)

Ok, well I've been googling for answers, but I'm coming up with a lot of dead ends.  So I've got some questions on your choice of versions to install.  

Is there any reason you have chosen to install the latest unstable version?
Would the stable version be better?
Would it not be easier to install a debian package version of this application rather than compiling from source?

This last error has me bamboozled, so if it was me I would be backtracking to see if I could find another solution, rather than trying to install the latest unstable version.  The error gets into area of compiling from source that is beyond my knowledge unfortunately. :)

We could leave it and wait for someone else to come along, or we could change tack and try something else. It's up to you.

---

### Post by Hiew on 2006-04-12
Well no there isn't any reason why i'm using the latest unstable version...and in hindsight it would be smarter to find a stable version however i couldn't find any .dep or even rpm packages for this particular program. i'm going to take a closer look and see what i can come up with.

The main reason i was concerned about this problem was due the the fact i really miss smartftp for windows and the transition to something similar to gftp has made it very uncomfortable since i've notices gftp tends to not like transferring large amounts of files at once or files contained inside folders. I am however getting this same problem for all the packages i've tried to compile by source. *looks for different kftpgrabber packages*

---

### Post by Mustard on 2006-04-12
[QUOTE=Hiew]Well no there isn't any reason why i'm using the latest unstable version...and in hindsight it would be smarter to find a stable version however i couldn't find any .dep or even rpm packages for this particular program. i'm going to take a closer look and see what i can come up with.

The main reason i was concerned about this problem was due the the fact i really miss smartftp for windows and the transition to something similar to gftp has made it very uncomfortable since i've notices gftp tends to not like transferring large amounts of files at once or files contained inside folders. I am however getting this same problem for all the packages i've tried to compile by source. *looks for different kftpgrabber packages*[/QUOTE]

I've been looking through the download pages and there are easier options, depending on how far back in the version you want to go...

[http://kftpgrabber.sourceforge.net/downloads.php](http://kftpgrabber.sourceforge.net/downloads.php)

They use the word 'obsolete' next to each earlier version, but I notice the only version they don't call obsolete is the latest unstable version.  I would assume that the versions that have debian packages for them would be easier to install, or at least compiling those versions from source would be easier.

I'd also recommend that when you come to the 'make install' part of compiling from source that you use the checkinstall command (you need to install this from the repositories first).  Checkinstall is a great little utility that makes a .deb package out of the compiled source and then installs it as a deb package.  The advantages of this are many, but primarily it makes it VERY easy to uninstall, which is one of the greatest inconveniences of compiling from source on a debian system.  The ability to go to Synaptic and just choose to uninstall the application and have it all work automatically is a priceless feature. :)

I'd be tempted to try these versions, preferably the older version..

> Release 0.6.0-beta1 [OBSOLETE]

    * Source: [BZ2]
    * Debian (unstable + KDE 3.4): [DEB] 


Release 0.5.0 [OBSOLETE]

    * Source: [BZ2]
    * Debian (sid): [DEB]
    * Arch Linux: [LINK] 

---

### Post by Hiew on 2006-04-12
hmm checkinstall does semm pretty advantageous since i know first hand how annoying uninstalling compiled programs can be if i don't remember where all the files went lol

---

### Post by Hiew on 2006-04-12
gah! ](*,)  i've downloaded the .deb version, which needed dependencies 
```

Depends: kdelibs4 (>= 4:3.4.0) but it is not installable
               Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable

```
So it told me what the dependencies were however there is no such package that seems to satisfy this dependency, i also have all the server lines uncommented in my sources.list file for respositories too.
This is what i also tried:
```

hiew@vijbot:~/downloads$ apt-cache search kdelibs
kde - The K Desktop Environment
kdelibs3-bin - the K Desktop Environment - transitional package
openoffice.org-mimelnk - OpenOffice.org MIME bindings for KDE
kdelibs - core libraries from the official KDE release
kdelibs4c2 - core libraries for all KDE applications
kdelibs4c2-dbg - debugging symbols for kdelibs4c2
kdelibs4-dev - development files for the KDE core libraries
kdelibs4-doc - developer documentation for the KDE core libraries
kdelibs-bin - core binaries for all KDE applications
kdelibs-data - core shared data for all KDE applications

```

or with smaller results:

```

hiew@vijbot:~$ apt-cache search kdelibs4
kdelibs4c2 - core libraries for all KDE applications
kdelibs4c2-dbg - debugging symbols for kdelibs4c2
kdelibs4-dev - development files for the KDE core libraries
kdelibs4-doc - developer documentation for the KDE core libraries

```

i have installed:
kdelibs
kdelibs4c2
kdelibs4-dev
kdelibs4-bin
kdelibs4-data

gah so confusing why it would be doing this....

I've also noticed that when i search up kde in synaptic it shows kde as not installed, i'm trying that again since last time i tried it said it needed to remove several different kde packages while now it's only saying it will remove kubuntu-desktop and akode while installing several different kde programs..

---

### Post by Mustard on 2006-04-12
[QUOTE=Hiew]gah! ](*,)  i've downloaded the .deb version, which needed dependencies 
```

Depends: kdelibs4 (>= 4:3.4.0) but it is not installable
               Depends: libqt3c102-mt (>= 3:3.3.4) but it is not installable

```
So it told me what the dependencies were however there is no such package that seems to satisfy this dependency, i also have all the server lines uncommented in my sources.list file for respositories too.
This is what i also tried:
```

hiew@vijbot:~/downloads$ apt-cache search kdelibs
kde - The K Desktop Environment
kdelibs3-bin - the K Desktop Environment - transitional package
openoffice.org-mimelnk - OpenOffice.org MIME bindings for KDE
kdelibs - core libraries from the official KDE release
kdelibs4c2 - core libraries for all KDE applications
kdelibs4c2-dbg - debugging symbols for kdelibs4c2
kdelibs4-dev - development files for the KDE core libraries
kdelibs4-doc - developer documentation for the KDE core libraries
kdelibs-bin - core binaries for all KDE applications
kdelibs-data - core shared data for all KDE applications

```

or with smaller results:

```

hiew@vijbot:~$ apt-cache search kdelibs4
kdelibs4c2 - core libraries for all KDE applications
kdelibs4c2-dbg - debugging symbols for kdelibs4c2
kdelibs4-dev - development files for the KDE core libraries
kdelibs4-doc - developer documentation for the KDE core libraries

```

i have installed:
kdelibs
kdelibs4c2
kdelibs4-dev
kdelibs4-bin
kdelibs4-data

gah so confusing why it would be doing this....

I've also noticed that when i search up kde in synaptic it shows kde as not installed, i'm trying that again since last time i tried it said it needed to remove several different kde packages while now it's only saying it will remove kubuntu-desktop and akode while installing several different kde programs..[/QUOTE]

What version of KDE are you currently running?  It could be that its either trying to downgrade you to an older version or upgrade you to a newer version. :)

With a debian package too, when it has dependency issues you can often use this command to fix them..

```
sudo apt-get -f install
```

You would want to read what changes it wants to make though, as it sounds like this package you are installing wants to radically change your setup. :)  I'd be wary that it doesn't bust your system in some way.  Certainly wanting to uninstall kubuntu-desktop seems to indicate that there is something major going on in terms of the changes it wants to make.

At this stage its probably worth mentioning another good tool with Ubuntu.  'Aptitude' is a pretty cool package manager that can remember all the packages that were installed and can make reversing the installlation of a large number of packages a lot simpler than if you used Adept/Synaptic/Apt-get.

---

### Post by Hiew on 2006-04-13
my KDE is 3.51 i think it's the newest one supported by ubuntu... anyways i also did the change but nothing happened except it made a lot more programs work as well as more screensavers etc..lol

Linux is like a learning experience for me, i'm trying to learn how to completely get all my windows programs over on windows and leave it solely for gaming, since sadly i dont think Oblivion is going to be ported to linux anytime soon :(

---

### Post by bakert on 2006-06-30
I got these exact same errors trying to install k9copy.

The instructions here fixed all problems for me:

```
https://help.ubuntu.com/community/BuildingK9CopyfromSource
```

Which makes me think that what you need to do is install these:

```
sudo apt-get install libdvdread3-dev kdebase-dev kdelibs4-dev libqt3-mt-dev qt3-dev-tools libqt3-headers libjpeg62-dev build-essential checkinstall
```

---

### Post by thilly on 2006-09-05
Hi when i try to configure the plugins..
i get this:
checking for ANSI C header files... (cached) yes
checking errno.h usability... yes
checking errno.h presence... yes
checking for errno.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking for sys_errlist and sys_nerr... yes
checking for licq header files... "/home/menne/licq-1.3.2/include"
checking for X... no
configure: error: You need to have the X11 libraries and headers installed
make: *** No targets specified and no makefile found.  Stop.
menne@menne-desktop:~/licq-1.3.2/plugins/qt-gui$  

but i cannot find the good package to install!
What do i forget?
thanks thilly

---

### Post by Chris Jones on 2006-09-20
I had a similar problem trying to compile Lyx with a QT frontend. I knew all the needed libraries were installed but they seemed to be all over the place. I spent about three hours trying to figure out how I could put them in one place (symlinks and the like) and adding prefixes to the ./configure command before searching for more information to read.

I found the answer to what seemed non-compliance with LSB, or rather the place the source expected to find them, in the following documentation.

(I used the command zless to read the file)

/usr/share/doc/libqt3-mt-dev/README.Debian.gz 

I have cut and pasted what I found to be the relevant bit of information.....

2. General Overview

As Qt is a huge package that contains a complete environment for
developers, it needs to be split up into several packages that make it
easier for everyone else to handle it and not to require
unnecessary disk space for end-users. Additionally, Qt can be configured
in several ways - and therefore also used in several ways. Qt development
usually requires the environment variable QTDIR. As Debian is placing
libraries and header files in a quite specific filesystem order, this
usually breaks setting a single environment variable to meet the
requirements of packages. Therefore, symlinks are used to set up the system
to meet both, the Debian filesystem standard and the QTDIR variable. All of
Qt (so the QTDIR path) is available in /usr/share/qt3. If you need to set
QTDIR, do export QTDIR=/usr/share/qt3

So, having read this....
On a command line I did the suggested export and this then allowed me to add: --with-prefix=/usr/share/qt3 to the configuration options (see ./configure --help, for options) and Lyx with a qt frontend compiled without any complaint. 

I also installed the g77 fortran compiler on top of the development tools suggested by the Ubuntu meta package.

---

### Post by l4lucas on 2006-10-09
Hmm, I installed that, and my install is still giving me the same message.

---

### Post by Maxorata on 2006-10-13
After you've installed the development package for QT you must install the Development package for KDE, without it you won't be able to comile any application. After you've installed this package you will presented with a bunch of more applications that also need to be installed, so you should accept the installation of them also.
Hope this helps.

---

### Post by giomir1599 on 2006-10-14
Hello Guys,
I've the same problem with QT Headers, the message is always the same,for each program I try to install.
"checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021) and < 4.0) (library qt-mt) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!"
I've done evrything mentioned in this forum,but with no luck.
I'm atotal newbie.
Please help me!!!!!

Regards

Giorgio

---

### Post by wyldwayne on 2007-01-10
All, after reading through this post and having simular errors I found that if you add the kubuntu repos this will clear your problem up.

The problem that I was having was trying to install the entire Koffice Suite under Gnome.
You can spend the time and cache all needed dependicies or you can simply let apt-get do its job by using repos. I find the latter alot less nerve wrecking.

Here is a something that i found to be really helpful for ubuntu users.

Edgy:
> [http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/lista-repository-sourceslist-ottimizzata-per-ubuntu-kubuntu-linux/)

Dapper:
> [http://3v1n0.tuxfamily.org/blog/informatica/linux/lista-repository-sourceslist-per-ubuntu-kubuntu-dapper-archivio/](http://3v1n0.tuxfamily.org/blog/informatica/linux/lista-repository-sourceslist-per-ubuntu-kubuntu-dapper-archivio/)

Saved me alot of time and headache

---

### Post by Felipe Butcher on 2007-05-01
long time trying, That works for me:

sudo apt-get install libqt3-mt-dev

i found solution in there

[http://ubuntuforums.org/showthread.php?t=386945&highlight=checking+for+Qt...+configure%3A+error%3A+Qt+%28%26gt%3B%3D+Qt+3.3+%26lt%3B+4.0%29+%28library+qt-mt%29+-found.+Please+check+your+installation%21](http://ubuntuforums.org/showthread.php?t=386945&highlight=checking+for+Qt...+configure%3A+error%3A+Qt+%28%26gt%3B%3D+Qt+3.3+%26lt%3B+4.0%29+%28library+qt-mt%29+-found.+Please+check+your+installation%21)

---

### Post by dempl_dempl on 2007-05-14
Ok, I have problems with compiling Basic KDE App with KDevelop.
when I run ./configure I get the output :


---------------------------------------------------------------------------------------------------------------------------
   checking for Qt... 
  configure: error: Qt (>= Qt 3.2 and < 4.0) (library qt-mt) not found. Please check your   installation!
For more details about this problem, look at the end of config.log.
Make sure that you have compiled Qt with thread support!
*** Exited with status: 1 ***
--------------------------------------------------------------------------------------------------------------------------

Ok, I'm not stupid I've installed Qt , both versions 3 and 4 using "apt-get install".

I've searched the forum but I couldn't find anything directly concerning this problem.

Now , when I type the following:

$apt-cache search libqt  | grep mt

I get theese results:
----------------------------------------------------------------------------------------------------------------
libqt3-mt - Qt GUI Library (Threaded runtime version), Version 3
libqt3-mt-dev - Qt development files (Threaded)
libqt3-mt-mysql - MySQL database driver for Qt3 (Threaded)
libqt3-mt-odbc - ODBC database driver for Qt3 (Threaded)
libqt3-mt-psql - PostgreSQL database driver for Qt3 (Threaded)
libqt3-mt-sqlite - SQLite database driver for Qt3 (Threaded)
----------------------------------------------------------------------------------------------------------------

$apt-cache search libqt  | grep qt4 

I get theese:

----------------------------------------------------------------------------------------------------------------
libqt4-core - Qt 4 core non-GUI functionality runtime library
libqt4-debug - Qt 4 library debugging symbols
libqt4-dev - Qt 4 development files
libqt4-gui - Qt 4 core GUI functionality runtime library
libqt4-qt3support - Qt 3 compatibility library for Qt 4
libqt4-sql - Qt 4 SQL database module
libqt0-ruby1.8-qt4 - Qt4 bindings for Ruby
libqt4-core-kdecopy - Qt 4 core non-GUI functionality runtime library
libqt4-debug-dev-kdecopy - Qt 4 debugging development files
libqt4-debug-kdecopy - Qt 4 debugging runtime libraries
libqt4-dev-kdecopy - Qt 4 development files
libqt4-gui-kdecopy - Qt 4 core GUI functionality runtime library
libqt4-qt3support-kdecopy - Qt 3 compatibility library for Qt 4
libqt4-ruby - ruby bindings for the Qt4 GUI library
libqt4-ruby1.8 - ruby bindings for the Qt4 GUI library
libqt4-sql-kdecopy - Qt 4 SQL database module
----------------------------------------------------------------------------------------------------------------


Is there something missing or wrong here?
Should I simply try to install Anjuta?:) 

BTW,   I use Kubuntu feisty, and compiling terminal c++ apps works.
Kdevelop is 3.4.0.

---

### Post by Kavar on 2007-06-03
Hey I found in other forums this wonderful solution (assuming you do have all the QT elements installed and you are still receiving the error)  
export CC=/usr/bin/gcc-4.1    (use whatever gcc version you have)
export CXX=/usr/bin/g++-4.1  (again, use whatever g++ you have)
export CPP=/usr/bin/cpp-4.1 (and finally for those with no learning curve... use whatever cpp you have)

now you are ready to ./configure :)

---

### Post by uzaenuri on 2007-07-06
:(
 I have already try to use your suggest with reinstall libqt3-headers libqt3-compat-headers, but until now I still get same error like this :

" configure: error: Qt (>= Qt 3.0.3) (headers and libraries) not found. Please check your installation!"

I want to use KsqlAnalyzer to connecting MS SQL Database

Anyone can help me ..? :D

Thx

---

### Post by CaTTiusha on 2007-07-08
I had that error when installing new k3b 1.0.2

```
"Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found"
```

but the libavahi-qt3-dev  fixed the problem. I'm pretty green in this so I'm not sure if it help you. :)

---

### Post by zaak on 2009-01-04
libqt3-headers solves the "Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found." problem. However, the "KDE... configure: error" keeps coming.

---

### Post by zaak on 2009-01-04
And use this method to solve the KDE header problem.
[http://ubuntuforums.org/showthread.php?p=4177745]("http://ubuntuforums.org/showthread.php?p=4177745")

---

### Post by Tikhon03 on 2010-09-10
Hi I have tried all of the suggestions on this thread.  I am trying to install Knights (a KDE based 3D-chess GUI) I am getting the following error
```
checking for Qt... configure: error: Qt (>= Qt 3.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.
```I suppose I could post the contents of config.log, but I found them fairly unilluminating.  I have just about every qt4-dev file installed.  Should I be trying the qt3-dev files instead?  By the way.  I have tried finding .deb packages for this program, found at least one, but had no success at getting it to install.

---

