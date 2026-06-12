---
title: "help me to install my modem"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by medya on 2008-07-13
hey guys it is the 3rd fax-modem which I buy ,
(because the previous two modems didnt work in linux)

I have both kubuntu 32 and 64 bit CDs****
this new one is , Motorola Speaker phone 56K
kubuntu recognizes it as :
> 04:02.0 Modem: SILICON Laboratories Intel 537 [Winmodem] (rev 04)
 

 I runned scanModem and here is the result :

>  Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-16-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-16-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu Apr 10 13:23:42 UTC 2008
 scanModem update of:  2008_07_12

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 0951:1605 Kingston Technology 
 ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
 ID 0a5c:2045 Broadcom Corp. 
 ID 147a:e02d Formosa Industrial Computing, Inc. 

USB modems not recognized

For candidate card in slot 04:02.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 04:02.0	1543:3052	1543:3000	Modem: SILICON Laboratories Intel 537 [Winmodem] 

 Modem interrupt assignment and sharing: 
 18:          0          0   IO-APIC-fasteoi   uhci_hcd:usb3
 --- Bootup diagnostics for card in PCI slot 04:02.0 ----
[   41.665573] ACPI: PCI Interrupt 0000:04:02.0[A] -> GSI 18 (level, low) -> IRQ 18
[   41.665705] 0000:04:02.0: ttyS1 at I/O 0xd108 (irq = 18) is a 16450
[   41.665792] 0000:04:02.0: ttyS2 at I/O 0xd110 (irq = 18) is a 8250
[   41.665878] 0000:04:02.0: ttyS3 at I/O 0xd118 (irq = 18) is a 16450
[   41.665908] Couldn't register serial port 0000:04:02.0: -28

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	1458:a002	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 16:      15369      15321   IO-APIC-fasteoi   uhci_hcd:usb4, HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[   87.465227] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   87.465238] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-02: ALC883 Analog : ALC883 Analog : capture 1
00-01: ALC883 Digital : ALC883 Digital : playback 1 : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfa100000 irq 16
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 04:02.0:
	Modem chipset  detected on
NAME="Modem: SILICON Laboratories Intel 537 [Winmodem] "
CLASS=0703
PCIDEV=1543:3052
SUBSYS=1543:3000
IRQ=18
IDENT=INTEL537_on_1543:3052

 For candidate modem in:  04:02.0
   0703 Modem: SILICON Laboratories Intel 537 [Winmodem] 
      Primary device ID:  1543:3052
 Support type needed or chipset:	INTEL537_on_1543:3052
 

----------------end Softmodem section --------------

Writing DOCs/Intel.txt


Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
NAME="Audio device: Intel Corporation 82801G "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=1458:a002
IRQ=16
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
   0403 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  1458:a002 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.2.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.2.3
             and the compiler used in kernel assembly: 4.2.3


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.2
   linuc_headers base folder /lib/modules/2.6.24-16-generic/build

 However some compilations and executable functions may need additional files,
 in the FileNames.h (so called kernel "h"eaders) collection installed in  /usr/include/ .
 For martian_modem, additional required packages are n. The also required headers of package libc6 are commonly installed by default. 
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
	-rwsr-xr-- 1 root dip 269256 2007-10-04 19:57 /usr/sbin/pppd

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0
Which can interfere with Browser naviagation.

 Don't worry about the following, it is for experts should trouble shooting be necessary.
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




can you help me what I can do to make it work ?

---

### Post by nowshining on 2008-07-13
u bought winmodems - they are tough to get to work in linux - requires windows drivers. If u can, return it and buy a hardware modem that is **NOT** a winmodem **(check the box) **- that way all u need to do is set-up kppp and dial-in to get the net. Yes if your wondering it will **NOT** be an internal modem.

You can buy a USB or Serial hardware modem or one with both.

---

### Post by medya on 2008-07-14
I am sorry I can not return the modem, isnt any way to make it work ? :( 
I am disappointed with ubuntu

---

### Post by nowshining on 2008-07-14
don't blame ubuntu nor linux, but blame of course the makers of the winmodems for only providing windows drivers and not open sourcing the drivers so linux hackers can get a driver working well with the linux operating system.

---

### Post by cariboo on 2008-07-14
Have you checked to see if the module mentioned in your listing is installed? to do this in a Applications-->Accessories-->Termina type:

```
lsmob | grep snd-hda-intel
```

If it isn't try to load the modlue

```
sudo modprobe snd-hda-intel
```

If the module loads it will not echo anything back. If it loads with no problem in a terminal try:

```
atdt1234567890
```

to see if your modem is working you should here it dialing. If all this works. Try using kppp to set up your modem connection.

Jim

---

