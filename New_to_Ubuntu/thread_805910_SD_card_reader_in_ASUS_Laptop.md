---
title: "SD card reader in ASUS Laptop"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by AopicieR on 2008-05-24
Hi, I'm completely new to Ubuntu. 
I have an Asus A6VM Laptop which has a built-in slot for SD/MMC/MS/MS PRO cards. Now I have no idea how to access this under Ubuntu. What should I look for in /dev in order to mount it? How can I find out if the system has even recognized it?

There are also other devices I'd like to use, like an IR port and a camera. I'd appreciate comments concerning those as well.
Thank you very much.

---

### Post by angelsguitar on 2008-05-24
> **tantris said:**
> Hi, I'm completely new to Ubuntu. 
I have an Asus A6VM Laptop which has a built-in slot for SD/MMC/MS/MS PRO cards. Now I have no idea how to access this under Ubuntu. What should I look for in /dev in order to mount it? How can I find out if the system has even recognized it?

Try inserting a card into the slot.  It should mount automatically, and you should see an icon coresponding to the card on your desktop.

> There are also other devices I'd like to use, like an IR port and a camera. I'd appreciate comments concerning those as well.
Thank you very much.

Tha camera, if supported by Ubuntu, should be auto detected too.  Usually you connect the camera and Ubuntu asks if you want to import the photos (asuming you have taken photos) to F-Spot.  With some cameras you should be able to see its storage area as a removable drive.

About the IR, sorry, don't know about it. I hope the rest of the info was helpful, though.

---

### Post by alexandremrj on 2008-05-24
About IR you can install the package irda-utils.

Search for it in Synaptic or use the command line with:

sudo apt-get install irda-utils

---

### Post by AopicieR on 2008-05-24
I'm afraid it's not mounted automatically. If I insert a card, nothing happens. That's why I'm not sure it has been properly recognized. How can I find that out?

I have installed irda-utils and I've tried the things described on the following websites:
[http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-ir-port-with-ubuntu](http://www.len.ro/work/tools/ubuntu-feisty-fawn-on-a-dell-latitude-d820/use-the-ir-port-with-ubuntu)

[http://ubuntuforums.org/showthread.php?t=129693](http://ubuntuforums.org/showthread.php?t=129693)

When using irxfer my mobile phone does not detect the computer when trying to send something.

And when using obex_test c I get "Transport connect error", while obexftp -iv -l gives 
"Connecting...failed: connect
Still trying to connect"

---

### Post by AopicieR on 2008-05-25
lspci gives

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
01:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
03:00.0 VGA compatible controller: nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300] (rev a1)
```

There are several things which look like the card reader. But how can I find out how to mount it? Or where it's mounted automatically if it is?

---

### Post by AopicieR on 2008-05-25
The camera I mentioned is actually a built-in webcam. 
I've installed drivers as described under
[http://ubuntuforums.org/showthread.php?p=3437115](http://ubuntuforums.org/showthread.php?p=3437115)
but it still doesn't work. There is no /dev/video0 and programs like cheese or Ekiga don't detect any installed video devices.

lsusb gives 
```
Bus 005 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 001 Device 001: ID 0000:0000  

```

Thanks for any help.

---

### Post by AbtZ on 2008-05-27
Tantris -- check this out:
[http://ubuntuforums.org/showpost.php?p=5055135&postcount=6](http://ubuntuforums.org/showpost.php?p=5055135&postcount=6)

Hope it helps! :)

---

### Post by AopicieR on 2008-05-27
Awesome, this works (although I have no idea what I've just done). Thank you very much indeed! :)

---

