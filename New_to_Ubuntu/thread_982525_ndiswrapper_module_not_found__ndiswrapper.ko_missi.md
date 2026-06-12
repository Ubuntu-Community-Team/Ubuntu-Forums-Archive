---
title: "ndiswrapper module not found / ndiswrapper.ko missing"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by shadowthi3f on 2008-11-14
so I ve been using Linux for a while but only recently have i switched to Ubuntu 8.10 from xUbuntu 8.04. at the time i also reinstalled my windows partition.

but in the course of things i tried to get my wireless working, i have a Netgear WG511 v2 wireless card. i used apt-get to install ndiswrapper-common and -utils-1.9 after installingndisgtk as well and installing the driver from the CD i checked for the driver with *ndiswrapper -l* and the driver was installed and the card was detected. 

at this time *modprobe ndiswrapper* returned an error saying that /lib/modules/2.6.27-7-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko was not found.

on several forums i found instructions that *depmod -a* followed by *modprobe ndiswrapper* would fix this. however after the depmod, modprobe returned the error "FATAL: Module ndiswrapper not found."

*dmesg, sudo lshw -C Network, lsmod | grep ndis* all failed to show any reasons for the error or config problems, i think that the crux ofthe problem was the depmod that made my further attempts to modprobe fail but im not shure.

oddly *lspci* did return this 
> 02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:09.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

not shure what it means

im running a IBM Thinkpad R32 laptop
x86 32-bit Ubuntu 8.10

---

