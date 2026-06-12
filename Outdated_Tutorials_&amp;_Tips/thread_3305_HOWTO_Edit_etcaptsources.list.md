---
title: "HOWTO: Edit /etc/apt/sources.list"
date: 2004-11-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Magneto on 2004-11-05
Show your sources.list - you have any secrets in there?

here's mine- i separated everything all neat and orderly for use in synaptics just check and uncheck things when I can't find that certain bit of software.
Can be very useful when trying to get apps with weird dependencies blocking your progress.

The mods and everyone else will be sure to tell you-[Color=Red] **INSTALL from other than ubuntu warty main and  warty-security main at your own risk**[/color]

n00bs- this file is what apt-get/synaptics uses to find available software for you to install.Any lines with the # will be ignored.  Be very careful when upgrading your system with any UNSUPPORTED software repositories activated (not commented out with a # sign). You don't want a miss-matched hoary-warty-debiantesting system, unless you do and you have plenty of time and tylenol ;) but then you'd be using Gentoo. Anyway if this is all new to you try "man apt-get" before you modify anything. Good luck.

/etc/apt/sources.list

[Color=Green]deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

#############Ubuntu Warty##############

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main 
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty restricted

deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main 
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty restricted


##############Ubuntu Security############## 

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main 
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security restricted 
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security universe 
#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security multiverse  

deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main 
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security restricted 
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security universe 
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security multiverse  


##############Ubuntu Warty Updates################
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates main 
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates restricted 
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates multiverse 

# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates main
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates restricted
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty-updates multiverse 

#--------------------------------------------------------------------
#---------------------------Hoary------------------------------------
#############Ubuntu Hoary##############
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main 
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted

# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main 
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary restricted


##############Ubuntu Security############## 
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main 
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted 
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
# deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse  

# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security restricted 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security universe 
# deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security multiverse  



#---------------------------Non_Ubuntu------------------------------



###############Debian###############


#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable main
#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable contrib
#deb [http://http.us.debian.org/debian](http://http.us.debian.org/debian) stable non-free

#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US main
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US contrib
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) stable/non-US non-free


#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable main 
#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable non-free 
#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) unstable contrib 

#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) unstable/non-US main
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) unstable/non-US contrib 
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) unstable/non-US non-free


#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing main 
#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing non-free 
#deb [http://ftp.us.debian.org/debian/](http://ftp.us.debian.org/debian/) testing contrib 

#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) testing/non-US main
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) testing/non-US contrib 
#deb [http://non-us.debian.org/debian-non-US](http://non-us.debian.org/debian-non-US) testing/non-US non-free




###########Individual Packages############

#amarok binaries
# deb [http://www.kalyxo.org/debian/](http://www.kalyxo.org/debian/) unstable main 


#Packages: lame, lame-dev, lame-extras, liblame0, lame-ha, lame-dev-ha, lame-extras-ha, liblame0-ha, xmms-musepack, xmms-musepack-386, xmms-musepack-k7, cue2toc, libaudio-wav-perl, shntool, shorten, xmms-shn
# deb [http://rarewares.org/debian/packages/unstable/](http://rarewares.org/debian/packages/unstable/) ./ 


#[http://marillat.free.fr/](http://marillat.free.fr/)  mplayer +
# deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 
 [/color]

---

### Post by oddabe19 on 2004-11-05
```
root@ubuntu:/home/oddabel/Desktop # cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20040928)]/ unstable main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#Universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted


#Multimedia
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

#Mono
deb [http://www.getsweaaa.com/~tseng/ubuntu/debs/](http://www.getsweaaa.com/~tseng/ubuntu/debs/) ./
deb-src [http://www.getsweaaa.com/~tseng/ubuntu/debs/](http://www.getsweaaa.com/~tseng/ubuntu/debs/) ./

#Multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted universe multiverse

#hoary release
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

#KDE 3.3, really slow, so screw it.
#deb [http://geeksoc.org/~jr/ubuntu/](http://geeksoc.org/~jr/ubuntu/) unstable main

#Misc stuff
#deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
#deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib non-free
root@ubuntu:/home/oddabel/Desktop #

```

I use hoary, that's why the Warty Source repos are commented out. I was getting conflicts compiling sources... so i just keep the hoary source repos now.

---

### Post by jdodson on 2004-11-05
thats great!  thanks!  make sure to put HOWTO in the subject next time :-) 

HOWTO: add to sources list, or add other repositories, etc.

---

### Post by Magneto on 2004-11-05
[QUOTE=jdodson]thats great!  thanks!  make sure to put HOWTO in the subject next time :-) 

HOWTO: add to sources list, or add other repositories, etc.[/QUOTE]
Who am I to disagree with Mr. T. I changed it.

---

### Post by jmontano on 2004-11-05
here goes mine

got mplayer working fine - also xine streamtuner - some kde apps - latest gaim - Im using hoary

------------------------------
# tseng's cool mono repository. Get muine, it rocks.

deb [http://www.getsweaaa.com/~tseng/ubuntu/debs/](http://www.getsweaaa.com/~tseng/ubuntu/debs/) ./

# This is for illegal stuff. You want w32codecs for sure, and the mplayer stuff,
# make sure you snag totem-xine from universe, and you'll be able to play
# anything. Don't blame me if this is illegal in your country, heh.

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://mirror.switch.ch/ftp/mirror/ubuntu/](http://mirror.switch.ch/ftp/mirror/ubuntu/) hoary main restricted universe

deb [http://ftp.de.debian.org/debian/](http://ftp.de.debian.org/debian/) testing non-free

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

# gdesklets from apt-get.org
deb [http://j.portalier.free.fr/debian/](http://j.portalier.free.fr/debian/) testing main

# [http://www.ubuntuforums.org/showthread.php?t=1968](http://www.ubuntuforums.org/showthread.php?t=1968)
# How can I use FreeNX with Ubuntu?
deb [http://kanotix.com/files/debian/](http://kanotix.com/files/debian/) ./


# wine
deb [http://www.fs.tum.de/~bunk/debian](http://www.fs.tum.de/~bunk/debian) woody/bunk-1 main contrib non-free
# arp-fun: Arp-fun, an ARP Spoofing utility
deb [http://people.debian.org/~amaya/debian](http://people.debian.org/~amaya/debian) ./

# kopete
deb [http://kopete.creativa.cl/debian/sid](http://kopete.creativa.cl/debian/sid) ./

# opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free

# logreports: lire
deb [http://apt.logreport.org/pub/debian](http://apt.logreport.org/pub/debian) local contrib

# chmviewer
deb [http://www.herdsoft.com/debian](http://www.herdsoft.com/debian) woody main non-free

# dansguardian
deb [http://www.pcxperience.org/apt/debian](http://www.pcxperience.org/apt/debian) stable/

# wajig system administration by command line tool.
deb [http://www.togaware.com/debian](http://www.togaware.com/debian) ./

# jabber
deb [http://sgolovan.nes.ru/debian/](http://sgolovan.nes.ru/debian/) ./

---

### Post by tvlad on 2004-11-06
What is the difference between restricted, main, and multiverse, i mean i know it's in the packages, but how and in what way, universe from what i gather also holds non free packages as well.

---

