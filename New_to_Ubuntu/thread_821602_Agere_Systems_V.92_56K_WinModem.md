---
title: "Agere Systems V.92 56K WinModem"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by sameer.india on 2008-06-07
I have seen people talk about making it work on the forums but on my laptop I have ubuntu 7.10 on which scanmodem doesn't detect my modem. Does anyone have any Ideas.

---

### Post by sameer.india on 2008-06-07
anybody has any answers????????????

---

### Post by sameer.india on 2008-06-07
nobody????????

---

### Post by rapattack1 on 2008-06-07
I have sometimes been able to get dialup modems to work with Ubuntu but only external modems or pcmcia and that is all. Winmodems have never worked for me. I had one that was agere last year and scanmodem didn't help.

---

### Post by sameer.india on 2008-06-09
This is the output of scanmodem


 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008
 scanModem update of:  2008_06_05

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
 ID 04f2:b008 Chicony Electronics Co., Ltd 
 ID 10fd:2535 Anubis Electronics, Ltd 
 ID 0471:0845 Philips 
 ID 0a5c:2101 Broadcom Corp. 

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	17aa:3837	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 21:     170943          2   IO-APIC-fasteoi   ohci1394, sdhci:slot0, HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   20.020000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   20.020000] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:1b.0 has a High Definition Audio Card

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-01: ALC262 Digital : ALC262 Digital : playback 1
00-00: ALC262 Analog : ALC262 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4340000 irq 21
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

A candidate modem is not evident among the PCI devices:
------------------------------------------------
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
------------------------------------------------
 with USB and bridge devices not displayed.

 If your modem is connected by an external serial cable,
 or mounted internally on an ISA card, scanModem would not access it. 
 Try with Root permission
 $ sudo wvdialconf  /etc/wvdial.conf
 to detect these modem types and some USB modems.
 If the detection is successful, read the DOCs/wvdial.txt .
 Edit the /etc/wvdial.conf with Root permission:
 	sudo  gedit  /etc/wvdial.conf
  will be able to dial out with Root permission:
	sudo wvdial

 Many modems for which scanModem fails have Conexant chips. 
 From [http://www.linuxant.com/drivers/modemident.php](http://www.linuxant.com/drivers/modemident.php)
 get the ListModem tool, which will report on Conexant chipset modems

 If the above tests fail, please provide any independent information available on your modem.
 If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information. From the Driver Details TAB, copy out the VENdor and DEVice information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAsameer.tgz

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
CLASS="Class 0403: 8086:27d8"
NAME="Audio device: Intel Corporation 82801G "
SUBSYS=17aa:3837
PCIDEV=8086:27d8
IRQ=21
HDA=8086:27d8
SOFT=8086:27d8.HDA


 High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem, 
 and many are supported by the ALSA audio+modem driver snd-hda-intel
 A modem was not detected on HDA card 8086:27d8.
 If another modem card is present, then most likely 8086:27d8 does not host a modem.
 If another modem card has not been detected, then possibilities are:
	1) A Conexant modem chip is present on 8086:27d8, as Conexant chips
 are frequently not detectable by ALSA diagnostics
	2) The modem may be of the older non-PCI Controller Chipset (hardware) type.
Try detection with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 For candidate modem in:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  17aa:3837 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.1.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

----------------end Softmodem section --------------

Writing DOCs/Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.07full_k2.6.22_14_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt

Writing DOCs/Smartlink.txt
============ end Smartlink section =====================


 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.3
             and the compiler used in kernel assembly: 4.1.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.22-14-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,
 linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 
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
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-05 01:27 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 eth1
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by sameer.india on 2008-06-09
This is the output of scanmodem


 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.22-14-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008
 scanModem update of:  2008_06_05

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
 ID 04f2:b008 Chicony Electronics Co., Ltd 
 ID 10fd:2535 Anubis Electronics, Ltd 
 ID 0471:0845 Philips 
 ID 0a5c:2101 Broadcom Corp. 

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	17aa:3837	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 21:     170943          2   IO-APIC-fasteoi   ohci1394, sdhci:slot0, HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   20.020000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[   20.020000] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.
 PCI slot 00:1b.0 has a High Definition Audio Card

The ALSA verion is 1.0.16
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-01: ALC262 Digital : ALC262 Digital : playback 1
00-00: ALC262 Analog : ALC262 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd4340000 irq 21
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

