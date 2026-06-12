---
title: "help with dell modem requiring driver bcom_wan_v20"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by midmiwlf on 2008-10-02
I have just received and installed ubuntu 8.04.1 lts desktop and have installed it everything has gone fine so far and am excited to be attempting to switch from windows finally. But upon trying to connect to internet i had to download scanmodem as the directions in installing a modem and found i had a dell modem witch it stated that i needed driver bcom_wan_v20 from dell i went to dell and found it but also found the drivers are only for redhat versions and in an rpm mode is there a driver for this modem for ubuntu ? and where can i find it or is there another way to make this work before im forced to go find another modem?

---

### Post by mrtomservo on 2008-10-02
Well first off, could you open up a terminal and post the output of 
```
sudo lsusb
```
and
```
sudo lspci
```

From there perhaps myself, or someone else could try and figure it out with you. :)

---

### Post by midmiwlf on 2008-10-03
here are the things you asked me to do and any help i can get would be nice and appreciated ty

 Sudo lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0979:0227 Jeilin Technology Corp., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 062a:0000 Creative Labs Optical Mouse 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

sudo lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02) 
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) 
02:02.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem 
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by mrtomservo on 2008-10-03
Could you also post the output of that scanmodem script?  I've seen a couple of people who have gotten this modem to work in Ubuntu, so hopefully we can to.

EDIT: I think we might also need the info from file ModemData.txt.

---

### Post by midmiwlf on 2008-10-04
heres the scanmodem txt.....


--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008
 scanModem update of:  2008_08_26

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0979:0227 Jeilin Technology Corp., Ltd 
 ID 062a:0000 Creative Labs Optical Mouse

USB modems not recognized

For candidate card in slot 02:02.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:02.0	14e4:4212	14e4:0002	Modem: Broadcom Corporation BCM4212 v.90 56k modem

 Modem interrupt assignment and sharing: 
 16:       6008   IO-APIC-fasteoi   uhci_hcd:usb3
 --- Bootup diagnostics for card in PCI slot 02:02.0 ----
[   30.303496] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 16

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 02:02.0:
	Modem chipset  detected on
NAME="Modem: Broadcom Corporation BCM4212 v.90 56k modem"
CLASS=0703
PCIDEV=14e4:4212
SUBSYS=14e4:0002
IRQ=16
IDENT=Broadcom

 For candidate modem in:  02:02.0
   0703 Modem: Broadcom Corporation BCM4212 v.90 56k modem
      Primary device ID:  14e4:4212
 Support type needed or chipset:	Broadcom
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read DOCs/InfoGeneral.txt about alternatives.

----------------end Softmodem section --------------
 Vendor 14e4 is Broadcom [http://www.broadcom.com/](http://www.broadcom.com/) , now focusing on broadband tools.
 14e4:4212 is the PCI id of a  BCM V.90 56k modem
 There is no support under 2.6.n kernels for the 14e4:4212 modems.

 There is a driver for 2.2.n kernels called  BCOM_WAN_V20.
    Search for it at [http://www.dell.com](http://www.dell.com) 
 However the code has not been updated for some time.
 For  2.4 kernels, a fix by Giacomo Comes must be used. See :
   [http://linmodems.technion.ac.il/archive-third/msg01652.html](http://linmodems.technion.ac.il/archive-third/msg01652.html)
   [http://cengique.2y.net/~cengiz/BCMSM/](http://cengique.2y.net/~cengiz/BCMSM/)

 There are BCM Subsystems 14e4:4d64 serving under Intel ICH series softmodem controllers.
 which are supported.  Their AC97 codecs are BCM64 or SIL24.
 Kernels of version 2.6.6 or later are necessary.  See success reports:
   [http://linmodems.technion.ac.il/archive-fifth/msg02486.html](http://linmodems.technion.ac.il/archive-fifth/msg02486.html)
   [http://linmodems.technion.ac.il/archive-fourth/msg03690.html](http://linmodems.technion.ac.il/archive-fourth/msg03690.html)
   [http://oboc.ucdavis.edu/Marik/inspiron/](http://oboc.ucdavis.edu/Marik/inspiron/) 
 The support is typically achieved through the snd-intel8x0m driver, plus slmodemd helper.
 ====== end Broadcom  section =======

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-19-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are needed. The also required headers of package libc6 are commonly installed by default. 
 Compiling hsfmodem drivers does require linux-libc-dev and libc6-dev packages, for kernels 2.6.24 and later versions.
 In not included on your install CD, search for them at [http://packages.ubuntu.com](http://packages.ubuntu.com)
 or comparable Repository for other Linux distros.
 When compiling ALSA drivers, the utility "patch" will also be needed.




If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed packages.
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

### Post by mrtomservo on 2008-10-04
Well, after reading through that text and reading a few other posts of people with the same modem, it doesn't look all that promising after all.  

However, I did find that to get the modem to work you also need to use a package called:
"sl-modem-daemon"
Try installing that and see what happens.  You may need to enable the contrib and non-free repositories to find it.  It seems the modem is access somehow through ALSA drivers, but it requires the sl-modem-daemon too.

---

### Post by midmiwlf on 2008-10-11
well it doesnt work still can not find modem or connect

---

### Post by mrtomservo on 2008-10-11
Yeah, then you're probably going to have to get another modem.  Might I suggest asking around these forums for a suitable one, or you could try this link too.  Sorry I couldn't be of more assistance!

[http://tldp.org/HOWTO/Hardware-HOWTO/modems.html]("http://tldp.org/HOWTO/Hardware-HOWTO/modems.html")

---

