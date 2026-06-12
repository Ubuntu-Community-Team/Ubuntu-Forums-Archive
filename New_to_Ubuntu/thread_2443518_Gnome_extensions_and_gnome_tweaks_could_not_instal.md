---
title: "Gnome extensions and gnome tweaks could not install"
date: 2020-05-16
forum: New to Ubuntu
---

### Post by dimitargeorgiev5 on 2020-05-16
Hello,

I am new to ubuntu, and i have beew following this thread [https://itsfoss.com/things-to-do-after-installing-ubuntu-18-04/](https://itsfoss.com/things-to-do-after-installing-ubuntu-18-04/) i tried installing Gnome Tweaks, and i am not able to, the Software center says that the following packages have unmet dependencies. I tried installing gnome extensions and i have the same answer... I would appreciate some help. Thanks

The following packages have unmet dependencies:
 gnome-tweak-tool : Depends: gnome-tweaks but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by CelticWarrior on 2020-05-16
Please run 'sudo apt update' in terminal and post the full error messages.

---

### Post by dimitargeorgiev5 on 2020-05-16
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Get:3 [https://mega.nz/linux/MEGAsync/xUbuntu_20.04](https://mega.nz/linux/MEGAsync/xUbuntu_20.04) ./ InRelease [2441 B]
Fetched 2441 B in 1s (3727 B/s)    
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.

---

### Post by CelticWarrior on 2020-05-16
So far so good... But I wonder if that's all. You may not have all the usual repositories selected. That can be checked easily in Software & Updates. Make sure "main", "universe", "restricted" and "multiverse" are enabled. Then fully update the system by running 'sudo apt full-upgrade'. Then, if no errors, try again to install the software you want.

---

