---
title: "Help install Modem dial up connection"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by CoreyB. on 2008-10-30
New to Ubuntu.  Just installed 8.10 and am trying to use my modem for a dial up connection.  I used scanModem and it gave me the ModemData.txt file, I have no idea what to look for in the txt file.  If anyone could help that would be awesome.

---

### Post by ets2006 on 2008-10-30
what modem are you using?

---

### Post by ets2006 on 2008-10-30
ok i have opened it. i assume that your modem is inside your pc (on the motherboard or expansion card)

---

### Post by CoreyB. on 2008-10-30
> **ets2006 said:**
> what modem are you using?

In windows, it says I have a Conexant HDA D330 MDC V.93 Modem.

ModemData txt file:

 Only plain text email is forwarded by the  [email]Discuss@Linmodems.org[/email] List Server,
 as HTML can contain viruses. Use as the email Subject Line:
           YourName, YourCountry  kernel 2.6.27-7-generic 
 With this Subject Line cogent experts will be alerted, and useful case names left in the Archive.
 YourCountry will enable Country specific guidance. Linux experts in YourCountry 
 can be found through: [http://www.linux.org/groups/index.html](http://www.linux.org/groups/index.html).
They will know your Country's modem code, which may be essential for dialup service.
Responses from [email]Discuss@Linmodems.org[/email] are sometimes blocked by an Internet Provider mail filters.
 So in a day, also check the Archived responses at [http://www.linmodems.org](http://www.linmodems.org) 
--------------------------  System information ----------------------------
CPU=i686,  
Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008
 scanModem update of:  2008_10_24

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 05dc:a710 Lexar Media, Inc. 
 ID 1d6b:0002 Linux Foundation 2.0 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0002 Linux Foundation 2.0 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub

USB modems not recognized

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:284b	1028:022f	Audio device: Intel Corporation 82801H 

 Modem interrupt assignment and sharing: 
 21:       1306       1307   IO-APIC-fasteoi   uhci_hcd:usb2, uhci_hcd:usb5, HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.568215] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fe9fc000, fe9fffff]
[    0.568272] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.568277] pci 0000:00:1b.0: PME# disabled
[   12.236651] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   12.236674] HDA Intel 0000:00:1b.0: setting latency timer to 64

 The PCI slot 00:1b.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 


===== Advanced Linux Sound Architecture (ALSA) diagnostics ===== 
The ALSA packages provide audio support and also drivers for some modems.
ALSA diagnostics are written during bootup to /proc/asound/ folders.

The ALSA verion is 1.0.17
The modem cards detected by "aplay -l"  are: None


The /proc/asound/pcm file reports:
-----------------------
00-00: STAC92xx Analog : STAC92xx Analog : playback 1 : capture 3
00-03: ATI HDMI : ATI HDMI : playback 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9fc000 irq 21

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset  detected on
NAME="Audio device: Intel Corporation 82801H "
CLASS=0403
PCIDEV=8086:284b
SUBSYS=1028:022f
IRQ=21
HDA=8086:284b
SOFT=8086:284b.HDA
ArchivedChip=0x14f12bfa
CodecClass=14f1
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801H 
      Primary device ID:  8086:284b
    Subsystem PCI_id  1028:022f 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 0x14f12bfa
                        
      

Support type needed or chipset:	hsfmodem


Writing DOCs/Intel.txt

For owners of a Dell PCs with Conexant HSF modems, a driver source package with full speed enabled is available, but requires driver compiling. Read DOCs/Conexant.txt


