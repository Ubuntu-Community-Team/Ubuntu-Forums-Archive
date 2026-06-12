---
title: "Missing WiFi Firmware"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by doppel.ganger on 2012-06-23
I installed Ubuntu on my friend's Compaq Presario. I don't know the model, but it's pretty old. Anyway, when I was trying to connect to the WiFi, but it said in the menu that firmware was missing. I don't know what firmware it needs. Does anyone know the right firmware and where I can get it?

Thanks!
DG

---

### Post by anewguy on 2012-06-23
Please type the following in a terminal window and post the results back here:

lspci

that will list all of your PCI devices so we hopefully can see what wireless adapter you have.

To be on the safe side, also post the output of:

lsusb

---

### Post by doppel.ganger on 2012-06-23
lspci:

```
theo@Janet-Presario-C500-GF370AV:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01) 
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 01) 
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01) 
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01) 
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01) 
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1) 
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) 
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 01) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01) 
06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
theo@Janet-Presario-C500-GF370AV:~$ 
```

lsusb:

```
theo@Janet-Presario-C500-GF370AV:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
theo@Janet-Presario-C500-GF370AV:~$ 
```

---

### Post by arochester on 2012-06-23
> 06:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 

In a Terminal. Connected to the Internet. Issue this command: > sudo apt-get install b43-fwcutter firmware-b43-installer

After it installs disconnect your wired connection and restart your computer.

---

### Post by doppel.ganger on 2012-06-23
That worked! Thank you SOOOOO much!

---

### Post by weidnerr on 2012-07-11
Thank you for mentioning disconnect wired connection....I was trying to run the command without being hard wired.
After plugging in the ethernet it worked the first time I rebooted after disconnecting the ethernet cable

---

