---
title: "[SOLVED] How do I install install flash 10 release candidate?"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by bmann11 on 2008-08-21
I have downloaded the package but have no idea what to do next, although I assume I need to get rid of flash 9 first?

---

### Post by aysiu on 2008-08-21
Yes, you'll have to remove Flash 9 first.

How did you install Flash 9?

---

### Post by bmann11 on 2008-08-21
I can't remember.  I think I unpacked and then put a lib somewhere, but I don't know for sure.  I searched through my posts, but it isn't in there, so I don't know how I accessed the information.

---

### Post by aysiu on 2008-08-21
> **bmann11 said:**
> I can't remember.  I think I unpacked and then put a lib somewhere, but I don't know for sure.  I searched through my posts, but it isn't in there, so I don't know how I accessed the information.
Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
dpkg -s flashplugin-nonfree
ls /usr/lib/firefox/plugins/
sudo updatedb
locate libflash
``` Warning: the third command might take a couple of minutes to execute.

---

### Post by bmann11 on 2008-08-22
here goes:

bradley@bradley-laptop:~$ dpkg -s flashplugin-nonfree
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
bradley@bradley-laptop:~$ ls/usr/lib/firefox/plugins
bash: ls/usr/lib/firefox/plugins: No such file or directory
bradley@bradley-laptop:~$ ls /usr/lib/firefox/plugins/
xineplugin.so
bradley@bradley-laptop:~$ sudo updatedb
[sudo] password for bradley: 
bradley@bradley-laptop:~$ locate libflash
/home/bradley/.mozilla/plugins/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so

---

### Post by aysiu on 2008-08-22
Okay.

Close Firefox, paste in these commands, and you should be good: ```
rm /home/bradley/.mozilla/plugins/libflashplayer.so
sudo apt-get remove flashplugin-nonfree
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_081108.tar.gz
tar -xvzf flashplayer10_install_linux_081108.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/xulrunner-addons/plugins/
```

---

### Post by bmann11 on 2008-08-22
This successfully uninstalled flash 9 but didn't install flash 10, any other ideas?

---

### Post by alienexplorers on 2008-08-22
Just download the adobe flash 10 file from adobe.  Un-tar it and run install.

---

### Post by bmann11 on 2008-08-22
That didn't work either.

Actually, it may have helped, I'm just not totally certain how to tell.  I thought I would see the espn.com (on the home page) media player with flash 10, but perhaps that is a completely different issue

Edit: Sorry, I do have flash 10, just not the flash player. Newbness, what can I say?

---

