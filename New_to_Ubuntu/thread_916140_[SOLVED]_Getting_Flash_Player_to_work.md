---
title: "[SOLVED] Getting Flash Player to work"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by Big Chris on 2008-09-10
Hi all

I am very new to Linux so any help will be greatly received:
Both me and my Son have put Ubunto 8.04 on to our computers and are enjoying the experience.
Anyway we both installed Adobe Flash player 9 on our computers following instructions from Adobe, mine works fine, but I can't get my sons to work - it says on Adobe web site that it is installed, but when we go onto Youtube there is just a grey space where the video should be playing.
Can anyone help?

---

### Post by aysiu on 2008-09-10
> **Big Chris said:**
> Hi all

I am very new to Linux so any help will be greatly received:
Both me and my Son have put Ubunto 8.04 on to our computers and are enjoying the experience.
Anyway we both installed Adobe Flash player 9 on our computers following instructions from Adobe, mine works fine, but I can't get my sons to work - it says on Adobe web site that it is installed, but when we go onto Youtube there is just a grey space where the video should be playing.
Can anyone help?
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output back here? ```
uname -m
cat /etc/lsb-release
cat /etc/apt/sources.list
sudo updatedb
locate libflash
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
ls -l /usr/lib/firefox/plugins
``` Note: the fourth command may take a few minutes to execute. Be patient.

---

### Post by Big Chris on 2008-09-10
Hi AYSIU - did as you suggested see below - I haven't got a clue what it all means:

rhys@rhys-desktop:~$ uname -m
i686
rhys@rhys-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
rhys@rhys-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
rhys@rhys-desktop:~$ sudo updatedb
[sudo] password for rhys: 
rhys@rhys-desktop:~$ locate libflash
/home/rhys/.local/share/Trash/files/libflashplayer.so
/home/rhys/.local/share/Trash/files/install_flash_player_9_linux/libflashplayer.so
/home/rhys/.local/share/Trash/files/install_flash_player_9_linux.2/install_flash_player_9_linux/libflashplayer.so
/home/rhys/.local/share/Trash/info/libflashplayer.so.trashinfo
/home/rhys/.mozilla/plugins/libflashplayer.so
/home/rhys/Desktop/install_flash_player_9_linux/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
rhys@rhys-desktop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
rhys@rhys-desktop:~$ dpkd -s mozilla-plugin-gnash
bash: dpkd: command not found
rhys@rhys-desktop:~$ dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 308
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Source: gnash
Version: 0.8.2-0ubuntu3
Depends: gnash (= 0.8.2-0ubuntu3), libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1-21), libstdc++6 (>= 4.2.1-4), libx11-6, libxi6
Description: free SWF movie player - Plugin for Mozilla and derivatives
 Gnash is a free Flash movie player, which works either standalone, or as
 plugin for Firefox/Mozilla or Konqueror.
 .
 This package includes the plugin for Firefox/Mozilla Web Browser.
 .
 Homepage: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Gnash SWF Player
Original-Maintainer: Miriam Ruiz <little_miry@yahoo.es>
rhys@rhys-desktop:~$ dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
rhys@rhys-desktop:~$ ls -l/usr/lib/firefox/plugins
ls: invalid option -- /
Try `ls --help' for more information.
rhys@rhys-desktop:~$ ls -l /usr/lib/firefox/plugins
total 0
lrwxrwxrwx 1 root root 37 2008-09-06 10:39 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
lrwxrwxrwx 1 root root 43 2008-09-07 22:19 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root 44 2008-09-07 22:19 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root 42 2008-09-07 22:19 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root 43 2008-09-07 22:19 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root 42 2008-09-07 22:19 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root 43 2008-09-07 22:19 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root 39 2008-09-07 22:19 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root 43 2008-09-07 22:19 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root 44 2008-09-07 22:19 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root 40 2008-09-07 22:19 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
rhys@rhys-desktop:~$

---

### Post by SunnyRabbiera on 2008-09-10
How did you install flash may I ask?

---

### Post by Big Chris on 2008-09-10
Hi 
WE tried firstly through the Synaptic way, but got nowhere so we downloaded from Adobe and followed their instructions and still got no-where.

---

### Post by aysiu on 2008-09-10
Okay. I see the problem.

**Step 1**
Close Firefox or whatever web browser you're using

**Step 2**
Paste these commands in the terminal: ```
mv /home/rhys/.mozilla/plugins/libflashplayer.so ~/Desktop/
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get update
sudo apt-get install --reinstall flashplugin-nonfree
```

**Step 3**
Start Firefox again (or whatever web browser you use)

---

### Post by Big Chris on 2008-09-10
A Big thanks Aysiu

All working now and I have a happy Son - just got to get him to bed.

Anyway what did we do wrong?

---

### Post by SunnyRabbiera on 2008-09-10
> **Big Chris said:**
> A Big thanks Aysiu

All working now and I have a happy Son - just got to get him to bed.

Anyway what did we do wrong?

maybe not removing the gnash plugin, or installing flash the "windows way"

---

### Post by aysiu on 2008-09-10
> **Big Chris said:**
> A Big thanks Aysiu

All working now and I have a happy Son - just got to get him to bed. Glad to hear it.

> Anyway what did we do wrong? I don't know how it ended up this way, but you basically had about three Flash players installed. One was installed locally in your Firefox profile. One was an open source Flash player called Gnash. And the third was the Adobe Flash player (otherwise known as *flashplugin-nonfree*).

When you have Gnash installed, sometimes it overpowers Adobe Flash and then you get the grey spots instead of video. Gnash is open source, and that's why a lot of Ubuntu users are interested in it, but it isn't fully functional.

So the instructions I gave you removed Gnash, removed the locally-installed Flash plugin, and reinstalled (as it was already installed) the Adobe Flash plugin (just to be sure).

---

