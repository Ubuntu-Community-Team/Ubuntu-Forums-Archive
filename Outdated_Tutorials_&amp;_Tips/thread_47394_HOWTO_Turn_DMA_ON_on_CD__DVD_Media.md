---
title: "HOWTO: Turn DMA ON on CD / DVD Media"
date: 2005-07-08
forum: Outdated Tutorials &amp; Tips
---

### Post by fedemw on 2005-07-08
Hi to everyone,

I hope it helps for configure DMA ON on your media devices.

One help was helping me in Ubuntu chat and i wish to share this information.

It is usefull to burn CD/DVD, because device speed turns fastest.

So if you try to do:
jef@exodus:~$ sudo hdparm -d1 /dev/hdc

/dev/hdc:
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off) 

You can't turn DMA ON. 


In my case, the solution was load via82cxxx in /etc/modules. So when i reboot, i can turn it on with hdparm command. See modules config file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

via82cxxx
ide-cd
ide-disk
ide-generic
lp
mousedev
psmouse


This should work with motherboards based on VIA CHIPSET (like Asus k8v-x model).

Summary from posts I read:

nForce Chipset (and amd):
Add amd74xx to your /etc/modules file before ide-cd.
Rboot and set dma with hdparm -d1 /dev/hdx (change x to your drive)


I hope it helps, bye !  :smile:

---

### Post by Caboto on 2005-07-08
There's already a HowTo for turning DMA on. Right [here](http://ubuntuforums.org/showthread.php?t=30949).

Only through your thread I realized, that DMA is not turned on. That's why my dvd burner burns only with 1x. Had to change the order (or adding, if it doesn't exist) in /etc/modules like described [here](http://www.ubuntuforums.org/showthread.php?p=93238#post93238), because I've got an Intel Chipset.

---

### Post by thagame on 2005-07-10
i just ran sudo hdparm -d1 /dev/hdc and it said 

/dev/hdc:
 setting using_dma to 1 (on)
 using_dma    =  1 (on)

i did nothing for dma before so im guessing it autoset at install.

---

### Post by Jesus Franco on 2005-07-20
YEA! I knew there was something wrong. HDPARM doesnt work on some motherboards because of the missing module. Thanks man. My nforce2 can now use it by adding the amd74xx just like you said. Thanks alot.

---

### Post by OneSeventeen on 2005-07-29
Here's my lspci:
```

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:04.0 PCI bridge: ATI Technologies Inc: Unknown device 5a36
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 10)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc: Unknown device 4370 (rev 01)
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 4378 (rev 01)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5955
0000:03:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:03:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0000:03:04.0 CardBus bridge: Texas Instruments: Unknown device 8031
0000:03:04.3 Unknown mass storage controller: Texas Instruments: Unknown device 8033
0000:03:04.4 0805: Texas Instruments: Unknown device 8034
0000:03:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Any ideas what module I should be using?  the amd74xx trick didn't work :(

I'm getting that 
setting using_dma to 1 (on)
HDIO_SET_DMA failed: Operation not permitted
using_dma = 0 (off) 

message

---

### Post by lunarcloud on 2008-06-04
Theres a conflict between the proprietary ati drivers and dma.

---

