---
title: "ia64 problems with Firefox and Adobe Flash"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by mikedetch on 2008-11-08
I have an AMD 64 bit processor and installed the 64 bit version of Ubuntu. I cannot get Flashplayer to work, having tried to download it from Adobe.  Of course I get the "wrong architecture" error message stemming from ia32.

Does anyone know how to get Flash to work on ia64?  Here is my data:

mike@StevieRay:~$ uname -m
x86_64

mike@StevieRay:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"

mike@StevieRay:~$ locate libflash
/home/mike/Desktop/install_flash_player_9_linux/libflashplayer.so
/usr/lib/firefox-addons/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so

mike@StevieRay:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: purge ok not-installed
Priority: optional
Section: contrib/web

mike@StevieRay:~$ dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: purge ok not-installed
Priority: optional
Section: utils

mike@StevieRay:~$ dpkg -s swfdec-mozilla
Package: swfdec-mozilla
Status: purge ok not-installed
Priority: optional
Section: utils
:confused:

---

### Post by keplerspeed on 2008-11-08
Install the flashplugin-nonfree from synaptic. ensure you have the required repositories enabled in system>administration>software sources.

---

### Post by 3rdalbum on 2008-11-08
Just to correct something. ia64 is Itanium architecture, not your 64-bit x86.

Installing the "flashplugin-nonfree" package from Synaptic Package Manager will work on your 64-bit machine. It appears to install Flash system-wide so even if you install another Mozilla-compatible web browser later it will still work with the new browser.

---

### Post by mikedetch on 2008-11-08
Thanks! I stand corrected, on the x86_64.  This worked after descending several levels though synaptic installer.   One more question:  some sites say flashplayer 9 is required.  The one I just installed works fine for several sites.

What is the upgrade path to flash 9?

Thanks again!
Mike D
Austin Texas

---

