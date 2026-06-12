---
title: "[SOLVED] Ubuntu wireless problem"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by inxygnuu on 2008-09-28
can anyone tell me how to use my wireless in Ubuntu?:confused: I looked on their help page and it did not help at all. I made a gigantic mistake and accidentally wiped out most of my vista, while trying to install dual-boot:(. Having Ubuntu, I realize that vista truly is the easy life, but I don't fell that i need to buy it again. I do have a backup drive:), but I can't access it:(. please realize that I am very young (don't want to give my real age) and don't have a lot of time or money. any help would be nice. My wireless router is a Netgear, and I got Online no-problem with vistas automatic-connect. Thank you for reading my request.
Here are all of my specs:
processor model  	AMD Turion 64 X2 TL-60  
processor speed 	2.0 GHz  
hard drive capacity 	200 GB  
memory 	3 GB  
memory type 	DDR2 SDRAM  
maximum memory capacity 	4 GB  
Wi-Fi capability included (Wi-Fi ready) 	yes  
included integrated drives 	DVD±RW/DVD-RAM/DVD+R Double Layer  
diagonal screen size 	15.4 inches  
notebook computer weight 	6.06 lb  
screen type 	TFT active matrix LCD  
operating system 	Windows Vista Home Premium with Service Pack 1  
screen resolution 	1280 x 800  
software included 	yes  
warranty length 	1-year limited  
number of USB 2.0 ports 	3  
number of USB 1.1 ports 	0  
modem standard 	56K V.90  
audio hardware 	Altec Lansing  
frontside bus speed 	1600 MHz  
integrated speaker 	yes  
integrated memory card reader 	yes  
mouse pointer type 	touchpad  can anyone tell me how to use my wireless in Ubuntu? I looked on their help page and it did not help at all. I made a gigantic mistake and accidentally wiped out most of my vista, while trying to install dual-boot. Having Ubuntu, I realize that vista truly is the easy life, but I don't fell that i need to buy it again. I do have a backup dive 
number of VGA video ports 	1  
video hardware 	nVidia GeForce Go 7150M  
video memory 	1071MB shared  
thickness 	1.56 inches  
width 	14.05 inches  
depth 	10.12 inches  
Ethernet port 	yes  
number of parallel ports 	0  
number of PS/2 ports 	0  
number of S-video outputs 	1  
number of serial ports 	0  
infrared port 	yes  
computer battery type 	lithium-ion  
number of FireWire ports 	1  
Energy Star qualified 	yes  
model name 	Pavilion dv6910us  
brand name 	HP  
manufacturer 	Hewlett-Packard

---

### Post by Sealbhach on 2008-09-28
Hi. A lot of people have trouble setting up wireless in Ubuntu but this can usually be overcome. Have you got a wired connection, or wireless only?

Please type this in terminal and paste the output of that here:

```
lshw -C network
```


.

---

### Post by inxygnuu on 2008-09-30
*-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:95:10:70
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=xxx.xxx.x.xx latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by aparigraha on 2008-09-30
Your wireless is AR242x 802.11abg Wireless PCI Express Adapter.
I have the same on a Fujitsu SIemens and got it to work doing this:

[http://ubuntuforums.org/showpost.php?p=5711824&postcount=6]("http://ubuntuforums.org/showpost.php?p=5711824&postcount=6")

People have also used this one. 
[http://ubuntuforums.org/showthread.php?t=921329&highlight=242x]("http://ubuntuforums.org/showthread.php?t=921329&highlight=242x")

Can't really say which one to use though. Good luck

---

