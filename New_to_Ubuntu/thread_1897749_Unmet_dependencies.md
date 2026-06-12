---
title: "Unmet dependencies"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by nicckc on 2011-12-19
As a little history i had ubuntu 11.04 on my laptop and updated to 11.10 via the update manager and it was running fine until i tried to install some extra applications. The software center says i can not install things such as 

Advanced Settings: 
The following packages have unmet dependencies:

gnome-tweak-tool: Depends: python (< 2.8) but 2.7.2-7ubuntu2 is to be installed

Audacity:
The following packages have unmet dependencies:

audacity: Depends: audacity-data (= 1.3.13-5) but 1.3.13-5 is to be installed
          Depends: libavcodec-extra-53 (>= 4:0.7-1) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavformat-extra-53 (>= 4:0.7-1) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavutil-extra-51 (>= 4:0.7-1) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libc6 (>= 2.11) but 2.13-20ubuntu5 is to be installed
          Depends: libexpat1 (>= 1.95.8) but 2.0.1-7ubuntu3 is to be installed
          Depends: libflac++6 (>= 1.2.1) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.30.0-0ubuntu4 is to be installed
          Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.6-0ubuntu5 is to be installed
          Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
          Depends: libmad0 (>= 0.15.1b-3) but it is not going to be installed
          Depends: libportaudio2 (>= 19+svn20101113-2~) but 19+svn20110326-2 is to be installed
          Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.11.0) but 2.8.11.0-0ubuntu10 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.11.0) but 2.8.11.0-0ubuntu10 is to be installed

and others this problem seemed to be worse than i thought and on second check i do have all these installed. i have no idea what to do from here.

---

### Post by nicckc on 2011-12-19
for clarification the smiley faces are supposed to be 8.) without the period. its my first post sorry for the inconvenience.

---

### Post by wolfen69 on 2011-12-19
Please post the output of 
```
cat /etc/apt/sources.list

```

---

### Post by nicckc on 2011-12-19
i got this

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
# deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu natty main
# deb-src http://extras.ubuntu.com/ubuntu natty main
```

---

### Post by wolfen69 on 2011-12-19
First do
```
gksudo gedit /etc/apt/sources.list
```
then we need to remove the "#" from the beginning of the following lines.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

Save, then
```
sudo apt-get update
```
Try again to install software.

---

### Post by nicckc on 2011-12-19
did i not post the right thing?

---

### Post by wolfen69 on 2011-12-19
> **nicckc said:**
> did i not post the right thing?

Yes you did, see post above your last.

---

### Post by nicckc on 2011-12-19
oops sorry your first post came up as ".............................." so i assumed i had messed up but i did as you suggested and tried to install audacity and got this message from the software center.

The following packages have unmet dependencies:

audacity: Depends: audacity-data (= 1.3.13-5) but 1.3.13-5 is to be installed
          Depends: libavcodec-extra-53 (>= 4:0.7-1) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavformat-extra-53 (>= 4:0.7-1) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libavutil-extra-51 (>= 4:0.7-1) but 4:0.7.2.1ubuntu1 is to be installed
          Depends: libc6 (>= 2.11) but 2.13-20ubuntu5 is to be installed
          Depends: libexpat1 (>= 1.95.8) but 2.0.1-7ubuntu3 is to be installed
          Depends: libflac++6 (>= 1.2.1) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.30.0-0ubuntu4 is to be installed
          Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.6-0ubuntu5 is to be installed
          Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
          Depends: libmad0 (>= 0.15.1b-3) but it is not going to be installed
          Depends: libportaudio2 (>= 19+svn20101113-2~) but 19+svn20110326-2 is to be installed
          Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.11.0) but 2.8.11.0-0ubuntu10 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.11.0) but 2.8.11.0-0ubuntu10 is to be installed

---

### Post by wolfen69 on 2011-12-19
I just noticed something else too. Try removing the # from the following lines also.

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

---

### Post by nicckc on 2011-12-19
That did it! THANK YOU! :D

---

