---
title: "Unable to install wine1.7 through terminal on chrubuntu toshiba chromebook 14.10"
date: 2014-11-18
forum: New to Ubuntu
---

### Post by jopax035 on 2014-11-18
funny_chinx@funny_chinx:~$ sudo apt-get install wine1.7 winetricks
sudo: unable to resolve host funny_chinx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 wine1.7 : Depends: wine1.7-i386 (= 1:1.7.31-0ubuntu1~ppa1) but it is not installable
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: ttf-wqy-microhei
E: Unable to correct problems, you have held broken packages.

---

### Post by sffvba[e0rt on 2014-11-19
*Thread moved to **New to Ubuntu**.*

Have you tried specifying only **wine **and not **wine1.7**? - sudo apt-get install **wine** winetricks

(I am also wondering about *sudo: unable to resolve host funny_chinx* seems odd).

---

