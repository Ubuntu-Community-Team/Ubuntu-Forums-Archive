---
title: "Driver issue I guess?!"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by adiazrael on 2008-07-20
Hey guys,
I am beginer the Ubuntu and Linux in general....
I haven't done much on Windows command promt neither...so beginer to everthing....
Ok, here is my issue..
I have installed Ubuntu on HP dv6205us with Vista and couldn't get wireless to work...than I tryed the Live CD option but it still didn't work...It prompted me with ERROR: Firmware file "b43/ucode5.fw" not found ...go to [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) to download lates firmware
I did folow the link and used the "b43 driver from linux-2.6.25 or compat-wireless-2.6" option and tryed to follow the steps, but I couldn't get it to work I tryed to play around in Terminal to get these commands to work but no success....
If anyone has any idea how can I install this driver....I like Ubuntu allready but no wireless internet....

---

### Post by Dark_Stang on 2008-07-20
Post the output of "lspci" for us. To do this type "lspci" in a terminal (without the quote marks) and just copy and paste it. This way we can see what wireless card you have and can go from there.

---

### Post by adiazrael on 2008-07-20
Ok here it is....

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
05:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
05:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
05:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by Dark_Stang on 2008-07-20
You have the same wireless card as I do. Click the link in my sig for the hp dv6636nr and follow the directions for the wireless card. You'll be up and going within a few minutes.

---

### Post by adiazrael on 2008-07-20
Update....
I have followed you code from the link and it seams that this portion did not work:
 
ubuntu@ubuntu:~$ cd
ubuntu@ubuntu:~$ ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ cd Documents
ubuntu@ubuntu:~/Documents$ cd
ubuntu@ubuntu:~$ ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos
ubuntu@ubuntu:~$ cd Documents
ubuntu@ubuntu:~/Documents$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found
ubuntu@ubuntu:~/Documents$ sudo ndiswrapper -i bcmwl5.inf
sudo: ndiswrapper: command not found

I have extracted the files in folder documents....
Than I thought ok maybe I need to install this on my HD before it works but I think there is something not cooparating with my HD. When I get to "prepare disk space" I have only these options 
Guided - use entire disk

---

### Post by adiazrael on 2008-07-20
..sorry didn't finish...
so I have only
*Guided - use entire disk
____ *SCSI1 (0,0,0) (sda) - 80.0 GB ATA Hitachi HTS54168
*Manual
I tried manual but I have no option of creating a new partition, just editing the ones that I have

Also for some reason when I was running a LIVE CD option I was not able to access my HD, I could see it but not access it.
I have about 6GB for my Vista and it is mostly used and I was going to create a 6GB for Ubuntu also...
Please help!!!

---

### Post by matt17y on 2008-07-20
I have had similiar broadcom trouble too.  You will need to install ubuntu to your hard drive first, and then install ndiswrapper-utils from the repository.  Then the above tutorial should work.

---

### Post by adiazrael on 2008-07-20
But my ubuntu doesn't "see" my HD i can't partion it to install :confused:

---

### Post by matt17y on 2008-07-20
Hmm.  Strange.. Ive never had that problem before..  when you click on manual, you said it shows the partitions but it doesn't allow you to create a new one..   Maybe you need to resize a current partition first.  It could be that if you have vista installed it has already utilized the entire disk for itself.  There should be an option when clicking manual to resize an existing partition.. but i have always heard that it is best defrag windows first before attempting this.

---

### Post by Flyingjester on 2008-07-20
what they are saying is correct, the steps to get your wireless working will only work after it is installed.

---

### Post by adiazrael on 2008-07-20
I have about 6GB for HP recovery and about 28GB of free space on the rest of the HD...

---

### Post by adiazrael on 2008-07-20
Ok...now for some reason I can see my HD and my files when I use the LIVE CD option...but when I start to install still the same...

---

### Post by Dark_Stang on 2008-07-20
There are some new intel motherboards that have issues with kernels before 2.6.25. Try installing it through Windows with Wubi. Or try the testing version of Ubuntu. Use the testing version of Ubuntu at your own risk.

Link to intrepid (testing/unstable version of ubuntu)
[http://fridge.ubuntu.com/node/1587](http://fridge.ubuntu.com/node/1587)

---

### Post by adiazrael on 2008-07-20
I used Wubi to install Ubuntu but still have the wireless issue and I followed the steps but when I search for ndiswrapper it is not there! 
this is so frustrating :mad::mad:

---

### Post by Dark_Stang on 2008-07-20
ndiswrapper should be able to be installed through synaptic. System > Administration > Synaptic Package Manager.

---

