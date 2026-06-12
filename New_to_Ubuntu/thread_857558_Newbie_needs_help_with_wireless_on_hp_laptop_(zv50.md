---
title: "Newbie needs help with wireless on hp laptop (zv5000)"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by huntis619 on 2008-07-12
Hi all. I've been trying to get wireless on my laptop since I upgraded from 7.10 to 8.04 (April 08). Every time I come to the forum site someone is directing me to the "Broadcom Wireless Setup for Hardy" guide by alex_kent_18. I see that a lot of people have had sucess with this guide but I haven't. I don't know if I'm doing something wrong or what. In step 2 of the guide which one do I use, I have a Broadcom BCM4306 (rev 03) wireless card. Also I need someone to explain the guide to me (especially steps 5 - 8) as if I we're a 5th grader. I will do the guide again and post my results. In the meantime here is some basic info about my hardware. Please I hope someone is able to help me, I've been on this 100 ft. ethernet cable far to long.

lspci
00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)

---

### Post by TSS on 2008-07-12
Broadcom cards are a real pain, I have one myself.

This guide has always worked for me: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by huntis619 on 2008-07-12
Before I read the guide you posted, here is the results from the above mentioned guide. I'm about to restart my computer (final step; step 9) and I let you know what happens.

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
steven@steven-laptop:~$ sudo apt-get install ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@steven-laptop:~$ mkdir ~/bcm43xx; cd ~/bcm43xx
mkdir: cannot create directory `/home/steven/bcm43xx': File exists
steven@steven-laptop:~/bcm43xx$ sudo apt-get install cabextract
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cabextract is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steven@steven-laptop:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
--16:37:18--  [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe.6'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.

    [               <=>                   ] 4,318,656      1.42M/s             

16:37:21 (1.41 MB/s) - `sp33008.exe.6' saved [4318656]

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
module configuration already contains alias directive

steven@steven-laptop:~/bcm43xx$ echo 'ndiswrapper' | sudo tee -a /etc/modules
ndiswrapper
steven@steven-laptop:~/bcm43xx$ echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
ENABLED=0
steven@steven-laptop:~/bcm43xx$ sudo aptitude remove b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  b43-fwcutter 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 102kB will be freed.
Writing extended state information... Done
(Reading database ... 113965 files and directories currently installed.)
Removing b43-fwcutter ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
steven@steven-laptop:~/bcm43xx$ sudo gedit /etc/init.d/wirelessfix.sh
steven@steven-laptop:~/bcm43xx$ cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
steven@steven-laptop:/etc/init.d$ sudo update-rc.d wirelessfix.sh defaults 
 System startup links for /etc/init.d/wirelessfix.sh already exist.
steven@steven-laptop:/etc/init.d$

---

### Post by huntis619 on 2008-07-12
Still no response. I guess no one KNOWS how to help with my problem.

---

### Post by TSS on 2008-07-12
Sorry, I can't quite tell from your previous posts.  Did you try to follow the guide I gave you?  If you look at the tesimonials section, people have gotten your wireless card to work using that guide.

---

### Post by anewguy on 2008-07-12
The very first thing I do every time I set up a connection using ndiswrapper is to be sure I start at a "clean slate" with ndiswrapper.  So,
what I would do is:

sudo ndiswrapper -l

for every entry returned above:

sudo ndiswrapper -e xxxxxxx <- where xxxxxxx is the name returned from the list command.

repeat this until you have an empty list.  This will have cleaned all the drivers (or in some case, bad files one thought was a driver) out of ndiswrapper.

Now go back and do the sudo ndiswrapper -i xxxxxxxx  stuff including all the depmod, etc..

Post back if you still have problems after that.  :)

---

