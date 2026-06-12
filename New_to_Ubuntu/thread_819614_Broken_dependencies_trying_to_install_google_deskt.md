---
title: "Broken dependencies? trying to install google desktop"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-06-05
apparently i have broken dependencies what does that mean?

```
dreamsofubuntu@dreamsofubuntu-desktop:~$ sudo apt-get -y install libtool automake autoconf libxul-dev libghc6-mozembed-dev libcurl4-gnutls-dev libxml2-dev zlib1g-dev xulrunner libgtk2.0-dev libcairo2-dev libdbus-1-dev libdbus-glib-1-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libqt4-dev build-essential spidermonkey-bin libmozjs-dev
[sudo] password for dreamsofubuntu:
Reading package lists... Done
Building dependency tree
Reading state information... Done
libtool is already the newest version.
automake is already the newest version.
autoconf is already the newest version.
xulrunner is already the newest version.
build-essential is already the newest version.
spidermonkey-bin is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libcurl4-gnutls-dev: Depends: libldap2-dev but it is not going to be installed
  libmozjs-dev: Depends: libnspr4-dev but it is not going to be installed
  libxul-dev: Depends: libnspr4-dev but it is not going to be installed
              Depends: libnss3-dev but it is not going to be installed
E: Broken packages
dreamsofubuntu@dreamsofubuntu-desktop:~$   
```

---

### Post by shifty_powers on 2008-06-05
a dependecy is where a file requires another file, such as a library, to run. basically, you must have installed, or have acess to, all of the dependecies for a program, which can be recursive, to install. This can lead to what is known as dependecny hell, as the dependency for one file may have dpendencies of it's own, leading you on a meery goose chase ;)

try having a look at your repo's that are enabled in synaptic, or try going to

[http://packages.ubuntu.com](http://packages.ubuntu.com)

and searching for the ones apt has highlighted..

---

### Post by shifty_powers on 2008-06-05
all of those missing packages are available as downoads from that link btw ;)

---

### Post by wolfen69 on 2008-06-05
go to system>admin>software sources and make sure you have all repos checked off. also check the third party tab and check those off too.

---

### Post by kamitsukai on 2008-06-05
still not working ive downloaded libnss3-dev and tried to install but i get "ERROR: Cannot Install 'libnspr4-dev'

all sources are checked maybe the problem is caused by this? [http://news.softpedia.com/news/Kernel-Vulnerability-in-Ubuntu-8-04-LTS-Upgrade-Now-87195.shtml](http://news.softpedia.com/news/Kernel-Vulnerability-in-Ubuntu-8-04-LTS-Upgrade-Now-87195.shtml)

---

### Post by Oldsoldier2003 on 2008-06-05
have you updated your sources? if you have and have ensured the repos are enabled then its probably just an issue of all the packages not being updated. just out of curiosity could you post your /etc/apt/sources.list

---

### Post by kamitsukai on 2008-06-05
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://ppa.launchpad.net/jscinoz/ubuntu hardy main
deb http://moblock-deb.sourceforge.net/debian hardy main
deb-src http://moblock-deb.sourceforge.net/debian hardy main
deb http://javadesktop.org/lg3d/debian stable contrib
# Eternity Screensaver
deb http://ppa.launchpad.net/eternity/ubuntu feisty main
deb-src http://ppa.launchpad.net/eternity/ubuntu feisty main
```

---

### Post by shifty_powers on 2008-06-05
try uncommenting the backports, the do

```
sudo apt-get update
```

and try to reinstall google desktop

---

### Post by Oldsoldier2003 on 2008-06-05
also he is showing some fiesty based repos. it probably wouldn't hurt to comment them out for troubleshooting purposes

---

### Post by kamitsukai on 2008-06-05
did what you both suggested but it still isnt working...wasnt there some kind of kernal fix a few days ago? [http://news.softpedia.com/news/Kernel-Vulnerability-in-Ubuntu-8-04-LTS-Upgrade-Now-87195.shtml](http://news.softpedia.com/news/Kernel-Vulnerability-in-Ubuntu-8-04-LTS-Upgrade-Now-87195.shtml)

---

