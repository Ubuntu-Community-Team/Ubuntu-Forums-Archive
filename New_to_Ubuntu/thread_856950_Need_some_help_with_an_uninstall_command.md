---
title: "Need some help with an uninstall command"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by erans on 2008-07-12
I'm trying to uninstall a bunch of packages (I think one of them is causing an annoying problem with viewing YouTube movies in fullscreen, as I didn't have the problem before I installed them). 

The packages are ```
autoconf libglib1.2ldbl libgtk1.2 libgtk1.2-common libmikmod2
  libpthread-stubs0 libpthread-stubs0-dev libx11-dev libxau-dev
  libxcb-xlib0-dev libxcb1-dev libxdmcp-dev libxext-dev libxi-dev libxml1 m4
  mesa-common-dev x11proto-core-dev x11proto-input-dev x11proto-kb-dev
  x11proto-xext-dev x11proto-xf86vidmode-dev xtrans-dev zlib1g-dev

```

sudo uninstall didn't work, and I figure I should ask for advice since I don't know what I'm doing. :)

---

### Post by lazyart on 2008-07-12
sudo apt-get remove *package1 package2 package3*
or
sudo apt-get purge *package1 package2 package3*
to remove configuration files as well.

---

### Post by erans on 2008-07-12
Thanks! That worked.. didn't solve my problem, though. Oh well.

---

### Post by hovzio on 2008-07-12
sometimes when you install a package it installs many other packages. (dependencies) These are not removed with

sudo apt-get remove *package

if you use:

sudo apt-get autoremove *package

Then the dependencies are also remove. (that is as long as they are not needed elsewhere.

---

### Post by erans on 2008-07-12
Great tip! Thanks.

---

### Post by tenor on 2008-09-21
I need some help with the following:

To add additional repositories I types=d in the terminal window:
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

AND

sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

AND

sudo apt-get update

Then I get the message:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

At the desktop screen a traffic sign ' one way' can be seen.

The fault is probably the word 'feisty' since I use the ubuntu hardy distribution.

What is the procedure for correcting this?.

Thanks very much, Daniel

---

