---
title: "medibuntu downloads"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by stmcc on 2013-09-06
Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

---

### Post by newb85 on 2013-09-06
How about giving us a better idea of what is going on?  A quote of the medibuntu entry in your sources list would be helpful, for example.

The address packages.medibuntu.org is valid, but I'm getting no response on the IP address listed.  Have you tried a different DNS server?

---

### Post by Frogs Hair on 2013-09-06
I used the method at the link a few hours ago , so it may be a temporary problem. 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by stmcc on 2013-09-07
W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by stmcc on 2013-09-07
> **Frogs Hair said:**
> I used the method at the link a few hours ago , so it may be a temporary problem. 

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I tried this
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
Had the same results

---

### Post by carl4926 on 2013-09-07
Try and download a package manually
[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

---

### Post by bapoumba on 2013-09-07
Please post your sources.list : **cat/etc/apt/sources.list**
In your post #4, some of the links I can get to, some others give a 404 (hello not found ;)).

---

### Post by stmcc on 2013-09-07
: cat/etc/apt/sources.list: No such file or directory

---

### Post by carl4926 on 2013-09-07
> **stmcc said:**
> : cat/etc/apt/sources.list: No such file or directory

There should be a space after cat

```
cat /etc/apt/sources.list
```

---

### Post by bapoumba on 2013-09-07
Thanks carl4926, and sorry about the typo..

---

### Post by stmcc on 2013-09-07
mac@HOME:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120823.1)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
# deb cdrom:[Kubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120820.1)]/ dists/precise/main/binary-i386/
# deb cdrom:[Kubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Kubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120820.1)]/ precise main restricted
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise universe
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise multiverse
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise-security main restricted
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise-security universe
deb [http://mirrors.ucr.ac.cr/ubuntu/](http://mirrors.ucr.ac.cr/ubuntu/) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) precise partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

---

### Post by newb85 on 2013-09-07
Doesn't seem to be in the main source list.  What's the output of 
```
ls /etc/apt/sources.list.d
```

---

### Post by stmcc on 2013-09-08
mac@HOME:~$ ls /etc/apt/sources.list.d
alexmurray-indicator-sensors-precise.list
alexmurray-indicator-sensors-precise.list.save
bumblebee-stable-precise.list
bumblebee-stable-precise.list.save
diesch-testing-precise.list
diesch-testing-precise.list.save
google-chrome.list
google-chrome.list.save
google-earth.list
google-earth.list.save
medibuntu.list
medibuntu.list.save
michael-gruz-canon-oneiric.list
michael-gruz-canon-oneiric.list~
michael-gruz-canon-oneiric.list.save
michael-gruz-canon-precise.list
michael-gruz-canon-precise.list.save
opera.list
opera.list.save
ubuntu-wine-ppa-precise.list
ubuntu-wine-ppa-precise.list.save
ubuntu-x-swat-x-updates-precise.list
ubuntu-x-swat-x-updates-precise.list.save
Untitled Document 1
webupd8team-java-precise.list
webupd8team-java-precise.list.save
xorg-edgers-ppa-precise.list
xorg-edgers-ppa-precise.list.save
mac@HOME:~$

---

### Post by newb85 on 2013-09-08
Found it.  Please give the output of
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by stmcc on 2013-09-08
mac@HOME:~$ cat /etc/apt/sources.list.d/medibuntu.list
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
#deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
mac@HOME:~$

---

### Post by stmcc on 2013-09-08
also medibuntu is not listed on Synaptic package manager and Synaptic Package manager will not reload.

---

### Post by newb85 on 2013-09-09
Perhaps you should remove the medibuntu repository lists
```

sudo rm /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.save
```

and try re-adding the medibuntu repo according to one of the methods here.  [http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/](http://www.unixmen.com/how-to-add-medibuntu-repository-in-ubuntu-via-terminal-and-gui/)

---

### Post by stmcc on 2013-09-09
I get the same results;
```
sudo rm /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.savemac@HOME:~$ sudo rm /etc/apt/sources.list.d/medibuntu.list /etc/apt/so.d/medibuntu.list.save
[sudo] password for mac: 
mac@HOME:~$ sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2013-09-09 07:02:43--  [http://www.medibuntu.org/sources.list.d/precise.list](http://www.medibuntu.org/sources.list.d/precise.list)
Resolving [www.medibuntu.org]("http://www.medibuntu.org") ([www.medibuntu.org]("http://www.medibuntu.org"))... 88.191.127.22
Connecting to [www.medibuntu.org]("http://www.medibuntu.org") ([www.medibuntu.org)|88.191.127.22|:80]("http://www.medibuntu.org)|88.191.127.22|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 284 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 284         --.-K/s   in 0s      

2013-09-09 07:02:43 (38.5 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [284/284]

Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise Release.gpg
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates Release.gpg
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security Release.gpg
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise Release
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates Release
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security Release
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/main amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/restricted amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/universe amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/multiverse amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/main i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/restricted i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/universe i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/multiverse i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/main TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/multiverse TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/restricted TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/universe TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/main amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/restricted amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/universe amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/multiverse amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/main i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/restricted i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/universe i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/multiverse i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/main TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/multiverse TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/restricted TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/universe TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/main amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/restricted amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/universe amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/multiverse amd64 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/main i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/restricted i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/universe i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/multiverse i386 Packages
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/main TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/multiverse TranslationIndex
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/restricted TranslationIndex
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/universe TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/main Translation-en
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/multiverse Translation-en
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/restricted Translation-en
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise/universe Translation-en
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/main Translation-en
Hit [http://deb.opera.com](http://deb.opera.com) stable Release
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/multiverse Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/restricted Translation-en
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-updates/universe Translation-en
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/main Translation-en
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/multiverse Translation-en
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/restricted Translation-en
Ign [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/universe Translation-en_US
Hit [http://mirrors.ucr.ac.cr](http://mirrors.ucr.ac.cr) precise-security/universe Translation-en
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources
Hit [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Hit [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release.gpg
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en
  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]
W: Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en_US)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en_US)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

W: Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Unable to connect to packages.medibuntu.org:http: [IP: 88.191.101.8 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by stmcc on 2013-09-09
I think I am in a heap of trouble. I tried to remove medibuntu and all its pkgs. Now I can't log on to ubuntu 12.04.  I can still access 10.10 so I hope I can save the data before I have to reinstall 12.04

---

### Post by oldos2er on 2013-09-09
> **stmcc said:**
> I tried to remove medibuntu and all its pkgs. 

How exactly did you do this?

---

### Post by stmcc on 2013-09-09
sudo apt-get purge medibuntu-keyring
sudo rm -rf /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update


PKGS=$(dpkg -l | awk '{print $2}' | grep -e aacgain -e aacplusenc -e acroread-fonts -e alsa-firmware -e app-install-data-medibuntu -e apport-hooks-medibuntu -e hot-babe -e ices -e libavcodec-extra-53 -e libavdevice-extra-53 -e libav-extra-dbg -e libavfilter-extra-2 -e libavformat-extra-53 -e libavutil-extra-51 -e libdvdcss2 -e libdvdcss-dev -e libpostproc-extra-52 -e libswscale-extra-2 -e medibuntu-keyring -e mencoder -e mplayer-dbg -e mplayer-doc -e mplayer-gui -e mplayer -e

---

