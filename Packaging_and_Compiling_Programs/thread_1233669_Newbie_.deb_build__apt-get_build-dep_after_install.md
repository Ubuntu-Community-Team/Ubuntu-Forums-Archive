---
title: "Newbie .deb build : apt-get build-dep after install + more"
date: 2009-08-06
forum: Packaging and Compiling Programs
---

### Post by zackiv31 on 2009-08-06
So I'm just getting into this package building myself for ubuntu as I've needed the latest and greatest of some packages out there... So here's my question, maybe followed by some others...

1. I downloaded a Source Package... is there an easy way to build a deb from it (minimal/easy instructions?)  I've seen checkinstall but it doesn't "require" other packages, so moving the deb to another machine doesn't require any of the necessary packages.

2. The file I want to install is in the repo's... but its not the latest... I learned of this apt-get build-dep function that can tell what you need to run the package... Is there a similar function I can run *after* the package has been installed (or an older version is installed)?

Short Version:

Just trying to build .deb files from a straight tarball of the source... want it to require all necessary files, and be able to be moved to another machine and install. (This should work for tarballs that are old and in the repo's, or not in there at all)

---

### Post by s3a on 2009-08-11
[http://ubuntuforums.org/showthread.php?t=1237600](http://ubuntuforums.org/showthread.php?t=1237600)

I am asking a similar question but maybe my usual procedure is the answer you seek. You could also get the source from a repository of a later version of Ubuntu than that you're using and not need to do dh_make --createorig or if you use an upstream source, you would have to do that. build-dep packagename only works if there is an older version in the repositories. If there is no older version, you will need to obtain the dependencies manually via apt-get by checking a readme file or something. By the way, Checkinstall is a terrible way to make .debs.

---

### Post by zackiv31 on 2009-08-13
This is a start s3a... But I dont know what I'm doing wrong...

```

me@me:~/Desktop/libtorrent-rasterbar-0.14.4$ dh_make --createorig

Type of package: single binary, multiple binary, library, kernel module, kernel patch or cdbs?
 [s/m/l/k/n/b] s

Maintainer name : me me
Email-Address   : me@unknown 
Date            : Thu, 13 Aug 2009 00:53:37 -0400
Package Name    : libtorrent-rasterbar
Version         : 0.14.4
License         : blank
Using dpatch    : no
Using quilt     : no
Type of Package : Single
Hit <enter> to confirm: 
Done. Please edit the files in the debian/ subdirectory now. libtorrent-rasterbar
uses a configure script, so you probably don't have to edit the Makefiles.

me@me:~/Desktop/libtorrent-rasterbar-0.14.4$ sudo apt-get build-dep libtorrent-rasterbar
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

me@me:~/Desktop/libtorrent-rasterbar-0.14.4$ dpkg-buildpackage 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package libtorrent-rasterbar
dpkg-buildpackage: source version 0.14.4-1
dpkg-buildpackage: source changed by me me <me@me>
dpkg-buildpackage: host architecture amd64
dpkg-checkbuilddeps: Unmet build dependencies: autotools-dev
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)

```

Any guidance?



EDIT:

```

sudo apt-get install autotools-dev

```

---

### Post by s3a on 2009-08-13
It seems build-dep did not find any dependencies. Are you sure that's the correct name for the package in the repositories?

Edit: According to this link ([http://packages.ubuntu.com/search?keywords=libtorrent-rasterbar&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=libtorrent-rasterbar&searchon=names&suite=jaunty&section=all)), you need to do *sudo apt-get build-dep _libtorrent-rasterbar2_*.

---

### Post by zackiv31 on 2009-08-20
No I have already installed all the build-dep packages (because I've installed libtorrent manually)...

I.E.... I have it installed on my box already, but I want to build a package on it so I can move it to another comp and install it there (without having to do a ./configure make make install again)

---

