---
title: "11c1:044e Agere Systems LT WinModem"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by safetycopy on 2008-07-08
Hi everyone,

I'm totally new to Linux, and I'm trying to get my modem set up. I downloaded and ran scanModem (the output of which is below) and think I need martian (I also downloaded this: martian-full-20080617.tar.gz). I've got this far, but now I'm stuck - I need 'for dummies' style instructions please!... I should also mention that presently, I have no internet from Ubuntu.

After I've got my modem working, I need to install nVidia drivers (it says they're installed and they are checked but not being used?). Would EnvyNG be the best way to do this?

Thanks in advance, and here's the ModemData.txt:

___________________________

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
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
 scanModem update of:  2008_06_28

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC 
 ID 045e:0039 Microsoft Corp. IntelliMouse Optical
 ID 109f:7148 eSOL Co., Ltd 

USB modems not recognized

For candidate card in slot 01:0b.0, firmware information and bootup diagnostics are:
 PCI slot    PCI ID        SubsystemID    Name
 ----------    ---------    ---------    --------------
 01:0b.0    11c1:044e    1235:044e    Communication controller: Agere Systems LT WinModem 

 Modem interrupt assignment and sharing: 
===================================
 The modem interrupt (IRQ) is 255 . IRQs of 0 or 255 are not functional!! 
 The CPU cannot control the modem until this situation is corrected!!
 Possible corrections are:
   1) Within the boot up BIOS, change from a Windows to a non-PNP/Other Operating System type.
   Instructions for accessing BIOS are at:
      [http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within:  Additional Resourcces.
   2a) Add an option "pci=routeirq" to the kernel boot up line.
      Here is an example paragraph from  /boot/grub/menu.lst :
    title           Ubuntu, kernel 2.6.15-26-686
    root            (hd0,6)
    kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/hda7 ro pci=routeirq
    initrd          /boot/initrd.img-2.6.15-26-686
    savedefault
   2b) Same as above, but use "pollirq" instead of "pci=routeirq". 
   3) Within some BIOS setups, IRQ assignments can be changed.
   4) On non-laptop systems, moving the modem card to another slot has helped.
   5) Sometimes upgrading the kernel changes IRQ assignment.
=====================================

 --- Bootup diagnostics for card in PCI slot 01:0b.0 ----

=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive diagnostics for card in bus 01:0b.0:
    Modem chipset  detected on
NAME="Communication controller: Agere Systems LT WinModem "
CLASS=0780
PCIDEV=11c1:044e
SUBSYS=1235:044e
IRQ=255
IDENT=Agere.DSP

 For candidate modem in:  01:0b.0
   0780 Communication controller: Agere Systems LT WinModem 
      Primary device ID:  11c1:044e
 Support type needed or chipset:    Agere.DSP
 

----------------end Softmodem section --------------

 The modem has a Lucent/Agere/LSI Mars or Apollo DSP (digital signal processing) chipset. 
Support packages for 2.6.n kernels are at:
 [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/) , with current update martian-full-20071011.tar.gz

 See DOCs/AgereDSP.txt for Details.


 Vendor 11c1 is Lucent Technologies with modem technology now under LSI Inc. 
Their Linux  code developer/maintainer is Soumyendu Sarkar. Support for a chipset and its 
 continued maintenance is only initiated at the request of a major chipset buyer,
 or comparable sponsor. Several different  modem chipset types  are produced: 
 with varying support under Linux.
 Device ID  Support        Name           Comment
 ---------  -------------  -----------    -----------------------------
 0480       serial drivers Venus           controller chipset 1673JV7
 0440-045d  martian        Mars/Apollo     DSP (digital signal processing) chipsets
 0462       none           56K.V90/ADSL Wildwire 
 048d none                  SV2P            soft modem 
 048(c or f) AGRSM         SV2P            soft modem
 0600       none           soft modem, very few in the field.
 0620       AGRSM          Pinball  soft modem, in some HP desktop PCs
 011c11040  AGRSM_RedFlag  Softmodem on some High Definition Audio cards, support only for Red Flag kernel 2.6.21-20
 062(1-3)   none           SV92PP,Pinball  soft modem, in some HP desktop PCs

