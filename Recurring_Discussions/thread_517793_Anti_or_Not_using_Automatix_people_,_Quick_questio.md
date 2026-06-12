---
title: "Anti or Not using Automatix people , Quick question."
date: 2007-08-05
forum: Recurring Discussions
---

### Post by Wiebelhaus on 2007-08-05
After reading what [Matthew Garrett wrote about Automatix]("http://mjg59.livejournal.com/77440.html") I've decided to drastically change the way I install ubuntu , I don't just perform Ubuntu installs on my home pc , I probably install half a dozen a week or more , So having a fail safe and relatively fast way of setting up Ubuntu is crucial.

My question is to the people that either do not recommend automatix or outright hate it , is there a protocol from which you install and set up ubuntu with everything that's needed for a fully functioning desktop that doesn't require much user intervention? If something advanced is needed I'm the person that does it.

Here's what I did after I read this article , Backed up about 80gigs worth of data on my network and formatted both machines , Set up XP on the main machine and Ubuntu dual booting with dual WD 250gigs Sata drives , Now I have a clean Ubuntu installation (and wouldn't you know it , the xp installation crashed the first time I booted it - lol) anyway i think Automatix has made me either lazy or more of a noob , Because I'm somewhat lost as where to start , I'm going to hit the package manager and start finding stuff of course , But my question is .. is there a protocol you follow? maybe some master list of where to obtain the plugins and the other little things.?

Thanks.

---

### Post by superstylin on 2007-08-05
For my Ubuntu install, I simply add the Wine HQ Repos and the Medibuntu Repos, and it has everything I could possible want... and more... 

>.>

<.<


\\:D/

---

### Post by eentonig on 2007-08-05
I have a USB stick with :
- A small script that basically just updates the sources.list file. And then does apt-get && apt-upgrade. And then does "apt-get install <huge list of standard things I install by default>"
- And a folder with "/etc/" containing the configuration files with changes I always seem to make.

After the default install, I just run that script. 

It's not much, but I don't do regular install. So it serves my needs.

---

### Post by Wiebelhaus on 2007-08-05
> **eentonig said:**
> I have a USB stick with :
- A small script that basically just updates the sources.list file. And then does apt-get && apt-upgrade. And then does "apt-get install <huge list of standard things I install by default>"
- And a folder with "/etc/" containing the configuration files with changes I always seem to make.

After the default install, I just run that script. 

It's not much, but I don't do regular install. So it serves my needs.

May I ask you to```
 ....
```link that huge list please sir?.

---

### Post by eentonig on 2007-08-05
Can you wait untill tomorrow? I have the stick laying somewhere at work. But basically, I constructed it from all the guides/howto's from Ubuntu help pages and other howto's I followed.

---

### Post by Wiebelhaus on 2007-08-05
> **eentonig said:**
> Can you wait untill tomorrow? I have the stick laying somewhere at work. But basically, I constructed it from all the guides/howto's from Ubuntu help pages and other howto's I followed.

no hurries or worries mate.

---

### Post by eentonig on 2007-08-17
It seems that I lost the file with the list.

But I'm trying to create a script that would generate a list with additional installed packages.

I'm just trying to find out how to define which packages are installed by a default install.

---

### Post by Steveway on 2007-08-17
I use Trevinos source list.
It has almost every repo out there in it but it is only meant to use if you know the risks.

---

### Post by eentonig on 2007-08-17
I think the security risks in using Trevino's sources.list, far outweigh the risks involved in using automatix.

I only enable repo's manually. And only after verifying which packages they serve beside the one I'm interested in.

---

### Post by ugm6hr on 2007-08-17
Potentially, you could use Synaptic on a fresh Feisty install to "Generate Package Download Script" (in File Menu) after marking all the packages you want, download all the wanted packages from this script, then copy the script and all packages on to CD or USB.

Then, on each fresh install, it would just be a case of using "Add downloaded packages".

