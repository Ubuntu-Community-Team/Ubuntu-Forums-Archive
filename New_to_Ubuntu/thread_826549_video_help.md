---
title: "video help"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by windows hater on 2008-06-12
hello im trying to watch a movie on my ubuntu laptop and get the picture and audio on the tv i have the s-video cable connected to the tv the piture comes in but the picture quilty sucks and its a hd tv and as well there is no audio but i have the audio cables connected and since i did this my gui is messed up and i have unplugged the svideo cable and its still like this so 

if anyone can help increase the quilty of picture and audio as well as help me with my gui problem

please help thnx in advance

---

### Post by overdrank on 2008-06-12
> **windows hater said:**
> hello im trying to watch a movie on my ubuntu laptop and get the picture and audio on the tv i have the s-video cable connected to the tv the piture comes in but the picture quilty sucks and its a hd tv and as well there is no audio but i have the audio cables connected and since i did this my gui is messed up and i have unplugged the svideo cable and its still like this so 

if anyone can help increase the quilty of picture and audio as well as help me with my gui problem

please help thnx in advance

HI, what is the model of the graphics card and have you installed the correct drivers?

---

### Post by windows hater on 2008-06-12
i really have no idea its an xps m 140 laptop best guess on board and yea im not using any restricted drivers nothing to special does it really make a difference

---

### Post by overdrank on 2008-06-12
> **windows hater said:**
> i really have no idea its an xps m 140 laptop best guess on board and yea im not using any restricted drivers nothing to special does it really make a difference

Hi and you can use the command in the terminal 
```
lspci
``` and look for VGA or you can just post the output here.

---

### Post by windows hater on 2008-06-12
output

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

---

### Post by overdrank on 2008-06-12
Hi and you graphics card 
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
I also have the same in a laptop and have not made it work with the s-video as of yet. SO I can not be of any help to you. sorry. :(

---

### Post by fenian on 2008-06-12
S-video is standard definition and won't look good on your High Definition TV no matter what drivers you use.Can you connect the laptop to the tv using VGA or DVI?

---

### Post by windows hater on 2008-06-12
would it really make a difference all i wanted to do is watch a movie dvi/vga 
which will work with my hd tv

---

### Post by fenian on 2008-06-12
Yes both DVI and VGA can output HD resolutions.What it boils down to is...

A)What video can your laptop output?Some can output DVI others can't while most can output VGA and others only output S-Video or nothing at all.

B)What type of inputs does your HDTV accept some accept DVI or VGA connections many do not.

If you are unsure what I mean by VGA and DVI connectors read [here]("http://en.wikipedia.org/wiki/VGA_connector") and [here ]("http://en.wikipedia.org/wiki/Digital_Visual_Interface")

---

### Post by windows hater on 2008-06-12
thanks for the help i know what i must do

---

