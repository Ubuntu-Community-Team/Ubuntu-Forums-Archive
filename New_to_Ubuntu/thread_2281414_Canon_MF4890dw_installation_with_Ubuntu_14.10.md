---
title: "Canon MF4890dw installation with Ubuntu 14.10"
date: 2015-06-06
forum: New to Ubuntu
---

### Post by michel18 on 2015-06-06
**My problem**

I've used the information given by [[COLOR=#000000]martin.danjou14[/COLOR]]("http://ubuntuforums.org/member.php?u=1895858") in [http://ubuntuforums.org/showthread.php?t=2197588](http://ubuntuforums.org/showthread.php?t=2197588) in order to install
a Canon MF4890dw printer with on my newly installed Ubuntu 14.10, but it didn't work. As the thread is now closed, I have no
other choice than opening a new one.

**What I've done**

After downloading the package from Canon website, I've entered the following commands:

sudo apt-get install libglib2.0-dev
sudo apt-get install automake
sudo apt-get install libtool-bin
sudo apt-get install libgtk2.0-dev
sudo apt-get install libglade2-dev

unzip o147mfr_linuxfrII-0290

cd francais
cd Sources
cp cndrvcups-common-2.90-1.tar.gz cndrvcups-common_2.90.orig.tar.gz

tar -xf cndrvcups-common-2.90-1.tar.gz
cd cndrvcups-common-2.90

dpkg-buildpackage -us -uc[h=2][FONT=Liberation Mono, monospace][SIZE=2]At this point, the gcc compiler didn't find the include file <cups/cups.h> when compiling the c file « printerinfo.c » located in the directory  "cndrvcups-common-2.[/SIZE][/FONT][FONT=Liberation Mono, monospace][SIZE=2]9[/SIZE][/FONT][FONT=Liberation Mono, monospace][SIZE=2]0/[/SIZE][/FONT][FONT=Liberation Mono, monospace][SIZE=2]cngplp/src"[/SIZE][/FONT][/h] [FONT=Liberation Mono, monospace][SIZE=2](The following commands should come next :[/SIZE][/FONT]

cd ..
cp cndrvcups-lb-2.90-1.tar.gz cndrvcups-lb_2.90.orig.tar.gz
tar xf cndrvcups-lb-2.70-1.tar.gz
cd cndrvcups-lb-2.70 
dh_shlibdeps --dpkg-shlibdeps-params=--ignore-missing-info
dpkg-buildpackage -us -uc
cd ..)


I've tried to uninstall the cups package and to install it again, but it doesn't help and I'm somehow lost.

Can anyone give me a hint in order to solve the problem?

Thank you in advance

Michel

---

### Post by pdc on 2015-06-08
Hi Michel; bienvenu to the ubuntu forums;

that's a very nice printer you have there; so it uses Canon's UFR driver and you can get that from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html) and if you click to download and save, it ends up in your Downloads folder and you will be downloading Linux_UFRII_PrinterDriver_V300_uk_EN.tar.gz

_______________

This is the version 3.0 driver; it was issued only 6 days ago; Canon have updated it; I am concerned about the > I've tried to uninstall the cups package and to install it again, but it doesn't help and I'm somehow lost. so I hope you have restored what was there before: 

_____________

can you please tell us which of the 32bit or 64bit options you have;

from there, I can give you a series of steps to follow to install Canon's driver;

_________________

I have downloaded this new, version 3 of the driver to look at it; Canon now include an install script; so one just has to run that; (and install a couple of extra libraries)

---

### Post by michel18 on 2015-06-08
Hi pdc, and thank you for giving me some hints.

I have a 32bit option installed. I'm waiting for your advice.

Michel

---

### Post by michel18 on 2015-06-08
Hi pdc, it's me again. 

I managed to install the driver with the following command given in the directory "Linux_UFRII_PrinterDriver_V300_uk_EN/Sources":

sudo ./install.sh

I just have to find out how to get the scanner function of my printer working ... Do you have a hint on this?

Many thanks for your help.

Michel

---

### Post by pdc on 2015-06-09
magnificent!

 if you go to post #2 here [http://forums.linuxmint.com/viewtopic.php?f=51&t=194081&p=1006693&hilit=rolf+bensch#p1006693](http://forums.linuxmint.com/viewtopic.php?f=51&t=194081&p=1006693&hilit=rolf+bensch#p1006693)

...... it tells you how to add the latest sane version; it supports the 4800series so your device should be included in that; please ask if you need guidance with how to use Rolf's ppa;

---

