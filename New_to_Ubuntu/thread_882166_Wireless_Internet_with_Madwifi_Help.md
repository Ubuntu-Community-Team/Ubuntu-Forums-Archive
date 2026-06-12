---
title: "Wireless Internet with Madwifi Help"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Kray378 on 2008-08-06
I am completely new to Linux. Right now I am using Ubuntu and I am having a hard time getting my wireless card to work. It is an atheros 802.11g wireless LAN card. I downloaded madwifi and I don't know how to use it. Can anyone help me?

---

### Post by pytheas22 on 2008-08-06
madwifi already comes built into Ubuntu, so if your card doesn't "just work" out-of-the-box, madwifi probably doesn't support it (it supports most Atheros cards, but there are some exceptions).  It may help to download the latest version--the one in Ubuntu is a few months old--but chances are that you will instead have to use ndiswrapper, a program to drive your wireless using the Windows drivers for your card.

In order to figure out the exact model of your card and find out how to make it work in Linux, please post the output of these commands:
```

lspci -nn
lsusb
lshw -C Network
```

---

### Post by Kray378 on 2008-08-06
I don't know what part of the output you want. It comes up with a lot of information that I do not understand. Like I said, I am completely new to Linux and don't understand much of it. If you could tell me how to use the wrap(sp) that would be great because I can't understand the install instructions.

---

### Post by pytheas22 on 2008-08-06
Please post all of the output of:
```

lspci -nn
lsusb
lshw -C Network
```

It might be a little long, but not too bad.  You can highlight it in the terminal, right click, select copy, and then paste it here (if you don't have any Internet connection on your Ubuntu machine, paste it into a text file and transfer it to another computer using a USB drive or something).  I can't tell you how to install ndiswrapper until I know which chipset you have, and that information will tell me.

If it's really difficult to copy and paste here let me know and I'll tell you just what I minimally need to see, but it would be best to see everything.

---

### Post by Kray378 on 2008-08-06
Alright, here it is.

lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS690 Host Bridge [1002:7910]
00:02.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Graphics Port 0) [1002:7913]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 1) [1002:7915]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2) [1002:7916]
00:07.0 PCI bridge [0604]: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3) [1002:7917]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 14)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 2400 [1002:94c9]
01:00.1 Audio device [0403]: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO] [1002:aa10]
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
14:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
1a:04.0 CardBus bridge [0607]: Texas Instruments PCIxx12 Cardbus Controller [104c:8039]
1a:04.1 FireWire (IEEE 1394) [0c00]: Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller [104c:803a]
1a:04.2 Mass storage controller [0180]: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) [104c:803b]
1a:04.3 SD Host controller [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller [104c:803c]

 lsusb
Bus 006 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:01:86:87
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0

---

### Post by pytheas22 on 2008-08-06
Thanks for the information.  You have an Atheros AR242X chipset.  Incidentally, I just helped someone with it yesterday, and she was kind enough to write up a comprehensive how-to on getting her card working once we figured it out.

Please take a look at this [post]("http://ubuntuforums.org/showpost.php?p=5525672&postcount=73") and see the attached Word document, which has instructions that should make your card work.  Please try to follow them and let me know how it goes.  Even if the name of your laptop isn't the same as hers, the guide should still work, because your wireless card has the same exact chipset.

And just so you know, we determined in that thread that madwifi doesn't yet support the kind of chipset in question, or at least she couldn't get it to even after trying pretty hard.

---

### Post by Kray378 on 2008-08-06
I tried it and couldn't get the wireless connections to come up on the network connections. I got tired of trying so I'll try again tomorrow and tell you how it goes.

---

### Post by pytheas22 on 2008-08-06
Alright, give it another shot tomorrow.  You may want to try with these steps, which are the same as what's in the Word document, except here it's all just plain commands that you have to run:
```

sudo -s
apt-get remove --purge ndiswrapper*
apt-get install ndiswrapper*
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
```

Now reboot, then continue:

```
sudo -s
wget ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
unzip Wireless_Atheros.zip
cd Atheros
unzip HR2H01WW.zip
ndiswrapper -i net5211.inf
echo 'ndiswrapper' | sudo tee -a /etc/modules
modprobe ndiswrapper
```

At this point your wireless should work. If not, make sure that the wireless switch is turned on. If it still doesn't work, please post the output of:
```

lsmod | grep ndis
ndiswrapper -l
cat /etc/modprobe.d/blacklist
iwlist scan
uname -m
```

---

### Post by acreech on 2008-08-06
I have an aspire 7520-5185 with an Atheros AR5BXB63 wireless network card that is not working. I tried the above directions and still had no luck in getting it to work. 

I don't see a place on the computer that looks like a "Wireless Switch" where would you find such a thing?

> 
lsmod | grep ndis


> 
ndiswrapper           243872  0 
usbcore               169904  6 uvcvideo,ndiswrapper,usbhid,ehci_hcd,ohci_hcd


> 
ndiswrapper -l


> 
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)


