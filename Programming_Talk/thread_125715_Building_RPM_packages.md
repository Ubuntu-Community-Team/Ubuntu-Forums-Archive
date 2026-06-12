---
title: "Building RPM packages"
date: 2006-02-04
forum: Programming Talk
---

### Post by Scirious on 2006-02-04
Hi, people! I've been using SUSE for a while but I'm currently in the direction of changing distribution. My two choices are Mandriva or Ubuntu. I'm more tempted to stick with Ubuntu in my home and work workstations. However I need to create RPM packages to distribute it to other people. So, my question is: Is it possible to use Ubuntu to build RPM packages?

Thanks for your support,
Scirious.

---

### Post by diebels on 2006-02-04
Never tried, but there is a few rpm packages in ubuntu:

$ apt-cache search --names-only rpm
librpm-dev - RPM shared library, development kit
librpm4 - RPM shared library
rpm - Red Hat package manager
apt-rpm-repository - tools to create an APT RPM repository
libapt-rpm-pkg-dev - development files for APT for RPM library
libapt-rpm-pkg-libc6.3-6-0 - APT for RPM library
lsb-rpm - Red Hat package manager for LSB package building
python2.4-rpm - Python bindings for RPM
rpm2html - Generate HTML index from directories of RPMs

---

### Post by abedsalem2003 on 2010-01-27
try to install ubuntu-devtool

apt-get install ubuntu-dev-tools


cheers :) :popcorn:

---

### Post by Schotty on 2010-01-27
I would avoid trying to use another distro for building.  My bet is to setup a vm that is going to be your buidl environment and use that for making your rpms.  So if you need to use SLED 10 for work as your build target, use that as your build environment.  

Realize that you can do it on ubuntu, but you are _inviting_ major problems to crop up.  My rpm build box runs centos as its base, with vms of centos, rhel, fedora, and ubuntu.  Of course the latter does debs, but for packaging thats basically the safest sure fire bet that anyone I know has come up with.  

And as a word of advice, anyone that tells you to use checkinstall to make packages isn't doing commercial grade apps or packages and ignore them :D

---

### Post by schdvntn on 2010-08-20
I use ubuntu to build rpm package, and i havent really faced any issues till date.
u need to have rpmbuild and other essentials on Ubuntu. To install, run:
sudo apt-get install rpm

---

