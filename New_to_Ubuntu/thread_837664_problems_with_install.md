---
title: "problems with install"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by huntis619 on 2008-06-22
Hi all. I have ubuntu on my laptop a hp zv5410us.I installed ubuntu 7.10 in December 2007. I was enjoying the linux experience. With the help of other members on this site I was up and fully functional in 3 days. Then I received a update notice for ubuntu 8.04. I did the update and I have been having problems ever since Right now I need to know how to uninstall/remove ubuntu. Right now I have 2 versions of ubuntu 7.10 and 2 versions of ubuntu 8.04 on my hard drive.Can someone please help me.

---

### Post by Ub1476 on 2008-06-22
Post the output of the command below to see what partitions you have on your HDD:

```
sudo fdisk -l
```

Eventuelly, you can install gparted, which you can create, delete and edit partitions with. It's better to check here if you're unsure though.

---

### Post by tjwoosta on 2008-06-22
well... 

if what you want to do is just completely delete partitions, then you can do that with gparted **from the ubuntu live cd** (just go to System-Administration-Partition Editor)

> [QUOTE]Eventuelly, you can install gparted, which you can create, delete and edit partitions with. It's better to check here if you're unsure though.[/QUOTE]

if you were to install gparted on your harddisk it becomes practically useless because you cant edit the partition that gparted is stored on (which is why you just have to use a live cd or flash drive)

---

### Post by Biggy on 2008-06-22
download [PartedMagic]("http://exo.enarel.eu/mirror/partedmagic/pmagic-2.2.iso") to create,edit delete partitions.
for more info se [PartedMagic Home]("http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.UsingGParted")

---

### Post by huntis619 on 2008-06-22
ok I'll try it and get back to you.

---

### Post by trucker33377 on 2008-06-22
sounds like you just updated not repartitioned your drives am i right?

---

### Post by huntis619 on 2008-06-22
Thank you all for your advice. I have removed all versions of ubuntu and installed a clean install of ubuntu 8.04. Now I have a another problem/question. When I tried to install the restricted drivers for my hardware.it states that my wireless driver is in use but the enabled box isn't checked. When I restated the computer it states there was an error with the firmware update.Do I use the same commands that I used for ubuntu 7.10 to set up my wireless connection for 8.04

---

### Post by DGortze380 on 2008-06-22
> **huntis619 said:**
> Thank you all for your advice. I have removed all versions of ubuntu and installed a clean install of ubuntu 8.04. Now I have a another problem/question. When I tried to install the restricted drivers for my hardware.it states that my wireless driver is in use but the enabled box isn't checked. When I restated the computer it states there was an error with the firmware update.Do I use the same commands that I used for ubuntu 7.10 to set up my wireless connection for 8.04

to disable your wireless try the following. (Commands in quotes)
"ifconfig" (check to see which device is being used for your wireless
"sudo ifdown ath0" (replace ath0 with your device name)

Now update and restart.

---

### Post by Biggy on 2008-06-22
go System > Administration > Software Sources 

check all options in first tab ( Ubuntu Software ) 

close reload

go to System > Administration > Update Manager

pres check and install updates

---

### Post by huntis619 on 2008-06-22
I did all of my updates when I installed ubuntu 8.04. DGortze380, Ill try the commands but can you tell how I find the name of my wireless card again.Also no one answered my question. Can I use the same commands that I used to set up my wireless internet connection for ubuntu 7.10 for ubuntu 8.04.

---

### Post by DGortze380 on 2008-06-22
type "ifconfig" into a terminal. It will show all your network interfaces. your wireless should be either wifi or ath depending on your driver. (if youre not sure, copy and paste the contents of the file here).

You can try the same commands as 7.10. No guarantees, could work, could do nothing, could break stuff.

---

### Post by huntis619 on 2008-06-22
ok I'll try it and let you know what happens.

---

### Post by huntis619 on 2008-06-22
ifconfig didn't show my wireless card.Under my hardware drivers the broadcom B43 wireless card is in use but not enabled. I check the enabled box and restarted computer. When I checked the drivers again, it was the same.

---

### Post by DGortze380 on 2008-06-22
Sorry then, not much more I can help with, not familiar with the card. Anyone else?

---

### Post by huntis619 on 2008-06-22
~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
steven@steven-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@steven-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/steven/bcm43xx': File exists
steven@steven-laptop:~/bcm43xx$ 
steven@steven-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@steven-laptop:~/bcm43xx$ wget [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
--21:33:16--  [ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe.1'
Resolving ftp.hp.com... 15.200.30.24, 15.200.30.22
Connecting to ftp.hp.com|15.200.30.24|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656    389.08K/s    ETA 00:00

21:33:23 (763.39 KB/s) - `sp33008.exe.1' saved [4318656]

steven@steven-laptop:~/bcm43xx$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
steven@steven-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
steven@steven-laptop:~/bcm43xx$ sudo ndiswrapper -i bcmwl5.inf
driver bcmwl5 is already installed
steven@steven-laptop:~/bcm43xx$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)
steven@steven-laptop:~/bcm43xx$ sudo depmod -a
steven@steven-laptop:~/bcm43xx$ sudo modprobe ndiswrapper
steven@steven-laptop:~/bcm43xx$ sudo cp /etc/network/interfaces /etc/network/interfaces.orig
steven@steven-laptop:~/bcm43xx$ echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
auto lo
iface lo inet loopback

steven@steven-laptop:~/bcm43xx$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

steven@steven-laptop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
steven@steven-laptop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
steven@steven-laptop:~/bcm43xx$

---

