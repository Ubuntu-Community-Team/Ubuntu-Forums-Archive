---
title: "cryptic wifi problem"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by nnjond on 2008-08-20
Hi, Can anyone help me please?

I've Ubuntued over Vista on this laptop only to discover there are wifi complications; I have “the dreaded 
Atheros wireless...“ which requires the installation of:

“ndiswrapper-common
ndiswrapper-utils-1.9 (or whatever version is displayed)
ndisgtk”.

And

net5211.inf

If I managed it correctly, it didn't seem to work.

Alternatively;  “That particular card has various names and Hardy miss-detects it.

The actual card is called the AR5007EG, however in gutsy gibbon ubuntu it was called the AR5006EG, now under hardy heron it is called the AR242x . They're actually the same card...strange but true”


I think I need to get back to sq 1. before I can move on

NB: I want to enable the wifi capability of this Laptop for when I travel as I use a landline at here.


May be this info will put you in the pcture:

nnjond@nnjond-laptop:~$ iwconfig

lo no wireless extensions.

eth0 no wireless extensions.


nnjond@nnjond-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)

08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 04)

nnjond@nnjond-laptop:~$


Thanks.

---

### Post by oldsoundguy on 2008-08-20
My D-Link Atheros wireless cards installed right out of the box.  I have them on two Gutsy machines and I installed using network under the system/administration.  All I had to do was enter the WEP and was on line.  My third Gutsy machine is hard wired via an eithernet card.

BUT ... I installed the wireless cards by going HARD WIRED FIRST to get all updates.  Then installed the wireless .. then disconnected the eithernet.

Router is a DI-624 D-Link.

---

