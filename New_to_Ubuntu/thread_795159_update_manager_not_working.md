---
title: "update manager not working"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by hazman on 2008-05-15
hi,
yesterday i uninstalled ubuntu descktop and replaced it with xubutntu.reason being i have a lowish spec m/c.now i tried using update manager for some updates it was highlighting and was stuck doing nothing for 2hrs

---

### Post by Mhurst1 on 2008-05-15
Did you get the update for update manager yesterday? That could be a problem? Also are you sure you had an internet connection? Thirdly I wouldnt of deleted ubuntu desktop I would of kept it and just installed Xbuntu.

---

### Post by Kobalt on 2008-05-15
Can you please post the error message you have?

---

### Post by hazman on 2008-05-15
well thats when they were highlighted and it didn't work yesterday.so i thought in my wisdom think maybe there was some confict with ubuntu and xubuntu to delete ubuntu

---

### Post by GolanTrevize on 2008-05-15
my machine here also refuses to work with the update manager for some days now. But I can use apt-get upgrade to retrieve the updates.

Does that work at your machine or does there still happens nothing?

---

### Post by hazman on 2008-05-15
there was no error message it just sat there doing nothing but curcor was spin as tho it was

---

### Post by Kobalt on 2008-05-15
And you do have Internet connection working?

---

### Post by hazman on 2008-05-15
yes i can do that .thats now i installed xubunu desktop.yes internet fine

---

### Post by Kobalt on 2008-05-15
Can you please open a Terminal (Applications > Accessories > Terminal) and post here the results of the following command lines :
```
cat /etc/apt/sources.list
sudo aptitude update
```

---

### Post by hazman on 2008-05-15
here are results
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
wayne@ubuntu:~$ sudo aptitude update

[sudo] password for wayne: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
wayne@ubuntu:~$

---

### Post by Kobalt on 2008-05-15
And now try the following command, it should perform updates from the Terminal:
```
sudo aptitude full-upgrade
```

---

### Post by hazman on 2008-05-15
that seems to have done trick thanks

---

### Post by Kobalt on 2008-05-15
You're welcome :)

---

### Post by hazman on 2008-05-15
on a totally different matter have you any idea how i can get my external cd-rom working. will i have to do another post

---

