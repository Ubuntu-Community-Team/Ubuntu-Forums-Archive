---
title: "apt-get after updating to breezy"
date: 2006-01-25
forum: Repositories &amp; Backports
---

### Post by ]Nbx*cmD[ on 2006-01-25
Problems again :'(
I work with VIM as editor, and i realized that after updating to breezy the graphical interface (gVIM) has been uninstalled... so i try to apt-get it:

```

nabax@Trepidance-2:~$ sudo apt-get install vim-gtk
Password:
S'està llegint la llista de paquets... Fet
S'està construint l'arbre de dependències... Fet
No s'han pogut instal·lar alguns paquets. Això pot ser degut a que vàreu
requerir una situació imposible o a que esteu usant la distribució
unstable i alguns paquets requerits encara no han estat creats o bé
encara no els hi han afegit.

Degut a que sols heu requerit una única operació, serà molt
probable que el paquet no sigui instal·lable i que s'hagi d'emetre
un informe d'error en contra d'aquest per a arxivar-lo.
La següent informació pot ajudar-vos a resoldre la situació:

Els següents paquets tenen dependències sense satisfer:
  vim-gtk: Depén: vim (= 1:6.3-046+1ubuntu7.1) però s'instal·larà 1:6.3-078+1ubuntu3
E: Paquets trencats

```

Well, it is in catalan but i think it's quite understandable, it says that vim-gtk depends on vim (= 1:6.3-046+1ubuntu7.1) but 1:6.3-078+1ubuntu3 is gonna be installed. E: broken packages

What's happening? :confused:

---

### Post by endersshadow on 2006-01-25
Please post your /etc/apt/sources.list file.

---

### Post by ]Nbx*cmD[ on 2006-01-25
Here is it:

```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

#deb-src http://es.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted
#deb-src http://es.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse

#deb-src http://es.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

# PROPIS

# deb http://ftp.debian.org/debian ../project/experimental main
# deb http://wine.sourceforge.net/apt/ binary/

#deb http://download.videolan.org/pub/videolan/debian sarge main
#deb-src http://download.videolan.org/pub/videolan/debian sarge main

#deb http://wine.sourceforge.net/apt/ binary/

```

---

### Post by endersshadow on 2006-01-25
Here, use this as your sources.list:

```
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
```

Then run:

```
sudo apt-get update
sudo apt-get upgrade
```

You're looking in the Hoary respositories for Breezy software...are you sure you upgraded to Breezy?

---

### Post by ]Nbx*cmD[ on 2006-01-25
I upgraded to breezy but conserved sources.list ](*,)
Now i'm apt-get upgrading... thx for the reply!

---

### Post by ]Nbx*cmD[ on 2006-01-25
gVim working now!!
Thanks a lot :)

---

### Post by endersshadow on 2006-01-25
Quite welcome :-D

---

