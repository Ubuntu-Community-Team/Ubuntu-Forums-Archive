---
title: "reinstall graphic drivers"
date: 2013-04-07
forum: New to Ubuntu
---

### Post by ave2 on 2013-04-07
I haven't installed any other drivers, only use the default ones included on setup. After the last update, my screen started flickering when I scroll through a webpage, so I was wondering how to reinstall those default drivers.

---

### Post by ajgreeny on 2013-04-07
More info needed please.

What hardware?  If you have not installed any proprietary drivers the one you have now will simply be the updated version of the one you had at install time, but to know how to proceed we need to know your graphic card.

Let's see the output of **lspci** in terminal please.

---

### Post by ave2 on 2013-04-08
Thank you for your reply. Here is the info you requested: (Thats quite a handy function- I must jot that down somewhere)

00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 03)
00:1a.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 6
00:1d.0 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller #1
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller #2
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV770 [Radeon HD 4850]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI RV770 HDMI Audio [Radeon HD 4850/4870]
02:00.0 Ethernet controller: Atheros Communications Inc. AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b2)
04:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:01.0 Network controller: Atheros Communications Inc. AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn] (rev 01)

---

### Post by ppjdee on 2013-04-08
thats an pretty old gfx card isnt it?
i thought i remember seeing something, somewhere about driver issues for this card...

---

### Post by 3rdalbum on 2013-04-08
The driver version is linked to the kernel version, so to use the older driver you should choose the older kernel version from the GRUB menu.

Unfortunately you are stuck with the open-source graphics driver - AMD no longer makes a driver for that card on Linux.

---

### Post by ave2 on 2013-05-07
Aaah, that's not good news. I'll have to invest in some newer hardware...... Thanks.

---

