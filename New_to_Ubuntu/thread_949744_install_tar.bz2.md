---
title: "install tar.bz2"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by DarinB on 2008-10-16
i downloaded an app to convert .mov to m4v to paly on my ipod video
it comes as a tar.bz2 when i extract it the type ./configure it says no file found...i must be missing a step somehow. i followed th e procedure from a youtube. i extracted the file then i opened a terminal cd to desktop then to exctracted file then ./configure ... no file found. 
what do i need to do i must be missing a step since i can't do this with tar gz files either same response no file found or make file not found when i get to the make part. is it a permission thing??? o ram i doing something fundamentally wrong.

---

### Post by nothingspecial on 2008-10-16
You need to cd into the file

---

### Post by nothingspecial on 2008-10-16
> **DarinB said:**
>  i extracted the file then i opened a terminal cd to desktop then to exctracted file 

Sorry, just read your post properley. What is is you are trying to install?

---

### Post by philinux on 2008-10-16
cd Desktop then
cd to folder. Use the tab key to autocomplete.

Then ./configure

---

### Post by DarinB on 2008-10-16
darin@darin-desktop:~$ cd Desktop/
darin@darin-desktop:~/Desktop$ cd thinliquidfilm/
darin@darin-desktop:~/Desktop/thinliquidfilm$ ls
add.png         manual.png     StuffIt Expander.png
getFileInfo.py  preview.png    thinliquidfilm.desktop
install.py      quit.png       thinliquidfilm.py
invert.png      README.txt     timeConvert.py
ipod_mount.png  remove.png     uploadFileInfo.py
main.py         selectall.png
darin@darin-desktop:~/Desktop/thinliquidfilm$ ./configure
bash: ./configure: No such file or directory
darin@darin-desktop:~/Desktop/thinliquidfilm$ 


what am i doing wrong????

---

### Post by stoneage on 2008-10-16
Just a guess, but from the file list it looks like you need to run the install.py file.

Try ```
sudo ./install.py
```

---

### Post by oldos2er on 2008-10-16
Read the README. It looks like you've got python code, not source code. Try running "python install.py"

---

### Post by DarinB on 2008-10-16
i did the sudo install.py this is what i got??
Checking dependencies ...
-------------------------

Couldn't find pyqt.  thin liquid film will not work without pyqt.  Aborting installation.
darin@darin-desktop:~/Desktop/thinliquidfilm$ 
where do i find the dependency it is not in synaptic??

---

### Post by nothingspecial on 2008-10-17
Try this

```
sudo apt-get install python-qt4
```

---

### Post by DarinB on 2008-10-17
darin@darin-desktop:~$ sudo apt-get install python-qt4
[sudo] password for darin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-qt4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package python-qt4 has no installation candidate
darin@darin-desktop:~$ 
i am not sure what to do?

---

### Post by nothingspecial on 2008-10-17
I have python-qt4 available. If you post the results of ```
cat /etc/apt/sources.list
```  I can tell you what to enable and hopefully you can install pyqt and thinliquidfilm.

---

### Post by DarinB on 2008-10-17
**_here is the post its pretty long_**

darin@darin-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
# Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/
darin@darin-desktop:~$

---

