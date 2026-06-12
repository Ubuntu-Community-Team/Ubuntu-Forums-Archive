---
title: "Dialup in Ubuntu 8.10??"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by nitehawk777 on 2008-11-20
I have been using Ubuntu 8.04 for awhile now,...getting dial-up with my little dial-up ISP seemed pretty easy (and I was able to use Synaptic to also install Gnome PPP).  I had TWO little dial-up services going pretty well.

Well,....I just installed Ubuntu 8.10,...and can't for-the-life-of-me,  find anyplace that I can even _begin_ to configure a little dial-up service!  Has dial-up become obsolete in the new Ubuntu????  Say it isn't so!!!

Or am I just not looking in the right place?:confused:

---

### Post by cek on 2008-11-20
I was hoping 8.10 would have dialup connection settings in the network manager, but that is NOT the case.

The Modem Monitor applet doesn't work either (going to properties gives a general error about not being able to launch the application, though I can find no indication of what application it is trying to start).

That said, you are still able to use the dialup connection with wvdial.

Run wvdialconf, it should detect your modem and create a default wvdial.conf (in /etc/wvdial.conf).  Edit this file to add the phone number, username and password for your ISP.  Then run wvdial to connect.  It's working flawlessly for me.

That said (though I haven't tried) you can still use GnomePP or KPPP to get a GUI interface to setup the pppd parameters.

---

### Post by phidia on 2008-11-20
It sounds like this is a fresh install of 8.10.
Cek is right you can use wvdial to dial out and once you're connected you can download gnome-ppp for easier non-cli access.

If you have problems with wvdial you might need to issue "pppconfig" from a terminal to set things up.

---

### Post by nitehawk777 on 2008-11-20
Thanks for your replys,...
but I'm really "terminally" handicapped  (I don't know very much about using the terminal) if that is how to use "wvdialconf".......:(
I'm still quite a bit of a linux "newbie" and guess all the time I used Ubuntu 8.04,..I was really lazy and used the GUI mostly.

EDIT:  Have been struggling in Ubuntu 8.10 for awhile now,...maybe I MIGHT be able to eventually get dialup working in it (really is a lovely looking update,...isn't it???)  But I don't think Ubuntu is too very friendly to us little newbie "dial-uppers" now,....well,..the world and technical progress moves onward and forward,....(maybe time for me to look elsewhere),.........
At least Puppy Linux (and others, still work for us,...)

---

### Post by Shazaam on 2008-11-20
This works if your dial-up modem is autodetected....
```
gksudo gedit /etc/wvdial.conf
```
This code is- graphical sudo run gedit (as root) the file wvdial.conf. Add your info... (default example)
```
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes
```
Save it (File-Save). Open terminal (Applications>Accessories>Terminal) and  enter this...
```
sudo wvdial
```
This code (using your info you added earlier to wvdial.conf) will connect you to your isp and the internet. Do NOT close terminal or do a CTRL+C as this will disconnect you. Open Software Sources (System>Administration), check all but "Sources" on the first tab and choose "Main server" (or one closer to you). On the second tab (Third-Party Software) check all. On the third tab (Updates) make sure only 1, 2, and 4 are checked (uncheck "Proposed"). Close Software sources. It will pop up a box saying that you need to reload the list. Click cancel.
Go back to (or start another instance of) terminal. Type this in...
```
sudo apt-get update
```
This will update the package list. Once that is done run this...
```
sudo apt-get install gnome-ppp
```
(or sudo apt-get install kppp if you are using kubuntu) This will install the gnome dialer. Configure it. Now you can re-edit wvdial.conf back to default (no info) or not, it shouldn't matter.

---

### Post by cek on 2008-11-20
Shazaam's post is spot on.

First open a terminal, then type:

sudo wvdialconf

Input your password when prompted, hopefully this will autodetect your modem (it should, unless you have a winmodem).

Then follow Shazaam's post, with each command in the same terminal window.

---

### Post by nitehawk777 on 2008-11-20
I'm delighted at the detailed instructions (I was very discouraged and floundering in a confused stew!!!!).
That info just may well keep me with this terrific distro,................(much appreciated!):KS

EDIT:  How about that!  It took me only a few minutes following you folks' instructions,...........and here I am coming to you from my new Ubuntu 8.10 dial-up!  I hope this thread helps out others who may be having the very same problem.  (and looks like you'll be having to put up with me in and around the Ubuntu forums for a looooooooong time now)...:lolflag:

---

### Post by moth17 on 2008-12-07
No such luck for me, cek. In the terminal window I get the message "Sorry, no modem was detected! Is it in use by another program? Did you configure it properly with setserial? Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)
If you still have problems, send mail to <wvdial-list@lists.nit.ca>"

Well, that URL is a dead end, and I have not sent an email. Fool me once...

I have been using 8.10 for about two hours now- just installed it today to get the taste of Vista out of my mouth that Dell shoved down my throat when I bought a refurbed Inspiron 530. A friend talked me into trying Linux, so here I am. The modem fired up no problem using Vista. This is ridiculous. I expected more from Ubuntu. If it's this hard just to use a dialup modem, what does my Ubuntu future hold? Can anyone help, as my results seem to vary here? 

Don't mark this "solved" just yet...

BTW- I have a Conextant D850 PCI V.92 Modem.

---

### Post by moth17 on 2008-12-07
ScamModem returns this gibberish, how do I interpret or proceed?

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
 scanModem update of:  2008_11_06

 There are no blacklisted modem drivers in /etc/modprobe*  files 
Attached USB devices are:
 ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
 ID 1d6b:0002 Linux Foundation 2.0 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 413c:3012 Dell Computer Corp. 
 ID 413c:2003 Dell Computer Corp. Keyboard
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 05dc:0080 Lexar Media, Inc. Jumpdrive Secure 64MB
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0002 Linux Foundation 2.0 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub
 ID 1d6b:0001 Linux Foundation 1.1 root hub

USB modems not recognized

For candidate card in slot 02:00.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 02:00.0	14f1:2f20	14f1:200f	Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem

 Modem interrupt assignment and sharing: 
 --- Bootup diagnostics for card in PCI slot 02:00.0 ----
[    0.541131] PCI: 0000:02:00.0 reg 10 32bit mmio: [fddf0000, fddfffff]
[    0.541138] PCI: 0000:02:00.0 reg 14 io port: [df00, df07]
[    0.541178] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.541183] pci 0000:02:00.0: PME# disabled

 The PCI slot 02:00.0 of the modem card may be disabled early in 
 a bootup process,  but then enabled later. If modem drivers load 
 but the  modem is not responsive, read DOCs/Bootup.txt about possible fixes.
 Send dmesg.txt along with ModemData.txt to [email]discuss@linmodems.org[/email]
 if help is needed.
 

