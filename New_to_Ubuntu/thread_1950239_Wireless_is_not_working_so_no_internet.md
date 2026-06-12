---
title: "Wireless is not working so no internet"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by brumas on 2012-03-31
Hi,

I just installed ubuntu 11.10 yesterday, but I can't put the wireless to work. I think the drivers of the old laptop Acer Aspire 5000 are not installed.

I had ubuntu 9 a year and half ago in other desktop that I didn't struggled so much as I am now.

So I don't have internet, and by what the foruns and ubuntu docomentation mention we can install something like a ndiswrapper I tried a few suggestions and so far couldn't take anything from the CD.

Can anybody help me, please?

---

### Post by uRock on 2012-03-31
Hello and welcome to the forum. Could you copy and paste the following command into a terminal, then copy and paste the output here?```
lspci
```

---

### Post by brumas on 2012-03-31
> **uRock said:**
> Hello and welcome to the forum. Could you copy and paste the following command into a terminal, then copy and paste the output here?```
lspci
```

[COLOR=#000000][FONT=Arial]evey@evey-Aspire-5000:~$ lspci[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2/3 SMBus controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS7012 AC'97 Sound Controller (rev a0)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]evey@evey-Aspire-5000:~$ 

I'm not being warned by email about new replies, i imagine that will be easy to find, hopefully 
[/FONT][/COLOR]

---

### Post by uRock on 2012-03-31
> **brumas said:**
> ```
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

This link may be helpful with getting that card working. [http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)

---

### Post by brumas on 2012-03-31
> **uRock said:**
> This link may be helpful with getting that card working. [http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/](http://nfolamp.wordpress.com/2011/10/15/ubuntu-11-10-getting-wireless-bcm4311-working/)


the guy has this instructions for my case

Use a wired ethernet connection to the internet.  These instructions are  for getting wireless working.  It is assumed you have a wired  connection already.  If you don’t have that, then ask a friend to  download the packages to flash.  Then install the packages from flash.   If you are downloading the packages to flash, you will need two  packages: “firmware-b43-installer” and “b43-fwcutter”.  The packages can  be downloaded from launchpad.net.   Mount the flash drive, open a  cmdline, and use “dpkg -i package_file …” to install the packages from  the cmdline.

I don't have internet so I'm trying to download with a pc that has windows xp, I don't think that comand line is for windows or is it to put on a comand line in the website (launchpad.net)?

How can I do this?

---

### Post by brumas on 2012-03-31
I did this line on the terminal, hopping that actually I could copy the files from the CD (I don't know if it will but im trying everything).

dpkg -i package_file firmware-b43-installer

and it came with an error
dpkg: error: request operation requires superuser privilege

can someone tell me how can give privileges of superuser to my user?

---

### Post by drexeltux on 2012-03-31
type 'sudo' before using that command, it should prompt for an admin password

---

### Post by brumas on 2012-03-31
> **drexeltux said:**
> type 'sudo' before using that command, it should prompt for an admin password
 
Thanks, that worked, but the package wasnt found or wasnt possible to access.

anyone knows if the packages “firmware-b43-installer” and “b43-fwcutter” are in the installation CD (ubuntu 11.10), if yes how can access them, if no, how can i download in a windows computer to a pen and then bring it to the computer with ubuntu.

---

### Post by Hadaka on 2012-03-31
connect the acer to a hardwired connection
in Ubuntu.  press ctrl/alt/t to ativate a terminal
enter code
sudo apt-get install b43-fwcutter firmware-b43-installer
this will load the correct drivers for your wireless card.

---

### Post by Hadaka on 2012-03-31
After re-reading your post. It looks as though you have loaded
Ubuntu on to your acer laptop...along with windows. Your "aquired" wireless
connection will work with windows and the broadcom card. but will NOT
work with Ubuntu. Untill you hardwire attach the laptop to the net, you will
not be able to load the b-43 dirvers you need.

---

### Post by wildmanne39 on 2012-03-31
Hi, this is an easy way to do it.

Download the b43 zip file to a flash drive then drag and drop the file to your ubuntu desktop. Right-click it and select Extract Here. Open a terminal and do:
```
sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
unplug wire connection and it should work.
Thanks

---

### Post by jlh on 2012-03-31
wildmanne39, thank you. I had wireless from my native "b" wireless card, but could not get my add-on broadcom "g" card recognized. Your instructions did it.

---

### Post by brumas on 2012-04-01
thanks everybody the problem is solved

---

### Post by raja.genupula on 2012-04-01
thats  good news , now please mark the thread as solved from thread tools . 

Thank you .

---

### Post by wildmanne39 on 2012-04-01
Hi, your welcome! please tell us how you fixed it so the whole community can benefit from your solution and use thread tools at the top of the page to mark the thread solved.
Thanks

---

