---
title: "Pupynere fails to build"
date: 2014-02-21
forum: Packaging and Compiling Programs
---

### Post by epikvision on 2014-02-21
I'm trying to package a Python module called Pupynere. 

After uploading to my ppa [1], It failed to build on amd64 [2] and i386 [3]. The last two links are build log files.  I suppose the error occurred because of...
[LIST]
[*]**no public key available. **I used my private key, but must I use my public key as well? If so, how is this done? 
[*]**ImportError: No module named setuptools** This error appears at the end of the logs, and I'm sure it caused the fail. Am I supposed to include this in the control? 
[/LIST]

Adding python-distutils-extra didn't help after all.  If you would like to view the files contents, please see my branch [4].

Locally, it seemed to build fine. This is the message pbuilder gave me during the build:

```

john@sparrow:~/dev/build-area$ pbuilder-dist trusty build pupynere_1.0.15-0ubuntu1.dsc 
W: /home/john/.pbuilderrc does not exist
I: Logging to /home/john/pbuilder/trusty_result/last_operation.log
I: using fakeroot in build.
I: Current time: Fri Feb 21 17:43:04 PST 2014
I: pbuilder-time-stamp: 1393033384
I: Building the build Environment
I: extracting base tarball [/home/john/pbuilder/trusty-base.tgz]
I: creating local configuration
I: copying local configuration
W: --override-config is not set; not updating apt.conf Read the manpage for details.
I: mounting /proc filesystem
I: mounting /dev/pts filesystem
I: Mounting /var/cache/pbuilder/ccache
I: policy-rc.d already exists
I: Obtaining the cached apt archive contents
I: Setting up ccache
I: Installing the build-deps
 -> Attempting to satisfy build-dependencies
 -> Creating pbuilder-satisfydepends-dummy package
Package: pbuilder-satisfydepends-dummy
Version: 0.invalid.0
Architecture: amd64
Maintainer: Debian Pbuilder Team <pbuilder-maint@lists.alioth.debian.org>
Description: Dummy package to satisfy dependencies with aptitude - created by pbuilder
 This package was created automatically by pbuilder to satisfy the
 build-dependencies of the package being currently built.
Depends: debhelper (>= 9)
dpkg-deb: building package `pbuilder-satisfydepends-dummy' in `/tmp/satisfydepends-aptitude/pbuilder-satisfydepends-dummy.deb'.
Selecting previously unselected package pbuilder-satisfydepends-dummy.
(Reading database ... 11824 files and directories currently installed.)
Preparing to unpack .../pbuilder-satisfydepends-dummy.deb ...
Unpacking pbuilder-satisfydepends-dummy (0.invalid.0) ...
dpkg: pbuilder-satisfydepends-dummy: dependency problems, but configuring anyway as you requested:
 pbuilder-satisfydepends-dummy depends on debhelper (>= 9); however:
  Package debhelper is not installed.

Setting up pbuilder-satisfydepends-dummy (0.invalid.0) ...
Reading package lists...
Building dependency tree...
Reading state information...
Initializing package states...
Writing extended state information...
The following NEW packages will be installed:
  apparmor-easyprof{a} bsdmainutils{a} debhelper{a} dh-apparmor{a} 
  dh-python{a} file{a} gettext{a} gettext-base{a} groff-base{a} 
  intltool-debian{a} libasprintf0c2{a} libcroco3{a} libexpat1{a} libffi6{a} 
  libglib2.0-0{a} libmagic1{a} libmpdec2{a} libpipeline1{a} 
  libpython3-stdlib{a} libpython3.4-minimal{a} libpython3.4-stdlib{a} 
  libssl1.0.0{a} libunistring0{a} libxml2{a} man-db{a} mime-support{a} 
  po-debconf{a} python3{a} python3-minimal{a} python3.4{a} 
  python3.4-minimal{a} 
0 packages upgraded, 31 newly installed, 0 to remove and 0 not upgraded.
Need to get 1646 kB/11.1 MB of archives. After unpacking 44.2 MB will be used.
Writing extended state information...
Err http://archive.ubuntu.com/ubuntu/ trusty/main libglib2.0-0 amd64 2.39.4-0ubuntu1
  404  Not Found [IP: 91.189.91.14 80]
Err http://archive.ubuntu.com/ubuntu/ trusty/main debhelper all 9.20131127ubuntu2
  404  Not Found [IP: 91.189.91.14 80]
E: Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glib2.0/libglib2.0-0_2.39.4-0ubuntu1_amd64.deb: 404  Not Found [IP: 91.189.91.14 80]
E: Unable to correct for unavailable packages
Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
Writing extended state information...
E: pbuilder-satisfydepends failed.
I: Copying back the cached apt archive contents
I: unmounting /var/cache/pbuilder/ccache filesystem
I: unmounting dev/pts filesystem
I: unmounting proc filesystem
I: cleaning the build env 
I: removing directory /var/cache/pbuilder/build//13894 and its subdirectories

```

I don't know what it is that I did wrong. I followed the Packaging Guide carefully, but there are probably some things I haven't caught.

[1] [https://launchpad.net/~kotux/+archive/pupynere](https://launchpad.net/~kotux/+archive/pupynere)
[2] [https://launchpad.net/~kotux/+archive/pupynere/+build/5626060/+files/buildlog_ubuntu-trusty-amd64.pupynere_1.0.15-0ubuntu2_FAILEDTOBUILD.txt.gz]("https://launchpad.net/%7Ekotux/+archive/pupynere/+build/5626060/+files/buildlog_ubuntu-trusty-amd64.pupynere_1.0.15-0ubuntu2_FAILEDTOBUILD.txt.gz")
[3] [https://launchpad.net/~kotux/+archive/pupynere/+build/5626061/+files/buildlog_ubuntu-trusty-i386.pupynere_1.0.15-0ubuntu2_FAILEDTOBUILD.txt.gz]("https://launchpad.net/%7Ekotux/+archive/pupynere/+build/5626061/+files/buildlog_ubuntu-trusty-i386.pupynere_1.0.15-0ubuntu2_FAILEDTOBUILD.txt.gz")
[4] [https://code.launchpad.net/~kotux/+junk/pupynere-package-2](https://code.launchpad.net/~kotux/+junk/pupynere-package-2)

---

### Post by epikvision on 2014-02-25
Well, what do you know? Pupynere succeeded to build by:


[LIST]
[*]Adding "python-setuptools" in BuildDepends field in the control. 
[*]Adding "python-numpy" in Depends field in the control. (The developer told me that this was the only dependency.) 
[/LIST]

Debugging does pay off in the long run. ;)

[img]http://img32.imageshack.us/img32/6295/jghn.png[/img]

---

