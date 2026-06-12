---
title: "Problem with creating deb package"
date: 2007-12-08
forum: Packaging and Compiling Programs
---

### Post by Sesivany on 2007-12-08
I would like to learn how to create deb package. So that's why I chose program Jabbim ([http://dev.jabbim.cz/jabbim](http://dev.jabbim.cz/jabbim)) because Jabbim doesn't have a deb package yet.
I followed this tutorial: [http://www.us.debian.org/doc/manuals/maint-guide/index.en.html#contents](http://www.us.debian.org/doc/manuals/maint-guide/index.en.html#contents) (I created /debian etc.) The problem appeared when I executed command  "dpkg-buildpackage -rfakeroot". It writes this:
> make[1]: Entering directory `/home/eischmann/Stahuj/jabbim2/jabbim-0.3'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/eischmann/Stahuj/jabbim2/jabbim-0.3'
make: *** [build-stamp] Error 2
 
it makes files *.diff.gz and *.dsc but not *.changes and *.deb
The directory prepared by me for creating a package is here: [http://www.eischmann.cz/jabbim-0.31.tar.bz2](http://www.eischmann.cz/jabbim-0.31.tar.bz2) (it's just compressed in archive)
I think the problem is that Jabbim source code doesn't have makefile because it's written in Python and there is just shell script jabbim.sh which executes jabbim.py.
Any advice?

---

### Post by engla on 2007-12-09
Well you somehow have to make a build and install system for it. Debian package generation depends on some kind of install script for the package (does not have to be anything specific, could be anything).

Is there no install script/method in the upstream tarball? (for example a setup.py file is a common method) if not you have to make your own; but it could be very simple for this package.

But you have to find out where the files are to be installed, the deb must put them somewhere inside /usr (normally one file in /usr/bin and the rest where they belong somewhere else in /usr)

---

### Post by engla on 2007-12-09
Well I looked at the package and I think you should ask upstream if they can ship something to install the package with in the sources. Or you look in the fedora package and see what they have done.

I would think it would be unreasonable as a packager to reimplement an install script for the whole package. And then patch the whole program so it can still find its files when they are not in the same directory.

---

### Post by dholbach on 2007-12-10
You could install all files to a place by just using debian/install (check dh_install manpage), but as said in the thread before, it makes sense to talk to upstream.

Using Python's distutils might be the easiest option. (Check out  apt-get source bughelper  for an example.)

---