The only thing this wouldn't resolve is Realplayer - but I gather that helix fulfills the same needs (although I use Realplayer).

Of course - you still need to decide which packages you think are necessary - probably the easiest thing is to look through this list and search for them in Synaptic: [http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks#Automatix2_on_.28K.2FX.29Ubuntu_7.04_i386.2FAMD64_.28Feisty.29](http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks#Automatix2_on_.28K.2FX.29Ubuntu_7.04_i386.2FAMD64_.28Feisty.29)

---

### Post by hyper_ch on 2007-08-17
well, here's my little script...

I have additional repos that I copy back first (I backed up the whole /etc/apt folder ;)
Then I just update and install stuff

```

#!/bin/bash

################ RESTORE SOURCES.LIST ###############

cp -f backup_files/sources.list /etc/apt/sources.list
cp -f backup_files/secring.gpg /etc/apt/secring.gpg
cp -f backup_files/trustdb.gpg /etc/apt/trustdb.gpg
cp -f backup_files/trusted.gpg /etc/apt/trusted.gpg

#####################################################

aptitude -y remove mozilla-thunderbird

aptitude update
aptitude -y upgrade

# Skype
aptitude -y install skype

# Java
aptitude -y install sun-java6-jre sun-java5-jre

# Postfix
aptitude -y install postfix

#KDE Appz
aptitude -y install kopete konversation konqueror k3b amarok krfb ktorrent
aptitude -y install kftpgrabber kate kontact kdepim-kio-plugins kgpg
aptitude -y install akregator gdb

# Burn Programs
aptitude -y install gnomebaker

# GnuPGP Key Management
aptitude -y install seahorse file-roller

# aMSN
aptitude -y install amsn

# IRSSI / OpenSSH
aptitude -y install irssi openssh-server

# GnuMP3d
# aptitude -y install gnump3d

# OTR
aptitude -y install python-glade-1.2 python-gtk-1.2

# VmWare
aptitude -y install linux-headers-`uname -r` build-essential xinetd

# Browsers
aptitude -y install kazehakase opera flashplugin-nonfree

# Codecs
aptitude -y install libdvdcss2 gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui w32codecs mplayer

# VLC
aptitude -y install vlc

# Samba
aptitude -y install samba

# Midnight Commander
aptitude -y install mc

# UNRAR
aptitude -y install unrar

# GParted
aptitude -y install gparted

# CheckRootKit
aptitude -y install chkrootkit

# OpenOffice
aptitude -y install openoffice.org openoffice.org-gtk

# ImageMagic
aptitude -y install imagemagick

# Numlock & fonts
aptitude -y install numlockx msttcorefonts

# Timeserver
aptitude -y install ntp ntpdate

# HDD Encryption
aptitude -y install cryptsetup hashalot

# various
aptitude -y install whois phpmyadmin mysql-server mysql-client libmysqlclient15-dev adesklets d4x googleearth htop traceroute libjack0.100.0-dev

#######################
#######################

# Restore other files

cp -f backup_files/sysinfo /usr/share/apps/konversation/scripts/sysinfo
cp -f backup_files/screenshot /usr/bin/screenshot

```

---

### Post by venik212 on 2007-08-17
This last suggestion sounds great!  However, I use Kubuntu with Adept.  Can Adept do this trick of saving the list of downloaded packages?  I could not find it in the menus.

---

### Post by hyper_ch on 2007-08-18
you can also install synaptic... apt-get and aptitude ae already insalled...

---

### Post by mcduck on 2007-08-18
I always first add all the repositories I need (Universe, Multiverse, Backports, Medibuntu and Trevino's). Then I just open Synaptic, mark everything I want, click "Apply" and drink a cup of coffee while everything gets installed.. :D

In the past I had a script to install everything for me, but as it's such a simple task I haven't bothered updating the script for ages and just use Synaptic instead.

---