For candidate card in slot 00:1b.0, firmware information and bootup diagnostics are:
 PCI slot	PCI ID		SubsystemID	Name
 ----------	---------	---------	--------------
 00:1b.0	8086:293e	1028:020d	Audio device: Intel Corporation 82801I 

 Modem interrupt assignment and sharing: 
 22:       1425       1457   IO-APIC-fasteoi   HDA Intel
 --- Bootup diagnostics for card in PCI slot 00:1b.0 ----
[    0.540355] PCI: 0000:00:1b.0 reg 10 64bit mmio: [fdff4000, fdff7fff]
[    0.540394] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.540398] pci 0000:00:1b.0: PME# disabled
[   12.478750] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.478778] HDA Intel 0000:00:1b.0: setting latency timer to 64

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
00-02: ALC888 Analog : ALC888 Analog : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1 : capture 1
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1

about /proc/asound/cards:
------------------------
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22

 PCI slot 00:1b.0 has a High Definition Audio Card
 The drivers are in the kernel modules tree at:
 /lib/modules/2.6.27-7-generic/kernel/sound/pci/hda/snd-hda-intel.ko
=== Finished firmware and bootup diagnostics, next deducing cogent software. ===

Predictive  diagnostics for card in bus 02:00.0:
	Modem chipset  detected on
NAME="Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem"
CLASS=0780
PCIDEV=14f1:2f20
SUBSYS=14f1:200f
IRQ=4
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  02:00.0
   0780 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
      Primary device ID:  14f1:2f20
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



Predictive  diagnostics for card in bus 00:1b.0:
	Modem chipset not detected on
NAME="Audio device: Intel Corporation 82801I "
CLASS=0403
PCIDEV=8086:293e
SUBSYS=1028:020d
IRQ=22
HDA=8086:293e
SOFT=8086:293e.HDA


 High Definition Audio (HDA) cards MAY host a modem chip in their Subsystem, 
 and many are supported by the ALSA audio+modem driver snd-hda-intel
 A modem was not detected on HDA card 8086:293e.
 If another modem card is present, then most likely 8086:293e does not host a modem.
 If another modem card has not been detected, then possibilities are:
	1) A Conexant modem chip is present on 8086:293e, as Conexant chips
 are frequently not detectable by ALSA diagnostics
	2) The modem may be of the older non-PCI Controller Chipset (hardware) type.
Try detection with Root permission:
	sudo wvdialconf  /etc/wvdial.conf

 For candidate modem in:  00:1b.0
   0403 Audio device: Intel Corporation 82801I 
      Primary device ID:  8086:293e
    Subsystem PCI_id  1028:020d 
    Softmodem codec or chipset from diagnostics: 
                               from    Archives: 
                        
      

Support type needed or chipset:	

Support can likely be achieved through two mutually exclusive alternatives:
1) The hsfmodem software for Conexant chipset modems: Read DOCs/Conexant.txt
The following ALSA alternative CANNOT work with Conexant modems.

