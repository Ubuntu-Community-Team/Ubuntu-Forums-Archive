---
title: "Problems making deb package of qemu"
date: 2007-10-29
forum: Packaging and Compiling Programs
---

### Post by go_beep_yourself on 2007-10-29
I am following this guide. What is wrong? How can I fix it

```
root@ubuntu:/tmp/qemu-0.9.0# dpkg-buildpackage -rfakeroot
dpkg-buildpackage: source package is qemu
dpkg-buildpackage: source version is 0.9.0-1
dpkg-buildpackage: source changed by root <root@ubuntu>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 0.9.0-1
dpkg-checkbuilddeps: error: syntax error in control file debian/control at line 12: line with unknown format (not field-colon-value)
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
root@ubuntu:/tmp/qemu-0.9.0#
root@ubuntu:/tmp/qemu-0.9.0# dpkg-buildpackage -rfakeroot -d
dpkg-buildpackage: source package is qemu
dpkg-buildpackage: source version is 0.9.0-1
dpkg-buildpackage: source changed by root <root@ubuntu>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 0.9.0-1
 fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/tmp/qemu-0.9.0'
Makefile:3: config-host.mak: No such file or directory
make[1]: *** No rule to make target `config-host.mak'.  Stop.
make[1]: Leaving directory `/tmp/qemu-0.9.0'
make: [clean] Error 2 (ignored)
rm -f config.sub config.guess
dh_clean 
 dpkg-source -b qemu-0.9.0
dpkg-source: error: syntax error in control file ./qemu-0.9.0/debian/control at line 12: line with unknown format (not field-colon-value)
root@ubuntu:/tmp/qemu-0.9.0# 
 
```

Here is my debian/control file.

```
root@ubuntu:/tmp/qemu-0.9.0# cat debian/control 
Source: qemu
Section: uknown
Priority: extra
Maintainer: Chris L <good_bye300@gmail.cm>
Build-Depends: debhelper (>= 5), autotools-dev
Standards-Version: 3.7.2

Package: qemu
Architecture: any
Depends: ${shlibs:Depends}, ${misc:Depends}
Description: fast processor emulator
Virtualization
root@ubuntu:/tmp/qemu-0.9.0#
```

---

### Post by mlind on 2007-10-31
Ubuntu (gutsy and hardy) archive already contains the qemu package. Is there a reason you're duplicating the effort or are not using already existing source base as base for yours?

---

### Post by go_beep_yourself on 2007-10-31
> **mlind said:**
> Ubuntu (gutsy and hardy) archive already contains the qemu package. Is there a reason you're duplicating the effort or are not using already existing source base as base for yours?

Yes, I want to learn how to make a package, and why the steps I took to create one did not work. By creating packages, I can always have the latest versions of software and be able to remove software using the package management system.

---

### Post by mlind on 2007-10-31
> **go_beep_yourself said:**
> Yes, I want to learn how to make a package, and why the steps I took to create one did not work. By creating packages, I can always have the latest versions of software and be able to remove software using the package management system.

right. you probably have some garbage in the [debian/control]("http://www.debian.org/doc/maint-guide/ch-dreq.en.html#s-control") file. Did you use dh_make to create the 'skeleton' source package? You should if you didn't.
If you're not yet familiar with *New maintainers guide*, then it's best to start with that [http://www.debian.org/doc/maint-guide](http://www.debian.org/doc/maint-guide).

---

