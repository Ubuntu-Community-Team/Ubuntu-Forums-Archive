---
title: "[SOLVED] Adobe Flash Player"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by atliia on 2008-10-30
I am using 8.04 version of Ubuntu and I am having a problem with my flash player. I have read some threads where people say try to download it manually or get and unoffical version. I have tried both and neither work.
When I am finsihed installing the program I get a message that reads:

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Any help would be appreciated.

---

### Post by rockerphil on 2008-10-30
ok, i'm guessing (correct me if i'm wrong) that you're trying to get Flash working in Firefox. so my advice would be to run this command in terminal:

```
sudo apt-get install flashplugin-nonfree
```

then restart Firefox and that should do the trick. hope it helps,

Phil

---

### Post by atliia on 2008-10-30
you would be correct and thanks for the reply but, I have tried that already and it does not work. It goes through the whole download and install process then says flash-plugin not installed. Specificly I am trying to get the chat box on [http://www.miniconomy.com/promote.php?code=nq5u362kl8](http://www.miniconomy.com/promote.php?code=nq5u362kl8) to work. I believe it is because of my Flash player but I am not 100% sure of that.

---

### Post by LowSky on 2008-10-30
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by atliia on 2008-10-30
E: Couldn't find package ubuntu-restricted-extras
:( thanks anyway

---

### Post by LowSky on 2008-10-30
ah now i know your issue!!!

Go to System>Admin Software sources. when it opens make sure all the Repos are check except for source files you dont need that

then

run the command: sudo apt-get install ubuntu-restricted-extras

---

### Post by aysiu on 2008-10-30
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo updatedb
locate libflash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
cat /etc/apt/sources.list
``` Warning: the first command may take a few minutes to execute.

---

### Post by kansasnoob on 2008-10-30
LowSky is right you need to have the Hardy Partner repo checked.

```
sudo apt-get install ubuntu-restricted-extras
```

Should get you the bare essential Java and Flash 9. If you want to use the new Flash 10 do this afterwards:

```
sudo apt-get --purge remove flashplugin-nonfree
```

Then install the Flash 10 .deb from here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

When done you need to restart Firefox, go to File > Quit, click Quit, then restart Firefox. Occasionally I've had to restart the desktop by Ctrl > Alt > Backspace (I don't know why).

---

### Post by atliia on 2008-10-30
kyle@desktop:~$ su
Password: 
root@desktop:/home/kyle# sudo updatedb
root@desktop:/home/kyle# 
root@desktop:/home/kyle# locate libflash
/home/kyle/.mozilla/plugins/libflashplayer.so
/home/kyle/Desktop/usr/lib/flash-plugin/libflashplayer.so
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
root@desktop:/home/kyle# uname -m
i686
root@desktop:/home/kyle# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
root@desktop:/home/kyle# dpkg -s flashplugin-nonfree
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
root@desktop:/home/kyle# dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: purge ok not-installed
Priority: optional
Section: utils
root@desktop:/home/kyle# dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 176
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 0.6.0-2ubuntu1
Replaces: swf-player
Provides: swf-player
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.5.14), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.12.0), liboil0.3, libpango1.0-0 (>= 1.20.0), libswfdec-0.6-90
Conflicts: swf-player
Description: Mozilla plugin for SWF files (Macromedia Flash)
 A GTK+ and swfdec based Mozilla plugin for SWF files,
 commonly known as Macromedia Flash animations.
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Swfdec player for Adobe/Macromedia Flash
Original-Maintainer: Santiago Garcia Mantinan <manty@debian.org>
root@desktop:/home/kyle# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe
deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

root@desktop:/home/kyle#

---

### Post by anjilslaire on 2008-10-30
agreed ^^^. Get the official Adobe deb for Flash 10

---

### Post by atliia on 2008-10-30
Well thanks everyone now I have adobe player 10 working but it did not fix my chat box problem could it be as simple as a java update?

---

### Post by aysiu on 2008-10-30
It looks as if you have several versions of Flash installed, and that may be the problem. Paste these commands in: ```
mv /home/kyle/.mozilla/plugins/libflashplayer.so /home/kyle/.local/share/Trash/files/
sudo apt-get remove swfdec-mozilla
``` Then close Firefox and restart Firefox again and see if the problem persists.

---

### Post by atliia on 2008-10-30
Well It works now I would like to thank everyone for thier help. For the record it seams the second flashplayer was the problem I installed 8.10 and got rid of the other player and this is the first time in many months I have been able to chat!

---