> 
cat /etc/modprobe.d/blacklist


> 
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci


> 
iwlist scan


> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


> 
uname -m


> 
x86_64


---

### Post by pytheas22 on 2008-08-07
@ acreech:

I think the problem is that you're using a 64-bit kernel, but you have loaded a 32-bit Windows driver into ndiswrapper.  This doesn't work, as the architecture of the Windows drivers needs to match that of your Linux kernel.

To remove the 32-bit Windows driver, run:
```

sudo ndiswrapper -r net5211
```

And you can get and install the new driver with (the download may take a while because the site seems slow and the driver is of course packaged with several megabytes' worth of useless stuff):
```

wget http://america.giga-byte.com/FileList/Driver/comm_driver_superwireless_v.5.2.0.117.zip
unzip comm*
cd GIGA*
cd Driver
cd VistaX64
ndiswrapper -i netathrx.inf
```

Then reboot and see if your wireless works.  If not, please post:
```

ndiswrapper -l
lsmod | grep ndis
iwlist scan
```

---

### Post by Kray378 on 2008-08-07
It still didn't work. Here are the outputs of those commands you gave me.

 lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

 ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

 cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist ath_pci

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

 uname -m
x86_64

---

### Post by pytheas22 on 2008-08-07
> It still didn't work. Here are the outputs of those commands you gave me.

Ah, the problem is that you have a 64-bit kernel (same as acreech who posted above).  Please run this code to install the 64-bit Windows driver, which should get you up and running:
```

sudo ndiswrapper -r net5211
wget http://america.giga-byte.com/FileList/Driver/comm_driver_superwireless_v.5.2.0.117.zip
unzip comm*
cd GIGA*
cd Driver
cd VistaX64
ndiswrapper -i netathrx.inf
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

This should work; please let me know.

---

### Post by Kray378 on 2008-08-07
It still does not work for me. In the last set of codes you gave me the command "ndiswrapper -i netathrx.inf" said I did not have permission if that would have anything to do with it.

---

### Post by silverglade00 on 2008-08-07
Try

```
sudo ndiswrapper -i netathrx.inf
```


Sorry to butt in Pytheas, I was just driving by and saw it.

---

### Post by Kray378 on 2008-08-07
the sudo in front of that command worked, but alas, It still didn't fix my problem. Anymore suggestions? Is it possible I'm doing something wrong? To let you know, I am copying and pasting these commands just so I don't accidentally type the wrong thing in.

---

### Post by pytheas22 on 2008-08-07
> Sorry to butt in Pytheas, I was just driving by and saw it.

No, thanks for the help :)
> 
the sudo in front of that command worked, but alas, It still didn't fix my problem. Anymore suggestions? Is it possible I'm doing something wrong? To let you know, I am copying and pasting these commands just so I don't accidentally type the wrong thing in.

Please post these outputs so we can figure out what's going on:
```

ndiswrapper -l
lsmod | grep ndis
sudo modprobe -v ndiswrapper
lshw -C Network
```

---

### Post by Kray378 on 2008-08-07
Alright, here they are:

 ndiswrapper -l
netathrx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

 lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

 lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:ec:01:86:87
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.102 latency=0 module=r8169 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:14:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0



Nothing came up when I entered "sudo modprobe -v ndiswrapper"

---

### Post by pytheas22 on 2008-08-07
hmmm, from ndiswrapper's output, everything looks like it should be working correctly; unfortunately the wireless card remains unclaimed and it's not clear why.

One possible reason is that there's a switch on your laptop (either a physical switch that you move back and forth, or something you enable by pressing a key combination, like function-F2).  If so, please make sure it's turned on (if you don't know which position is on, switch it from wherever it is now).

If that doesn't help, please also try rebooting, then run these commands and post the output:
```

lsmod | grep ndis
sudo modprobe --verbose ndiswrapper
dpkg -s ndiswrapper-common
dpkg -s ndiswrapper-utils-1.9
```

Sorry it's not going as smoothly as we'd like, but I think we should have this solved soon.  Thanks for your quick responses so far.

---

### Post by Kray378 on 2008-08-07
It's alright. Thanks for helping me though. Your doing more than I expected from one person. Here are the outputs:

 lsmod | grep ndis
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ehci_hcd,ohci_hcd

 dpkg -s ndiswrapper-common
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 92
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.50-1ubuntu1
Replaces: ndiswrapper-utils
Suggests: ndiswrapper-source
Description: Common scripts required to use the utilities for ndiswrapper
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains wrapper scripts to call out to the proper
 versions of whatever -utils-X.X package is installed.
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
Original-Maintainer: Kel Modderman <kel@otaku42.de>

dpkg -s ndiswrapper-utils-1.9
Package: ndiswrapper-utils-1.9
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 120
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: ndiswrapper
Version: 1.50-1ubuntu1
Depends: libc6 (>= 2.6.1-1), ndiswrapper-common, perl
Suggests: ndiswrapper-source
Description: Userspace utilities for the ndiswrapper Linux kernel module
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
Homepage: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/)
Original-Maintainer: Kel Modderman <kel@otaku42.de>

---

### Post by pytheas22 on 2008-08-07
Thanks for that...ndiswrapper looks like it's installed alright.  Could you please also post:
```

dmesg | grep -e ndis -e wlan -e neta
sudo rmmod ndiswrapper
sudo modprobe --verbose ndiswrapper
sudo ifconfig wlan0 up
iwlist scan
```

---

### Post by Kray378 on 2008-08-07
Here it is.

 dmesg | grep -e ndis -e wlan -e neta
[   38.983046] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   39.094132] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   39.094141] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   39.094147] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   39.094165] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   39.094185] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   39.094192] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   39.094199] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   39.094205] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   39.094211] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   39.094218] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   39.094224] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   39.094243] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   39.094250] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   39.094257] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   39.094264] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   39.094271] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   39.094279] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   39.094289] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   39.094296] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   39.094320] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   39.094330] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   39.094339] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   39.094352] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   39.094359] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   39.094366] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   39.094374] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   39.094381] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   39.094388] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   39.094394] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   39.094401] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   39.094410] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   39.094417] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   39.094426] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   39.094433] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   39.094440] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   39.094446] ndi
swrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   39.094453] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   39.094460] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   39.094467] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   39.094473] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netathrx'
[   39.095033] ndiswrapper (load_wrap_driver:112): couldn't load driver netathrx; check system log for messages from 'loadndisdriver'
[   39.095101] usbcore: registered new interface driver ndiswrapper

 sudo modprobe --verbose ndiswrapper
insmod /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

 iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by pytheas22 on 2008-08-07
The dmesg output explains a lot.  Obviously ndiswrapper doesn't like the Windows driver that you loaded into it.  I'm not sure why, because this worked for someone yesterday with the exact same chipset and the same Windows driver.  Maybe uninstalling ndiswrapper and starting from scratch would help:

```
sudo apt-get remove --purge ndiswrapper
sudo apt-get install ndiswrapper*
```

Now reboot, then continue with:
```

wget http://america.giga-byte.com/FileList/Driver/comm_driver_superwireless_v.5.2.0.117.zip
unzip comm*
cd GIGA*
cd Driver
cd VistaX64
sudo ndiswrapper -i netathrx.inf
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

Hopefully at this point, the wireless will be up and running.  If not, please let me see:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by Kray378 on 2008-08-07
It still does not work. Here are the outputs.

dmesg | grep -e ndis -e wlan
[   46.128653] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   46.238560] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeInitializeGuardedMutex'
[   46.238569] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeAcquireGuardedMutex'
[   46.238574] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'KeReleaseGuardedMutex'
[   46.238589] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   46.238606] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   46.238612] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   46.238618] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   46.238624] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisRetreatNetBufferDataStart'
[   46.238629] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   46.238635] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAdvanceNetBufferDataStart'
[   46.238641] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   46.238656] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   46.238663] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMFreeNetBufferSGList'
[   46.238669] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   46.238676] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   46.238682] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   46.238689] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   46.238698] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   46.238704] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   46.238723] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   46.238732] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   46.238739] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMResetComplete'
[   46.238750] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   46.238756] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   46.238762] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   46.238769] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   46.238775] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   46.238781] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
[   46.238786] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
[   46.238792] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   46.238800] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
[   46.238805] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
[   46.238813] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   46.238819] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
[   46.238825] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   46.238831] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
[   46.238836] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   46.238842] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   46.238848] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMAllocateNetBufferSGList'
[   46.238854] ndiswrapper (load_sys_files:210): couldn't prepare driver 'netathrx'
[   46.239404] ndiswrapper (load_wrap_driver:112): couldn't load driver netathrx; check system log for messages from 'loadndisdriver'
[   46.239471] usbcore: registered new interface driver ndiswrapper

 driver installed
	device (168C:001C) present (alternate driver: ath_pci)

