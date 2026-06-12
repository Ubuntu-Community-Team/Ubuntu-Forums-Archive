---
title: "New user here - sudo apt upgrade"
date: 2020-04-14
forum: New to Ubuntu
---

### Post by renecek on 2020-04-14
Hello, 
new user here. Have installed Ubuntu 18.04 LTS Desktop. Minimal installation.
Just used sudo apt update and sudo apt upgrade

sudo apt upgrade shows me this:
> Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  conky conky-std fonts-liberation2 fonts-opensymbol gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gudev-1.0 gir1.2-udisks-2.0 grilo-plugins-0.3-base gstreamer1.0-gtk3
  libaudclient2 libboost-date-time1.65.1 libboost-filesystem1.65.1 libboost-iostreams1.65.1
  libboost-locale1.65.1 libcdr-0.1-1 libclucene-contribs1v5 libclucene-core1v5 libcmis-0.5-5v5
  libcolamd2 libdazzle-1.0-0 libe-book-0.1-1 libedataserverui-1.2-2 libeot0 libepubgen-0.1-1
  libetonyek-0.1-1 libevent-2.1-6 libexiv2-14 libfreerdp-client2-2 libfreerdp2-2 libfwup1 libgc1c2
  libgee-0.8-2 libgexiv2-2 libgif7 libgom-1.0-0 libgpgmepp6 libgpod-common libgpod4 libid3tag0
  libimlib2 liblangtag-common liblangtag1 liblirc-client0 liblua5.1-0 liblua5.3-0
  libmediaart-2.0-0 libmspub-0.1-1 libodfgen-0.1-1 libqqwing2v5 libraw16 librevenge-0.0-0
  libsgutils2-2 libssh-4 libsuitesparseconfig5 libvncclient1 libwayland-egl1-mesa libwinpr2-2
  libxapian30 libxmlsec1 libxmlsec1-nss libxmmsclient6 libxnvctrl0 lp-solve media-player-info
  python3-mako python3-markupsafe realpath syslinux syslinux-common syslinux-legacy
  usb-creator-common
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Is it safe to use sudo apt autoremove?
Thank you.

---

### Post by deadflowr on 2020-04-14
What have you installed or removed prior to running the upgrade commands?

---

### Post by renecek on 2020-04-15
installed a lot of apps. spotify, remmina, atom, filezilla, thunderbird, chrome etc.

---

### Post by Impavidus on 2020-04-15
Packages may become autoremovable when another package is upgraded and no longer has the same dependencies, but this is rare (other than kernel upgrades). It's more common that they become autoremovable because something was removed. Let's have a look at your log file:```
grep " remove " /var/log/dpkg.log
```

---

### Post by renecek on 2020-04-15
today installed conky and uninstalled imwheel, here is log:
> 2020-04-13 18:20:31 remove winehq-stable:amd64 5.0.0~bionic <none>
2020-04-13 18:54:52 remove discord:amd64 0.0.10 <none>
2020-04-13 21:52:50 remove conky:all 1.10.8-1 <none>
2020-04-14 18:43:54 remove conky-std:amd64 1.10.8-1 <none>
2020-04-14 19:38:18 remove conky-all:amd64 1.10.8-1 <none>
2020-04-14 19:38:18 remove conky-manager:amd64 2.4~136~ubuntu16.04.1 <none>
2020-04-15 19:50:20 remove imwheel:amd64 1.0.0pre12-12 <none>




---

### Post by deadflowr on 2020-04-15
So what have you added?
I see winehq which isn't from Ubuntu.
As well as discord, also not from Ubuntu.

