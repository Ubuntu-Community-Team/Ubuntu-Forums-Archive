---
title: "Webcams in Dreamlinux 3"
date: 2008-08-22
forum: Other OS Talk
---

### Post by luvinit on 2008-08-22
I am attempting to get my webcam that works perfectly in Ubuntu to work in Dreamlinux. Nobody on the Dreamlinux has any suggestions about how to make it work,therefore I was curious if any of the Ubuntu crowd might know. Dreamlinux is Debian based and looking through synaptic on one is much the same as another. This situation is quite unusual as this is the first GNU/linux distribution that I have tried where webcam recognition and function isn't automatic. Ubuntu remains on my main PC but I am trying out leaner faster distributions for an old PC, and dream both install and runs very noticibly quicker. Appreciate any help.

---

### Post by lswest on 2008-08-22
We'll need some more information before being able to help you.  Can you post the output of ```
lsusb
uname -r
``` and as much information as you can provide about the webcam, and what (if anything) you've done to try to get the cam working.

---

### Post by luvinit on 2008-08-22
Hi, thanks for the response. The webcam is a Typhoon Webshot 2. The output of those commands is as follows

mark@DL:~$ lsusb
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc. 
Bus 001 Device 002: ID 10fd:8050 Anubis Electronics, Ltd FlyCAM-USB 300 XP2
Bus 001 Device 001: ID 0000:0000  
mark@DL:~$ uname -r
2.6.23.12-dream
mark@DL:~$ 


I have tried just about all of the webcam drivers which are in synpatic, none have any effect, which isn't surprising because they are not necessary in Ubuntu, which implies that none of them are essential. I have Gspca-source and gspca-modules installed.

---

### Post by lswest on 2008-08-22
according to [this site]("http://mxhaard.free.fr/spca5xx.html") the driver you need is the spca5xx driver.  I do not know if dreamlinux has it available, but a bit of googling might find it for you.  Also, try modprobing the driver from dreamlinux, it might be there, but just not in use.

```
sudo modprobe spca5xx
``` should get it up and running if the driver is there.  If it works, add spca5xx to /etc/modules.  That's the best advice I can give you.

---

### Post by luvinit on 2008-08-23
Vielen dank, ich werde modprobe ausprobieren. Tchuess, ich wuensche Ihnen ein schoenes wochenende. :)

---

### Post by loell on 2008-08-23
dreamlinux is based on debian,surely they have spca5xx.

---

### Post by luvinit on 2008-08-23
Yes, as far as I am aware, the multitude of packages that I installed from synaptic includes the the spca5xx driver, but I don't think that can be the solution because the same packages are not necessary in Ubuntu, which implies to me that they are non essential in order to get it working.

---

### Post by luvinit on 2008-08-23
Ok I tried following this


but with gspca-source because spca5xx-source doesn't exist in the repositories.

[http://wiki.debian.org/USBWebCam](http://wiki.debian.org/USBWebCam)

here is what I get

Updated infos about 1 packages
Getting source for kernel version: 2.6.23.12-dream
Kernel headers available in /usr/src/linux-headers-2.6.23.12-dream
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 342 not upgraded.

Done!
unpack 
Extracting the package tarball, /usr/src/gspca.tar.bz2, please wait...
Target package file 
/usr/src/gspca-modules-2.6.23.12-dream_01.00.20-1+6_i386.deb already exists, 
not rebuilding!
(however, you could use the -f switch to ignore it)
dpkg -Ei /usr/src/gspca-modules-2.6.23.12-dream_01.00.20-1+6_i386.deb 
Selecting previously deselected package gspca-modules-2.6.23.12-dream.
(Reading database ... 90318 files and directories currently installed.)
Unpacking gspca-modules-2.6.23.12-dream (from .../gspca-modules-2.6.23.12-dream_01.00.20-1+6_i386.deb) ...
dpkg: dependency problems prevent configuration of gspca-modules-2.6.23.12-dream:
 gspca-modules-2.6.23.12-dream depends on linux-image-2.6.23.12-dream | kernel-image-2.6.23.12-dream; however:
  Package linux-image-2.6.23.12-dream is not installed.
  Package kernel-image-2.6.23.12-dream is not installed.
dpkg: error processing gspca-modules-2.6.23.12-dream (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gspca-modules-2.6.23.12-dream

I: Direct installation failed, trying to post-install the dependencies

apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  gspca-modules-2.6.23.12-dream
0 upgraded, 0 newly installed, 1 to remove and 342 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 434kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 90322 files and directories currently installed.)
Removing gspca-modules-2.6.23.12-dream ...


I'm gonna give up now, it isn't worth the trouble, but thanks for all help.

---

### Post by lswest on 2008-08-24
actually, running ```
sudo apt-get install linux-image-2.6.23.12-dream kernel-image-2.6.23.12-dream gspca-modules-2.6.23.12-dream
``` should give you what you need.  The error states that the two missing files are causing the install to fail, so if you install it it should be fine.  (Looks like it's trying to compile something, and for that it needs the above files).

Nice German btw :P

Ich wünsche ihnen einen schönen Tag, und viel erfolg!
Lswest

---

