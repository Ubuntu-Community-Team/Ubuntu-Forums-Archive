---
title: "Questions"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Shippou on 2008-07-18
Hello guys...
Questions:
1. How do I install flash player in ff3 b4? (firefox 3 beta 4) The install plugin wizard says that the plugin is unknown. If I try to DL from Adobe site, it would not run, saying that my PC is not supported.
2. How to upgrade an application via the command line? I always enjoy typing at the command line. :)
3. How to do a security update in Kubuntu 7.10?

---

### Post by richiewrt on 2008-07-18
ok I'll try and answer a few of your questions.

to upgrade your entire system from the command line
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
This should upgrade all you packages that are installed. that includes security updates.

---

### Post by sisco311 on 2008-07-18
1.)
```
sudo aptitude install flasplugin-nonfree
```or
```
sudo apt-get install flasplugin-nonfree
```for more info read the man page:
```
man aptitude
man apt-get
```(q to quit)

---

### Post by richiewrt on 2008-07-18
Installing flash. Add/Remove programs and search for flash. That should take care of it.

Installing flash the hard way.  Go here and download the tar.gz [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=shockwaveFlash)

Save it to your desktop and then untar it.

```
cd Desktop/install_flash_player_9_linux
```
```
sudo sh flashplayer-installer
```

and just follow the directions.

---

### Post by Shippou on 2008-07-18
> **richiewrt said:**
> Installing flash. Add/Remove programs and search for flash. That should take care of it.


I did this yesterday, but then I haven't been able to watch (still) Intrnet streaming videos.

Thanks for all the answers..:)

---

### Post by SunnyRabbiera on 2008-07-18
you may need medibuntu too:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by RomeReactor on 2008-07-18
Hi. What version of Kubuntu do you have--Feisty, Gutsy, Hardy? Is it 32 bit or 64? Did you install Firefox from the repositories or from Mozilla's site?

If you already have the Flash plugin installed, make sure Gnash isn't installed also, as it interferes with Flash; close Firefox, open a Konsole and run:
```
sudo aptitude purge mozilla-plugin-gnash && sudo aptitude install flashplugin-nonfree libflashsupport
```

Libflashsupport is included in case Kubuntu Hardy also uses Pulse (as Ubuntu does).

---

### Post by Shippou on 2008-07-18
I am a Kubuntu 7.10 user. I got flash by sudo apt-get (see post above).

Thanks for the help. :)

---

### Post by RomeReactor on 2008-07-18
Did you also get Firefox from the repositories? Did you try removing Gnash (in case it was installed) and adding libflashsupport?

Is it Kubuntu 64 bit? That would explain why downloading Flash from Adobe's site didn't work.

---

### Post by Shippou on 2008-07-18
Well, I tried your command, and here is the output: 
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages have been automatically kept back:
  linux-restricted-modules-common
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater amarok amarok-xine apt apt-utils
  avahi-autoipd avahi-daemon bind9-host bzip2 cupsys cupsys-bsd
  cupsys-client cupsys-common dnsutils e2fslibs e2fsprogs findutils foo2zjs
  ghostscript ghostscript-x gtk-qt-engine hpijs hplip hplip-data hplip-gui
  hwdb-client-common hwdb-client-kde k3b kaddressbook kaffeine karm kate
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data
  kdelibs4c2a kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesktop kdesudo kdm kfind khelpcenter kicker klipper kmail
  kmailcvt kmenuedit knotes konsole korganizer ksmserver ksplash ksysguard
  ksysguardd kwin language-pack-en language-pack-en-base
  language-pack-kde-en language-pack-kde-en-base libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1
  libavahi-core5 libavahi-qt3-1 libbind9-30 libblkid1 libbz2-1.0 libcairo2
  libcomerr2 libcupsimage2 libcupsys2 libdb4.4 libdns32 libflac++6 libflac8
  libgnutls13 libgs8 libicu36 libisc32 libisccc30 libisccfg30 libk3b2
  libkcal2b libkdepim1a libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libkrb53 libksieve0 libktnef1 liblwres30
  libmimelib1c2a libmysqlclient15off libnm-util0 libpcre3 libpng12-0
  libpoppler-qt2 libpoppler2 libpq5 libpulse0 libqt3-mt libqt4-core
  libqt4-gui libruby1.8 libsearchclient0 libsmbclient libsnmp-base
  libsnmp10 libspeex1 libss2 libssl0.9.8 libstreamanalyzer0 libstreams0
  libstrigihtmlgui0 libtheora0 libuuid1 libvolume-id0 libxfont1 libxml2
  linux-generic linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-headers-generic linux-image-2.6.22-14-generic linux-image-generic
  linux-restricted-modules-2.6.22-14-generic
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.22-14-generic
  mysql-common network-manager networkstatus ntfs-3g openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-impress openoffice.org-java-common openoffice.org-kde
  openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-human openoffice.org-writer openssh-client openssl
  poppler-utils python-libxml2 python-qt4 python-qt4-dbus python-uno
  python2.5 python2.5-dev python2.5-minimal rdiff-backup rsync ruby1.8
  samba-common smbclient ssl-cert strigi-daemon ttf-opensymbol tzdata udev
  unzip update-manager-core volumeid vorbis-tools xserver-xorg-core
  xserver-xorg-video-intel
