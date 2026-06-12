---
title: "Deleted /etc/apt/sources.list"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by mickee384 on 2013-04-28
Using ubuntu 13.04. I was having difficulty connecting with the software updater and managed to delete the sources.list file. I haven't been backing up /etc. I am wondering how to rebuild the Other software list in the Other Software tab? I have done alot of searching but have been unsuccessful up to this point. Any help is greatly appreciated.

---

### Post by ibjsb4 on 2013-04-28
Check for a /etc/apt/sources.list.save.  That should have your sources, if not ..

Its says beta, but should work.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by rburkartjo on 2013-04-28
ib i have used the link you posted and worked like a charm at least for me.

---

### Post by mickee384 on 2013-04-28
Ok, so I added what I could and appended the file. The section about keys, I just pasted in Terminal. Does that work? Looked like it did some stuff, (It's likely never a good idea to sudo things in Terminal if I don't know what they do, I suppose)

---

### Post by ibjsb4 on 2013-04-28
Well lets see what sort of stuff you did :)

In terminal:

```
cat /etc/apt/sources.list
```

You can also try running an update and see what happens.

```
sudo apt-get update
```

---

### Post by mickee384 on 2013-04-29
```
mickee@mickeymouse:~$ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)]/ precise main restricted
deb http://ca.archive.ubuntu.com/ubuntu/ raring main universe restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring main universe restricted multiverse #Added by software-properties


## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ raring-updates main universe restricted multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-updates main universe restricted multiverse #Added by software-properties


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.


## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner


# deb http://ca.archive.ubuntu.com/ubuntu/ raring-security main universe restricted multiverse
# deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-security main universe restricted multiverse #Added by software-properties
deb http://archive.canonical.com/ raring partner
deb-src http://archive.canonical.com/ raring partner


#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring main restricted universe


###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-security main restricted universe
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe


#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################


###### Ubuntu Main Repos
deb http://ca.archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring main restricted universe multiverse


###### Ubuntu Update Repos
deb http://ca.archive.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
deb http://ca.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-security main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ raring-updates main restricted universe multiverse


##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################


###### 3rd Party Binary Repos


#### Clementine PPA - http://www.clementine-player.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu raring main


#### Gimp PPA - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main


#### GNOME3 Extra Apps PPA - https://launchpad.net/~gnome3-team/+archive/gnome3
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main


#### Google Chrome Browser - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/chrome/deb/ stable main


#### Google Earth - http://www.google.com/linuxrepositories/
## Run this command: wget -q https://dl-ssl.google.com/linux/linux_signing_key.pub -O- | sudo apt-key add -
deb http://dl.google.com/linux/earth/deb/ stable main


#### JDownloader PPA - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb http://ppa.launchpad.net/jd-team/jdownloader/ubuntu raring main


#### LibreOffice - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main


#### Medibuntu - http://www.medibuntu.org/ 
## Run this command: sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
deb http://packages.medibuntu.org/ raring free non-free


#### Opera - http://www.opera.com/
## Run this command: sudo wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
deb http://deb.opera.com/opera/ stable non-free


#### Oracle Java (JDK) Installer PPA - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb http://ppa.launchpad.net/webupd8team/java/ubuntu raring main


#### Unsettings PPA - http://www.florian-diesch.de/software/unsettings/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
deb http://ppa.launchpad.net/diesch/testing/ubuntu raring main


#### X Updates - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main




####### 3rd Party Source Repos


#### Clementine PPA (Source) - http://www.clementine-player.org/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 044A3B98
deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu raring main


#### Gimp PPA (Source) - https://launchpad.net/~otto-kesselgulasch/+archive/gimp
## Run this command: sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 614C4B38
deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu raring main


#### GNOME3 Extra Apps PPA (Source) - https://launchpad.net/~gnome3-team/+archive/gnome3
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3B1510FD
deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu raring main


#### JDownloader PPA (Source) - https://launchpad.net/~jd-team
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6A68F637
deb-src http://ppa.launchpad.net/jd-team/jdownloader/ubuntu raring main


#### LibreOffice (Source) - http://www.documentfoundation.org/download/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu raring main


#### Medibuntu (Source) - http://www.medibuntu.org/ 
## Run this command: sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
deb-src http://packages.medibuntu.org/ raring free non-free


#### Oracle Java (JDK) Installer PPA (Source) - http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu raring main


#### Unsettings PPA (Source) - http://www.florian-diesch.de/software/unsettings/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 0FEB6DD9
deb-src http://ppa.launchpad.net/diesch/testing/ubuntu raring main


#### X Updates (Source) - https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu raring main



```

---

### Post by fantab on 2013-04-29
This is how my Raring /etc/apt/sources.list looks:

```
# deb cdrom:[Ubuntu 13.04 _Raring Ringtail_ - Alpha amd64 (20130130)]/ raring main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb-src http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe
deb-src http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb-src http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security main restricted
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb-src http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
# deb-src http://archive.canonical.com/ubuntu raring partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
# deb-src http://extras.ubuntu.com/ubuntu raring main
```

you can just replace the content of your /etc/apt/sources.list with that of mine. Copy-Paste should do fine. Use from Terminal:

```
gksudo gedit /etc/apt/sources.list
```

Then SAVE the file.

Good Luck

---

### Post by ibjsb4 on 2013-04-29
Me thinks you kind of got carried away.  A lot of your PPAs are for source code, something you do not want.

Fantab's source list would work nice.  And if you want to cut out all the excess entries, all you really need in your sources.list:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-security multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) raring partner
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) raring main


---

### Post by mickee384 on 2013-04-29
Cool thanks you two! I put fantab's source code in place. Unfortunately for me last night I ran an update with my source list I had previously, now i think it updated gnome to a version not working well with unity. My desktop wallpaper gone, replaced by a white screen. The icons are still there

---

### Post by mickee384 on 2013-05-04
In the end had to re-install from scratch. I see after a clean install of 13.04 I am getting the same error: "Failed to download repository information", so in Terminal, I did a sudo apt-get update, it showed a not found item.. So I figured out I had a repository in Other Software, in Software and Update. I unchecked the repository, works now

---

### Post by codingman on 2013-05-04
Does your internet work fine?

---

