---
title: "Problem in making .deb package"
date: 2008-08-09
forum: Packaging and Compiling Programs
---

### Post by jeyaganesh on 2008-08-09
Hi,
I am trying to make .deb package for Flock 2 beta 2 version. This is my first time to make .deb package. I followed instruction from this thread [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003).
But at last step, I got the following error message. 

jay@jay-desktop:~/Packages/flock-2.0b2$ dpkg-buildpackage -rfakeroot
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package flock
dpkg-buildpackage: source version 2.0b2-1
dpkg-buildpackage: source changed by jay <@.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: build-essential
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)


Should I change anything more in 'rules' file as mentioned in that forum?
Please help me. Thanks in advance!
Jay

---

### Post by koenn on 2008-08-09
> dpkg-checkbuilddeps: Unmet build dependencies: build-essential

you probably have to install the package "build-essential" first.

---

### Post by jeyaganesh on 2008-08-09
Hi, How to install the particular package's build essential?

---

### Post by Canis familiaris on 2008-08-09
> **jeyaganesh said:**
> Hi, How to install the particular package's build essential?

```
sudo apt-get install build-essential
```

(this is assuming you have an active internet connection)
Otherwise you could install by Ubuntu CD:

```
sudo apt-cdrom add
```
```
sudo apt-get install build-essential
```

---

### Post by jeyaganesh on 2008-08-09
After doing build essential, it shows the following error,

root@jay-desktop:/home/jay/Packages/flock-2.0b2# dpkg-buildpackage -rfakeroot
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package flock
dpkg-buildpackage: source version 2.0b2-1
dpkg-buildpackage: source changed by jeyaganesh rajamanickam <@.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
/usr/bin/fakeroot: 166: debian/rules: Permission denied
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 126

I used 'dpkg-buildpackage -rfakeroot' command from the extracted Flock directory where 'debian' folder is created during the packaging. Is that right?

---

### Post by Tux.Ice on 2008-08-09
> **jeyaganesh said:**
> After doing build essential, it shows the following error,

root@jay-desktop:/home/jay/Packages/flock-2.0b2# dpkg-buildpackage -rfakeroot
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package flock
dpkg-buildpackage: source version 2.0b2-1
dpkg-buildpackage: source changed by jeyaganesh rajamanickam <@.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
/usr/bin/fakeroot: 166: debian/rules: Permission denied
dpkg-buildpackage: failure: fakeroot debian/rules clean gave error exit status 126

I used 'dpkg-buildpackage -rfakeroot' command from the extracted Flock directory where 'debian' folder is created during the packaging. Is that right?

Try using sudo

sudo dpkg-buildpackage

---

### Post by jeyaganesh on 2008-08-09
Little improvement, there are two files created - .diff.gz and .dsc. New error message is,

root@jay-desktop:/home/jay/Packages/flock-2.0b2# sudo dpkg-buildpackage -rfakeroot
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package flock
dpkg-buildpackage: source version 2.0b2-1
dpkg-buildpackage: source changed by jeyaganesh rajamanickam <jeyaganesh.rajamanickam@gmail.com>
dpkg-buildpackage: host architecture i386
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
# Add here commands to clean up after the build process.
/usr/bin/make clean
make[1]: Entering directory `/home/jay/Packages/flock-2.0b2'
make[1]: *** No rule to make target `clean'. Stop.
make[1]: Leaving directory `/home/jay/Packages/flock-2.0b2'
make: [clean] Error 2 (ignored)
dh_clean 
 dpkg-source -b flock-2.0b2
dpkg-source: building flock using existing flock_2.0b2.orig.tar.gz
dpkg-source: building flock in flock_2.0b2-1.diff.gz
dpkg-source: building flock in flock_2.0b2-1.dsc
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/jay/Packages/flock-2.0b2'
make[1]: *** No targets specified and no makefile found. Stop.
make[1]: Leaving directory `/home/jay/Packages/flock-2.0b2'
make: *** [build-stamp] Error 2
dpkg-buildpackage: failure: debian/rules build gave error exit status 2

I used the 'rules' file without any modification. I think I have give commands for configure, clean and install as mentioned in the original post [http://ubuntuforums.org/showthread.php?t=51003](http://ubuntuforums.org/showthread.php?t=51003)

Commands for configure, clean and install are './configure', 'make clean' and 'sudo make install' respectively. Is that right?

Thank you very much for your help.

---

