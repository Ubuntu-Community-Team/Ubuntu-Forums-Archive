---
title: "Need help new user"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by bulldog014 on 2008-05-01
hello I'm a brand new user and I love the concept and love the way this os works how ever it has lived up to what I have heard about it and that it is it is a pain to get drivers going.  I'm a soldier currently deployed and I have a horrible internet connection, but I have a compaq presario 2570us with a broadcom 4306 802.11 b/g wireless card that I have looked in the forums for help and have tried at least 4 different sets of directions, my problem is I can see my card but i cannot turn it on, and I'm pretty sure I dont have the drivers installed I have tried to install ndiswrapper and wine, and have also made sure that fwcutter is active and still i cannot get the driver that I have on a thumb drive to install.  Help please I would love to can my windows depency but I need my wireless card to work before I do that, thank you ahead of time for your help

---

### Post by stalkingwolf on 2008-05-01
What version are you using?  7.04? 7.10?

---

### Post by sailor2001 on 2008-05-01
see if this works:  > I used the following steps to enable my Broadcom Wireless BCM4312 (rev 02).

Step 1 (run in terminal)

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx

For Step 2, if your wireless device is different from BCM4312, please refer to the following link for this step and you can continue again with step 3 onwards:

[https://help.ubuntu.com/community/Wi...f971ca757b2851](https://help.ubuntu.com/community/Wi...f971ca757b2851)

Step 2 (run in terminal)

sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe](ftp://ftp.compaq.com/pub/softpaq/sp3...00/sp34152.exe)
cabextract sp34152.exe

Step 3 (run in terminal)

sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Step 4 (run in terminal)

sudo aptitude remove b43-fwcutter

Step 5 (run in terminal)

sudo gedit /etc/init.d/wirelessfix.sh

Step 6

Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

Step 7 (run in terminal)

Run this :

cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

Step 8 (run in terminal)

finally run this:

sudo update-rc.d wirelessfix.sh defaults

Step 9

Restart your machine and enjoy the freedom from those wires....


---

### Post by bulldog014 on 2008-05-01
thank you for the help and will this work with the latest version as well? I'm running 8.04

---

