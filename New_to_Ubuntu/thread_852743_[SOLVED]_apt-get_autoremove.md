---
title: "[SOLVED] apt-get autoremove"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-07
The following packages were automatically installed and are no longer required:
  linux-backports-modules-2.6.22-14-generic
Use 'apt-get autoremove' to remove them.


am I suposed to do this everytime or periodically.  I just type that and enter it in?  I just noticed it.  Am I overdue for a good apt-get autoremove?

---

### Post by BGFG on 2008-07-07
Yup basically, you can do this every now and then to properly get rid of packages your system isn't using anymore. It's up to you how often you use it.

```
sudo apt-get autoremove
```

---

### Post by neurostu on 2008-07-07
Apt will let you you know when you need to run autoremove...  you only need to run it when apt tells you to... again need isn't the correct word.  You can have packages that aren't being used and it won't cause any problems at all (most of these packages are libraries). Its not like the windows registry that gets bloated and slows down your machine.

---

### Post by kansasnoob on 2008-07-07
Make sure your software sources are set correctly:

[ATTACH]76851[/ATTACH]

[ATTACH]76852[/ATTACH]

[ATTACH]76853[/ATTACH]

Nevermind the Medibuntu repo for now.

---

### Post by unutbu on 2008-07-07
adamogardner, I recommend that you look over all the packages before you autoremove them. Some times when users use both apt-get (or its brethren Synaptic or Adept) and also aptitude (not its brethren), apt-get can get confused about what packages are installed on the system and mistakenly mark packages for removable.

See [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=842399&highlight=dpkg](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=842399&highlight=dpkg)
for an example of the potential hazard.

---

### Post by adamogardner on 2008-07-08
in my third party software tab in software sources is quite different than the picture.  It's all gutsy stuff but I am using hardy.  Go figure.

where can I review these packages before deletion?  Am i supposed to know what the backport modules are?

---

### Post by unutbu on 2008-07-08
adamogardner, your last message sheds a lot of light on the situation. You are using Hardy. linux-backports-modules-2.6.22-14-generic is a Gutsy package. It is therefore not only safe to remove, it is advisable. I don't think it is generally a good idea to have Gutsy packages installed on a Hardy system. (It could make the system unstable).

If your third-party software tab is showing gutsy repositories instead of hardy ones, then your /etc/apt/sources.list has some incorrect lines in it. It needs to be fixed.
Please open a terminal and post the output to

```
cat /etc/apt/sources.list
```

---

### Post by adamogardner on 2008-07-08
below is the output you requested.  So should I simply "sudo apt-get autoremove?"  or wait for you?  If there is any chance of me screwing everything up then I would rather take my time and wait for counsel. 

adamogardner@CRONUS:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by len1x on 2008-07-08
how did you end up with that sources.list if you're using hardy -,-

---

### Post by adamogardner on 2008-07-08
I started with gutsy.  My friend helped me switch to Hardy. Neither one of us knows what we arre doing.

---

### Post by unutbu on 2008-07-08
Quit Synaptic.
Save a backup copy of your current sources.list, just in case:

```
cd /etc/apt
sudo mv sources.list sources.list-20080708
```

Now make a new sources.list
```

gksu gedit /etc/apt/sources.list
```

Paste this into the file:
```
deb http://archive.ubuntu.com/ubuntu hardy universe multiverse restricted main
deb-src http://archive.ubuntu.com/ubuntu hardy universe multiverse restricted main 

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse

## Updates.
deb http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## Security
deb http://security.ubuntu.com/ubuntu hardy-security universe main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security universe main multiverse restricted

## Backports
deb http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Canonical Partner Repository 

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu hardy partner
#deb-src http://archive.canonical.com/ubuntu hardy partner
```

Save and Quit gedit.

Now update your apt system so it knows about the new repository setup:

```
sudo apt-get update
```

Post if there are any errors. 

Just to be extra cautious, before you remove 
linux-backports-modules-2.6.22-14-generic
please post the output of 

```
dpkg --get-selections | grep ^linux
```

---

### Post by adamogardner on 2008-07-08
here is that output.   What is gksu?

ner@CRONUS:~$ dpkg --get-selections | grep ^linux
linux-backports-modules-2.6.22-14-generic	install
linux-generic					install
linux-headers-2.6.24-18				install
linux-headers-2.6.24-18-generic			install
linux-headers-2.6.24-19				install
linux-headers-2.6.24-19-generic			install
linux-headers-generic				install
linux-image-2.6.22-14-generic			install
linux-image-2.6.24-18-generic			install
linux-image-2.6.24-19-generic			install
linux-image-generic				install
linux-libc-dev					install
linux-restricted-modules-2.6.22-14-generic	install
linux-restricted-modules-2.6.24-18-generic	install
linux-restricted-modules-2.6.24-19-generic	install
linux-restricted-modules-common			install
linux-restricted-modules-generic		install
linux-sound-base				install
linux-ubuntu-modules-2.6.22-14-generic		install
linux-ubuntu-modules-2.6.24-18-generic		install
linux-ubuntu-modules-2.6.24-19-generic		install

---

### Post by unutbu on 2008-07-08
Type

```
sudo apt-get -s autoremove
```

The '-s' flag means 'simulate'.
This will simulate the autoremove operation, though no actual packages will be removed.

It should be safe to remove all version 2.6.22-14 packages because those were for Gutsy and you have 2.6.24-18 and -19 versions installed.

You can research the packages apt-get wants to autoremove by typing
```

apt-cache show PACKAGE
```

(or click on the package in Synaptic, and a description will appear in the lower-right panel).

When you are satisfied that all packages scheduled for autoremoval should be removed, type
```

sudo apt-get autoremove
```

gksu gives you superuser privileges while running a graphical app. 
Use sudo for terminal commands, use gksu for graphical apps.
Using sudo instead of gksu when launching a graphical app can on some rare occasions cause certain files in your home directory to be overwritten by root's. This causes the user problems. So to avoid problems, it's best to use gksu for graphical apps.

---

### Post by adamogardner on 2008-07-08
unutbu, I am very grateful for your help.  I learned a lot and had a fun time doing it because you have a very clear way of explaining things.

---

