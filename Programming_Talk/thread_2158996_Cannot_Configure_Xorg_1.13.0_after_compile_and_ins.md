---
title: "Cannot Configure Xorg 1.13.0 after compile and install"
date: 2013-07-01
forum: Programming Talk
---

### Post by KingOfHorses on 2013-07-01
Hello all,

I am trying to compile and install Xorg 1.13.0 on Ubuntu 12.04.2 LTS Precise in VirtualBox.  My procedure is as follows:

Install using this iso:
[http://releases.ubuntu.com/precise/ubuntu-12.04.2-alternate-amd64.iso](http://releases.ubuntu.com/precise/ubuntu-12.04.2-alternate-amd64.iso)

sudo apt-get install dh-autoreconf libudev-dev dpkg-dev libgcrypt11-dev  libgl1-mesa-dev libpciaccess-dev libxkbfile-dev libxfont-dev  libpixman-1-dev x11proto-bigreqs-dev x11proto-composite-dev  x11proto-core-dev x11proto-damage-dev x11proto-dmx-dev x11proto-dri2-dev  x11proto-fixes-dev x11proto-fonts-dev x11proto-gl-dev  x11proto-input-dev x11proto-kb-dev x11proto-print-dev x11proto-randr-dev  x11proto-record-dev x11proto-render-dev x11proto-resource-dev  x11proto-scrnsaver-dev x11proto-video-dev x11proto-xcmisc-dev  x11proto-xext-dev x11proto-xf86bigfont-dev x11proto-xf86dga-dev  x11proto-xf86dri-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xserver-xorg-dev x11proto-xcmisc-dev xutils-dev

sudo apt-get source xserver-xorg-dev-lts-quantal

cp -r <that source directory> xserver

**Drop to single user mode**

cd xserver
sudo ./configure
sudo make
sudo make install
sudo reboot

[B]Drop to single user mode; it's the only thing that works

[/B]trying to X will cause the server to fail with:
     Fatal server error:
     No screens found

trying to Xorg -configure will fail with:
     Missing output drivers.  Configuration failed.
     Server terminated with error (2).  Closing log file.

I am certain I have the latest pixman.  Any help would be appreciated.  My goal is to have this working so that I may recompile and reinstall at a later date with a few modifications, but I have been stuck trying to get this initial compilation to work for awhile, now.

---