---

### Post by pytheas22 on 2008-08-07
I'm sorry it's being so complicated.  I am trying to find another set of 64-bit Windows drivers that you could use.  In the meantime, please check to make sure that there's not a switch that you need to turn on to make the wireless work (someone said that for this card, the LED light may not come on even when the switch is turned on).  And make sure that:
```

iwlist scan; iwlist scan
```

gives you no output.

---

### Post by pytheas22 on 2008-08-07
Alright, I just found a second set of amd64 drivers to try.  Please try this:
```

sudo ndiswrapper -r netathrx
wget tar.gz from http://burnthesorbonne.com/files/atheros_64-bit.tar.gz
tar -xzvf atheros_64*
cd atheros_64
sudo ndiswrapper -i net5211.inf
```

Then reboot and maybe the wirless will be fixed...let's hope.

---

### Post by Kray378 on 2008-08-07
That still didn't work. I have made sure that the card switch is on.

---

### Post by pytheas22 on 2008-08-08
I'm sorry it's still not working.  When you get a chance, please post:
```

ndiswrapper -l
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
dmesg | grep -e ndis -e wlan
```

If you still get the same kind of errors in dmesg as before--all that "unknown symbol" stuff--your options are probably going to be 1) compiling ndiswrapper from source, which may or may not solve the problem, or 2) switching to a 32-bit kernel, where I know that ndiswrapper works with your card.

