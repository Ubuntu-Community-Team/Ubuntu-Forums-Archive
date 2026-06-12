---
title: "[SOLVED] Watching Youtube"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by jordank on 2008-08-23
With a fresh install of ubuntu, what do i need to view youtube videos?

---

### Post by perlluver on 2008-08-23
> **jordank said:**
> With a fresh install of ubuntu, what do i need to view youtube videos?

sudo apt-get install flashplugin-nonfree.

---

### Post by mc4100 on 2008-08-23
1. A working Internet Connection; go to System -> Admin -> Software Sources ... and tick the box "Software restricted by ... issues (multiverse)"
2. An open Terminal, (Applications -> Accessories -> Terminal)
3. Copy and paste:```
sudo apt-get install flashplugin-nonfree
```
4. Type your password

DONE!

---

### Post by jordank on 2008-08-23
kristie@kristie-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


still doesn't work.

---

### Post by jordank on 2008-08-24
should it not be working?

---

### Post by perlluver on 2008-08-24
> **jordank said:**
> should it not be working?

It should be working, youtube is flash.

---

### Post by schauerlich on 2008-08-24
Did you restart firefox?

---

### Post by brian mcgee on 2008-08-24
Do you have noscript installed? Any other Firefox plugins that might be blocking Flash? Does Flash work at other sites? e.g. break.com, kongregate.com

---

### Post by jordank on 2008-08-24
I did restart firefox, and no avail.
I don't know if i have noscript installed? I  don't know what that is.
Also, I don't think i have any other plugins  installed that would be blocking flash.

---

### Post by Therion on 2008-08-24
When you go to YouTube what DO you see?  What happens when you try to watch video?

Go to [www.albinoblacksheep.com](www.albinoblacksheep.com) 

Can you play videos on that site?

---

### Post by jordank on 2008-08-24
When i try to watch a video on youtube, it tells me:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "

on the blacksheep site, when I try to watch a video, a little toolbar at the top of the  site pops up saying that additional plugins are required to continue - when i click "install missing plugins" it allows me to download the latest adobe flash plugin. I click continue, and it tells me that it's already installed.

---

### Post by brian mcgee on 2008-08-24
> **jordank said:**
> When i try to watch a video on youtube, it tells me:

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. "

maybe you have javascript turned off

go to edit -> prefs -> content -> enable javascript

is that checked?

---

### Post by jordank on 2008-08-24
yeah, it's checked :S

---

### Post by aysiu on 2008-08-24
Can you paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? Warning: the first command may take a couple of minutes to execute: ```
sudo updatedb
locate libflash
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
cat /etc/lsb-release
uname -m
cat /etc/apt/sources.list
```

---

### Post by jordank on 2008-08-24
kristie@kristie-laptop:~$ sudo updatedb
kristie@kristie-laptop:~$ locate libflash
/home/kristie/Desktop/install_flash_player_9_linux/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
kristie@kristie-laptop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 156
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.48.0.2+really0ubuntu12
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g
Suggests: firefox, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplugin (<< 6), xfs (<< 1:1.0.1-5), flashplayer-mozilla
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
kristie@kristie-laptop:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
kristie@kristie-laptop:~$ dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
kristie@kristie-laptop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
kristie@kristie-laptop:~$ uname -m
i686
kristie@kristie-laptop:~$ cat /etc/apt/source.list
cat: /etc/apt/source.list: No such file or directory
kristie@kristie-laptop:~$

---

### Post by brian mcgee on 2008-08-24
> **jordank said:**
> 
kristie@kristie-laptop:~$ cat /etc/apt/source.list
cat: /etc/apt/source.list: No such file or directory
kristie@kristie-laptop:~$

That last one should be 

```
cat /etc/apt/sources.list
```

---

### Post by armageddon08 on 2008-08-24
Try after restarting your computer.

---

### Post by jordank on 2008-08-24
kristie@kristie-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
kristie@kristie-laptop:~$

---

