---
title: "Deciphering ModemData from the Scan Modem tool"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by jhod on 2008-07-23
Ok have have the modemData but I really don't understand what I am looking for here. Can somebody people help convert this into plain English for me please? :)

Thanks~!
Jill



 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.24-19-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008
 scanModem update of:  2008_07_21

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 04f2:b008 Chicony Electronics Co., Ltd 

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:27d8	1179:ff02	Audio device: Intel Corporation 82801G 

 Modem interrupt assignment and sharing: 
 21:        490          0   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[  165.152133] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 21
[  165.152194] PCI: Setting latency timer of device 0000:00:1b.0 to 64


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda/snd-hda-intel.ko

The ALSA verion is 1.0.15
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: ALC861VD Analog : ALC861VD Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc440000 irq 21
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801G "
CLASS=0403
PCIDEV=8086:27d8
SUBSYS=1179:ff02
IRQ=21
HDA=8086:27d8
SOFT=8086:27d8.HDA
ArchivedChip=0x11c11040
IDENT=11c11040

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801G 
      Primary device ID:  8086:27d8
    Subsystem PCI_id  1179:ff02 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x11c11040
                        
      

Support type needed or chipset:	11c11040

----------------end Softmodem section --------------

Writing DOCs/Intel.txt

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

Read Modem/DOCs/YourSystem.txt concerning other COMM channels: eth0 wlan0 wmaster0
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

---

### Post by phidia on 2008-07-23
Is this an internal/onboard modem? Please post the output of lspci -v?
Thanks, and welcome to Ubuntu.

There is also a specific [Ubuntu guide for dial up modems]("https://help.ubuntu.com/community/DialupModemHowto").

---

### Post by Bachstelze on 2008-07-23
Send this to the [email]discuss@linmodems.org[/email] mailing-list.

---

### Post by jhod on 2008-07-23
Thanks for your replies! I'm going to try emailing it because the other thread was as meaningful to me as if it were written in Greek.

Thankfully, I am only stuck with dial-up for another month. So if all else fails I shall wait until September to kill windows.

---