Start at [http://www.linuxant.com/drivers/hsf/downloads-license.php](http://www.linuxant.com/drivers/hsf/downloads-license.php) to find the
hsfmodem package matching your System. For several Linux distros, there are
precompiled drivers matched to specific kernels. These have within the FileName,
your KernelVersion:	2.6.27_7_generic
They can be found through [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) 
A more precise location may be given a few paragraphs below.
If an EXACT Match with your your KernelVersion is not found, one of the 
"Generic packages with source" near the bottom of the page must be used.
Downloaded packages must be moved into the Linux partition (home folder is OK)
and unzipped with:
	unzip hsf*.zip
The installation command for a .deb suffic packages is, with root/adm permission:
  sudo dpkg -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm

Support for Conexant chips hosted on High Definition Audio cards may require
installation of additional packages, one of the alsa-driver-linuxant packages
on  [http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)  At the same time download the 
alsa-driver-1.0.17-1.patch , in case it prove to be later needed. During the
hsfmodem install, there will be a message if there is necessary installation of
alsa-driver-linuxant

The installation command for a .deb suffic packages is, with root/adm permission:
  sudo alsa* -i hsf*.deb
while for .rpm suffix it is, with:
  rpm -i hsf*.rpm

There may a message that "Dependencies" are not satisfied.  In this case the Ubuntu/Debian packages to be installed are linux-libc-dev & libc6-dev. Package
names may be different for other Linuxes. If not on your install CD, these
packages can be searched for at [http://packages.ubuntu.com](http://packages.ubuntu.com).  After download,
they can be coinstalled with:
	sudo dpkg -i li*.deb
Again try the alsa-driver-linuxant

There may be a message that the patch must be applied.  In this case get the
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2) 
Under Linux, this package is unpacked with:
$ tar jxf alsa*.tar.bz2
Next the patch is applied with:
$ patch -p0 < alsa-driver-1.0.17-1.patch

See [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00838.html)
for details on compiling and installing replacement snd-hda-intel + its
dependent drivers.
After the installation is completed, rerun the hsfmodem installation.
Reboot and try to detect the modem with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.12full_k2.6.27_7_generic_ubuntu_i386.deb.zip 
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


 Completed candidate modem analyses.

 The base of the UDEV device file system is: /dev/.udev

 Versions adequately match for the compiler installed: 4.3.2
             and the compiler used in kernel assembly: 4.3.2


 
 Minimal compiling resources appear complete:
   make utility - /usr/bin/make
   Compiler version 4.3
   linuc_headers base folder /lib/modules/2.6.27-7-generic/build

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
Once downloaded and transferred into a Linux partition,
they can be installed alltogether with:
$ sudo dpkg -i *.deb


Checking pppd properties:
	-rwsr-xr-- 1 root dip 273064 2008-10-15 20:51 /usr/sbin/pppd

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

### Post by ets2006 on 2008-10-30
try opening system>administartion>network
you may have to click on "unlock" and then look for your modem

---

### Post by ets2006 on 2008-10-30
ubuntu 8.10 should automatically detect your modem, this could be a configuration error

under network there should be a modem connection. you will need the numbers to dial etc..
if you cant see the modem then it's a driver issue, otherwise you should probably check your dialing settings with your ISP.

---

### Post by CoreyB. on 2008-10-30
> **ets2006 said:**
> ubuntu 8.10 should automatically detect your modem, this could be a configuration error

under network there should be a modem connection. you will need the numbers to dial etc..
if you cant see the modem then it's a driver issue, otherwise you should probably check your dialing settings with your ISP.

I don't have a System->Administration->Network.  I have Network Tools, but not Network.

---

### Post by Irihapeti on 2008-10-30
If you have a Conexant modem, you'll need to install a driver package. [https://www.linuxant.com/](https://www.linuxant.com/) has more information. Note that you need to purchase a license if you want full speed.

Linuxant has several tools available (free) to help you sort out exactly which driver you'll need. If you want to use the "installer", back up your browser profile first; when I used it, it corrupted the profile.

I've been using these drivers for 15 months and I've found they work well.

Edit: Should also say that, unless Network Manager has been fixed in Intrepid, it doesn't work with dialup modems. I have used pppconfig (already installed) and Gnome-PPP to get internet access.

---

### Post by phidia on 2008-10-30
Just in case you need it there is a Ubuntu wiki entry for that make modem [here]("https://help.ubuntu.com/community/DialupModemHowto/Conexant").

As the irihapeti mentioned you do need to open a terminal and run pppconfig. That will create files and do the configuration for ppp to work correctly. Gnome-ppp is not installed by default so you need to use wvdial or pon to dial out. Once you have a connection you can use apt to install gnome-ppp.

---

### Post by CoreyB. on 2008-10-30
> **Irihapeti said:**
> If you have a Conexant modem, you'll need to install a driver package. [https://www.linuxant.com/](https://www.linuxant.com/) has more information. Note that you need to purchase a license if you want full speed.

Linuxant has several tools available (free) to help you sort out exactly which driver you'll need. If you want to use the "installer", back up your browser profile first; when I used it, it corrupted the profile.

I've been using these drivers for 15 months and I've found they work well.

Edit: Should also say that, unless Network Manager has been fixed in Intrepid, it doesn't work with dialup modems. I have used pppconfig (already installed) and Gnome-PPP to get internet access.

Bummer, is there any other way than to purchase a driver?

---

### Post by phidia on 2008-10-30
You can buy a external or hardware modem.
Most modems were designed to work with the windows OS. That is hardware parts were eliminated and software was used instead.

Most serial external modems work well with linux.

---

### Post by CoreyB. on 2008-10-30
I installed the driver free version of the driver you provided from Linuxant.  How do I set up my dialup connection?  How do I know that it installed correctly?  How come I don't have the System->Administration->Network option?

---

### Post by Irihapeti on 2008-10-30
I find the best way to configure a dialup connection is with pppconfig. To access it, open a terminal (Applications -> Accessories -> Terminal) and type the command

```
 sudo pppconfig
```

You will need to enter your password.

The program will ask you for a load of stuff such as phone number, username, password etc. When you set up the driver, it will have told you what the modem device name is; mine is /dev/ttySHSF0. You'll need to put this information in the "com" field.

Save the configuration as "provider" (without the quotes). Then you can connect simply by typing the command "pon" in a terminal and "poff" to disconnect.

Gnome-PPP is easier to use, but my experience with several versions of Ubuntu is that if I don't set up pppconfig first, Gnome-PPP will connect and then immediately hangup. I don't know why this is.

Hope that helps. If it needs simplifying, let me know.

---

### Post by CoreyB. on 2008-10-31
> **Irihapeti said:**
> I find the best way to configure a dialup connection is with pppconfig. To access it, open a terminal (Applications -> Accessories -> Terminal) and type the command

```
 sudo pppconfig
```

You will need to enter your password.

The program will ask you for a load of stuff such as phone number, username, password etc. When you set up the driver, it will have told you what the modem device name is; mine is /dev/ttySHSF0. You'll need to put this information in the "com" field.

Save the configuration as "provider" (without the quotes). Then you can connect simply by typing the command "pon" in a terminal and "poff" to disconnect.

Gnome-PPP is easier to use, but my experience with several versions of Ubuntu is that if I don't set up pppconfig first, Gnome-PPP will connect and then immediately hangup. I don't know why this is.

Hope that helps. If it needs simplifying, let me know.

Simplifying it would be great, thanks.

---

### Post by Irihapeti on 2008-10-31
OK, fair enough about simplifying. It's sometimes difficult to gauge how much someone knows already.

First of all, which driver do you have? Is it hsfmodem or hcfmodem? I use hsfmodem, and I'm not familiar with the other one. Probably they are set up very similarly, though.

I'll assume for the moment that you have hsfmodem. Open a terminal and enter the command
```
sudo hsfconfig -i
```
You should then get an output that includes "Config for modem unit 0" (or whatever). Could you post that here, leaving out any personal details, of course. (If you've not purchased a license, there shouldn't be any personal info.)

In the meantime I'll go offline and write up some further instructions, or at least see if I can find a useful link.

Irihapeti

---

### Post by CoreyB. on 2008-10-31
I ran the command and it said that the command could not be found.  I may have not installed the driver correctly.  I tried the hsfmodem one because I thought that was mentioned in my ModemData.txt file.  I tried to reinstall the driver but there was some sort of error when I tried that.  This is so frustrating.

The first step is to probably make sure I installed the driver correctly.  I do I uninstall it, the only option is to reinstall it.

---

### Post by phidia on 2008-10-31
> **CoreyB. said:**
> I ran the command and it said that the command could not be found.  I may have not installed the driver correctly.  I tried the hsfmodem one because I thought that was mentioned in my ModemData.txt file.  I tried to reinstall the driver but there was some sort of error when I tried that.  This is so frustrating.

The first step is to probably make sure I installed the driver correctly.  I do I uninstall it, the only option is to reinstall it.

Looking back I believe you have the hcf modem so the hsf command couldn't work. You would probably have the best luck with that modem by going to [this link]("http://www.conexant.com/support/md_driverassistance.html"), agreeing to the EULA and using the method for your specific modem.

---

### Post by Irihapeti on 2008-10-31
CoryB: You could use this link: [https://www.linuxant.com/drivers/hsf/downloads-installer.php](https://www.linuxant.com/drivers/hsf/downloads-installer.php) It will tell you what driver you need.

If you do, I strongly suggest you backup your Firefox profile first (just show hidden files, then make a copy of your .mozilla directory). The installer works well, but it corrupted my profile and I had to replace it.

The hcfmodem driver should be downloadable from linuxant as well.

I'll wait to see how you get on before I post my instructions on setting up pppconfig. Also, I have phone call with someone shortly and it could take a while.

Irihapeti

---

### Post by CoreyB. on 2008-10-31
> **Irihapeti said:**
> CoryB: You could use this link: [https://www.linuxant.com/drivers/hsf/downloads-installer.php](https://www.linuxant.com/drivers/hsf/downloads-installer.php) It will tell you what driver you need.

If you do, I strongly suggest you backup your Firefox profile first (just show hidden files, then make a copy of your .mozilla directory). The installer works well, but it corrupted my profile and I had to replace it.

The hcfmodem driver should be downloadable from linuxant as well.

I'll wait to see how you get on before I post my instructions on setting up pppconfig. Also, I have phone call with someone shortly and it could take a while.

Irihapeti

Thanks for your help Irihapeti, but this is too much of a hassle.  I found a simpler solution.  I dial in with my XP computer, and share the connection with Ubuntu.  That way, I don't have to pay and I get full speed.  Thanks for your help though, and sorry to waste so much of your time.

---

### Post by Irihapeti on 2008-10-31
> **CoreyB. said:**
> Thanks for your help Irihapeti, but this is too much of a hassle.  I found a simpler solution.  I dial in with my XP computer, and share the connection with Ubuntu.  That way, I don't have to pay and I get full speed.  Thanks for your help though, and sorry to waste so much of your time.

CoreyB, you're most welcome, and I don't see it as a waste of my time. I've learned a few things as a result, which I may be able to use to help other people. Definitely, dialup in Ubuntu (Linux generally, actually) can be a hassle. If you've got a working connection, that's the main thing. Go ahead and enjoy.

Irihapeti

---