---

### Post by Kray378 on 2008-08-10
ndiswrapper -l
net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

dmesg | grep -e ndis -e wlan
[   34.024470] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   34.116315] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   34.116321] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net5211'
[   34.116849] ndiswrapper (load_wrap_driver:112): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
[   34.116914] usbcore: registered new interface driver ndiswrapper
[  161.972070] usbcore: deregistering interface driver ndiswrapper
[  161.972296] ndiswrapper (ntoskernel_exit:2708): object ffff810037ba8c30(2) was not freed, freeing it now
[  177.386348] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  177.400260] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  177.400270] ndiswrapper (load_sys_files:210): couldn't prepare driver 'net5211'
[  177.400903] ndiswrapper (load_wrap_driver:112): couldn't load driver net5211; check system log for messages from 'loadndisdriver'
[  177.400964] usbcore: registered new interface driver ndiswrapper


Here is the stuff. I would prefer to go with the solution that is more likely to work. Sorry for the long delay in the post.

---

### Post by pytheas22 on 2008-08-10
Thanks for the information.

I guess the Windows driver that you have installed now is 32-bit (the place I downloaded it from said it was 64-bit, but I guess it lied), which is the problem.  But I don't know of any other 64-bit drivers beyond what you've already tried, which wouldn't work with ndiswrapper.

If you want the easiest solution, it's to reinstall Ubuntu using the 32-bit version instead of 64-bit.  Then ndiswrapper should almost definitely work with no problems.  The downside of this of course is that a 32-bit system is not quite as fast, and it may be inconvenient to you to reinstall Ubuntu (if you already have a lot of your stuff configured there).

The other possible solution is to compile ndiswrapper from source, but as I said, there's no guarantee that that will solve the problem.

Let me know what you want to do and we can go from there.

---

### Post by Kray378 on 2008-08-10
I think I'll go with the reinstall. What do I need to do to make sure the 32 bit driver is install.

---

### Post by pytheas22 on 2008-08-10
> I think I'll go with the reinstall. What do I need to do to make sure the 32 bit driver is install.

Alright.  First, obviously, install 32-bit Ubuntu by downloading the 32-bit ISO from ubuntu.com and burning it to a CD.