0 packages upgraded, 0 newly installed, 0 to remove and 185 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "libflashsupport"
The following packages have been automatically kept back:
  linux-restricted-modules-common
The following packages have been kept back:
  adept adept-batch adept-common adept-installer adept-manager
  adept-notifier adept-updater amarok amarok-xine apt apt-utils
  avahi-autoipd avahi-daemon bind9-host bzip2 cupsys cupsys-bsd
  cupsys-client cupsys-common dnsutils e2fslibs e2fsprogs findutils foo2zjs
  ghostscript ghostscript-x gtk-qt-engine hpijs hplip hplip-data hplip-gui
  hwdb-client-common hwdb-client-kde k3b kaddressbook kaffeine karm kate
  kcontrol kdebase-bin kdebase-data kdebase-kio-plugins kdelibs-data
  kdelibs4c2a kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesktop kdesudo kdm kfind khelpcenter kicker klipper kmail
  kmailcvt kmenuedit knotes konsole korganizer ksmserver ksplash ksysguard
  ksysguardd kwin language-pack-en language-pack-en-base
  language-pack-kde-en language-pack-kde-en-base libavahi-client3
  libavahi-common-data libavahi-common3 libavahi-compat-libdnssd1
  libavahi-core5 libavahi-qt3-1 libbind9-30 libblkid1 libbz2-1.0 libcairo2
  libcomerr2 libcupsimage2 libcupsys2 libdb4.4 libdns32 libflac++6 libflac8
  libgnutls13 libgs8 libicu36 libisc32 libisccc30 libisccfg30 libk3b2
  libkcal2b libkdepim1a libkleopatra1 libkmime2 libkonq4 libkpimexchange1
  libkpimidentities1 libkrb53 libksieve0 libktnef1 liblwres30
  libmimelib1c2a libmysqlclient15off libnm-util0 libpcre3 libpng12-0
  libpoppler-qt2 libpoppler2 libpq5 libpulse0 libqt3-mt libqt4-core
  libqt4-gui libruby1.8 libsearchclient0 libsmbclient libsnmp-base
  libsnmp10 libspeex1 libss2 libssl0.9.8 libstreamanalyzer0 libstreams0
  libstrigihtmlgui0 libtheora0 libuuid1 libvolume-id0 libxfont1 libxml2
  linux-generic linux-headers-2.6.22-14 linux-headers-2.6.22-14-generic
  linux-headers-generic linux-image-2.6.22-14-generic linux-image-generic
  linux-restricted-modules-2.6.22-14-generic
  linux-restricted-modules-generic linux-ubuntu-modules-2.6.22-14-generic
  mysql-common network-manager networkstatus ntfs-3g openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-impress openoffice.org-java-common openoffice.org-kde
  openoffice.org-math openoffice.org-style-crystal
  openoffice.org-style-human openoffice.org-writer openssh-client openssl
  poppler-utils python-libxml2 python-qt4 python-qt4-dbus python-uno
  python2.5 python2.5-dev python2.5-minimal rdiff-backup rsync ruby1.8
  samba-common smbclient ssl-cert strigi-daemon ttf-opensymbol tzdata udev
  unzip update-manager-core volumeid vorbis-tools xserver-xorg-core
  xserver-xorg-video-intel
0 packages upgraded, 0 newly installed, 0 to remove and 185 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done

```

After that I restarted firefox and visited youtube, and here is what it says when I try to play a video:

> 
Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 


During the past times, I tried to install flash by ff's built-in plugin installer, but it says that all plugins are installed or are incompatible.

I also tried to download the tar files in adobe's site. When I run ./configure after unpacking it, it says that my PC isn't suppoerted.

I am currently running FF3 beta 4.
Thanks for all the help. 

Clarification: What I mean by update is not all the packages, but only specific programs.

EDIT: I got firefox 3 beta 4 by sudo apt-get.

---

### Post by RomeReactor on 2008-07-18
I forgot libflashsupport isn't available in 7.10.

> **Shippou said:**
> During the past times, I tried to install flash by ff's built-in plugin installer, but it says that all plugins are installed or are incompatible.
Try pasting this in Firefox's address bar:
```
about:plugins
```
and post the section related to Flash.

> I also tried to download the tar files in adobe's site. When I run ./configure after unpacking it, it says that my PC isn't suppoerted.
That probably means you have Kubuntu 64 bit.

I'm not sure if this has to do with having 7.10, but I don't think you should be seeing these **The following packages have been automatically kept back** messages. Have you disabled any repositories?

---

### Post by Shippou on 2008-07-18
Here is the plugins info:

> 
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes


I think I haven't disabled repos.. in fact, I enabled them all. 

Here is my repos list: 
```

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
 deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu gutsy partner
 deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by RomeReactor on 2008-07-18
> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

File name: libnullplugin.so
The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type Description Suffixes Enabled
* All types .* No
Demo Print Plugin for unix/linux