Post what sources you have added:
```
grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by renecek on 2020-04-16
:~$ grep ^ /etc/apt/sources.list /etc/apt/sources.list.d/*
```
/etc/apt/sources.list:# deb cdrom:[Ubuntu 18.04.4 LTS _Bionic Beaver_ - Release amd64 (20200203.1)]/ bionic main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list:# newer versions of the distribution.
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic main restricted
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list:## distribution.
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic universe
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic universe
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic-updates universe
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list:## security team.
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic multiverse
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic multiverse
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list:deb http://sk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
/etc/apt/sources.list:# deb-src http://sk.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list:## 'partner' repository.
/etc/apt/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list:# deb http://archive.canonical.com/ubuntu bionic partner
/etc/apt/sources.list:# deb-src http://archive.canonical.com/ubuntu bionic partner
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu bionic-security main restricted
/etc/apt/sources.list:# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu bionic-security universe
/etc/apt/sources.list:# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu bionic-security multiverse
/etc/apt/sources.list:# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
/etc/apt/sources.list:deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
/etc/apt/sources.list:# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
/etc/apt/sources.list.d/alessandro-strada-ubuntu-ppa-bionic.list:deb http://ppa.launchpad.net/alessandro-strada/ppa/ubuntu bionic main
/etc/apt/sources.list.d/alessandro-strada-ubuntu-ppa-bionic.list:# deb-src http://ppa.launchpad.net/alessandro-strada/ppa/ubuntu bionic main
/etc/apt/sources.list.d/alessandro-strada-ubuntu-ppa-bionic.list.save:deb http://ppa.launchpad.net/alessandro-strada/ppa/ubuntu bionic main
/etc/apt/sources.list.d/alessandro-strada-ubuntu-ppa-bionic.list.save:# deb-src http://ppa.launchpad.net/alessandro-strada/ppa/ubuntu bionic main
/etc/apt/sources.list.d/cybermax-dexter-ubuntu-sdl2-backport-bionic.list:deb http://ppa.launchpad.net/cybermax-dexter/sdl2-backport/ubuntu bionic main
/etc/apt/sources.list.d/cybermax-dexter-ubuntu-sdl2-backport-bionic.list:# deb-src http://ppa.launchpad.net/cybermax-dexter/sdl2-backport/ubuntu bionic main
/etc/apt/sources.list.d/cybermax-dexter-ubuntu-sdl2-backport-bionic.list.save:deb http://ppa.launchpad.net/cybermax-dexter/sdl2-backport/ubuntu bionic main
/etc/apt/sources.list.d/cybermax-dexter-ubuntu-sdl2-backport-bionic.list.save:# deb-src http://ppa.launchpad.net/cybermax-dexter/sdl2-backport/ubuntu bionic main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/hluk-ubuntu-copyq-bionic.list:deb http://ppa.launchpad.net/hluk/copyq/ubuntu bionic main
/etc/apt/sources.list.d/hluk-ubuntu-copyq-bionic.list:# deb-src http://ppa.launchpad.net/hluk/copyq/ubuntu bionic main
/etc/apt/sources.list.d/hluk-ubuntu-copyq-bionic.list.save:deb http://ppa.launchpad.net/hluk/copyq/ubuntu bionic main
/etc/apt/sources.list.d/hluk-ubuntu-copyq-bionic.list.save:# deb-src http://ppa.launchpad.net/hluk/copyq/ubuntu bionic main
/etc/apt/sources.list.d/mark-pcnetspec-ubuntu-conky-manager-pm9-bionic.list:deb http://ppa.launchpad.net/mark-pcnetspec/conky-manager-pm9/ubuntu bionic main
/etc/apt/sources.list.d/mark-pcnetspec-ubuntu-conky-manager-pm9-bionic.list:# deb-src http://ppa.launchpad.net/mark-pcnetspec/conky-manager-pm9/ubuntu bionic main

```

---

### Post by SeijiSensei on 2020-04-16
I get autoremove lists all the time and run "sudo apt autoremove" when I do. It's never caused a problem. Often the lists will include outdated kernels or unneeded dependencies. An updated program might need an updated version of some library. If nothing else requires the old version of that library, it shows up in autoremove.

---

### Post by renecek on 2020-04-17
Thank you. So is it safe to run autoremove right?

---

### Post by Impavidus on 2020-04-17
Probably, but I didn't check every package on that list. They don't appear to be vital.

Whenever package management gets somewhat complex, I use the synaptic package manager. It can give you a nice list of all the autoremovable packages and you can select which to uninstall, so you can remove them one by one (or a few at a time, as some of them might depend on each other). If something goes wrong, reinstall the package you just removed.

---

### Post by TheFu on 2020-04-17
I always **apt autoremove**. Can't recall any issues recently (8+yrs).  OTOH, I have daily, automatic, versioned, backups, so if any thing bad happens, it is a minor inconvenience only. I say do it. Don't look back.  How bad can it be?  Really, if the system was important, you'd have backups.

---

### Post by renecek on 2020-04-22
used autoremove, rebooted computer. No problems

---