Once you've got 32-bit Ubuntu installed, run these commands and the wireless should work (make sure you have an ethernet connection first and have enabled the repositories in System>Administration>Software Sources):
```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*
wget ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
```

Then reboot, and your wireless should work.

---

### Post by TDragon on 2008-08-11
> **pytheas22 said:**
> madwifi already comes built into Ubuntu, so if your card doesn't "just work" out-of-the-box, madwifi probably doesn't support it (it supports most Atheros cards, but there are some exceptions). It may help to download the latest version--the one in Ubuntu is a few months old--but chances are that you will instead have to use ndiswrapper, a program to drive your wireless using the Windows drivers for your card.
 
In order to figure out the exact model of your card and find out how to make it work in Linux, please post the output of these commands:
```

lspci -nn
lsusb
lshw -C Network
```
 
 
 
That isn't necessarily true. I have a wireless card (DWA-552, draft-N) that did not work when initally used w/ Ubuntu. I had to download the latest version of madwifi (especially if your card needs the ath9k support), and my card worked.

---

### Post by pytheas22 on 2008-08-11
> That isn't necessarily true. I have a wireless card (DWA-552, draft-N) that did not work when initally used w/ Ubuntu. I had to download the latest version of madwifi (especially if your card needs the ath9k support), and my card worked.

This is true, and you can try to compile the latest madwifi if you like, but I don't think it's likely to help (I think I remember doing research on the original poster's card and wasn't able to find anything that said that madwifi would support it).  Also I thought the ath9k stuff is still not stable--does it really work fine for you?

In any case, we can at least get the card going with ndiswrapper, and then if you like, we can also try using madwifi (by disabling ndiswrapper, but keeping it installed so you can easily switch back).  Or if you're happy enough with ndiswrapper, you can stick with that.

---

### Post by TDragon on 2008-08-11
> **pytheas22 said:**
> This is true, and you can try to compile the latest madwifi if you like, but I don't think it's likely to help (I think I remember doing research on the original poster's card and wasn't able to find anything that said that madwifi would support it).  Also I thought the ath9k stuff is still not stable--does it really work fine for you?

In any case, we can at least get the card going with ndiswrapper, and then if you like, we can also try using madwifi (by disabling ndiswrapper, but keeping it installed so you can easily switch back).  Or if you're happy enough with ndiswrapper, you can stick with that.



The driver works very well for the card, but will need to be reinitialized once in a while (not often). I attempted to run ndiswrapper with d-link's drivers and caused my OS to become unstable. In fact, I couldn't get on the internet w/ the wrapper (which is nothing new for many Ubuntu Hardy users). If there was a better, native driver out there, I would be using it.

---

### Post by Kray378 on 2008-08-12
I'm sorry to say that my wireless is still not working. I'm sorry for all the trouble I'm making you go through but I do appreciate the help. Is there anything else I can do to get this working?

---

### Post by pytheas22 on 2008-08-12
> I'm sorry to say that my wireless is still not working. I'm sorry for all the trouble I'm making you go through but I do appreciate the help. Is there anything else I can do to get this working?

Don't worry, I just want to see it work.  I know that it works for your chipset on 32-bit, so please post the output of:
```

ndiswrapper -l
dmesg | grep -e ndis
iwlist scan
lshw -C Network
```

and hopefully we can figure out why it still doesn't want to work.  I'm sorry we're not there yet, but we should be a lot closer now that you're running 32-bit Linux.

---

### Post by Kray378 on 2008-08-13
Okay, here they are.

ndiswrapper -l 
net5211 : driver installed 
	device (168C:001C) present (alternate driver: ath_pci) 

iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

 lshw -C Network 
WARNING: you should run this program as super-user. 
  *-network               
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:0e:00.0 
       logical name: eth0 
       version: 01 
       serial: 00:1e:ec:01:86:87 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 
  *-network UNCLAIMED 
       description: Ethernet controller 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:14:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0

---

### Post by pytheas22 on 2008-08-13
It looks like the ndiswrapper is not loaded.  If you type:
```

sudo modprobe ndiswrapper
sudo ifconfig wlan0 up
```

can you see wireless networks then?  If not, please post the output of:
```

dmesg | grep -e ndis -e wlan
uname -m
```

---

### Post by Kray378 on 2008-08-13
Thankyou so much for the help man, it's finally working, with one little problem though. It doesn't seem to want to accept my passphrase no matter how many times I try. I checked to make sure it was right.

