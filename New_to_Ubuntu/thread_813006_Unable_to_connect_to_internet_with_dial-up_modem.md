---
title: "Unable to connect to internet with dial-up modem"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cotrean on 2008-05-30
## My problem:
I am unable to connect to internet with internal 56k dial-up modem

## My computer:
I have installed ubuntu 7.04 on a Dell 8200 Dimension running XP in a dual boot setup on one existing 160 GB IDE hard drive. I will refer to this computer as XP/ubuntu.

## How I access the internet:
The XP/ubuntu machine has an internal 56k modem: 
Ubuntu > System > Preferences > Hardware Information > Device Manager > BCM4212 v.90 56k modem
Vendor: Broadcom Corporation
Device: BCM4212 v90 56K modem
Bus Type: PCI
OEM Vender: Dell
info.linux.driver: string serial

The XP/ubuntu machine has an ethernet card and is connected to a second Windows 98/Red Hat 8 configured Dell. I can use a dial-up internal modem in each computer to access the internet. I have the XP configured so that when I connect to the internet via its internal 56k serial modem I can share the internet connection with the Windows 98/Red Hat 8 machine. The Red Hat 8 has a Samba configuration so it can be accessed from the XP machine. I can access the internet with Red Hat 8 also through the XP internet connection (I believe because of Samba). I have a fat 32 partition on the XP where I can place files to share when in ubuntu.

## My ISP:
My ISP is pcdialup.com. They are a local service (San Francisco,CA,USA) that charges $5/month for "unlimited" service. I would like to access this service with ubuntu if possible.


## What I have done:
I have downloaded and ran scanmodem on the XP/ubuntu machine, this is the result:

******************************* Start ModemData    **********************************
 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.20-15-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Your contry's local Linux experts
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html). 
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007
 scanModem update of:  2008_05_02

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 046d:0a02 Logitech, Inc. 
 ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
 ID 04b8:0121 Seiko Epson Corp. 

USB modems not recognized
For candidate card in slot 02:08.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:08.0	14e4:4212	1028:0002	Modem: Broadcom Corporation BCM4212 v.90 56k modem 

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 02:08.0 ----
[   23.033541] ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 17 (level, low) -> IRQ 16

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 02:08.0:
	Modem chipset  detected on
CLASS="Class 0703: 14e4:4212"
NAME="Modem: Broadcom Corporation BCM4212 v.90 56k modem "
SUBSYS=1028:0002
PCIDEV=14e4:4212
IRQ=16
IDENT=Broadcom

 For candidate modem in:  02:08.0
   Class 0703: 14e4:4212 Modem: Broadcom Corporation BCM4212 v.90 56k modem 
      Primary device ID:  14e4:4212
 Support type needed or chipset:	Broadcom
 Under Linux 2.6.n kernels, the chipset is NOT SUPPORTED . Read InfoGeneral.txt about alternatives.

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

 Versions adequately match for the compiler installed: 4.1.2
             and the compiler used in kernel assembly: 4.1.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.20-15-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,  linux-libc-dev). The also required headers of package libc6 are commonly installed by default. When compiling ALSA drivers, the utility "patch" will also be needed.



If a driver compilation fails, with message including some lack of some FileName.h (stdio.h for example), then
Some additional kernel-header files need installation to /usr/include. The minimal additional packages are libc6-dev
and any of its dependents, under Ubuntu linux-libc-dev

If an alternate ethernet connection is available,
$  apt-get update
$  apt-get -s install linux-kernel-devel
will install needed package
For Debian/Ubuntu related distributions, run the following command to display the needed package list:

Otherwise packages have to be found through [http://packages.ubuntu.com](http://packages.ubuntu.com)
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269224 2007-04-04 20:41 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
	$ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
	sudo chmod a+x /usr/sbin/pppd

Checking settings of:	/etc/ppp/options
asyncmap 0
noauth
crtscts
lock
hide-password
modem
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
noipx

In case of a message like:
   Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
see [http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/bigarch/archive-sixth/msg04656.html)

Read Modem/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for the experts
 should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------
******************************* End ModemData    **********************************

## What I have done with the scanmodem/ModemData:
I went to Dell and downloaded the available driver but it is specified for red had 7.3 so I have not tried to use in with ubuntu - because it doesn't support the ubuntu kernel.

I have read ModemData information several times and I don't get it.



## Ran the following code:
lspci
lsusb
lshw -C network
sudo dmesg | grep tty

Output to code below:

conley@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 04)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)
02:08.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:09.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
02:0a.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)


conley@ubuntu:~$ lsusb
Bus 002 Device 002: ID 046d:0a02 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 002: ID 04b8:0121 Seiko Epson Corp. 
Bus 001 Device 001: ID 0000:0000  


conley@ubuntu:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: 21x4x DEC-Tulip compatible 10/100 Ethernet
       vendor: Davicom Semiconductor, Inc.
       physical id: a
       bus info: pci@02:0a.0
       logical name: eth0
       version: 31
       serial: 00:08:a1:24:47:18
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=dmfe driverversion=1.36.4 latency=64 maxlatency=40 mingnt=20 multicast=yes
       resources: ioport:d800-d8ff iomemory:ff7fdc00-ff7fdcff irq:17


conley@ubuntu:~$ sudo dmesg | grep tty
[   23.032390] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.033297] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


## Manually configured modem setup in Ubuntu:
System > Administration > Network > Modem connection > Properties

General Tab: 
Phone number: 15455863
Dial Prefix: blank
Username: my username
Password: my password

Modem Tab:
Modem port: /dev/modem
Dial type: Tones
Volume: Low

Options Tab:
Checked Set modem as default route to internet
Checked Use the internet service providers nameservers
Unchecked Retry if the connection breaks of fails to start

Dial Up Connections > Connect to ppp0 via Modem (nothing happens)


## Read multipule threads on this subject.
Seems many people have this same problem. Solutions tend to be to buy a external serial modem or get DSL. These are both possible but I would like to try to use my existing modem. I don't really "need" ubuntu so I am hesitant to spend money, but curious enough to spend time. If I really needed ubuntu I think I would go the DSL route.

## What I have failed to do:
I have gone to ubuntu packages and done a search for a package I "think" I need in fiesty and the search results in a package. My plan is to download the "package" to my XP/ubuntu machine in the fat32 partition, restart into ubuntu, transfer the files to my /home directory and install them into ubuntu.

I click on the package in ubuntu package web site thinking it will produce some sort of file to download, but instead it produces a tree of other "packages". I click on those "packages" and yet another tree of "packages" is produced. I become overwhelmed and quit. Could someone throw some light on this process? 


Please help me?

Thank you,
Conley

---

### Post by shifty_powers on 2008-05-30
[http://ubuntuforums.org/showthread.php?t=161797](http://ubuntuforums.org/showthread.php?t=161797)

any use?

---

### Post by cotrean on 2008-05-30
Thank you for the quick response.

I will need some time to work through this. There is a lot of info there. Seems as if someone has made old dell modem driver work for new kernel in susie, but I wonder if I am capable enough to adapt it to ubuntu. I will give it try. Thank you the help. Will get back with result later today.

Thanks,
Conley

---

### Post by cotrean on 2008-05-31
Trying to create a driver for my internal modem is way over my head. Until I can find some way to access the internet directly with ubuntu, I can not take this OS seriously.

Thanks for your help.
Conley

---

