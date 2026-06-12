---
title: "Wireless woes"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by rich97 on 2008-10-26
Hi there,

I'm having a few problems trying to get the wireless running on my laptop. I googled around and found a tutorial ([http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html](http://i-eat-noobs.blogspot.com/2007/08/get-wireless-working-in-ubuntu-704.html)) on using ndiswrapper to install windows wireless drivers onto my Ubuntu installation. The thing is I'm a bit new to all this stuff and guess what...it doesn't work.

I'm using i686 Ubuntu 8.04 Hardy. If I use lspci then this is the output I get:

01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
08:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
08:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
08:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

iwconfig returns this:

lo        no wireless extensions.

eth0      no wireless extensions.

What I want to know is how do I test if the driver is installed? If possible could someone find the right driver to use with ndiswrapper? I have one but I'm not sure if it was the right one to download. Finally, once all this is finished can I just click and set up my network settings using the ubuntu network dialog or should I install a seperate program to manage this (I have wifi-radar installed alread)

- Many thanks, Richard Vanbergen

---

### Post by BDNiner on 2008-10-26
Setting up your card is not going to be easy but it is supposed to work with madwifi. check out this link:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

---

### Post by BDNiner on 2008-10-26
If you manage to compile the madwifi drivers then it should work.

---

### Post by Crandom on 2008-10-26
Type this command into a terminal and paste it here:
```
ndiswrapper -i
```
If it says you have hardware present and the driver installed, please paste any "alternative driver" name here and try these commands:
```
sudo rmmod madwifi
sudo depmod -a
sudo modprobe ndiswrapper
```
and see if it works now.

EDIT: Yikes, that tutorial is for Broadcom Cards (like mine), and is going to be different than that needed for atheros cards. Try this generalised Ndiswrapper tutorial that helped me: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by rich97 on 2008-10-26
> **Crandom said:**
> Type this command into a terminal and paste it here:
```
ndiswrapper -i
```
If it says you have hardware present and the driver installed, please paste any "alternative driver" name here and try these commands:
```
sudo rmmod madwifi
sudo depmod -a
sudo modprobe ndiswrapper
```
and see if it works now.

EDIT: Yikes, that tutorial is for Broadcom Cards (like mine), and is going to be different than that needed for atheros cards. Try this generalised Ndiswrapper tutorial that helped me: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I think you meant ndiswrapper -l. -i is for installing new ones :P.

-l returned
netathw : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

First command you wrote said:
ERROR: Module madwifi does not exist in /proc/modules
The others returned nothing. According to the Synaptic packet manager though I have the package madwifi-tools installed, I don't know if it is the same thing. I tried to "make" madwifi but it returned a massive list of errors. according to the README file the Atheros specific module is called "ath_pci" which as you can see is listed in ndiswrapper above again I dont know if this means if it's installed but I can't seem to find any wireless (I don't know how to search for it.)

If you need any more information please just ask.

- Rich

Eidt: I'll look into that turoial in the mean time. :)

---

### Post by rich97 on 2008-10-26
I used dmesg and I got this:

[   50.571353] ndiswrapper (link_pe_images:604): DLL initialize failed for athw.sys
[   50.571389] ndiswrapper: driver netathw (,06/27/2008,7.6.0.239) loaded
[   50.571716] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   50.571732] ndiswrapper (mp_init:207): assuming WDM (non-NDIS) driver

I'm not sure what this means but I'm sure it's not good.

---

### Post by rich97 on 2008-10-26
madwifi wont compile at all. make fails entirely, I'm almost out of ideas.

---

