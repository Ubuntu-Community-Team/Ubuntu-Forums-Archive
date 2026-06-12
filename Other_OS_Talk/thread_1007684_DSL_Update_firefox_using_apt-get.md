---
title: "DSL: Update firefox using apt-get"
date: 2008-12-10
forum: Other OS Talk
---

### Post by JacKeown on 2008-12-10
Hi I'm currently on DamnSmallLinux and need to use apt-get to update firefox to firefox 3 Currently I have Bon Echo. does anyone know what command to type in:guitar: Thanks.

---

### Post by jamesrfla on 2008-12-10
Maybe ```
sudo apt-get upgrade firefox
```

---

### Post by slick666 on 2008-12-10
you might need to updated you local cache

apt-get update
apt-get upgrade firefox

---

### Post by aysiu on 2008-12-10
Since Damn Small Linux is based on Debian, I'd just make sure you have the Debian testing repositories enabled and then do an *apt-get install firefox* to get the latest version.

---

### Post by JacKeown on 2008-12-10
how do you make sure that you have the debian testing repositories enabled?

---

### Post by kerry_s on 2008-12-10
prepare for breakage.
dsl is built on woody, it's far from compatible with testing.

what are your specs?
can you even run firefox 3?
if you have at least 128mb, i would recommend just doing a custom debian install.
net installer:
[http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_rc1/i386/iso-cd/debian-testing-i386-businesscard.iso)

uncheck the desktop to get a base install, then apt-get xorg and what ever window you want to use. i use jwm like dsl, so if you need help i can.

---

### Post by zmjjmz on 2008-12-10
I seriously would not recommend doing that. Leave it at Bon Echo, you should be fine.

---

### Post by JacKeown on 2008-12-10
Ok so how do you install flashplayer in dsl

---

### Post by aysiu on 2008-12-10
I don't think it can be done easily.

I just tried it out, and first of all, DSL doesn't enable *apt-get* by default. You have to go to Apps > Tools > Enable Apt just to be able to install anything.

Then it sticks you with the Woody (old) repositories, which don't have Firefox or Iceweasel in them.

If you try to switch to something newer, you get dependency problems.

The long way to do it would be to enable apt, edit the /etc/apt/sources.list file and change *stable* to *testing* and then do a full ```
apt-get dist-upgrade
``` and then install Iceweasel: ```
apt-get install iceweasel
```

---

### Post by JacKeown on 2008-12-10
It didn't work. at first when i typed apt-get dist-upgrade it said dpkg: error processing /var/cache/apt/archives/fileutils_4.1-10_i386.deb (--unpack): and it said that it couldn't find a package named iceweasel P.S all I really wan't to do is get flashplayer working on bon echo if anyone knows please I'm kind of a noob so a clear answer would be appreciated The reason I wanted firefox was I thought bon echo couldn't run flashplayer and still don't know?????? please respond if anyone knows

---

### Post by kerry_s on 2008-12-10
> **JacKeown said:**
> Ok so how do you install flashplayer in dsl

you need to grab flash 7:
[http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=6;t=18628](http://damnsmalllinux.org/cgi-bin/forums/ikonboard.cgi?act=ST;f=6;t=18628)

---

### Post by darrelljon on 2008-12-12
> **JacKeown said:**
> It didn't work. at first when i typed apt-get dist-upgrade it said dpkg: error processing /var/cache/apt/archives/fileutils_4.1-10_i386.deb (--unpack): and it said that it couldn't find a package named iceweasel P.S all I really wan't to do is get flashplayer working on bon echo if anyone knows please I'm kind of a noob so a clear answer would be appreciated The reason I wanted firefox was I thought bon echo couldn't run flashplayer and still don't know???????????????????????????????????????????????????????????

Do you know *Bon Echo* is an unbranded version of *Mozilla Firefox 2*? Do you know *Gran Paradiso* is an unbranded version of *Mozilla Firefox 3*?

---

### Post by RJARRRPCGP on 2008-12-18
> **JacKeown said:**
> It didn't work. at first when i typed apt-get dist-upgrade it said dpkg: error processing /var/cache/apt/archives/fileutils_4.1-10_i386.deb (--unpack): and it said that it couldn't find a package named iceweasel P.S all I really wan't to do is get flashplayer working on bon echo if anyone knows please I'm kind of a noob so a clear answer would be appreciated The reason I wanted firefox was I thought bon echo couldn't run flashplayer and still don't know?????? please respond if anyone knows

Did you forget to *sudo*?

---