### Post by aysiu on 2008-08-24
Hm. That's odd. *dpkg* says you have the software package *flashplugin-nonfree* installed, but when we did a search after a database reindex for *libflash* it didn't show up.

Can you try pasting these two commands in? ```
sudo apt-get update
sudo apt-get install --reinstall flashplugin-nonfree
``` and then restart Firefox?

P.S. Copy and paste instead of retyping. You're less likely to make a mistake, and it saves you a little work, too.

---

### Post by Pascal11110 on 2008-08-24
Try this:    (type in command prompt)     sudo apt-get install ubuntu-restricted-extras

this is how i got it to work

---

### Post by brian mcgee on 2008-08-24
> **jordank said:**
> 
kristie@kristie-laptop:~$ locate libflash
/home/kristie/Desktop/install_flash_player_9_linux/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so


Post the output of

```
ls /usr/lib/firefox/plugins/
```Then from your Desktop, in the install_flash... folder, copy the *libflashplayer.so* file to /usr/lib/firefox/plugins

This is not the clean way to do it...

---

### Post by jordank on 2008-08-24
kristie@kristie-laptop:~$ sudo apt-get update
[sudo] password for kristie:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Fetched 1B in 2s (0B/s)  
Reading package lists... Done
kristie@kristie-laptop:~$ sudo apt-get install --reinstall flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 91424 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 (using .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--22:57:41--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.130.70
Connecting to fpdownload.macromedia.com|72.246.130.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,044,538 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   98.71 KB/s
   50K .......... .......... .......... .......... ..........  3%  501.67 KB/s
  100K .......... .......... .......... .......... ..........  5%  561.14 KB/s
  150K .......... .......... .......... .......... ..........  6%  525.34 KB/s
  200K .......... .......... .......... .......... ..........  8%  594.62 KB/s
  250K .......... .......... .......... .......... .......... 10%  343.83 KB/s
  300K .......... .......... .......... .......... .......... 11%  494.90 KB/s
  350K .......... .......... .......... .......... .......... 13%  560.06 KB/s
  400K .......... .......... .......... .......... .......... 15%  594.83 KB/s
  450K .......... .......... .......... .......... .......... 16%  575.32 KB/s
  500K .......... .......... .......... .......... .......... 18%  571.86 KB/s
  550K .......... .......... .......... .......... .......... 20%  609.33 KB/s
  600K .......... .......... .......... .......... .......... 21%  576.66 KB/s
  650K .......... .......... .......... .......... .......... 23%  567.33 KB/s
  700K .......... .......... .......... .......... .......... 25%  614.68 KB/s
  750K .......... .......... .......... .......... .......... 26%  588.71 KB/s
  800K .......... .......... .......... .......... .......... 28%  575.83 KB/s
  850K .......... .......... .......... .......... .......... 30%  275.48 KB/s
  900K .......... .......... .......... .......... .......... 31%   67.56 MB/s
  950K .......... .......... .......... .......... .......... 33%   71.02 KB/s
 1000K .......... .......... .......... .......... .......... 35%  459.24 KB/s
 1050K .......... .......... .......... .......... .......... 36%  509.62 KB/s
 1100K .......... .......... .......... .......... .......... 38%  561.12 KB/s
 1150K .......... .......... .......... .......... .......... 40%  584.30 KB/s
 1200K .......... .......... .......... .......... .......... 42%  598.89 KB/s
 1250K .......... .......... .......... .......... .......... 43%  591.09 KB/s
 1300K .......... .......... .......... .......... .......... 45%  578.99 KB/s
 1350K .......... .......... .......... .......... .......... 47%  543.61 KB/s
 1400K .......... .......... .......... .......... .......... 48%  652.15 KB/s
 1450K .......... .......... .......... .......... .......... 50%  575.14 KB/s
 1500K .......... .......... .......... .......... .......... 52%  591.26 KB/s
 1550K .......... .......... .......... .......... .......... 53%  571.95 KB/s
 1600K .......... .......... .......... .......... .......... 55%  591.62 KB/s
 1650K .......... .......... .......... .......... .......... 57%  585.52 KB/s
 1700K .......... .......... .......... .......... .......... 58%  597.51 KB/s
 1750K .......... .......... .......... .......... .......... 60%  590.09 KB/s
 1800K .......... .......... .......... .......... .......... 62%  572.20 KB/s
 1850K .......... .......... .......... .......... .......... 63%  594.85 KB/s
 1900K .......... .......... .......... .......... .......... 65%  575.38 KB/s
 1950K .......... .......... .......... .......... .......... 67%  576.06 KB/s
 2000K .......... .......... .......... .......... .......... 68%  607.96 KB/s
 2050K .......... .......... .......... .......... .......... 70%  575.58 KB/s
 2100K .......... .......... .......... .......... .......... 72%  561.79 KB/s
 2150K .......... .......... .......... .......... .......... 73%  559.23 KB/s
 2200K .......... .......... .......... .......... .......... 75%  623.32 KB/s
 2250K .......... .......... .......... .......... .......... 77%  599.54 KB/s
 2300K .......... .......... .......... .......... .......... 79%  594.46 KB/s
 2350K .......... .......... .......... .......... .......... 80%  556.58 KB/s
 2400K .......... .......... .......... .......... .......... 82%  596.76 KB/s
 2450K .......... .......... .......... .......... .......... 84%  585.91 KB/s
 2500K .......... .......... .......... .......... .......... 85%  592.67 KB/s
 2550K .......... .......... .......... .......... .......... 87%  586.82 KB/s
 2600K .......... .......... .......... .......... .......... 89%  546.74 KB/s
 2650K .......... .......... .......... .......... .......... 90%  627.01 KB/s
 2700K .......... .......... .......... .......... .......... 92%  546.61 KB/s
 2750K .......... .......... .......... .......... .......... 94%  610.04 KB/s
 2800K .......... .......... .......... .......... .......... 95%  590.17 KB/s
 2850K .......... .......... .......... .......... .......... 97%  567.96 KB/s
 2900K .......... .......... .......... .......... .......... 99%  614.84 KB/s
 2950K .......... .......... ...                             100%  543.42 KB/s

22:57:49 (473.64 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.






I'm assuming the problem is the above.

---

### Post by jordank on 2008-08-24
kristie@kristie-laptop:~$ ls /usr/lib/firefox/plugins/
libjavaplugin.so           libtotem-mully-plugin.so
libtotem-basic-plugin.so   libtotem-mully-plugin.xpt
libtotem-basic-plugin.xpt  libtotem-narrowspace-plugin.so
libtotem-gmp-plugin.so     libtotem-narrowspace-plugin.xpt
libtotem-gmp-plugin.xpt    libunixprintplugin.so
kristie@kristie-laptop:~$

---

### Post by aysiu on 2008-08-24
> **jordank said:**
> 
22:57:49 (473.64 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3044538/3044538]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.






I'm assuming the problem is the above. Yes, that is the problem. It's officially installed, but the installation didn't complete. I thought this bug had been fixed. I forget the workaround. In the meantime, you might as well copy the libflashplayer.so file to /usr/lib/firefox/plugins/ manually.

---

### Post by brian mcgee on 2008-08-24
try solution here

[https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/+viewstatus](https://bugs.launchpad.net/ubuntu/gutsy/+source/flashplugin-nonfree/+bug/173890/+viewstatus)

---

### Post by jordank on 2008-08-24
thanks guys. all is well

---

### Post by brian mcgee on 2008-08-24
> **jordank said:**
> thanks guys. all is well

Good to hear. Which avenue worked for you? (thinking about others who read this thread)

---

### Post by mapleleaf on 2008-08-27
Thanks for the tips guys. I spent the last few days fixing this finally I re installed Ubuntu and installed flash plug non free from synaptic. Works perfect.

---

