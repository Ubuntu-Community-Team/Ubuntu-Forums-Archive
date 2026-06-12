---
title: "[SOLVED] help with updates"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by heiowge on 2008-07-17
Using the update manager, a file has appeared and is "greyed out".

The file is libpq5.

The manager won't let me download and install it, but it won't go away.

What is it?

Will I be able to install / get rid of it?

Cheers

---

### Post by hyper_ch on 2008-07-17
run in the terminal
```

sudo apt-get update

```
adn then
```

sudo apt-get upgrade

```

and post the output.

---

### Post by heiowge on 2008-07-17
sudo apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy Release 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports Release
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
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Reading package lists... Done
root@********-desktop:/home/********# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libpq5
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by heiowge on 2008-07-17
bump

---

### Post by hyper_ch on 2008-07-17
well, either you can wait until it sorts out or force upgrade with
```

sudo apt-get install dist-upgrade

```

I normally force upgrade but others had bad luck with it. Have a look at what other packages it might then remove. Just to be on the sure side.

---

### Post by Jim! on 2008-07-17
Try running the following commands and seeing if it will allow you to install the update afterwards:

> sudo apt-get autoremove

> sudo apt-get autoclean


PS: What are the tags to add "code" instead of quote?:D

---

### Post by hyper_ch on 2008-07-17
[noparse]```

```[/noparse]

and to display bbcode as bbcode use [noparse][noparse][/noparse][/noparse] tags ;)

---

### Post by Jim! on 2008-07-17
> **hyper_ch said:**
> [noparse]```

```[/noparse]

and to display bbcode as bbcode use [noparse][noparse][/noparse][/noparse] tags ;)

Hey Thanks! Knew it was something like that but just couldn't seem to figure it out so I kept it safe and used the 'quote' tags:)

@OP did running the commands have any effect on that 'uninstallable' update?

---

### Post by hyper_ch on 2008-07-17
quote tags have two disadvantages compared to code

(1) quote tags won't be quoted in another quote
(2) code tags use monoblock, meaning that the visual display remains intact... especially usefull if you have "tabs" or many empty spaces in between ;)

---

### Post by heiowge on 2008-07-17
Jim - It did nothing about the problem.  sorry.

hyper_ch - unsure about doing this.  What are the risks?

---

### Post by hyper_ch on 2008-07-17
something could get uninstalled

---

### Post by heiowge on 2008-07-17
Ok, did it.  It did not do anything noticable.  Sorry.

---

### Post by heiowge on 2008-07-18
bump

---

### Post by Jim! on 2008-07-18
Do you have the repositories enabled? (System>Admin>Software Sources)

---

### Post by heiowge on 2008-07-19
on ubuntu software, everything but source code.
On third party, only the unsupported and unsupported source
on updates, important and recommended

Are active

Is this ok?

---

### Post by heiowge on 2008-07-21
bump

---

### Post by heiowge on 2008-07-23
double bump

---

### Post by plucky on 2008-07-23
Open a terminal and post output of ```
cat /etc/apt/sources.list
```


The reason is you have in post #3 both Gutsy and Hardy repositories enabled.Not a good idea.

If you are on Hardy,comment out the Gutsy repositories or vice versa.

Then ```
sudo apt-get update
sudo apt-get upgrade
```

Good Luck

p.s Please use the [noparse]```

```[/noparse] brackets when posting large outputs(It is easier to read).See BBcode List in my signature.

---

### Post by heiowge on 2008-07-23
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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

---

### Post by sharks on 2008-07-23
forcing the update is the only way i think. it may work or break ur packages.

---

### Post by sharks on 2008-07-23
do u use gutsy or hardy?

---

### Post by sharks on 2008-07-23
bcoz there is both gutsy and hardy repos.

---

### Post by heiowge on 2008-07-23
Thanks to Plucky!  Removing the Gutsy repos cured it.

Sharks - I use Hardy.  Guess there are still some residual repos there from before the upgrade.

---

### Post by sharks on 2008-07-23
there are some gutsy repos. remove it using:

sudo gedit /etc/apt/sources.list

---

### Post by sharks on 2008-07-23
please mark the thread solved from thread tools.

---

### Post by heiowge on 2008-07-23
Ok.  will do.  used gedit to remove them already cheers.

---