martian - At [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)
AGRSM - At [http://linmodems.technion.ac.il/packages/ltmodem/sv92/](http://linmodems.technion.ac.il/packages/ltmodem/sv92/) , the agrsm-20080203.tar.gz
AGRSM_RedFlag at  At [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/)
The  suse-10-2a.tar.gz has newer Agere/LSI code, but there are compiling problems with newer kernels/

 0x044e -- Mars 3 Mercury data fax only
-------------- end Agere Systems section -------------------

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
    -rwsr-xr-- 1 root dip 269256 2007-10-04 15:57 /usr/sbin/pppd

In case of an "error 17" "serial loopback" problem, see:
    [http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html](http://linmodems.technion.ac.il/linmodems/archive-sixth/msg02637.html)

To enable dialout without Root permission do:
    $ su - root  (not for Ubuntu)
        sudo chmod a+x /usr/sbin/pppd
or under Ubuntu related Linuxes
    sudo chmod a+x /usr/sbin/pppd

Checking settings of:    /etc/ppp/options
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
/etc/modprobe.d/blacklist-modem:# Uncomment these entries in order to blacklist unwanted modem drivers
/etc/modprobe.d/blacklist-modem:# blacklist snd-atiixp-modem
/etc/modprobe.d/blacklist-modem:# blacklist snd-via82xx-modem
/etc/modprobe.d/alsa-base:options snd-atiixp-modem index=-2
/etc/modprobe.d/alsa-base:options snd-via82xx-modem index=-2
     Within any ancient /etc/devfs files:

     Within ancient kernel 2.4.n /etc/module.conf files:

--------- end modem support lines --------

---

### Post by safetycopy on 2008-07-08
Well - I managed to get the modem working, but now I'm not being properly authenticated when I try to connect to my ISP... I suspect this is an ISP problem though. I'm using Netscape Connect (the crappy WalMart version) and I have no clue what domain to have my username/password authenticated against. So... I suppose it's time to get a new ISP... Schmuckers...

---

### Post by Psychoscorpic on 2008-08-19
Hi Safetycopy

Glad you came right with the modem issue.
If you're still battling to connect, try using PPP to dial for you instead of wvdial. (type: sudo pppconfig) - that did it for me when wvdial would cut the connection saying my password was wrong.

As for nVidia drivers, you can use Envy, but I'd recommend not. Once you're on a live connection to the Web, go to the Restricted Drivers and click the checkbox. That will automatically start the download & installation process for the repository based driver - works very well.
Also avoids hassles later when you upgrade/update Ubuntu to the next release.

---

### Post by mdp25 on 2009-03-17
It looks like I have a problem with my modem similar to yours.
After running scanModem it appears I also have an Agere Systems LT WinModem.  Can you please explain in more detail how you solved your problem?  I just recently started experimenting with Linux after being a Window$ user for many years.

Thank you

---

### Post by Psychoscorpic on 2009-03-18
Hi mdp25

I never did come right after upgrading to 8.10 - but have since changed machines and didn't need to pursue it anymore.

However - try following what I did as outlined at [http://ubuntuforums.org/showthread.php?t=895319](http://ubuntuforums.org/showthread.php?t=895319) with the exception of using [http://linmodems.technion.ac.il/packages/ltmodem/11c11040/agrsm-2.6.27-9-generic_2.6.27-9.14a_i386.deb](http://linmodems.technion.ac.il/packages/ltmodem/11c11040/agrsm-2.6.27-9-generic_2.6.27-9.14a_i386.deb) driver instead (if your system is up to date & uses the 2.6.27-9 kernel)

I only failed back then because there was no updated driver, and I was scared of compiling one.

Hope that helps.

---

