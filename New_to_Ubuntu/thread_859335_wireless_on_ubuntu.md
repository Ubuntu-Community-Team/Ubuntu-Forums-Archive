---
title: "wireless on ubuntu"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by papermoon on 2008-07-14
Ok so I want to know how to set up wireless on ubuntu. I am using one of those USB wireless cards. it is a 208.11g and it is working fine in XP but i have no idea how to set it up in ubuntu. Can i use the same utility program in ubuntu? (using wine?)

---

### Post by Het Irv on 2008-07-14
What make/model do you have?  Can you paste the output of ```
lsusb
```

---

### Post by LowSky on 2008-07-14
you shouldn't need the utility.

first what brand  is the wireless card?

second look for the network icon on the top right. click on it and see if it shows an option for wireless

---

### Post by quantumstitch on 2008-07-14
I would try to set this up natively. Have a look at [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide) to get started.

---

### Post by jbrown96 on 2008-07-14
Wine won't work. What type of card is it? It will probably work, but it really depends on the model and chipset.

---

### Post by OffAxis on 2008-07-14
USB (including wireless cards) are usually plug and play.

you'll probably want to start here:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

then maybe here:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

or here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and finally here:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by appi2012 on 2008-07-14
you need ndiswrapper, which runs your windows drivers in ubuntu.

Do you have a wired connection?

If yes:

connect, and type in a terminal:

```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
```

If no:

insert a ubuntu cd and type in a terminal:
```
sudo apt-get install ndiswrapper-common ndiswrapper-modules-1.9 ndiswrapper-utils-1.9
```

After installing:

insert your driver cd
find the all the sys files the inf file that are for your driver, and copy them to a folder in your home folder.

then type in a terminal:
```
cd [name of the folder you copied the files to]
```
```
ndiswrapper -l
```
this should list nothing.
type:
```
sudo ndiswrapper -i [name of the inf file].inf 
```
```
ndiswrapper -l
```
now it should say:
```
device present
driver installed
``` or something similar.

now type:
```
sudo ndiswrapper -m
```
```
sudo modprobe ndiswrapper
```
That should set up your wireless!
hope that helps

---

### Post by Frenske on 2008-07-14
Could you give us a bit more information? Hardy Heron supports a lot of wireless cards and drivers. Are you using Ubuntu 8.04?
It is not clear whether you have tried to connect to the internet by just plug and play!!!

---

