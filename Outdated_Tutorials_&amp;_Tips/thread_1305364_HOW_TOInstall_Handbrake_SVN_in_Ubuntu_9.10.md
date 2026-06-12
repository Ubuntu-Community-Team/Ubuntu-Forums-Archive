---
title: "HOW TO:Install Handbrake SVN in Ubuntu 9.10"
date: 2009-10-29
forum: Outdated Tutorials &amp; Tips
---

### Post by fenian on 2009-10-29
As you may be aware the version of Handbrake that ships with 9.10 does not work.This is a guide for building the SVN (Subversion) Handbrake.

1-Downloadf all the dependencies,open a terminal and enter...

> sudo apt-get install subversion yasm build-essential autoconf libtool zlib1g-dev libbz2-dev intltool (gui) libglib2.0-dev libdbus-glib-1-dev libgtk2.0-dev libhal-dev libhal-storage-dev libwebkit-dev libnotify-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev checkinstall

2-Download the SVN source code,in the terminal enter...

> svn co svn://svn.handbrake.fr/HandBrake/trunk HandBrake-source

3-Move to the Handbrake-source directoy,in the terminal enter...

> cd ./HandBrake-source

4-Configure Handbrake (this will take a while),in the terminal enter...

> ./configure --launch

5-Move to the build directory,in the terminal enter...

> cd ./build

6-Make and install .deb package using checkinstall,in the terminal enter...

> sudo checkinstall

Because we used checkinstall rather than make install we can easily remove Handbrake in Synaptic Package Manager if we want to.

---

### Post by psikohunter on 2009-11-17
Been trying to install the SVN for a couple days. But no matter what I do it failes with this output. Any Ideas.

psiko@psikobuntu:~/HandBrake-source/build$ sudo checkinstall

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: n

*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@psikobuntu ]
1 -  Summary: [ Handbrake SVN V2904 ]
2 -  Name:    [ build ]
3 -  Version: [ 20091116 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ build ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ build ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make...Installing with install...

========================= Installation results ===========================
/bin/cp ./HandBrakeCLI /usr/local/bin/HandBrakeCLI
/bin/cp: cannot stat `./HandBrakeCLI': No such file or directory
make: *** [test.install] Error 1

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

---

### Post by JohnAStebbins on 2009-11-17
You can also follow fenian's instructions through step 3, then...
```

./configure --prefix=/usr
cd build
make
make pkg.create.deb

```

This creates deb packages that can be found in build/pkg when it's done.
The prefix is important since the deb rules file assumes /usr.

---

### Post by psikohunter on 2009-11-18
Awesome, That worked alot better for me.
Many Thanks.

---

### Post by Simi23 on 2010-05-07
Thanks, worked fine for Ubuntu 10.04 ;-)

---

### Post by forgewire on 2010-07-04
Worked well on Ubuntu 9.10 but needed libgudev-1.0-0

---

### Post by JohnAStebbins on 2010-07-04
There are nightly builds available now for karmic and lucid that can save you a lot of trouble building yourself.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by gspat on 2010-09-30
> **JohnAStebbins said:**
> There are nightly builds available now for karmic and lucid that can save you a lot of trouble building yourself.

[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

I added this, but "sudo apt-get install handbrake" fails with:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package handbrake is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package handbrake has no installation candidate

---

### Post by JohnAStebbins on 2010-10-01
You have to add the PPA to your software sources first.  The easy way would be
```

sudo add-apt-repository ppa:stebbins/handbrake-snapshots

```
then you can install
```

sudo apt-get update
sudo apt-get install handbrake-gtk

```

---

### Post by wrixis on 2011-05-30
Hi.
Do  you knwo where can I found the config folder? i looked for .handbreak under my user home and under .config folder.

The solution:
[https://forum.handbrake.fr/viewtopic.php?f=13&t=21200&p=97677#p97677](https://forum.handbrake.fr/viewtopic.php?f=13&t=21200&p=97677#p97677)

---

### Post by jacob2012 on 2011-06-01
Really good tutorial. I love this guide and this will help me alot, thankyou man! :)

---