2) An ALSA modem driver plus slmodemd.  Read DOCs/Smartlink.txt for details, and
to test get the package SLMODEMD.gcc4.3.tar.gz from:  
	[http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

----------------end Softmodem section --------------
Writing DOCs/Smartlink.txt
============ end Smartlink section =====================

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
	-rwsr-xr-- 1 root dip 273064 2008-10-15 18:51 /usr/sbin/pppd

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

This is nuts. I'm getting ready to chuck this. "User friendly" and "plug-and-play" my a$$. Do I dare even trying to connect a printer now? If I had a degree in Comp Sci and was retired maybe I could surf the dozen forums I have been across in the last day and make this work.

Losing hope.

---

### Post by moth17 on 2008-12-07
It seems like a solution could be here- but I'm afraid I could start doing real damage at this point:

[http://www.linuxant.com/drivers/hsf/install.php](http://www.linuxant.com/drivers/hsf/install.php)

I downloaded what is hopefully the right driver: 	hsfmodem_7.68.00.14full_k2.6.27_7_generic_ubuntu_i386.deb.zip
located at [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)

and I'm inferring I should follow the instruction labled "METHOD B: DEBIAN PACKAGE (*.deb)" , but I'm thinking I should stop here and get some guidance, because I really have no idea what I'm doing and I don't want to make a bigger mess.

Anybody out there?

---

### Post by moth17 on 2008-12-08
I'll just keep replying to myself- maybe the documentation trail will help someone else. Someone from linmodems.org replied with this info:

 "From  [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)
 download hsfmodem-7.68.00.12full_k2.6.27_7_generic_ubuntu_i386.deb.zip
 
Under Linux unpack with:
 $ unzip hsfmodem*.zip"

Which I have done, as the previous post shows. But then he goes on:

 "Then install with:
 $ sudo dpkg -i hsfmodem*.deb
 Subsequently, the modem should be found with
 $ sudo wvdialconf /etc/wvdial.conf
 Edit in your personal information with:
 $ sudo gedit /etc/wvdial.conf
 and try dialing out with:
 $ sudo wvdial.
 See DOCs/Testing.txt  for details.

 Read DOCs/Conexant.txt"

Which I need someone to spell out for me. My level of knowledge can handle a box that pops up and asks for a phone number, account name and password- but this stuff needs a little more detailed explanation. Anyone picking this up yet?

---

### Post by lkraemer on 2008-12-08
The Softmodems and Internal modems can be a bugger, so why not
look on Ebay for an External USRobotics USR5686D, then Flash it to
the latest firmware, and use a USB to Serial Converter to get
online via Dialup using wvdial.  Granted it's extra equipment, more cables,
Wall Wart, and Serial Cable but it at least works Great.  Ebay has
them for ~$20.00 at times.

The USB to Serial Converter is from [www.newegg.com](www.newegg.com) and is a N82E16812156008
SABRENT 1 ft. USB to Serial db9 Male RS-232 (9-pin) Converter Model SBT-USC1M - Retail @ $8.99.

These work wonderful.

lk

---

### Post by Shazaam on 2008-12-08
Never mind, senior moment. :)

---

### Post by mikeymouse on 2008-12-12
I have been using Ubuntu for quite some time and for many version back.
Never have i had to play about with dialup in the manner which is necessary in version 8.1.Ubuntu and Kubuntu.
There are a lot of people who still must use dialup to get online and the ones who set Ubuntu up seem to forget about the beginners and the ones who must use dialup to get online.
 I guese i have just arrived at the version of Ubuntu where i need to go elsewhere, there seems to be many other versions out there where they try to make it easy to go online so i guese I am gone to one of these.
 thanks for all the help i have had thru the years.
 mikeymouse

---

### Post by lkraemer on 2008-12-13
Well, for me there is NO CHOICE other than Dialup at home.
But I REFUSE to TOSS out UBUNTU for the price of an External Modem
and a USB to Serial Converter as suggested above.....EVEN if I have
a few extra cables, and another Wall Wart hanging on an outlet.

Just forget the Internal Modem, all the configuration, Compiling of code,
downloading of linmodems testing software, and take 2 minutes to power-up
that External USR Modem and configure wvdial.  Then let wvdial dial your
ISP and surf.  It's that easy.........And it WORKS!

Don't go OFF on the Folks that are bringing you UBUNTU..........after all they aren't waiting on your specific email so they can help only you.  They are working in the future to bring you an even better product.

And Dialup is going the way of the 3.5" Floppy, that also has had it's day.

Good Luck.....Don't Jump Ship....The Grass is not always Greener across the fence.......And there may be a MAD BULL in that field with HORNS!

lk

---

### Post by longtom on 2009-04-20
Or else - listen to these excellent tips of lkraemer here:

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

---

### Post by amoun on 2009-05-23
Try the Zoom 56K USB Modem Series 1063 albiet a wintype-modem. It comes with Linux Drivers.
It wasn't straightforward as I was a newbie at Linux but a friend helped me out.
**I haven't upgraded from Hardy to Intrepid though.**

---

