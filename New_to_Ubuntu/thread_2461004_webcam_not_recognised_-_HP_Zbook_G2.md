---
title: "webcam not recognised - HP Zbook G2"
date: 2021-04-22
forum: New to Ubuntu
---

### Post by optmed on 2021-04-22
hi everyone, 

i have replaced Windows 10 with it on a  refurbished HP ZBook 15 G2 laptop with Kubuntu 20.04. Before doing this I tested the laptop in Windows and everything worked - as it does in Kubuntu, the exception  being the integrated webcam.

Is perhaps the webcam suddenly out of order and is there anything I can  do to verify this - that is, before taking the laptop back to the  seller? Or have I inadvertently deleted the webcam drivers when I  install Kubuntu (just using my imagination here, I don't really know  what I"m talking about :)

Cheese tells me "no device found". The same when I try it on [https://meet.jit.si](https://meet.jit.si)  (where I'd normally needed). Here's some code that might be relevant (i  got this from other forums)? 

(if relevant) my machine's SKU is L6M83UC#ABA. 

Can you please help? Thanks!

[FONT=monospace][I][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lsusb [/COLOR]
Bus 002 Device 002: ID 8087:8000 Intel Corp.  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hu
b 
Bus 001 Device 004: ID 8087:07dc Intel Corp.  
Bus 001 Device 003: ID 138a:003f Validity Sensors, Inc. VFS49
5 Fingerprint Reader 
Bus 001 Device 002: ID 8087:8008 Intel Corp.  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[FONT=monospace][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lspci [/COLOR]
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Ge
n Core Processor DRAM Controller (rev 06) 
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen
Core Processor PCI Express x16 Controller (rev 06) 
00:02.0 VGA compatible controller: Intel Corporation 4th Gen 
Core Processor Integrated Graphics Controller (rev 06) 
00:16.0 Communication controller: Intel Corporation 8 Series/
C220 Series Chipset Family MEI Controller #1 (rev 04) 
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Se
ries Chipset Family KT Controller (rev 04) 
00:19.0 Ethernet controller: Intel Corporation Ethernet Conne
ction I217-LM (rev 04) 
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Serie
s Chipset Family USB EHCI #2 (rev 04) 
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series 
Chipset High Definition Audio Controller (rev 04) 
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Ch
ipset Family PCI Express Root Port #1 (rev d4) 
00:1c.6 PCI bridge: Intel Corporation 8 Series/C220 Series Ch
ipset Family PCI Express Root Port #7 (rev d4) 
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Serie
s Chipset Family USB EHCI #1 (rev 04) 
00:1f.0 ISA bridge: Intel Corporation QM87 Express LPC Contro
ller (rev 04) 
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Seri
es Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 0
4) 
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset
Family SMBus Controller (rev 04) 
01:00.0 VGA compatible controller: NVIDIA Corporation GK107GL
M [Quadro K1100M] (rev a1) 
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Con
troller (rev a1) 
3b:00.0 PCI bridge: Pericom Semiconductor PI7C9X2G404 EL/SL P
CIe2 4-Port/4-Lane Packet Switch (rev 05) 
3c:01.0 PCI bridge: Pericom Semiconductor PI7C9X2G404 EL/SL P
CIe2 4-Port/4-Lane Packet Switch (rev 05) 
3c:02.0 PCI bridge: Pericom Semiconductor PI7C9X2G404 EL/SL P
CIe2 4-Port/4-Lane Packet Switch (rev 05) 
3c:03.0 PCI bridge: Pericom Semiconductor PI7C9X2G404 EL/SL P
CIe2 4-Port/4-Lane Packet Switch (rev 05) 
3d:00.0 Network controller: Intel Corporation Wireless 7260 (
rev 6b) 
5f:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., L
td. RTS5249 PCI Express Card Reader (rev 01)[/FONT][/I][/FONT]

---

### Post by optmed on 2021-04-22
"i have replaced Windows 10 with it on a  refurbished HP ZBook 15 G2 laptop with Kubuntu 20.04": this is not clear at all, sorry. Bottom line: I now only have Kubuntu on this HP :)

---

### Post by optmed on 2021-05-02
bump? :)

---

### Post by ActionParsnip on 2021-05-02
Is there a key or shortcut to enable / disable the webcam?
Is the webcam enabled in BIOS?

---

### Post by optmed on 2021-05-03
thanks ActionParsnip for getting back to me. I can't unfortunately find any option in BIOS to either enable or disable the webcam...on the keyboard, I can "fn-f8" to enable/disable the microphone, but that's it...unless I need to use a different key combination - I can't find anything anywhere on this matter on the net, though. Every single forum I visited talks about solving this problem on Windows, i.e., going to "Device Manager" and/or downloading the relevant webcam drivers. I can't find any webcam option on the "Nvidia X server settings either, in this respect. 

is there any chance I can restore this HP webcam in Ubuntu - similarly to what I'd do in Windows (except that I don't have Windows on this HP, etc)?

---

