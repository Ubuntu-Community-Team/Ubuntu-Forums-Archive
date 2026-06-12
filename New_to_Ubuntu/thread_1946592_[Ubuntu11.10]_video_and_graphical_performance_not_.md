---
title: "[Ubuntu11.10] video and graphical performance not so well on ACER ASPIRE ONE D270"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by 842176cell on 2012-03-25
[FONT=Arial][SIZE=3]I just got a new netbook: ACER ASPIRE ONE D270, whose CPU is intel N2600 with GMA3600 embedded.

From [/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=DarkRed]**lspci-v  **[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3][COLOR=Black]I find every driver has been installed right, but when I was watching video stream, it lost frame and operation experience on GUI is not good either, like when I [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=3]operate firefox, drag pic or windows, it lags.

I am not sure if the driver of my VGA chip is not that fit, please help me check.[/SIZE][/FONT]
*************************************************************
[http://paste.ubuntu.com/898823/](http://paste.ubuntu.com/898823/)
    [COLOR=#000]                    
00:00.0 Host bridge: Intel Corporation Cedarview DRAM Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, fast devsel, latency 0

00:02.0 VGA compatible controller: Intel Corporation Cedarview Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, fast devsel, latency 0, IRQ 7
    Memory at 86000000 (32-bit, non-prefetchable) [size=1M]
    I/O ports at 50d0 [size=8]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 86100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 85000000-85ffffff
    Prefetchable memory behind bridge: 0000000080000000-0000000080ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 84000000-84ffffff
    Prefetchable memory behind bridge: 0000000081000000-0000000081ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 83000000-83ffffff
    Prefetchable memory behind bridge: 0000000082000000-0000000082ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 50a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 5080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 5060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 5040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, medium devsel, latency 0, IRQ 17
    Memory at 86105000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 44
    I/O ports at 50c8 [size=8]
    I/O ports at 50dc [size=4]
    I/O ports at 50c0 [size=8]
    I/O ports at 50d8 [size=4]
    I/O ports at 5020 [size=16]
    Memory at 86104000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: medium devsel, IRQ 10
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 4000 [size=256]
    Memory at 80004000 (64-bit, prefetchable) [size=4K]
    Memory at 80000000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Foxconn International, Inc. Device e042
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 84000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: brcmsmac
    Kernel modules: wl, bcma, brcmsmac

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
    Subsystem: Acer Incorporated [ALI] Device 061f
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 83000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: rts_pstor
    Kernel modules: rts_pstor
         
     [/COLOR]

---

### Post by 842176cell on 2012-03-26
Can anyone help?

And i can not initiate 3D effect&#12290;&#12290;

---

### Post by 2F4U on 2012-03-26
My understanding is that GMA3600 will receive basic support in kernel 3.3

[http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-3-Part-4-Drivers-1465292.html](http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-3-Part-4-Drivers-1465292.html)

---

### Post by NikTh on 2012-03-26
**@842176cell** try this PPA and install the driver from there. 
```
sudo apt-add repository [B]ppa:ubuntu-x-swat/x-updates
[/B]sudo apt-get update
sudo apt-get dist-upgrade
```reboot to see the changes.

---

### Post by 842176cell on 2012-03-27
> **NikTh said:**
> **@842176cell** try this PPA and install the driver from there. 
```
sudo apt-add repository [B]ppa:ubuntu-x-swat/x-updates
[/B]sudo apt-get update
sudo apt-get dist-upgrade
```reboot to see the changes.

@NikTh, thx a lot, i tried your method, and terminal response as follow:
```
The following packages will be upgraded:
  libva-x11-1 libva1 xserver-xorg-video-savage
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Now I am about to restart to see what happened..

---

### Post by 842176cell on 2012-03-27
I do not see any difference..

Ubuntu still doesnt have 3D option.

and the updated package seems only for video lib.... am I right?

---

### Post by 842176cell on 2012-03-27
> **2F4U said:**
> My understanding is that GMA3600 will receive basic support in kernel 3.3

[http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-3-Part-4-Drivers-1465292.html](http://www.h-online.com/open/features/Kernel-Log-Coming-in-3-3-Part-4-Drivers-1465292.html)
 
Dear, do you mean my netbook can only have limited performance since ever?

Maybe Intel N2600 is too new for Ubuntu to have proper driver. 

....

---

### Post by NikTh on 2012-03-27
> **842176cell said:**
> Dear, do you mean my netbook can only have limited performance since ever?

Maybe Intel N2600 is too new for Ubuntu to have proper driver. 

....

No , N2600 its not to new for linux , but i think that Intel likes to torturing us . Haha. No proprietary drivers for Intel users. Wait developers of open source intel driver to make their miracle. (Try new kernel 3.3 when release)

1-2 months from now , i will have in my hands a new netbook with intel graphics and N570 , i hope everything will run smoothly . :p

---

### Post by 842176cell on 2012-04-02
> **NikTh said:**
> No , N2600 its not to new for linux , but i think that Intel likes to torturing us . Haha. No proprietary drivers for Intel users. Wait developers of open source intel driver to make their miracle. (Try new kernel 3.3 when release)

1-2 months from now , i will have in my hands a new netbook with intel graphics and N570 , i hope everything will run smoothly . :p

Thx man, even though it is not working as smoothly as I expected, it works anyway.

Just ran the Unity 3D testing tool. Some options are not supported..

---

### Post by saturnino0105 on 2012-07-14
> **NikTh said:**
> **@842176cell** try this PPA and install the driver from there. 
```
sudo apt-add repository [B]ppa:ubuntu-x-swat/x-updates
[/B]sudo apt-get update
sudo apt-get dist-upgrade
```reboot to see the changes.

I am really not good at this... please help! where should I enter the code above that you have provided? I am newbie and needs your expert advice... tnx! :confused:

---

### Post by QIII on 2012-07-14
It would really be best for you to start a new thread of your own rather than tag on to one that is several months old.

---

