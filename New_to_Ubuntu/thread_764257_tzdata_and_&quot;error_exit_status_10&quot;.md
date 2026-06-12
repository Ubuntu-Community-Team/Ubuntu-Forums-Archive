---
title: "tzdata and &quot;error exit status 10&quot;"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Hammock on 2008-04-23
Hi all, 

I am running Kubuntu Gutsy in a dual boot set-up (with WinXP) on a Dell 700m laptop (80 MB hard drive and 512 MB RAM).  I have been unable to update my system using either Apt, Synaptic or Adept due to complications which seem to be from tzdata.

Running sudo apt-get dist-upgrade in the terminal gives me the results below.  It is a little long, but the sticking point seems to be the error processing tzdata which is reported towards the end.

```
user1@mymachine:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libgnomevfs2-extra libmagick++9c2a
The following packages will be upgraded:
  apt apt-utils avahi-autoipd avahi-daemon cupsys cupsys-bsd cupsys-client
  cupsys-common firefox flashplugin-nonfree ghostscript ghostscript-x
  gs-common gs-esp gs-esp-x inkscape kexi kformula koffice-data koffice-libs
  labyrinth libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1 libavahi-qt3-1
  libcupsimage2 libcupsys2 libcupsys2-dev libgs8 libpoppler-glib2
  libpoppler-qt2 libpoppler2 openssh-client poppler-utils
  postgresql-client-8.2 rsync update-manager-core
40 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/47.6MB of archives.
After unpacking 16.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firefox koffice-data koffice-libs kexi kformula
Install these packages without verification [y/N]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up tzdata (2008a-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I tried reinstalling tzdata using Synaptic, and that returns an error also.  I am reluctant to remove it for a fresh reinstall, because that would seem to remove a lot of other programs along with it, which I would then need to reinstall.  A simpler fix would be better, if possible.  

Does anyone have any insight into this problem?

Thank you all for your help!

Hammock

---

### Post by ZabiGG on 2008-05-22
Hi there ;)

Maybe the link below will help...

[http://ubuntuforums.org/archive/index.php/t-583024.html](http://ubuntuforums.org/archive/index.php/t-583024.html)

---

