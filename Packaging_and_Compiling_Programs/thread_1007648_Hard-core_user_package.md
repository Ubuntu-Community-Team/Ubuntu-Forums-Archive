---
title: "Hard-core user package"
date: 2008-12-10
forum: Packaging and Compiling Programs
---

### Post by rengolin on 2008-12-10
Hi all,

I've installed many copies of Ubuntu now and I find it a bit annoying that some packages are missing from the default installation. Packages such as build-essential, manpages-dev and openssh-server are the ones I miss most, but traceroute and nmap sometimes makes a difference (especially when you lost your connection!).

So I did a meta-package called 'hard-core-user' that one can install upon every release, which only depends on other packages (mentioned above). We could do a second-step-install, after the system is installed and updated, something that flashes on the user's panel, asking him if he's a hard-core user, or a C++ or Java developer, of if he just want to install all common plug-ins and codecs to have an easier life while browsing and watching films.

The package control file is ludicrously simple, of course:
Package: hard-core-user
Version: 0.1
Section: admin 
Priority: optional
Architecture: all
Essential: no
Depends: build-essential, manpages-dev, openssh-server, traceroute, nmap, cvs, subversion, sysv-rc-conf
Installed-Size: 0
Maintainer: Renato Golin [rengolin@systemcall.org]
Provides: hard-core-user
Description: Ubuntu is a fantastic distro but the default installation lacks a lot of useful tools that the hard-core user often needs up-front.

How easy it is to add this (or something similar) to the Ubuntu's repository?

What do you think about the second-stage install thing?

cheers,
--renato

---