File name: libunixprintplugin.so
The demo print plugin for unix.

MIME Type Description Suffixes Enabled
application/x-print-unix-nsplugin Demo Print Plugin for Unix/Linux .pnt Yes

Is this the complete output of "about: plugins"? If so, you have practically no plugins in Firefox--video, audio, Flash or Java. Does Flash work in Konqueror?

To verify that **flashplugin-nonfree** is correctly installed, run this in Konsole:
```
aptitude show flashplugin-nonfree
```
and post the output.

---

### Post by L815 on 2008-07-18
Check System > Administration > Software Sources > [Tab] Updates to see if Backports are enabled?


You can also try to install flash through firefox, when you visit a site requiring flash, there usually is a bar that pops up at the top. There should be a few options to install flash.

You could also try and download your preferred version of flash from Adobes site, and manually copy the libflashplugin (or w/e the name is) file, and place it into "/home/USERNAME/.mozilla/plugins (if you don't see plugins folder, make it yourself).

If you do the third method here, you may want to uninstall any previous versions of flash via terminal:
```
sudo apt-get remove flashplugin-nonfree
```

Restart firefox, and check if flash is installed.

---

### Post by Shippou on 2008-07-18
> **RomeReactor said:**
> Is this the complete output of "about: plugins"? If so, you have practically no plugins in Firefox--video, audio, Flash or Java. Does Flash work in Konqueror?


Yes. I thought as much. I unistalled Konqueror. Sorry.

> To verify that **flashplugin-nonfree** is correctly installed, run this in Konsole:
```
aptitude show flashplugin-nonfree
```
and post the output.

Here is the output:
```

shippou@Shippou:~$ aptitude show flashplugin-nonfree
Package: flashplugin-nonfree
State: installed
Automatically installed: yes
Version: 9.0.124.0ubuntu1~gutsy1
Priority: optional
Section: multiverse/web
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 160k
Depends: nspluginwrapper (>= 0.9.91.4-2ubuntu1), debconf | debconf-2.0, wget,
         libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6,
         libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0,
         libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6,
         libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2,
         libxrender1, zlib1g
Suggests: firefox, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts,
          ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>=
          1:1.0.1-5)
Conflicts: flashplugin (< 6), xfs (< 1:1.0.1-5), flashplayer-mozilla
Replaces: flashplugin (< 6)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can use
 the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.

 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from www.adobe.com.  The distribution license of the Adobe flash
 plugin is available at www.adobe.com.  Installing this Ubuntu package implies
 that you have accepted the terms of that license.

 Homepage: http://wiki.ubuntu.com/FlashPlayer9

```

---

### Post by Shippou on 2008-07-18
> **L815 said:**
> Check System > Administration > Software Sources > [Tab] Updates to see if Backports are enabled?


Cannot see it in the KDE menu.

> 
You can also try to install flash through firefox, when you visit a site requiring flash, there usually is a bar that pops up at the top. There should be a few options to install flash.

You could also try and download your preferred version of flash from Adobes site, and manually copy the libflashplugin (or w/e the name is) file, and place it into "/home/USERNAME/.mozilla/plugins (if you don't see plugins folder, make it yourself).

If you do the third method here, you may want to uninstall any previous versions of flash via terminal:
```
sudo apt-get remove flashplugin-nonfree
```

Restart firefox, and check if flash is installed.

I have done all this in the past, and none works.

Yes, I am using Kubuntu 64 bit. Sorry for the late info.

---

### Post by RomeReactor on 2008-07-18
Let's try deleting the **xpti.dat** file inside your home's .mozilla folder (close Firefox first):
```
rm ~/.mozilla/firefox/*default/xpti.dat
```
Then open Firefox again so it rebuilds the file, and see if you get the Flash plugin in "about: plugins".

---

### Post by Shippou on 2008-07-18
Aaargh! still does not work.

The about:plugins page still displays the same message.

---

### Post by RomeReactor on 2008-07-19
For the moment I'm out of suggestions; try doing an update and upgrade and see if that helps:
```
sudo aptitude update && sudo aptitude upgrade
```

Beyond that, I would suggest making a backup of your **.mozilla** folder by renaming it, and opening Firefox again so it recreates its preferences:
```
mv ~/.mozilla mozilla.backup
```
You'll find the backup as **mozilla.backup** in your home directory.

---

### Post by Shippou on 2008-07-19
> **RomeReactor said:**
> For the moment I'm out of suggestions; try doing an update and upgrade and see if that helps:
```
sudo aptitude update && sudo aptitude upgrade
```

Beyond that, I would suggest making a backup of your **.mozilla** folder by renaming it, and opening Firefox again so it recreates its preferences:
```
mv ~/.mozilla mozilla.backup
```
You'll find the backup as **mozilla.backup** in your home directory.

Ok. I have done this... I'll be back after 1 hour... (figuratively)

Thanks for those who helped. :)

---

### Post by Shippou on 2008-07-19
Hello again...

Just finished upgrading.

Should I install konqueror again? Or should I try to reinstall flash?

---

