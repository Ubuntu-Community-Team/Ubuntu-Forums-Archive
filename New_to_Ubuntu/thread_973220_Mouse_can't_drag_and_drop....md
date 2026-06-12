---
title: "Mouse can't drag and drop..."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by dsurge on 2008-11-06
Seems like I'm posting a lot here lately, sorry...

Ok so I downloaded the patch to the issue of my scroll not working on the trackpoint on my T61 laptop, but now my trackpoint mouse won't drag and drop, highlight, or hold the left click.

Link to bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/282387](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/282387)

Link to fix:

sudo apt-get build-dep xserver-xorg-input-evdev
apt-get source xserver-xorg-input-evdev
cd xserver-xorg-input-evdev-2.0.99+git20080912
patch -p1 < /path/to/preinit.diff
./autogen --prefix=/usr
make
sudo make install

and the preinit.diff file is here:

[http://launchpadlibrarian.net/18944364/preinit.diff](http://launchpadlibrarian.net/18944364/preinit.diff)

There's another release for a patch there but I can't figure out what it does... or how to install it.

I can still double click/single click with my trackpoint mouse and the mouse with my touchpad works fine (it drags and drops, the whole shabang).

Thanks in advance as usual guys

-DSurge

---

