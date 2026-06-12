---
title: "wireless internet help"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by huntis619 on 2008-06-23
Hi all. I have a hp zv5410us laptop. I can't get on the internet with my wireless connection. My wireless connection is not set up. Here is a little info about my laptop.

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
steven@steven-laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

steven@steven-laptop:~$

---

### Post by wolfen69 on 2008-06-23
click on the network icon on the taskbar. you should see a list of available networks. if not, go to system>admin>hardware drivers and see if there is a driver there to download. if not, you will have to use ndiswrapper to get it working.

---

### Post by Pjotr123 on 2008-06-23
This will do the job:
[http://ubuntutip.googlepages.com/nointernetconnection](http://ubuntutip.googlepages.com/nointernetconnection)

---

### Post by Kevbert on 2008-06-23
Hi.  You have a Broadcom BCM4306 wireless card which can be set up using this [guide]("http://ubuntuforums.org/showthread.php?t=766560").

---

### Post by huntis619 on 2008-06-23
OK thank you all I'll try them all and let you know the outcome shortly.

---

### Post by edwardLS on 2008-06-23
I also have the Broadcom BCM 4306 wireless card.  After many struggles and failures, I followed the guide pointed to by 'Kevbert' and I now have wireless working exceptionally well.

Good Luck.

---

### Post by huntis619 on 2008-06-23
-laptop:~$ lshw -c network
Hardware Lister (lshw) - B.02.12.01
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.12.01)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)

steven@steven-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for steven: 
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
steven@steven-laptop:~/bcm43xx$ wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
--15:07:19--  [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe.2'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.

    [                <=>                  ] 4,318,656      1.33M/s             

15:07:23 (1.32 MB/s) - `sp33008.exe.2' saved [4318656]

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
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  b43-fwcutter 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 102kB will be freed.
Writing extended state information... Done
(Reading database ... 113948 files and directories currently installed.)
Removing b43-fwcutter ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
steven@steven-laptop:~/bcm43xx$ sudo gedit /etc/init.d/wirelessfix.sh
cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh

sudo update-rc.d wirelessfix.sh defaults


OK I got lost after step 6 can you guide me from there. Remember I'm new to this.

---

### Post by huntis619 on 2008-06-23
OK lets try it this way. After step 6 it says paste the following


Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

SAVE IT WHERE? Please explain this one step in detail.

---

### Post by huntis619 on 2008-06-23
Ok Now I rebooted my laptop and I see my router under wireless networks. I type in my passphrase and it still won't connect. What is my problem now. Should I try a new code or reboot my router?

---

### Post by huntis619 on 2008-06-23
Can someone help me with the guide that Kevbert referred me to: "Broadcom wireless setup for Hardy" by Alex_Kent_18. First after step 1 it takes you to another page where you have to pick a command based on your wireless card. My wireless card is listed as Broadcom 4306(rev 03). My card is not listed, is it okay to use Broadcom 4306 or Broadcom 4306(rev 02) or do I use the command listed with Broadcom 43xx. The next thing I was unsure of was the steps for step 6. How and where do I save the commands. Do I do each command separately or all together. Please can someone help me I am totally new to this. Here is step  6:


Paste the followings in the opened file(wirelessfix.sh)and make sure you save it before continuing Step 7

#!/bin/bash
modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

---

### Post by huntis619 on 2008-06-23
would be nice if someone could help me with my problem

---

### Post by Kevbert on 2008-06-23
Use the 4306 settings (mine also was Rev 03). At step 5 you open the file wirelessfix.sh in directory /etc/initd/ for editing with 
```
sudo gedit /etc/init.d/wirelessfix.sh
```
If it doesn't exist it will be generated as a new file.
Copy the commands in step 6) by highlighting and use Ctrl+C and then paste them into wirelessfix.sh (which you've just opened) with Ctrl+V.  Now click on Save and Quit the editor with Ctrl+Q.

---

### Post by huntis619 on 2008-06-23
Thank you I'll try it now and let you know how it goes.

---

### Post by huntis619 on 2008-06-23
Still won't work. I know its step 6 I know I must be doing something wrong. I'll try again and post results.

---

### Post by huntis619 on 2008-06-23
Here's what I've done so far. I'm about to reboot I'll let you know what happens in about 5 minutes.


steven@steven-laptop:~$ echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
[sudo] password for steven: 
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
--17:27:40--  [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
           => `sp33008.exe.4'
Resolving ftp.compaq.com... 161.114.23.171
Connecting to ftp.compaq.com|161.114.23.171|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.

    [                <=>                  ] 4,318,656      1.31M/s             

17:27:44 (1.31 MB/s) - `sp33008.exe.4' saved [4318656]

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
steven@steven-laptop:~/bcm43xx$ 
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
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
steven@steven-laptop:~/bcm43xx$ sudo gedit /etc/init.d/wirelessfix.sh
steven@steven-laptop:~/bcm43xx$ cd /etc/init.d/ && sudo chmod 755 wirelessfix.sh
steven@steven-laptop:/etc/init.d$ sudo update-rc.d wirelessfix.sh defaults 
 System startup links for /etc/init.d/wirelessfix.sh already exist.
steven@steven-laptop:/etc/init.d$

---

### Post by huntis619 on 2008-06-23
Nope still won't work. I click on my network name,type in passphrase,then searches for connection and finally  BOOM  nothing. Now what do I do.I 've been reading different threads and this seems to be the tutorial that works for most. Anybody have any ideas, suggestions, opinions ... anything... HELLLP.

---

### Post by huntis619 on 2008-06-23
I just noticed I went to check my hardware drivers and I noticed that I don't see the driver for my wireless card. Could this be my problem and if so how do I get it back.

---

### Post by Kevbert on 2008-06-24
Please post the terminal output of
```
ifconfig
iwconfig
iwlist scanning
```
The last command should not work if it's a driver problem,  
If you do get a reply you need to try temporarily to turn off all encryption on your router.  To do this you'll need to either connect to it via an ethernet cable or use a PC which you can connect via wireless.  Once this has occurred you need to open a browser and enter the router address which will be something like 
```
http://192.168.0.1
```
The info should be in your router manual.  If not, post the make and model here.  The router will ask you for a username and password (defaults may be admin and password, but will be in the manual).  Somewhere on the page, that opens, will be wireless setup and within that will be your encryption and password.  Turn the encryption off and see if you can connect.  If you can, then you need to set up wpa supplicant (more software) on your PC.

---