A candidate modem is not evident among the PCI devices:
------------------------------------------------
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
------------------------------------------------
 with USB and bridge devices not displayed.

 If your modem is connected by an external serial cable,
 or mounted internally on an ISA card, scanModem would not access it. 
 Try with Root permission
 $ sudo wvdialconf  /etc/wvdial.conf
 to detect these modem types and some USB modems.
 If the detection is successful, read the DOCs/wvdial.txt .
 Edit the /etc/wvdial.conf with Root permission:
 	sudo  gedit  /etc/wvdial.conf
  will be able to dial out with Root permission:
	sudo wvdial

 Many modems for which scanModem fails have Conexant chips. 
 From [http://www.linuxant.com/drivers/modemident.php](http://www.linuxant.com/drivers/modemident.php)
 get the ListModem tool, which will report on Conexant chipset modems

 If the above tests fail, please provide any independent information available on your modem.
 If an alternative boot into Microsoft windows can be done, do mouse
clicks on:
   Start > Settings > Control Panel > Classical View (for Window XP) > System
> Hardware > Device Manager > Modems > Click on the + > Modem. Double click to
expand the graphic. Manufacturer information may be displayed. For example, CXT
stands for Conexant. Click the Diagnostics Tab. Record any hardware ID or vendor
and device information. From the Driver Details TAB, copy out the VENdor and DEVice information.
Next do the Query Modem and record the ATI specifications displayed such as:
    ATI3 - Agere SoftModem Version 2.1.22
    ATI5 - 2.1.22, AMR Intel MB, AC97 ID:SIL REV:0x27
Try to identify the modem setup file, with name perhaps MODEM.INF.
If may contain chipset Vendor informaton.

 The /proc/asound/ audio+modem diagostics are being copied.
 Finished copy to Modem/ALSAsameer.tgz

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
CLASS="Class 0403: 8086:27d8"
NAME="Audio device: Intel Corporation 82801G "
SUBSYS=17aa:3837
PCIDEV=8086:27d8
IRQ=21
HDA=8086:27d8
SOFT=8086:27d8.HDA


 High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem, 
 and many are supported by the ALSA audio+modem driver snd-hda-intel
 A modem was not detected on HDA card 8086:27d8.
 If another modem card is present, then most likely 8086:27d8 does not host a modem.
 If another modem card has not been detected, then possibilities are:
	1) A Conexant modem chip is present on 8086:27d8, as Conexant chips
 are frequently not detectable by ALSA diagnostics
	2) The modem may be of the older non-PCI Controller Chipset (hardware) type.
Try detection with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 For candidate modem in:  00:1b.0
   Class 0403: 8086:27d8 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  17aa:3837 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.1.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

----------------end Softmodem section --------------

Writing DOCs/Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.07full_k2.6.22_14_generic_ubuntu_i386.deb.zip 
 Under Linux unpack with:
 $ unzip hsfmodem*.zip
 Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.
 
 Read DOCs/Conexant.txt

Writing DOCs/Conexant.txt

Writing DOCs/Smartlink.txt
============ end Smartlink section =====================


 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.1.3
             and the compiler used in kernel assembly: 4.1.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.1
   linuc_headers base folder /lib/modules/2.6.22-14-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are libc6-dev (and for Debian/Ubuntu,
 linux-libc-dev). The also required headers of package libc6 are commonly installed by default. 
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
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 269256 2007-10-05 01:27 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 eth1
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
==========================================================

 Checking for modem support lines:
 --------------------------------------
     /device/modem symbolic link:   
slmodemd created symbolic link /dev/ttySL0:  
     Within /etc/udev/ files:

     Within /etc/modprobe.conf files:
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by madjr on 2008-06-09
here is a good modem you can buy, works out of the box no configuration

Actiontec USB/Serial 56K External Modem
[http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1198353430&sr=8-1](http://www.amazon.com/Actiontec-USB-Serial-External-Modem/dp/B000EAQ08C/ref=pd_bbs_1?ie=UTF8&s=electronics&qid=1198353430&sr=8-1)


but if you want to do it the hard way here:
[https://wiki.ubuntu.com/SettingUpModems](https://wiki.ubuntu.com/SettingUpModems)

---

