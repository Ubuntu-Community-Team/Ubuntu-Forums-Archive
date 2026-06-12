---
title: "How can I create .deb virtual package?"
date: 2005-10-29
forum: Packaging and Compiling Programs
---

### Post by naraku on 2005-10-29
Hi,

How can I create virtual .deb package? I want a package, what install all necessary packages after ubuntu-server installation, like openssh-server, php5, apache2, mysql-server, ....

But I don't want remember this package list. I write my package list to the control file's Depends: field, but debuild not work, because no program to make, or compile, just dependecies.

Thx any help.

Naraku

---

### Post by KIAaze on 2008-05-17
I found this post while searching for virtual packages because I'm having a problem with one of them.

But to answer your question (altough it's more than 2 years old):
```
[65][~/Desktop]$  cat metapackage_test/DEBIAN/control
Package: PackageName
Version: 1.0.0
Section: utils
Priority: optional
Architecture: i386
Depends: python, intltool, libgtk2.0-0, python-gtk2, python-notify, pcmciautils, openarena
Suggests:
Conflicts:
Installed-Size: 124 kb
Maintainer: superman <superman@krypton.com>
Description: This is a metapackage.
        It installs the dependencies. :)
[66][~/Desktop]$  dpkg-deb -b metapackage_test .
dpkg-deb: building package `packagename' in `./packagename_1.0.0_i386.deb'.
[67][~/Desktop]$  ls metapackage_test/
DEBIAN
[68][~/Desktop]$  ls metapackage_test/*
control
[69][~/Desktop]$  gdebi packagename_1.0.0_i386.deb
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done

Requires the installation of the following packages:
openarena  openarena-data
This is a metapackage.
        It installs the dependencies. :)
Need to be root to install packages

```

This works perfectly for me.
I opened the .deb with gdebi-gtk to be sure and it lists the dependencies to be installed, so it should work.

I hope the console copy-paste is clear enough as "instructions". ;)

edit:
OK, I finally understood what a "virtual package" is.
It is not a "metapackage" which is what you are trying to do and what I indicated how to do.
Here's how a virtual package works:
[http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg](http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg)
[http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-virtual)

So **a "virtual package" doesn't exist at all** unlike a "metapackage"!

---

