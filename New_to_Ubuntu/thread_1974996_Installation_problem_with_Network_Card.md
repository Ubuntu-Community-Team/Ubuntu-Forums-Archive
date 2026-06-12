---
title: "Installation problem with Network Card"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by MikeAllen on 2012-05-06
I am brand new to xubuntu 12.04 and decided I wanted to use an outdated computer as a server. I used the aternative install disk to load xubuntu to a blank hard drive and during the installation the software was able to download files but after the installation and a reboot I could not connect to the internet. After logging into my router I discovered the computer was not receiving an IP address. 
 
I reinstalled XP to make sure the network card still worked and discovered that I had to install drivers for the network card to get an IP address and internet connection but did confirm the the onboard network card does in fact work once the drives are loaded onto the xp system. I reformated the disk and reinstalled xubuntu. Again it downloaded files during the installation but after rebooting to the hard drive the network card again does not work.
 
The onboard network adaptor is a Intel EtherExpress PRO/100 VE. According to xubuntu it is product 82562EZ 10/100 bus info PCI@0000:02:08.0 eth0 driver e100 IO port B000. Do I need a different driver? If so where do I get it and is there a place where I can download step by step instructions. Like I said I am just starting to learn the system.

---

### Post by Hadaka on 2012-05-06
Hi, sounds like you have the same problem as many have had.
are you able to attach to the internet with the xp os?
also..pleaseeinter this in a terminal    ctrl/alt t for terminal

lspci -nnk | grep -iA2 net

and post back the results

thanks

---

### Post by MikeAllen on 2012-05-06
> **Hadaka said:**
> Hi, sounds like you have the same problem as many have had.
are you able to attach to the internet with the xp os?
also..pleaseeinter this in a terminal    ctrl/alt t for terminal

lspci -nnk | grep -iA2 net

and post back the results

thanks
Yes in xp I can get to the internet but only after installing the network driver that came with the computer. Results are as follows:
 
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet controller [8086: 1050] (rev 01)
         Subsystem: Intel Corporation Device [8086: 3033]
         Kernel Driver in use: e100

---

### Post by Hadaka on 2012-05-06
when you issued that command in a terminal

lspci -nnk | grep -iA2 net

did it display what driver was in use?...like..b44....b43?

---

### Post by Hadaka on 2012-05-06
also..what type of pc are you using?  HP,dell.acer? and what are its specs?
need some detailed info to suggest correct commands to trouble shoot this.

---

### Post by Hadaka on 2012-05-06
sorry..i didnt see the s100 driver..on research there is mention of raid for the server
type configuration you are trying to set up. I dont have enough experience with servers
to be of much help to you. I would suggest entering the type of pc and the s100 driver
into a google search or search the ubuntu threads for a fix. Perhaps someone with
more experience and knowledge will read the post and help you out as well. thanks

---

### Post by MikeAllen on 2012-05-07
I thought the driver was e100. It is not set up as raid.

thanks

---

### Post by MikeAllen on 2012-05-07
It is a PowerSpec 9340. The specs are online by searching for "PowerSpec 9340" in google. I can download them and attach it tonight when I get home if you want me to.

---

### Post by MikeAllen on 2012-05-07
> **Hadaka said:**
> also..what type of pc are you using?  HP,dell.acer? and what are its specs?
need some detailed info to suggest correct commands to trouble shoot this.
Here are the specs for the PowerSpec 9340.
 
[Processor]("http://www.powerspec.com/systems/system_components.phtml?component=733&selection=9340")
Intel® Pentium® 4 Processor with HT Technology at 3.0GHz
[OS]("http://www.powerspec.com/systems/system_components.phtml?component=492&selection=9340")
[genuine]("http://www.powerspec.com/systems/system_specs.phtml?selection=9340#") Microsoft® Windows® XP Professional Edition
[System Board]("http://www.powerspec.com/systems/system_components.phtml?component=735&selection=9340")
Intel® D865PERC
[System Memory]("http://www.powerspec.com/systems/system_components.phtml?component=769&selection=9340")
1GB composed of 2- 512MB PC3200 SDRAM 184-pin DIMMs
[Diskette Drive]("http://www.powerspec.com/systems/system_components.phtml?component=531&selection=9340")
3.5" 1.44MB Floppy Disk Drive
[Hard Drive]("http://www.powerspec.com/systems/system_components.phtml?component=630&selection=9340")
120GB ATA/100 7200 RPM
[DVD-ROM Drive]("http://www.powerspec.com/systems/system_components.phtml?component=515&selection=9340")
16x DVD-ROM Drive - LTN-163
[DVD ±R/±RW Drive]("http://www.powerspec.com/systems/system_components.phtml?component=737&selection=9340")
4x DVD±R/±RW Drive
[Video]("http://www.powerspec.com/systems/system_components.phtml?component=736&selection=9340")
e-GeForce FX 5200 128MB DDR TV-Out Graphics Card
[Sound]("http://www.powerspec.com/systems/system_components.phtml?component=1028&selection=9340")
Integrated SoundMAX® Audio
[Modem]("http://www.powerspec.com/systems/system_components.phtml?component=725&selection=9340")
Lectron 56K V.92 PCI Internal Modem
[LAN]("http://www.powerspec.com/systems/system_components.phtml?component=847&selection=9340")
Intel® PRO/100 VE Integrated Ethernet
[Ports/Connectors]("http://www.powerspec.com/systems/system_components.phtml?component=1026&selection=9340")
Built-in USB 2.0
[Ports/Connectors]("http://www.powerspec.com/systems/system_components.phtml?component=592&selection=9340")
PCI to IEEE 1394 Card - 3 port
[Speakers]("http://www.powerspec.com/systems/system_components.phtml?component=530&selection=9340")
Stereo Speakers
[Keyboard]("http://www.powerspec.com/systems/system_components.phtml?component=528&selection=9340")
Chicony KB-2961 PS/2 Keyboard
[Mouse]("http://www.powerspec.com/systems/system_components.phtml?component=529&selection=9340")
2-Button PS/2 Scroll Mouse
[Warranty]("http://www.powerspec.com/systems/system_components.phtml?component=115&selection=9340")
On-Site Limited Warranty

 
Hope that helps. It is not configured as Raid.

---