---

### Post by pytheas22 on 2008-08-13
Well I'm glad to hear you've finally gotten this up, after all that...and sorry we couldn't get this working on 64-bit; I know it's dumb to compromise your processor's resources just because of a wireless card.  Hopefully by the next release of Ubuntu madwifi will be supporting your card and you won't have to deal with all of this ndiswrapper stuff.

Anyway, I'm not sure why it keeps asking for the passphrase, but I'd bet it's a problem with Network Manager.  You could see if [wicd]("http://wicd.sourceforge.net") works better; it does for many people.

If wicd doesn't help, please post the output of:
```

iwlist scan
```

and also, if possible, please turn off encryption on your router temporarily and see if you can connect then.

Also, right now, if you reboot, ndiswrapper won't work till you run "sudo modprobe ndiswrapper" again.  To avoid having to run that command each time you restart, run this once:
```

echo 'ndiswrapper' | sudo tee -a /etc/modules
```

and ndiswrapper should be loaded at boot, like it's supposed to.

---

### Post by Kray378 on 2008-08-13
Man, your awesome. If it weren't for you, I wouldn't be using my wireless right now. Just to let you know, wicd doesn't pick up my wireless internet but I figured out if I went to manual connection in the default program and entered the info that way, it worked. Thank you for all of your help.

---

### Post by acreech on 2008-08-17
> 
Then reboot and see if your wireless works.  If not, please post:
```

ndiswrapper -l
lsmod | grep ndis
iwlist scan
```

I have been out of town and unable to post the results. Your suggestion did not seem to help me with the wireless card. As I have read through this entire thread I see that the easiest solution to this problem is to reinstall with a 32 bit Ubuntu instead of the 64 bit (which I am willing to do). Can you give me the instructions that I will need to get and install the driver for my system with the 32 bit Ubuntu? below is the commands that you asked for. Thanks for the help. 

> 
ndiswrapper -l


> 
netathrx : driver installed
	device (168C:001C) present (alternate driver: ath_pci)


> 
lsmod | grep ndis


> 
ndiswrapper           243872  0 
usbcore               169904  6 ndiswrapper,uvcvideo,usbhid,ohci_hcd,ehci_hcd


> 
iwlist scan


> 
lo        Interface doesn't support scanning.

ath0      Interface doesn't support scanning.


---

### Post by pytheas22 on 2008-08-17
> Can you give me the instructions that I will need to get and install the driver for my system with the 32 bit Ubuntu?

Sure.  Install 32-bit Ubuntu, then run these commands (they assume that you have a working ethernet connection; if that's impossible, let me know):
```

sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*
wget ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip
unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules
```

Then reboot and it should work.  If not, please post:
```

ndiswrapper -l
lshw -C Network
dmesg | grep ndis
```

Unfortunately it doesn't seem possible to make this card work on a 64-bit kernel right now, because ndiswrapper doesn't like the 64-bit Windows driver.  Hopefully madwifi will support the device soon, though, and all this ndiswrapper stuff will no longer be necessary.

---

### Post by acreech on 2008-08-18
Thank you for the help. Reloading the system with the 32 bit and using those codes for my drivers made the wireless network card work. 

Thank you for the help. Hopefully they will get the 64 bit OS fixed in the next editions.

---

### Post by pytheas22 on 2008-08-18
I'm glad it worked (for both Kray and acreech.  Hopefully Ibex will support this card natively on 64-bit...but unfortunately as I understand it, madwifi depends on a proprietary, closed-source compatibility layer distributed by Atheros, so we have to wait for them to release an update of the 64-bit layer before madwifi can support this card.

...another example of why we're better off with free software, where no one has to wait on some corporation to decide that it's going to let you do what you want with your computer :)

---

### Post by nicedude on 2008-08-18
To anyone that has a AR5007 Atheros wifi adapter and wants to get it going using the Madwifi drivers I have written a guide that is step by step and if you follow it to the letter you will have WIFI. The driver I link to there is also aircrack patched and supports Injection as well as the latest Ubuntu Kernel. Just remember it is only for AR5007 Atheros adapters not other Atheros adapters. Just thought I should post here as many have this problem still.

MY AR5007 MADWIFI INSTALL GUIDE
[http://ubuntuforums.org/showthread.php?t=795984](http://ubuntuforums.org/showthread.php?t=795984)

Hope this helps someone here

---

