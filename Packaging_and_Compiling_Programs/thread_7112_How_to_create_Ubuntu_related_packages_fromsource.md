---
title: "How to create Ubuntu related packages fromsource?"
date: 2004-12-04
forum: Packaging and Compiling Programs
---

### Post by urke on 2004-12-04
I download sources for building new packages:

glib 2.4.8
atk 1.9.0
pango 1.7.0
gtk 2.4.14
gnumeric 1.4.0
leafnode 2.0.0alpha20041113a
xdtv 2.0.0

Now I need to know how to get debian/* files prepared for Ubuntu in sources of this packages, and to build Ubuntu related deb's for this ?

P.S. I'm new i debian based building environment :)

---

### Post by ubuntu_demon on 2004-12-04
I've read somewhere on this forum about something called "checkinstall"

instead of make you would run "make checkinstall"

---

### Post by urke on 2004-12-04
Checkinstall is not what I wish to get. I wish to get: libgtk2.0, libgrk2.0-bin, libgtk2.0-common, libgtk2.0-dev for Gtk+ 2.4.14, not yust gtk+2-2.4.14 (that produce checkinstall), so I can upgrade installed libgtk2.0's from Synaptic.

Also, I wish to get which dependencies gtk+2 require to be installed, and when I build all packages and place it into /var/cache/apt/archives and chose in Synaptic libgtk2.0, to be automaticaly upgraded all other packages (atk, pango, etc).

---

### Post by az on 2004-12-04
apt-get source whateverpackage

Make sure you have the deb-src repositories enabled.  

Is this what you mean?  Or do you want to make a debian package from scratch.  Look up debhelper and dh-make.

Read up on the new maintainers corner on debian.org

---

### Post by urke on 2004-12-04
Thanks azz. I wish exactly that - to get deb's from scratch.

I get dh-make, dh-buildinfo, debhelper. Where I can get complet debian/* directory for some of gtk+2 versions, yust as template, to see how and what I need to reenter?

TIA

---

### Post by p!=f on 2004-12-08
Mini HOWTO:
1) Unpack your sources and cd to it
2) run **deb-make** to debianize the sources
3) Tweak **control** (contains package information, dependencies,...) and **rules** (for compile options) files in Debian directory
4) run **dpkg-buildpackage** to build a Debian package

---

