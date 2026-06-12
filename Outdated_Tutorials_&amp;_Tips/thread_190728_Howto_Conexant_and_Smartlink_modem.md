---
title: "Howto Conexant and Smartlink modem"
date: 2006-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2006-06-06
Hi,
   I have had to revise the Howto's for installing a Conexant winmodem and a Smartlink winmodem due to some changes after installing Dapper kubuntu.
As some of you wanted this urgently here goes:  (*** also note that some of this information (and drivers) may be out of date as I have not used the Smartlink modem since updating to Feisty)***

Howto get Conexant HSF modem to work in Dapper Kubuntu
***Please note that this open driver used below does not work in Edgy or Feisty, the only free driver that does work is by Linuxant and is restricted to 14400 and needs registration at a fee to open up.***

Conexant modems can mostly be made to work in linux by using older drivers that were open source and thus free. Do not laugh, but presently Conexant drivers are free for Windows, but have to be purchased seperately at about $15 for free linux! These purchased drivers are said to be free, but the free version only supports speeds up to14400 and if you want maximum 56k you have to pay. Below you will find two different methods for installing the open source drivers that run at the full 56k and this should work in Ubuntu Dapper and other versions, but I have only tested in Dapper Kubuntu. This came about when Rafael Espíndola ported the latest Conexant open source version to 2.6.x kernels. AlexandreOttoStrube packaged it for Ubuntu Breezy using kernel 2.6.12-9 The.deb file thus will not work on any newer kernel unless you compile it yourself as below. The files can be downloaded from  [http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/) or [ftp://ftp.wizzy.com/pub/wizzy/conexant/](ftp://ftp.wizzy.com/pub/wizzy/conexant/) courtesy AndyRabagliati 
Firstly to ensure you have a modem that may work with these drivers, look at the make and model of your modem, by looking at the chipset. If it shows HSF and the number CX11252 (maybe other numbers here) on the chip then you have a softmodem/winmodem/linmodem and this driver should work. You can also install it on a Windows pc and do a modem query and if it shows PCI/VEN_14F1&DEV2F00 then you know it should work. 
The best way is to use your terminal to check your Vendor:Device pci id with "lspci" :
lspci
     0000:01:0b.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
Then, type "lspci -n" and look at the same identifying numbers to get the vendor:device id
lspci -n
     0000:01:0b.0 0780: 14f1:2f00 (rev 01)
In this example, it's 14f1:2f00. Vendor ID is first part (14f1), then a ":"  separates the Device ID (2f00).

Vendor ID's that are suported are listed here:
Vendor id  14fi  = Conexant
               8086 = Intel or Ambient
               125D = ESS Technologies/Creative
               2003 = Smartlink/Netodragon
               10B9 = ALI/Netodragon  Acer Labs Incorporated


VendorID=14F1 : DeviceID=2F00 Tested and works on Dapper
VendorID=14F1 : DeviceID=2F01
VendorID=14F1 : DeviceID=2013 Tested and works
VendorID=14F1 : DeviceID=2014
VendorID=14F1 : DeviceID=2015
VendorID=14F1 : DeviceID=2016
VendorID=14F1 : DeviceID=2F10
VendorID=14F1 : DeviceID=2F11
VendorID=14F1 : DeviceID=2F12
VendorID=14F1 : DeviceID=2F13
VendorID=14F1 : DeviceID=2F14
VendorID=14F1 : DeviceID=2F20
VendorID=14F1 : DeviceID=4311
VendorID=127A : DeviceID=1025
VendorID=127A : DeviceID=2004
VendorID=127A : DeviceID=2005
VendorID=127A : DeviceID=2013
VendorID=127A : DeviceID=2014
VendorID=127A : DeviceID=2015
VendorID=127A : DeviceID=2016
VendorID=127A : DeviceID=4311
VendorID=127A : DeviceID=2114
VendorID=8086 : DeviceID=2416
VendorID=8086 : DeviceID=2446
VendorID=8086 : DeviceID=2486
VendorID=1106 : DeviceID=3068
VendorID=10B9 : DeviceID=5453
VendorID=10B9 : DeviceID=5457
VendorID=14F1 : DeviceID=2043
VendorID=14F1 : DeviceID=2044
VendorID=14F1 : DeviceID=2045
VendorID=14F1 : DeviceID=2046
VendorID=14F1 : DeviceID=2443
VendorID=14F1 : DeviceID=1631
VendorID=14F1 : DeviceID=1636
VendorID=14F1 : DeviceID=1637

Download the following files:
modem-hsfpci.tar.bz2 from [https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2 ]("https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2")
conexant_192-1ubuntu-1.tar.gz from [ftp://ftp.wizzy.com/pub/wizzy/conexant/conexant_192-1ubuntu-1.tar.gz](ftp://ftp.wizzy.com/pub/wizzy/conexant/conexant_192-1ubuntu-1.tar.gz)

This software supports the Conexant HSF 56k HSFi Modem, and was not tested with all models, anyone varifying a model to please update this with &#8220;tested and works&#8221; next to the ID list for help to others.
As you are going to compile your own drivers it is necessary that the required files are installed, check and/or install with Synaptic that the following are there:
build-essential, linux-headers-ARCH, debhelper and fakeroot is installed, ARCH is the result you get if typing uname -r in a terminal &#8211; version of kernel.

Method A:
This comprises of creating a .deb file and then using that to install and configure the driver.
1.Create a folder called HSFmodem on your Desktop and put both downloaded files in it, modem-hsfpci.tar.bz2 and conexant_192-1ubuntu-1.tar.gz
2.Now right click on modem-hsfpci.tar.bz2 and Extract Here (in same folder) a folder and a folder modem-hsfpci-0.1 and a file HOWTO.txt will be created.
3.No go to the konsole and enter:
cd Desktop/HSFmodem
./HOWTO.txt
and a file modem-hsfpci_0.1-0ubuntu1_386.deb will be created in folder /HSFmodem
4.You can install it with
sudo dpkg -i modem-hsfpci_0.1-0ubuntu1_i386.deb
5.Go to file    /etc/modem-hsfpci/modem-hsfpci.conf  Right click, click Actions then Edit as Root and Kwrite should open file modem-hsfpci.conf
Remove the comment # from your country and also from the Vendor:Device ID number determined above. If your ID are not shown you can try to create it in a new line, but there is no guarentee that it will work. If you do not do this the country will default to USA and the script will try to determine the Vendor ID with lspci.
6.Now you have to do the following to compile and install the configuration files and modules for your kernel version.
sudo /usr/sbin/modem-hsf    --install 
You should see the last line refering to modem installed and available on /dev/modem A symlink has also been created to the /dev/ttySHSF0 device.
7.You may have to reboot. The modem can be tested in Kppp by using Modem Query on /dev/modem. If it sees it you are OK and ATI 5 should show your country code.
8.You can uninstall by using Synaptic to completely uninstall modem-hsfpci_0.1-0ubuntu1

Note: Everytime you install a new kernel, especially after an update you will have to use the sudo /usr/sbin/modem-hsf    --install command to build kernel modules for it.

It has been suggested that you also try ATW2DT instead of ATDT when setting up your dialler (Kppp).

Method B:

1.Put the downloaded file  conexant_192-1ubuntu-1.tar.gz on your Desktop and right click &#8220;Extract  Here&#8221; and a folder &#8220;conexant&#8221; will be created on your Desktop.
2.Read the txt files in the folder for more info.
3.Open the folder &#8220;conexant/modules/makefile&#8221;, right click on makefile, click Actions, then Edit as Root and Kwrite should open the file /conexant/makefile. Now find the 2 lines that start with # KERNELDIR? = /lib/modules..... etc. and KERNELDIR?= /usr/src... etc Remove the comment # in the first line and insert comment # on second line and save changes.
4.Now open the /conexant/makefile in the same way and find the commented line # rm -rf $$DESTDIR/dev/ttySHFS0. Remove the comments from the mentioned line and the following 3 lines up to &#8220;update modules&#8221; and save changes
5.cd Desktop/conexant
6.make
7.sudo make install
8.sudo modprobe hsfserial     (you should get no result report if OK)
9.dmesg | grep hsfserial         ( you should get no result report if OK)
10.The /dev/ttySHFS0 is created for the modem
11.To test, use the query modem on Kppp

To remove the installation:
rm /dev/ttySHFS0
rm -r /etc/hsf
rm /lib/modules/ARCH/misc/hsf*


 **_Howto get Smartlink winmodem working in edgy_**
   
  Smartlink soft modems work quite well in ubuntu, but some problems have been found and the process below works in Edgy. It also seems as if the Smartlink modems with Netodragon chip MDV92XP do not work, but the ND92XPA chip works with the process below. Also read the ubuntu wiki dialupmodemhowto for details and other methods.
  Use Synaptic or Adept to ensure that you have all the necessary packages installed for compiling your drivers. This includes build-essential, linux-headers-ARCH (where ARCH is your kernel version  and can be found with uname -r in the terminal), fakeroot, module-assistant and debhelper.
  Basically the sl-modem-source has to be installed first and then the sl-modem-daemon. It seems as if the latest daemon also looks for ungrab-winmodem so download and install this from the linmodem website.
  Please note that you will have to do this after everytime you update your kernel.
   
  [B][U]Method A:

[/U][/B]This method uses the latest packages from linmodems and the latest daemon on the Edgy repository or from the Debian repositories and works well.
   1.Download  slmodem-2.9.11-20061021.tar.gz from[http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/)  
This package seems to work better in breezy and dapper and does not give the dialing problem that causes the modem to fail on ATDT and not dial out.
   2.Also download and install the ungrab-winmodem from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/). 
linmodem website by using extract, make and sudo make install. (same as step 3)
   3.Copy the sl-modem-2.9.11-20061021.tar.gz file to your Desktop and right click on it and select &#8220;Extract here&#8221; and a folder wth the same name will be created with the extracted files on your Desktop.
   4.Now rename the folder to an easier name such as &#8220;slmodem&#8221;.
   5.Open a terminal and cd in to the slmodem folder or drag and drop in the terminal and select cd when asked.
   6.Type make
   7.Type sudo make install
   8.Type sudo modprobe slamr
   9.Type dmesg | grep slamr
   10.Now enable your repositories and install sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb with Synaptic or Adept or download sl-modem-daemon_2.9.9d+e-pre2-7.deb from the debian website [http://packages.debian.org/unstable/misc/sl-modem-daemon](http://packages.debian.org/unstable/misc/sl-modem-daemon) if you want the latest daemon.
   11.Use Kppp to query the modem on /dev/modem, if this works you are there! If you are not using Kubuntu then just see if it works from Gnome-ppp (wvdial must first be set up)
   12.Edit  /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY= USA to i.e SOUTHAFRICA or your country
   13.Type sudo /etc/init.d/sl-modem-daemon restart to restart the daemon or just reboot.
   14.If you again do a &#8220;Query modem&#8221; in Kppp and you will see that your country has changed.
 
 
   
  **_Method B:_**
  This is the ideal way. Synaptic or adept to install sl-modem daemon and sl-modem-source as well as ungrab-winmodem as a dependancy from the repositories 
  This also means that the files need to be updated for the newer versions of the kernel everytime. Unfortunately the sl-modem files on bothe the dapper and edgy repositories are long out dated and do not work. Someone needs to compile new drives from the files as in method A
  [COLOR=red]( At the moment this fails and the sl-modem-module is not created when installing with Synaptic, the install is successful if the install is done with sudo module-assistant  auto-install sl-modem, sudo depmod -a The modem is then detected but fails on ATDT and does not dial out) This problem was already noted in Breezy. We need a .deb file made from  slmodem-2.9.11-20061021.tar.gz that has already been proven to work in Breezy and Dapper)[/COLOR][LIST]
[*]Also download and install the ungrab-winmodem      from the [http://phep2.technion.ac.il/linmodems/packages/smartlink/](http://phep2.technion.ac.il/linmodems/packages/smartlink/). linmodem website. Install with, extract, make,      sudo make install.
[*]Enable the universe/multiverse repositories
[*]Use Synaptic or Adept to search for sl-modem
     You will find 2 files called      sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb and      sl-modem-source_xxxxxx.deb  (this      file with xxxxxx is not ready yet)
[*]Install the sl-modem-source and then the      sl-modem-daemon
[*]Now go to /etc/default/sl-modem-daemon, right      click, Action, Edit as Root, find the line SLMODEMD_COUNTRY=USA and change the USA to      SOUTHAFRICA or your country name.
[*]Go to the konsole:
[*]sudo       modprobe slamr
[*]sudo       /etc/init.d/sl-modem-daemon       restart
[*]Now go to Kppp and select /dev/modem and use the      Query Modem to test you modem. Now setup Kppp and go on line![/LIST]**_Note:_** If you are going to use Kppp it is advisable that you first activate the line #noauth by removing the # comment in  /etc/ppp/peers/kppp-options.
   
  To** release a locked up Smartlink modem** use  sudo modprobe ungrab-winmodem, then sudo modprobe slamr, then restart the daemon with sudo /etc/init.d/sl-modem-daemon restart. This may help you from rebooting.
   
  **_Footnote:_**
  The daemon package shown above, whether from the debian repo or ubuntu repos works with any of the driver packages, but only the linmodem driver package  slmodem-2.9.11-20061021.tar.gz seems to be the latest for the edgy and dapper kernel version. We thus need this package to be put on the ubuntu repos. The ungrab-winmodem package should also be a 'dependancy&#8221; for the daemon package and also be installed together by Synaptic. 
   
  To remove any installation go to Synaptic, search for sl-modem and  uninstall completely. Then use Krusader in root mode to search for sl-modem. Double click on any found (except those in your repository or download folder) and right click for delete. This clears all left over dreggs and leftovers of a previous installation that may be causing a problem with a new sl-modem install. Be very careful before you delete anything in this way.

---

### Post by maxbaggi on 2006-06-21
Hi, thanks for the excellent HOWTO... works perfectly in Kubuntu Dapper.
But how do I get this to work in Ubuntu Dapper?

---

### Post by Matchless on 2006-06-24
Hi,
  I have not used Gnome (ubuntu) since the first kubuntu hit the streets, but theoretically it should work, just use gedit to edit the files and gnome-ppp to test and use.
If anyone out there can confirm please do.
Thanks

---

### Post by maxbaggi on 2006-06-24
Hi Matchless,
I used gedit to edit the files but I did not use gnome-ppp to test it.  I used System > Administration > Networking to test it instead.  I'll install gnome-ppp and see if it works.  I'll report back in a few minutes. :D

Edit: It doesn't seem to be working.  Please let me know if anyone has gotten this to work in Ubuntu.

---

### Post by Matchless on 2006-06-25
Hi,
    What modem are you tryin to install and what seems not to be working? Does the modprobe work? I am asking this as it may also be your dialler that is not working. Hve you tried pon and poff or WVdial?

---

### Post by maxbaggi on 2006-06-25
[QUOTE=Matchless]Hi,
    What modem are you tryin to install and what seems not to be working? Does the modprobe work? I am asking this as it may also be your dialler that is not working. Hve you tried pon and poff or WVdial?[/QUOTE]
Hi, thanks for suggesting pon and poff.  I created a connection using ```
sudo pppconfig
``` It works perfectly under Ubuntu now. :mrgreen: 
My modem is a Conexant HSF 56k HSFi Modem,  I tried using gnome-ppp but that didn't work (it simply failed to dial)... and about WvDial... I think gnome-ppp uses WvDial as its backend so if gnome-ppp doesn't work then Wvdial won't work either... not very sure though.
anyway... I have another question.
I used Method B of your guide to get my Conexant HSF modem to work.  So what do I have to do to get my modem to work again if I update to a newer kernel when it becomes available in the repository?

Thanks again for the excellent HOWTO :mrgreen:

Edit: Additional Information about my modem

```
lspci | grep Conexant
```
gives the following output
```
0000:02:01.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
```

```
lspci -n | grep 0000:02:01.0
```
gives the following output
```
0000:02:01.0 0780: 14f1:2f00 (rev 01)
```

---

### Post by Matchless on 2006-06-26
Hi,
    Do the uninstall at the bottom of method B and do a new make, make install etc. Just make sure that you have the latest updated linux-header installed, it does not normally install by default. I use Synaptic.

---

### Post by Gyrotwister on 2006-06-29
Hi, I've been trying to follow these instructions in Ubuntu which is my first attempt at using any Linux distribution so I've nexer had to compile a driver before.  I'm flying blind in the hope of getting my internal modem going.  
Using method B for the conexant modem I get the following errors.  


@Robert:~$ cd Desktop/conexant
r@Robert:~/Desktop/conexant$ make
make -C inf
make[1]: Entering directory `/home/r/Desktop/conexant/inf'
cc -I../modules/imported/include -I../modules/osspec/include -O2 -Wall   -c -o inf2bin.o inf2bin.c
inf2bin.c: In function ‘ProcessString’:
inf2bin.c:236: warning: pointer targets in assignment differ in signedness
inf2bin.c: In function ‘ProcessCtryStruct’:
inf2bin.c:393: warning: pointer targets in assignment differ in signedness
cc -o hsfinf2bin inf2bin.o
(./preprocess.sh linux_hsfi-14f1-2f00.bin > linux_hsfi-14f1-2f00.bin.temp; ./hsfinf2bin linux_hsfi-14f1-2f00.bin.temp linux_hsfi-14f1-2f00.bin)
(./preprocess.sh linux_hsfi-8086-24c6.bin > linux_hsfi-8086-24c6.bin.temp; ./hsfinf2bin linux_hsfi-8086-24c6.bin.temp linux_hsfi-8086-24c6.bin)
(./preprocess.sh linux_hsfi-14f1-2f30.bin > linux_hsfi-14f1-2f30.bin.temp; ./hsfinf2bin linux_hsfi-14f1-2f30.bin.temp linux_hsfi-14f1-2f30.bin)
make[1]: Leaving directory `/home/r/Desktop/conexant/inf'
make -C modules
make[1]: Entering directory `/home/r/Desktop/conexant/modules'
make -C /lib/modules/$(uname -r)/build M=/home/r/Desktop/conexant/modules modules
make: Entering an unknown directory
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/r/Desktop/conexant/modules'
make: *** [all] Error 2
r@Robert:~/Desktop/conexant$ sudo make install
Password:
mkdir -p $DESTDIR/lib/modules/`uname -r`/misc
cp modules/*.ko $DESTDIR/lib/modules/`uname -r`/misc
cp: cannot stat `modules/*.ko': No such file or directory
make: *** [install] Error 1
r@Robert:~/Desktop/conexant$ sudo modprobe hsfserial
FATAL: Module hsfserial not found.

What should I do?

---

### Post by kosmo on 2006-07-03
Thanks for the wonderful howto!!!

Can you anybody resolve this:
   milan@ubuntu:~$ dmesg | grep hsf
[4294685.399000] hsfosspec: module license 'Copyright (C) 1996-2001 Conexant Systems Inc. All Rights Reserved.' taints kernel.
[4294685.998000] cnxthsf_OsFOpen("/etc/hsf/nvram.bin", "w"): error -30
[4294685.998000] NVM_SaveAll: Could not open "/etc/hsf/nvram.bin"

Btw, modem working with no sound on my ac97. Modem model without speaker.

---

### Post by Gyrotwister on 2006-07-10
Ok, Maxbaggi was kind enough to suggest that the most likely reason for the failure to compile was that I hadn't installed the required packages.  
I found debhelper, fakeroot and linux-headers-ARCH were missing.  
After installing these, it compiled ok and my modem was detected and setup using GNOME PPP.  
Also the command to reveal your ARCH code is “uname -r”, “uname-r” doesn't work.  A space between e and – is required.  

Another internal Conexant modem up and running in Ubuntu!  
Thanks to Matchless for providing this information.

---

### Post by fallingleaf on 2006-07-12
Many thanks to Matchless for this Howto.  I feel I am on the verge of getting connected with my smartlink modem.  

I used method A for smartlink.  I'm running Ubuntu so used gnome-ppp to connect.  I can hear it dial and connect, but then it drops the connection, saying "NO CARRIER".  I unchecked th option "Check carrier line" in gnome-ppp settings, but still no luck.  Any ideas?

Thanks,
fallingleaf

---

### Post by Matchless on 2006-07-12
Hi,
   I have never tried gnome-ppp as I use Kubuntu, but try pon and poff or WVdial. if this works your modem is working and then it is only gnome-ppp that may be the issue. kppp is quite finicky and needs proper setting up of the lan card as well otherwise it fails.


> **fallingleaf said:**
> Many thanks to Matchless for this Howto.  I feel I am on the verge of getting connected with my smartlink modem.  

I used method A for smartlink.  I'm running Ubuntu so used gnome-ppp to connect.  I can hear it dial and connect, but then it drops the connection, saying "NO CARRIER".  I unchecked th option "Check carrier line" in gnome-ppp settings, but still no luck.  Any ideas?

Thanks,
fallingleaf

---

### Post by fallingleaf on 2006-07-12
OK, I tried wvdial and I get the same thing, no carrier.

I tried editing wvdial.conf to add the line "Carrier Check = no" but it makes no difference.

Thanks for you help,
fallingleaf



[INDENT][/INDENT]

> **Matchless said:**
> Hi,
   I have never tried gnome-ppp as I use Kubuntu, but try pon and poff or WVdial. if this works your modem is working and then it is only gnome-ppp that may be the issue. kppp is quite finicky and needs proper setting up of the lan card as well otherwise it fails.

---

### Post by autocrosser on 2006-07-12
I can confirm that method B works with a SmartLink SL A-1801 in Gnome--I did a quick set-up with the Network Settings panel & it dialed out the first time--I'll check it with Gnome-PPP and report back--I got the modem from eBay for 15.98 shipped (was advertised as a Linux modem--and was)

A bandwidth test reported 44.5Kbps & I'm out quite a ways from town:-D

OK--It works in Gnome-PPP--detected as /dev/ttySL0--I created a custom init string that "connects" at 48000--

AT&F&C1&D2&E0

Looks good to me:-D

Update--I got the Init string for XP--Allows V92 modulation & LAPM compression

AT&F E0 V1 &A3 &D2 &C1 S0=0

---

### Post by darkdbr on 2006-07-13
it work for me :-D 
my modem: VendorID=14F1 : DeviceID=2F12
ubuntu dapper kernel 2.6.15-23-386
i'm using wvdial...

thanks for the howto ;)

---

### Post by bhdenterprises on 2006-07-13
Hi guys, 

I have a problem with my modem and I posted it in this thread as I have other issues that are somehow related to my modem problem. Please follow this link: [http://www.ubuntuforums.org/showthread.php?p=1253435#post1253435]("http://www.ubuntuforums.org/showthread.php?p=1253435#post1253435").

Thanks a lot...

---

### Post by autocrosser on 2006-07-14
This might be a harder way around, but it seems to me that you could download the .deb(s) in windows & then either burn to a cd or (assuming) transfer them to a fat32 disc storage--I use Gdebi Package installer to install .deb(s)--I would bet if you cruise the forums you will find other ideas.....

---

### Post by kurup on 2006-08-10
> Download the following files:
modem-hsfpci.tar.bz2 from [https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2](https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2)
The above link is not working. Any idea where else I could download it from?

---

### Post by Matchless on 2006-08-18
Go to the wiki and open dialupmodemhowto the link in there is still active

---

### Post by flyingrhino on 2006-08-22
My experience just in case someone has this problem too -
Make sure you apt-get install the stuff
build-essential, linux-headers-ARCH, debhelper and fakeroot

because otherwise it will fail the make procedure.

Also a reboot is required, if you make-install, the device is there but doesn't get recognized.
I did this using 2.6.15-26 and it worked well for me on kubuntu.
kppp comes by default.

---

### Post by mikelygee on 2006-08-31
*I did this using 2.6.15-26 and it worked well for me on kubuntu.*

Did you use the Conexant drivers, or the Smartlink drivers?

I'm trying to get the modem on my HP Pavilion ZE4300 working, but haven't had luck with either. The Conexant driver doesn't install /dev/ttySHSF0 or /dev/modem, though no complaints are issued. Under slmodemd the system locks up when I try to do anything with the modem (via "Networking" under GNOME). I've tried using both pre-built and locally-built kernels.

PCI id is 10B9:5457, so it *should* be supported by the Conexant driver.

---

### Post by williamts99 on 2006-09-02
Is there someone out there that would be willing to create a script to take care of all of this?

---

### Post by autocrosser on 2006-09-12
Has anyone tried this with Edgy?  I'm going to try it later today & report if it works--the Smartlink modem in my system works very well with Dapper--so far, in Edgy I get that the module has a mis-match (using the Synaptic sl-modem-source).

---

### Post by autocrosser on 2006-09-13
Well--I gave it a try. Using the downloaded module drivers would not work--error'd out during build--installing via the downloaded files from Dapper & using Gdeb package installer worked--but gave this output with modprobe & dmesg | grep

dean@Linux:~$ sudo modprobe slamr
Password:
FATAL: Error inserting slamr (/lib/modules/2.6.17-6-386/extra/slamr.ko): Invalid module format
dean@Linux:~$ dmesg | grep slamr
[17179594.392000] slamr: disagrees about version of symbol struct_module
[17179608.304000] slamr: disagrees about version of symbol struct_module
[17179608.312000] slamr: disagrees about version of symbol struct_module
[17179608.392000] slamr: disagrees about version of symbol struct_module
[17180118.304000] slamr: disagrees about version of symbol struct_module

Any ideas anyone????

---

### Post by Carbon Based on 2006-09-23
When installing my Conexant modem using method A or B I get this error:

WARNING: Error inserting hsfosspec (/lib/modules/2.6.15-27-386/misc/hsfosspec.ko): Invalid module format
WARNING: Error inserting hsfbasic2 (/lib/modules/2.6.15-27-386/misc/hsfbasic2.ko): Invalid module format
WARNING: Error inserting hsfengine (/lib/modules/2.6.15-27-386/misc/hsfengine.ko): Invalid module format
FATAL: Error inserting hsfserial (/lib/modules/2.6.15-27-386/misc/hsfserial.ko): Invalid module format

Apparently this occurs during the "sudo modprobe hsfserial" command. Any ideas?

---

### Post by nitin_india on 2006-09-28
Hello,

I had one more thred for the same problem. Here is the link to the thred [http://www.ubuntuforums.org/showthread.php?t=249078](http://www.ubuntuforums.org/showthread.php?t=249078)
I am using Kubuntu and Kernel Version is 2.16.15.23
Can some one help.
On the thred I have posted complete details about the errors I got while using the methog A and B.
The modem is working fine with free linmodem driver. So I am almost there with some minor mistake I am doing. Is it because I dont have the debhelper package. 

If that is the case can some one suggest where I can download it.

Thanks

Nitin

---

### Post by LivingSouL on 2006-11-02
I've tried the Method A on my Ubuntu 6.06 Dapper and it depends on debhelper 4.0.0, but i can't find any debhelper on the synaptic, and the debhelper version now is 5.x.x

Sir Matchless, we have the same modem and i've tried the method B, still doesnt work :|

---

### Post by autocrosser on 2006-11-02
Well--I've tried just about every way I can think of to get my smartlink to work in Edgy--I get stopped every time building the slamr module--code looks like--

dean@linux:~/Desktop/slmodem-2.9.11-20051101$ make
make -C modem all
make[1]: Entering directory `/home/dean/Desktop/slmodem-2.9.11-20051101/modem'
make[1]: Leaving directory `/home/dean/Desktop/slmodem-2.9.11-20051101/modem'
make -C drivers KERNEL_DIR=/lib/modules/2.6.17-10-generic/build
make[1]: Entering directory `/home/dean/Desktop/slmodem-2.9.11-20051101/drivers'
cc -I/lib/modules/2.6.17-10-generic/build/include -o kernel-ver kernel-ver.c
make all KERNEL_VER=2.6.17-10-generic
make[2]: Entering directory `/home/dean/Desktop/slmodem-2.9.11-20051101/drivers'
make modules -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/home/dean/Desktop/slmodem-2.9.11-20051101/drivers
make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/dean/Desktop/slmodem-2.9.11-20051101/drivers/amrmo_init.o
/home/dean/Desktop/slmodem-2.9.11-20051101/drivers/amrmo_init.c:704: error: expected ‘)’ before string constant
make[4]: *** [/home/dean/Desktop/slmodem-2.9.11-20051101/drivers/amrmo_init.o] Error 1
make[3]: *** [_module_/home/dean/Desktop/slmodem-2.9.11-20051101/drivers] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/dean/Desktop/slmodem-2.9.11-20051101/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dean/Desktop/slmodem-2.9.11-20051101/drivers'
make: *** [drivers] Error 2

Any ideas?

---

### Post by _duncan_ on 2006-11-03
hi autocrosser,

I'm not sure if this will work, but it's worth a try. I'm assuming '/home/dean/Desktop/slmodem-2.9.11-20051101' is where you unpacked the linmodems driver and 'dean' is your user ID. If not, you will have to change the 1st statement, and maybe put 'sudo' ahead of the 2nd and 3rd statements.

1. back-up and open the original amrmo_init.c file:
```

cd /home/dean/Desktop/slmodem-2.9.11-20051101/drivers
cp amrmo_init.c amrmo_init.c.unpatched
gedit amrmo_init.c

```

2. now go to line 704, you will probably see the following code:
```

MODULE_PARM(debug,"i");

```

3. you need to change this to:
```

module_param(debug, int, 1);

```
Note that 'module_param' is lowercase.

4. save and exit.

5. you will have to do the same thing for 'st7554.c'. Open the file 'st7554.c' using gedit, look for "MODULE_PARM(debug, "i");" and apply the same patch as above.

6. try compiling again.

I encountered this problem while trying out FC5 (kernel 2.6.17-xx), but since I don't have it installed anymore, I'm just doing this from memory and from the info you posted. I'm currently using Ubuntu Dapper 6.06, which uses an earlier kernel version, so I can't reproduce the exact error.

Please post a feedback coz I'm very interested in this topic. My modem is also smartlink so I'll probably meet this problem in the future if I upgrade.

---

### Post by autocrosser on 2006-11-03
Thanks for trying Duncan--

I patched both files--now the amrmo file passes ok---but I get an error with the st7554.c file----

make[3]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/dean/Desktop/slmodem-2.9.11-20051101/drivers/amrmo_init.o
  CC [M]  /home/dean/Desktop/slmodem-2.9.11-20051101/drivers/sysdep_amr.o
  CC [M]  /home/dean/Desktop/slmodem-2.9.11-20051101/drivers/st7554.o
/home/dean/Desktop/slmodem-2.9.11-20051101/drivers/st7554.c:1153: error: unknown field &#8216;owner&#8217; specified in initializer
/home/dean/Desktop/slmodem-2.9.11-20051101/drivers/st7554.c:1153: warning: initialization from incompatible pointer type
make[4]: *** [/home/dean/Desktop/slmodem-2.9.11-20051101/drivers/st7554.o] Error 1
make[3]: *** [_module_/home/dean/Desktop/slmodem-2.9.11-20051101/drivers] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/dean/Desktop/slmodem-2.9.11-20051101/drivers'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dean/Desktop/slmodem-2.9.11-20051101/drivers'
make: *** [drivers] Error 2

The line refers to the USB Modem option--any ideas on a fix?

Added: I tried with the "new" amrmo file & the unpatched 7554 file--got exactly the same result--

OK--just tried by deleting the 1153 line (owner-MODULE) with the patched 7554.c file & the driver built & I sudo make install (d) it--I'll test to see if it works--if so, I'll post both patched files for everyone.

---

### Post by autocrosser on 2006-11-03
OK--the only problem I seem to have now is a permissions one--as far as the PCI smartlink--it works fine--the patches are as above post--I removed the offending line in the 7554.c file--so I think that the driver will not work with a USB modem. Patched files attached below.....

---

### Post by _duncan_ on 2006-11-03
> OK--just tried by deleting the 1153 line (owner-MODULE) with the patched 7554.c file & the driver built & I sudo make install (d) it

You're on the right track. However, to make the driver useful for all kernel versions, you may want to change it back to look like this:

```
static struct usb_driver st7554_usb_driver = {
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,15)
	.owner =       THIS_MODULE,
#endif
	.name =	       "ST7554 USB Modem",
	.probe =       st7554_probe,
	.disconnect =  st7554_disconnect,
	.id_table =    st7554_ids,
};
```

note that 2 lines were added, before and after the ".owner = ..." line to check the kernel version.

---

### Post by autocrosser on 2006-11-03
Drivers-----

---

### Post by autocrosser on 2006-11-03
Already uploaded the patches before I saw your post--works OK for me---I just need to change the permissions for the modem & it'll all be golden;)

---

### Post by autocrosser on 2006-11-03
Ok--i have forgot how to change the permission on the modem--chmod (don't remember) /dev/ttySL0? For the moment, I've just sudo wvdial--to get out---

---

### Post by LivingSouL on 2006-11-04
Here's what i get when i install debhelper... that's the only thing left to install the modem.

```


marc@dapper:~$ apt-get install debhelper
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
marc@dapper:~$ sudo apt-get install debhelper
Password:
Reading package lists... Done
Building dependency tree... Done
Package debhelper is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package debhelper has no installation candidate
marc@dapper:~$

```

PLEASE do help me... i need to install my HSFi modem with full 56k connection. :( i've tried method B, but still doesnt work :|

---

### Post by autocrosser on 2006-11-04
Have you enabled all your extra repositories?

---

### Post by autocrosser on 2006-11-10
I just installed the "new" slmodem-2.9.11-20060727.tar.gz from linmodems & it compiled/installed without all the bull with the 20051101--running Edgy.:D

---

### Post by _duncan_ on 2006-11-10
That's great! The patch I gave you came from linmodems too about 5-6 months ago. Must've incorporated it into the new version. Hopefully the Ubuntu devs can update the sl-modem-source package.

Also, maybe Matchless can update the how-to to point to the newer version.

---

### Post by Matchless on 2006-11-10
Hi, I am still downloading edgy and will then install and get the smartlink modem going using the new driver file. I will then update the howto as well.
Thanks

---

### Post by LivingSouL on 2006-11-10
> **autocrosser said:**
> Have you enabled all your extra repositories?

can you post what repositories you have? all my repositories are enabled, nothing is int comment. but still can't install debhelper :|

---

### Post by towsonu2003 on 2006-11-10
Any chance you can incorporate this info to the wiki (in my signature)? unless, of course, if you didn't do so already :)

thanks :)

---

### Post by autocrosser on 2006-11-11
Well-I'm using Edgy--so edit as required--

####################################
### Official Ubuntu Repositories ###
####################################

#CDROM
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Alpha i386 (20060719)]/ edgy main restricted
#Sources
deb-src [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy restricted main multiverse universe
deb-src [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-security restricted main multiverse universe
deb-src [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-updates restricted main multiverse universe
deb-src [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-proposed restricted main multiverse universe
deb-src [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-backports restricted main multiverse universe
#Packages
deb [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy restricted main multiverse universe
deb [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-security restricted main multiverse universe
deb [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-updates restricted main multiverse universe
deb [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-proposed restricted main multiverse universe
deb [http://ftp.osuosl.org/pub/ubuntu/](http://ftp.osuosl.org/pub/ubuntu/) edgy-backports restricted main multiverse universe

##Opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

## BOINC packages for Debian "sid" (unstable)
deb [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main
deb-src [http://pkg-boinc.alioth.debian.org/debian](http://pkg-boinc.alioth.debian.org/debian) unstable main

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. (RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

##Apollon program
deb [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib
deb-src [http://apt.cerkinfo.be/](http://apt.cerkinfo.be/) unstable main contrib

##Updated WINE
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

##Beryl
deb [http://dev.realistanew.com/beryl](http://dev.realistanew.com/beryl) edgy beryl
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main-edgy

#Nvidia driver Testing
deb [http://people.ubuntu.com/~kees/test-lrm-2.6.17.6-1/](http://people.ubuntu.com/~kees/test-lrm-2.6.17.6-1/) ./
deb [http://amaranth.selfip.com](http://amaranth.selfip.com) edgy lrm

#Improved fonts for Edgy
deb [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts
deb-src [http://www.elisanet.fi/mlind/ubuntu](http://www.elisanet.fi/mlind/ubuntu) edgy fonts

# Google Picasa for Linux repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free


I don't remember where you can get the optimized list for repositories--I'd search for it--there are mirrors all over the world for Ubuntu & a "local" mirror is ofter MUCH faster than the main one;)



> **LivingSouL said:**
> can you post what repositories you have? all my repositories are enabled, nothing is int comment. but still can't install debhelper :|

---

### Post by Matchless on 2006-11-12
> **towsonu2003 said:**
> Any chance you can incorporate this info to the wiki (in my signature)? unless, of course, if you didn't do so already :)

thanks :)
Hi,
    I will rewrite the howto as per my edgy installation and will update where possible.
Will send you a pm.

---

### Post by towsonu2003 on 2006-11-12
> **Matchless said:**
> Hi,
    I will rewrite the howto as per my edgy installation and will update where possible.
Will send you a pm.

great, thanks a lot for the effort!

---

### Post by Matchless on 2006-11-12
Hi,
   I have updated the howto part for Smartlink on edgy

---

### Post by _duncan_ on 2006-11-12
thank you, Matchless.

---

### Post by LivingSouL on 2006-11-14
Thank you matchless for this great Howto...

After all of exploring, i finally got to install my modem properly... and i've downloaded debhelper. :D

I'm a total newbie on ubuntu.

I've downloaded (was using the 14.4kbps driver) automatix2 and installed it, that must've enabled the universe repository (that i only knew recently) and tried to do:

```

sudo apt-get update
sudo apt-get install debhelper

```

was surprised it downloaded it. and then removed the linuxant driver

```

sudo hsfconfig -r

```

and then continued installation with you Method A.

and done...

restarted, and connected! :D

BTW, i used the System>Administration>Networking to dial, 'coz gnome=ppp doesnt seem to work.. :)

thanks.

My question now is, how do i do this on edgy? :) have somebody tried it already? on ubuntu edgy?

---

### Post by lse34 on 2006-11-23
Hello

I'm using the conexant driver for my winmodem. It work very well with the Dapper but don't work in Edgy.
I've got some compilation errors with the new kernel generic in Edgy.

Help me please.

Thanks

---

### Post by Matchless on 2006-11-24
I will try the Conexant driver on Edgy soon, i have just managed to get the Intel536ep and Smartlink working and I had to do some changes to the process for Edgy. The Conexant is on my todo list and I will try and get to it asap. Watch this space !

---

### Post by DougieFresh4U on 2006-11-24
I need some help with smarlink if some could please take the time to deal with my ignorance on following a How-To, Thanks

---

### Post by Matchless on 2006-11-25
> **DougieFresh4U said:**
> I need some help with smarlink if some could please take the time to deal with my ignorance on following a How-To, Thanks

Can you give any details as to where you are getting stuck?

---

### Post by Matchless on 2006-11-25
Hi all,
         Some bad news, I checked out the Conexant install on Edgy and I will need to spend more time on this. I may need some expert help as there seems to be a failure in the script and I know nothing about programming. If anyone is willing to help I will do testing and post results, but at this moment in time with no help there is not much I can do it seems. At the moment it works on dapper but not on edgy.
Sorry!

---

### Post by autocrosser on 2006-11-25
Hi Matchless---

Post the error logs--I would bet it's a bin/bash problem--Edgy changed the way scripts run---

---

### Post by _duncan_ on 2006-11-25
hi Matchless,

Go ahead and post the error details. Maybe we can sort it out...

Duncan

---

### Post by Matchless on 2006-11-25
autocrosser,
                  Aha! Thanks, but can you just give me a bit of help in finding them. I will try and post them as soon as I know which and how.

---

### Post by autocrosser on 2006-11-25
Ahh-- I see Duncan is here too---GOOD!!

I haven't seen how the conexant is installed--are you just running in a term?  if so, just post the output complete up to the error & let us take a look---

---

### Post by autocrosser on 2006-11-25
Hi Matchless---
I'm downloading the conexant_192 file---seems I can't get to the:  [https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2](https://wiki.ubuntu.com/DialupModemH...hsfpci.tar.bz2)

said that the page is not made?

In any case--I'll look at building the 192 & see if it fails & where---

---

### Post by Matchless on 2006-11-25
Duncan & autocrosser,
                                You guys are great! Here is the log from the konsole after make on the extracted conexant_192-1ubuntu-1.tar.gz.
I hope this helps a bit.

> userid@Kubuntu2:~/Desktop/conexant$ make
make -C inf
make[1]: Entering directory `/home/userid/Desktop/conexant/inf'
cc -I../modules/imported/include -I../modules/osspec/include -O2 -Wall   -c -o inf2bin.o inf2bin.c
inf2bin.c: In function ‘ProcessString’:
inf2bin.c:236: warning: pointer targets in assignment differ in signedness
inf2bin.c: In function ‘ProcessCtryStruct’:
inf2bin.c:393: warning: pointer targets in assignment differ in signedness
cc -o hsfinf2bin inf2bin.o
(./preprocess.sh linux_hsfi-14f1-2f00.bin > linux_hsfi-14f1-2f00.bin.temp; ./hsfinf2bin linux_hsfi-14f1-2f00.bin.temp linux_hsfi-14f1-2f00.bi )
(./preprocess.sh linux_hsfi-8086-24c6.bin > linux_hsfi-8086-24c6.bin.temp; ./hsfinf2bin linux_hsfi-8086-24c6.bin.temp linux_hsfi-8086-24c6.bi )
(./preprocess.sh linux_hsfi-14f1-2f30.bin > linux_hsfi-14f1-2f30.bin.temp; ./hsfinf2bin linux_hsfi-14f1-2f30.bin.temp linux_hsfi-14f1-2f30.bin)
make[1]: Leaving directory `/home/userid/Desktop/conexant/inf'
make -C modules
make[1]: Entering directory `/home/userid/Desktop/conexant/modules'
make -C /lib/modules/$(uname -r)/build M=/home/userid/Desktop/conexant/modules modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/userid/Desktop/conexant/modules/mod_basic2.o
ld -r -d -o /home/userid/Desktop/conexant/modules/hsfbasic2-nc.O /home/userid/Desktop/conexant/modules/imported/hsfbasic2.O
  CC [M]  /home/userid/Desktop/conexant/modules/mod_engine.o
ld -r -d -o /home/userid/Desktop/conexant/modules/hsfengine-nc.O /home/userid/Desktop/conexant/modules/imported/hsfengine.O
  CC [M]  /home/userid/Desktop/conexant/modules/mod_ich.o
ld -r -d -o /home/userid/Desktop/conexant/modules/hsfich-nc.O /home/userid/Desktop/conexant/modules/imported/hsfich.O
  CC [M]  /home/userid/Desktop/conexant/modules/mod_osspec.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osmemory.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osstring.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osdebug.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osfloat.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osstdio.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osmodule.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/osnvm.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/ostime.o
  CC [M]  /home/userid/Desktop/conexant/modules/osspec/linuxres.o
/home/userid/Desktop/conexant/modules/osspec/linuxres.c: In function ‘cnxthsf_LinuxInitPowerManagement’:
/home/userid/Desktop/conexant/modules/osspec/linuxres.c:131: warning: implicit declaration of function ‘pm_register’
/home/userid/Desktop/conexant/modules/osspec/linuxres.c:131: warning: assignment makes pointer from integer without a cast
/home/userid/Desktop/conexant/modules/osspec/linuxres.c: In function ‘cnxthsf_LinuxTermPowerManagement’:
/home/userid/Desktop/conexant/modules/osspec/linuxres.c:141: warning: implicit declaration of function ‘pm_unregister’
  CC [M]  /home/userid/Desktop/conexant/modules/serial_hsf.o
/home/userid/Desktop/conexant/modules/serial_hsf.c: In function ‘hsf_rx_chars’:
/home/userid/Desktop/conexant/modules/serial_hsf.c:183: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:184: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:185: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:194: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:195: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:196: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:206: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:208: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:210: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c:211: error: ‘struct tty_struct’ has no member named ‘flip’
/home/userid/Desktop/conexant/modules/serial_hsf.c: At top level:
/home/userid/Desktop/conexant/modules/serial_hsf.c:670: warning: initialization from incompatible pointer type
/home/userid/Desktop/conexant/modules/serial_hsf.c:671: warning: initialization from incompatible pointer type
/home/userid/Desktop/conexant/modules/serial_hsf.c:695: error: expected ‘)’ before string constant
/home/userid/Desktop/conexant/modules/serial_hsf.c:699: error: expected ‘)’ before string constant
make[3]: *** [/home/userid/Desktop/conexant/modules/serial_hsf.o] Error 1
make[2]: *** [_module_/home/userid/Desktop/conexant/modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/userid/Desktop/conexant/modules'
make: *** [all] Error 2
userid@Kubuntu2:~/Desktop/conexant$ 

---

### Post by autocrosser on 2006-11-25
Yes--that's similar to what I am getting--I had a problem in conexant/modules right off the bat that I traced to the main makefile--line 24 was commented out & should not be---after that, my build looked like:


dean@linux:~/Desktop/conexant$ make
make -C inf
make[1]: Entering directory `/home/dean/Desktop/conexant/inf'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/dean/Desktop/conexant/inf'
make -C modules 
make[1]: Entering directory `/home/dean/Desktop/conexant/modules'
make -C /lib/modules/$(uname -r)/build M=/home/dean/Desktop/conexant/modules modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /home/dean/Desktop/conexant/modules/serial_hsf.o
/home/dean/Desktop/conexant/modules/serial_hsf.c: In function ‘hsf_rx_chars’:
/home/dean/Desktop/conexant/modules/serial_hsf.c:183: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:184: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:185: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:194: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:195: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:196: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:206: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:208: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:210: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c:211: error: ‘struct tty_struct’ has no member named ‘flip’
/home/dean/Desktop/conexant/modules/serial_hsf.c: At top level:
/home/dean/Desktop/conexant/modules/serial_hsf.c:670: warning: initialization from incompatible pointer type
/home/dean/Desktop/conexant/modules/serial_hsf.c:671: warning: initialization from incompatible pointer type
/home/dean/Desktop/conexant/modules/serial_hsf.c:695: error: expected ‘)’ before string constant
/home/dean/Desktop/conexant/modules/serial_hsf.c:699: error: expected ‘)’ before string constant
make[3]: *** [/home/dean/Desktop/conexant/modules/serial_hsf.o] Error 1
make[2]: *** [_module_/home/dean/Desktop/conexant/modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/dean/Desktop/conexant/modules'
make: *** [all] Error 2
dean@linux:~/Desktop/conexant$ 


Seems to not be very happy about the "flip"--any ideas duncan?  I'm posting the serial_hsf.c file--

---

### Post by Matchless on 2006-11-25
Dean,
        Your help is really much appreciated, glad you are seeing the same problem that I experienced.
How are your Smartlink modems performing with the new drivers on edgy? I have not had time to give mine a good long test, as I am running on an Intel536ep most of the time and pulled the Smartlink out of the 2nd PC to test Conexant HSF. I also have a Conexant HCF (Zoltrix) here that I have only managed to get going on the free slow drivers.

---

### Post by autocrosser on 2006-11-25
The smartlink works great in Edgy--I guess duncan had posted the fix with linmodems prior to us "fussing" with it--was good to see that they had updated it so quick---My speeds hang around 4.2k per sec;)---fairly good for daytime use in rural western US--off-hours I sometimes see 5.5k per sec or so---not bad for dial-up. The modem seems to work best in my 2nd PCI slot (very bad in 1st-right below the AGP)--as usual, taking the time to "tinker" with your equiptment pays off:-k

---

### Post by _duncan_ on 2006-11-25
> -I guess duncan had posted the fix with linmodems prior to us "fussing" with it

It's the other way around. I just listened in on a series of publicly-posted emails between linmodems and fedora/red hat devs to come up with the patch for smartlink. The only thing I can claim credit for is translating their geek-speak to layman's terms.

I'm following the same approach with the conexant driver. Red Hat, SuSE and their derivatives normally use newer kernels compared to Ubuntu. FC5 in particular, which uses the 2.6.17 kernel, has been around for more than 6 months. Unfortunately, my initial search using keywords from the error logs haven't turned up anything useful. But it's still early. I remember it took me 2 weeks to find the patch for smartlink.

In the meantime, maybe one of you (Matchless and/or autocrosser) can email linmodems with attached scanModem results? I would've done it myself, but since I don't have a conexant modem and still running Dapper, I won't be able to answer them intelligibly if the maintainers have follow-up questions.

---

### Post by Matchless on 2006-11-26
[quote=]
In the meantime, maybe one of you (Matchless and/or autocrosser) can email linmodems with attached scanModem results? [/quote]

I wonder if linmodems will even look at anything to do with Conexant. It seems as if they only have the free slow 14400 driver from Linuxant. I could not even find the older free drivers on their site - unless I have missed something.

---

### Post by _duncan_ on 2006-11-26
I downloaded the package "hsfmodem-7.47.00.05full.tar.gz" from linuxant, unpacked it and compared the file "serial_cnxt.c" to the file "serial_hsf.c" provided by autocrosser.

The similarities are striking, and more importantly, what appeared to be "patches" to take into account kernel versions can be found. It's not straight-forward, but with a bit of experimentation can be used as basis for patching the free version.

My dilemma is this:  is this legal / ethical?

---

### Post by Matchless on 2006-11-26
Duncan,
           I would say immediately that going that way and maybe using parts of the one version in the other will not be legal. IMHO a small change in the scripts to make them perform the same way as they did in Dapper, in Edgy would not be illegal, due to the fact that the version in question is already free anyway. If the inspiration or insight how to do this comes from just looking at how other people in the past have solved this and their work or parts of it are not used directly, then it would be very difficult for someone to actually consider it being illegal.
Thanks for looking at this, as this will be a great help to a lot of users if it can be solved.

---

### Post by autocrosser on 2006-11-26
Well--I was just building the driver, I don't have a modem to test it--I would say as long as the code is not removed & just pasted into the free driver we would be OK..  I would fix the commented out line 24 in the modules makefile--not everyone is going to have the KERNELDIR in /usr/src/linux (minor beef)--Duncan, could you send or post the serial file you have so I can look at it?

---

### Post by _duncan_ on 2006-11-26
autocrosser,

Better if you download the package directly from the linuxant site, since I don't think I can redistribute the package myself. Here's the link:

[linuxant tar package]("http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.47.00.05full/hsfmodem-7.47.00.05full.tar.gz")

Unpack the package, then go to the /modules/GPL subdirectory.

Hmmm, GPL! Why didn't I notice it before. Now that's something to think about! ;)

P.S. OK, I'll let you have first crack at it since I'll be busy for the next few days. Have fun!

---

### Post by autocrosser on 2006-11-26
Well!! that opens it up a bit:cool:!!!!!  I'll get it & look at it & see what I can "do":-k

Will keep you posted--

---

### Post by autocrosser on 2006-11-26
All right--taking a tip from the fix for the smartlink--I've "fixed" two error codes in serial_hsf.c--lines 695 & 699--changed the MODULE_PARM to module_param & changed (serialmajor, "i") and (calloutmajor, "i") to (serialmajor, int,0) and (calloutmajor, int,0) like the similar lines in serial_cnxt.h look like.

I'm still having errors in the earlier lines about "flip"---unsure what to do about that---

---

### Post by _duncan_ on 2006-12-04
I downloaded and installed Edgy as a dual-boot with Dapper so I can work on the free conexant driver. Spent the past few hours trying to get rid of the "flip" compile error, but no success.

---

### Post by Matchless on 2006-12-08
I hope you find something! Good luck

---

### Post by chmalan on 2006-12-12
Hi
I got the driver to compile with these changes in serial_hsf.c

line 183-188
comment out the if(tty-> block

line 193
chance the the three lines starting with *tty and tty to this single function call
tty_insert_flip_char(tty, 0, TTY_OVERRUN);
line 211
chance the the two lines starting with *tty and tty to this single function call
tty_insert_flip_char(tty, hsf_readbuf[hsf_readoffset++], flag);

but now i get this error when the modules are inserted with insmod
 Unknown symbol in module, or unknown parameter (see dmesg)

Hope this can help some one.

---

### Post by Matchless on 2006-12-15
Excellent! Thanks for this I will try as well during the week and report back. Duncan and Autocrosser will this help you on the way? If we can keep this thread alive until the howto works it will be great.

---

### Post by chinocracy on 2006-12-16
Whoa, it seems installing a dial-up modem is a complex affair in Ubuntu. It's almost as if Linux-based systems expect you to be on DSL already.  :/  Or is it that I'm too used to Win XP GUI install. :P
I'm on Ubuntu Dapper. I've tried the step B for Conexant outlined in the first post here, but "make install" is not recognized as a command when I type it in terminal. Is it because I lack some of the things to enable, like build-essential and fakeroot? I saw I should get them from repositories. But where are repositories? Are they on the Net so I still have to connect (which I can't) or are they available from my Ubuntu install via the Synaptic manager? Thanks.

---

### Post by towsonu2003 on 2006-12-16
> **chinocracy said:**
> 
I'm on Ubuntu Dapper. I've tried the step B for Conexant outlined in the first post here, but "make install" is not recognized as a command when I type it in terminal. Is it because I lack some of the things to enable, like build-essential and fakeroot? I saw I should get them from repositories. But where are repositories? Are they on the Net so I still have to connect (which I can't) or are they available from my Ubuntu install via the Synaptic manager? Thanks.

I think this link might be helpful to you:
[https://help.ubuntu.com/community/DialupModemHowto/FromSource](https://help.ubuntu.com/community/DialupModemHowto/FromSource)

---

### Post by _duncan_ on 2006-12-17
> **Matchless said:**
> Excellent! Thanks for this I will try as well during the week and report back. Duncan and Autocrosser will this help you on the way? If we can keep this thread alive until the howto works it will be great.

As far as I can tell, the changes made by chmalan are consistent with the patches coming from the linuxant driver. I was also working basically along the same lines. Our syntax vary a little, but should have the same effect.

I also remember having to change the syntax for MODULE_PARM in a couple of places, which I thnk chmalan also did but forgot to mention, otherwise he would not have been able to compile the driver successfully.

What worries me is that there are also major differences in the source codes between the 2 drivers aside from the cosmetic patches we applied. These differences has nothing to do with the compilation errors, but could affect whether the compiled codes will actually make the modem work. Differences even beyond the serial_hsf.c file.

---

### Post by chinocracy on 2006-12-17
Now my problem is like the others... being unable to install Debhelper. I plug in the Install CD, but debhelper doesn't install from here. Synaptic keeps on looking on the Net. I downloaded it separately, and I hope I can find out how to install it. 
Will try the apt-get method too.

---

### Post by chinocracy on 2006-12-17
Did Method A of COnexant on Matchless' first post... now proud to have my first post from the  Ubuntu interface... :)) :))

---

### Post by chinocracy on 2006-12-18
Just a note: One of the key problems here is accessing repository content. I could not install debhelper from the installer CD, since it seemed not to be there, so I found it as a deb on the Net, along with the needed associated debs (like html2text). After installing the 3 components, I was able to do the Conexant method A of Matchless and install my D-Link DFM562IS internal modem. Thanks, Matchless. By the way, the irony of the situation is that I had to use Windows to help me get the stuff to get my Ubuntu system online. So I still start from Windows. Perhaps this is the challenge OS developers can address later on.

---

### Post by Kaulbach on 2006-12-20
in conexant/modules/serial_hsf.c
#include <linux/tty_flip.h>
may get one step further

---

### Post by autocrosser on 2006-12-21
Sounds good--I'll take another look at it this weekend---

---

### Post by Matchless on 2006-12-24
Hi,
    Thanks for the input. Duncan and Autocrosser I think you are going to get a lot of help on this and should be able to sort this out soon. Would it not be a good idea to publish the modified file and highlighting the changes, then maybe more inputs from experts out there would be forthcoming?

---

### Post by juice_fi on 2006-12-26
Hey, thanks a lot. Works like a charm :)

---

### Post by Matchless on 2006-12-29
> **juice_fi said:**
> Hey, thanks a lot. Works like a charm :)

Hi,
   Please tell us what you did and is your working in Edgy?
Thanks

---

### Post by geordee on 2007-01-08
I am a linux noob. I followed all the instruction in this thread (and a few other threads) and got the drive compiled. Just that much!

I have changed the MODULE_PARAM, included tty_flip.h and replaced the lines to call tty_insert_flip_char. All these need to be done in serial_hsf.c.orig, which is copied as serial_hsf.c by /usr/sbin/modem-hsf script.

The compilation went successfully. However the insmod returns the below warning.

insmod /lib/modules/2.6.17-10-generic/misc/hsfosspec.ko
WARNING: Error inserting hsfosspec (/lib/modules/2.6.17-10-generic/misc/hsfosspec.ko): Unknown symbol in module, or unknown parameter (see demsg).

The same message comes for hsbasic2.ko, hsfengine.ko, hsfserial.ko.

I have done a demsg to get the following.
hsfosspec: module license 'Copyright (C) 1996-2001 Conexant Systems Inc. All Rights Reserved.' taints kernel.
hsfosspec: Unknown symbol pm_unregister
hsfbasic2: Unknown symbol cnxthsf_OSCreateTimer

and so on.

Hope to get some expert advice

- Geordee

---

### Post by entropic_existence on 2007-01-10
Hi folks,

I've sort of followed this thread because I had been attempting to install the Conexant modems so I could use linux on my laptop while at my parents place over the holidays, where only dial-up is available. Of course like many of you I have had problems (and am still unable to get the driver to install) but right now I actually don't care if I have it installed or not.

My problem now is that the Conexant module is sitting here half-configured which has broken apt on my system. I have not been able to remove Conexant using dpkg or apt because the various modules are not installed. Anyone have any suggestions on how to remove it?

---

### Post by george_apan on 2007-01-22
I can confirm that method B for the conexant modems works with kubuntu dapper for this device:
VendorID=10B9 : DeviceID=5457

It displays itself in lspci as "ALi Corporation M5457 AC'97 Modem Controller"

---

### Post by geordee on 2007-01-22
I got the driver compiled after commenting the calls to pm_unregister. My friend told me that it is a deprecated function in 2.6.17. But now the computer freezes with the new modules installed. I read something about 4K stack in other forums. Any help is appreciated.

---

### Post by hokutonoken on 2007-01-31
I am an Ubuntu 6.10 edgy user and own an old Conexant winmodem(VendorID=127A : DeviceID=2005)
Unfortunately where I live (Italy) I have no access to a broadband connection whatsoever.

As you all know Linux without a working internet connection is like a car without wheels, so I desperately need a working driver.
I tried linuxant drivers, but free version supports only an useless 14k connection.

I read this topic some days ago and rejoiced; uninstalled linuxant and went for both Method A and B from Matchless' great guide.
After a plethora of compiling and script errors and a modem not recognized, I read the whole topic and found that those free drivers are not compatible with Ubuntu 6.10 C libraries and shell scripting (and perhaps the new kernel itself)

I am not a Linux coder, know some C programming under dos but have no idea of what should be done to make these drivers compatible with the new kernel.

My naive idea was trying to manually install build-essential, debhelper and fakeroot  packets from old 6.06 Dapper cd-rom, then using old C libraries for compiling modem drivers and keeping, of course, 6.10 kernel headers.

Unfortunately, some packets conflict with 6.10 libc6, which depends on many other libraries , and I gave up fearing some big trouble to my sistem. This may not definitely be the right way.
I would like some expert's opinion about the feasibility of a C library downgrade to compile drivers over 6.10 kernel.
This may not be the definitive solution but meanwhile we would have our modem modules compiled and running on edgy.

Anyway, I'd like to hear if some work is still in progress on the road started by autocrosser
 and duncan.
I hope it's only a matter of cosmetic changes to C source and script code. We should need some kernel expert.

Why don't we ask for Rafael Espíndola and AlexandreOttoStrube's help? 
If they were able to port drivers to 2.6.x kernel, they shold be able to upgrade them to Edgy as well.
Matchless, what do you think? Have you tried to contact them yet?

Best regards

---

### Post by ubuscout on 2007-01-31
> **hokutonoken said:**
> I am an Ubuntu 6.10 edgy user...

Best regards



...same problem... same question :( 

...we trust and hope in you expert...   :)

---

### Post by _duncan_ on 2007-01-31
> Anyway, I'd like to hear if some work is still in progress on the road started by autocrosser
and duncan.
I hope it's only a matter of cosmetic changes to C source and script code. We should need some kernel expert.

You hit the problem right in the head. I know C/C++ but practically no knowledge in the kernel side of things. I was able to get rid of the cosmetic problems due to deprecated functions, etc. to a point where the driver compiles, but there are problems I think that only a kernel expert / device programmer can solve. That's why I stopped working on it altogether.

An idea I wanted to try before but didn't have the time was to downgrade edgy eft to a lower kernel (a good bet is the default kernel version of Dapper 6.06, 2.6.15.xx I think). Then make the driver work for that kernel. But this is a rather complicated and circuitous route to take.

A more practical approach perhaps is to see if winmodems based on the smartlink chipset are available in your area. I live in the Philippines and this type of winmodems are abundant and very cheap here (about 5 US dollars each). The open-source driver for smartlink works very well with Edgy 6.10. 

The smartlink driver itself is being maintained by linmodems.org, so there is a higher likelihood that patches for future new kernel versions will be released.

---

### Post by autocrosser on 2007-01-31
Sorry I havn't posted also---Seconding duncan's post. I run a smartlink & have had no problems with Edgy--I'm about to try it with Fiesty (cross fingers), most likely this weekend. I'll post about the results.

---

### Post by hokutonoken on 2007-02-01
Thank you very much
So you think it's a kernel-related thing..It's quite sad because there seem to be only small chances to get these winmodems to work under edgy.
What about Raphael Espindola? Is he still interested in porting old free drivers to new ubuntu releases?did you hear anything from him?
 
About the downgrade you suggested, Duncan..Perhaps we had quite a similar idea. I tried installing Dapper C libraries while keeping Edgy kernel. 
This would have solved most of the infamous compiling errors, leaving of course both kernel header and kernel routines problems (if there are any).
I am no linux expert but I didn't succeed as there are too many conflicting libraries.

I will think about downgrading to Dapper (it's not a great solution, I know, but pc is quite old and Dapper is still a Long-Term-Support version, while Edgy will be obsolete in a few months' time), and that will mean re-downloading and installing all needed packages, which will take a looong time with a 56k modem.

Meanwhile I will follow your suggestion and search for a smartlink/lucent winmodem.
I have one of them inside my Acer notebook, and it works - unfortunately however, after  installing standard slmodem package from ubuntu repository, speed is limited to just 33.6 kbps. Tried each and every initialization string with no luck..
It's better than linuxant 14.4 kbps, but I will try and follow Matchless tutorial.

Do you know some manufacturers/brands which use smartlink chipsets inside their 56kbps modem?

Thank you very much, again.

---

### Post by hokutonoken on 2007-02-01
About Matchless tutorial

As I told you in my last post, I own an Acer laptop equipped with a Lucent Winmodem.

I usually installed ONLY sl-modem-daemon package using Synaptic (or Aptitude). 
Source module is not required at all.
This is the same as Method B from Matchless tutorial, I suppose.

sl-modem-daemon doesn't require any additional module, as it uses ALSA module, which comes with standard kernel.

My problem is that here in Italy, as I have read from other newsgroups, the main provider doesn't support V92.
Standard drivers try to gain access to network but can't find any carrier.
The only way to connect is to restrict Lucent modem to V34 (which means 33.6 kbps). This is done using initialization string ATX3+MS=34.
Using either +MS=90 or +MS=92 means no connection at all (no carrier found).

Compiling drivers from source, following Matchless' method A doesn't give any result.

This is what I have done

I uninstalled sl-modem-daemon package

Downloades sl-modem sourceand ungrab-winmodem packages from linmodems.org
 
sudo make install both sl-modem source package and ungrab-winmodem 

Then sudo modprobe slamr

gnome-ppp can't detect any modem at all.

Re-installing then sl-modem-daemon package (NOTE: Debian package doesn't install, as it has some broken dependency - libasound2), I find the same behaviour listed before.
Modem is now recognized, but it only connects @33.6 kbps.
Perhaps it still uses ALSA module.

It seems there is no need to make install modules from linmodems.org, as they are not loaded by sl-modem-daemon.
What I am trying to explain is that in my case both method A and Method B from Matchless guide give the same result.
Perhaps compiling and installing modules from linmodems is totally useless if you add sl-modem-daemon from Ubuntu packages.

What do you think? Any suggestion?

---

### Post by _duncan_ on 2007-02-01
> My problem is that here in Italy, as I have read from other newsgroups, the main provider doesn't support V92.
Standard drivers try to gain access to network but can't find any carrier.
The only way to connect is to restrict Lucent modem to V34 (which means 33.6 kbps). This is done using initialization string ATX3+MS=34.
Using either +MS=90 or +MS=92 means no connection at all (no carrier found).

If you are sure about this, my guess is 33.6 kbps is the max connection speed you can get, since any modem / driver combination you get working will still be subject to the v.34 init string required by your provider.

However, if you can connect to the same provider using the same modem under windows at v.90 or v.92, then it should be possible to connect at the same level using linux.

BTW, 56kbps is somewhat misleading coz it's the theoretical maximum connection speed. Realistically, even with a good driver working at v.92/v.90 and a relatively *clean* phone line, the max actual speed is probably in the range 45-48kbps.

> Re-installing then sl-modem-daemon package (NOTE: Debian package doesn't install, as it has some broken dependency - libasound2), I
Seems like some of the problems you're having compiling the linmodems.org driver and installing the sl-modem-daemon deb package are related to your installing Dapper libraries into Edgy Eft. I could be wrong though.

---

### Post by hokutonoken on 2007-02-02
Hi again Duncan, thank you very much for your reply!

Well, I didn't want this thread to become a personal thing, but anyway, perhaps this may help some people having trouble with lucent/conexant modules installation.

Well, first of all, I own two winmodems:

1)a Conexant winmodem (VendorID=127A : DeviceID=2005) on a quite old desktop pc.

2)a Lucent winmodem (Agere AC 97) on a recent Acer laptop

I installed Ubuntu 6.10 Edgy Eft on both systems .

The first winmodem came with win9x drivers and works greatly (max. 46.6kbps) under Win98/ME.

The second system came with win2k/XP drivers and works flawlessly (max. 52.0kbps) under WinXP.


I haven't find any way of  making them work full-speed under Ubuntu, yet. 

This is what I tried:

1)System one: Conexant winmodem

*linuxant drivers (free): package for Ubuntu Edgy (HSF modem): they compile, install and work 100% ok. Speed is however limited to 14.4 kbps

*Conexant open source drivers
Followed both Method A and B from Matchless guide: drivers do not compile and give a plethora of compiling and script errors.
This is exactly the point of the thread: I was asking if there's a way to change C code and make them compatible with new kernel.

*downgrade to Dapper C libraries: I found it an almost impossible thing. 
Too many libraries involved and Synaptic preventing me from removing Edgy libC6.
I didn't create too much confusion here, anyway.
I simply reinstalled build-essential and related libraries from Edgy Cdrom and everything returned the same as before.

FINAL RESULT
-->Still stuck at 14.4kbps with linuxant free drivers

2)System two : Lucent winmodem

I read both this thread and this one: (In Italian: try and translate it using Babelfish or Google in case you can't understand it)
[http://3v1n0.tuxfamily.org/blog/informatica/linux/agere-systems-ac97-modem-in-ubuntu-kubuntu-linux/](http://3v1n0.tuxfamily.org/blog/informatica/linux/agere-systems-ac97-modem-in-ubuntu-kubuntu-linux/)

*installed sl-modem-daemon package ALONE (together with gnome-ppp). 
That's the same as Method B from Matchless' Smartlink tutorial, without the unnecessary sl-modem-source package.

Everything works fine, but connection is limited to 36.6 kbps with the initialization string ATX3+MS=34.
Without this string (that's simply using ATX3, which is mandatory in Italy), modem can't find any carrier.
The same result trying ATX3+MS=90 and ATX3+MS=92.

*removed sl-modem-daemon.
As suggested in Italian thread, I tried compiling and installing [http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20051101.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20051101.tar.gz)
(using make install), together with ungrab modeule
A lot of errors (package is perhaps too old and not compatible with edgy libraries). Modem doesn't load using sudo modprobe slamr.
No modem detected by gnome-ppp

*I tried compiling and installing 
[http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20061021.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20061021.tar.gz)
, together with ungrab module
This is the first part of Method A from Matchless' Smartlink tutorial.
Found some warnings! 
Modem doesn't load with sudo modprobe slamr
No modem detected by gnome-ppp

*I tried reinstalling sl-modem-daemon
(Thus completing Method A from Matchless' guide)
Modem is now detected, but still works only @33.6kbps with ATX3+MS=34 string.

I really wonder if compiling and installing slmodem-2.9.11-20061021.tar.gz package gives any result at all.
In my case it seems totally useless. 
Just sl-modem-daemon package alone and modem works all the same.

FINAL RESULT:
-->modem stuck @33.6kbps using string ATX3+MS=34


----------------

What do you suggest? 

I think you Duncan are right, maybe my lucent winmodem (system 2) is flawed by a driver/module issue as it works ok under WinXP.
Maybe it's not a provider problem..Or perhaps driver can't negotiate carrier with Italian provider..there's some incompatibility, I mean. That's what each and every Italian user has found.
And I can't find any working method to solve this.

I fear buying a brand new Lucent/Smartlink winmodem for my desktop pc would be totally worthless, as I would be stuck @33.6 kbps.

Perhaps the best idea is to install Dapper on desktop system and enjoy good old Conexant open source drivers @full-56kbps.

what do you think?

Many thanks, again!

---

### Post by hokutonoken on 2007-02-03
As I absolutely need a working 56kbps connection on my desktop pc, I formatted and reinstalled Ubuntu 6.06 Dapper.

First of all, let's have a look at the requirements for a FRESH UBUNTU DAPPER INSTALLATION, from official cd-rom.

Matchless' tutorial is quite obscure about this point.

>>>You have to install the following packages

1)FROM DAPPER CD-ROM (using Synaptic)
NOTE: Just let Synaptic enable the necessary dependencies.

a)fakeroot

b)build-essential

c)linux-headers-2.6.15-26-386
(NOTE: if your installed dapper and already updated kernel, you must download linux-header-YOURKERNELVERSION. use uname -r from a terminal window)


2)You have to MANUALLY DOWNLOAD (from a working connection) from site packages.ubuntu.com the following packages. They are not on Dapper CD-Rom!!
NOTE:make sure you download dapper version.

d)debconf-utils

e)html2text

f)debhelper

3)You have to MANUALLY INSTALL (e.g. double-click and let Synaptic do the job) the packages you downloaded, in the exact order c, d, e

Otherwise you will receive an error because of broken dependencies.

That's it.
Now you can follow Method A (or B) of Matchless tutorial.

Compilation returns some warnings, but modem is finally recognized!

Thus, my advice for those who have a Conexant winmodem is to install Ubuntu Dapper and enjoy a full 56kbps connection!


127A:2005 -> Works ok

---

### Post by hokutonoken on 2007-02-05
I think Matchless' great tutorial needs a little revision.

About SMARTLINK/LUCENT winmodems.

Module packages listed on tutorial are quite old and don't work anymore. 

You need to access THIS webpage:

[http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/)

which contains the latest modules available for Ubuntu Linux.

There you need to download the latest package available for your kernel (type uname -r in a terminal window to discover which one you need to choose)

After downloading, you need to extract them (e.g. Right-Click and "Extract Here")
Now open a terminal window, type "cd YOURFOLDER" to enter decompressed folder, 
and finally type "sudo sh setup".

You're done. Now you can connect full-speed to the Net (that is @56kbps, of course)

The package you downloaded contains sl-modem-daemon(..).deb, too.
This is Smartlink Modem Daemon, which provides automatic configuration of our modem upon startup.
Just double-click on it to install, in case you need it.

Notice that if you live in Italy you need to insert string "ATX3" on gnome-ppp (or kppp) configuration window, otherwise your modem won't be able to detect line carrier.
If your modem detects line carrier but you are rejected by your provider (check connection log for details)you'll need to enable "Ignore terminal messages (Stupid Mode)" on gnome-ppp settings.
This is again needed for Italy's main provider.

Bye again

---

### Post by alexander1 on 2007-06-03
Hello,

I'm a Newbie in Linux (Ubuntu Feisty Fawn) and I'm sorry for my bad english. (I'm a German)
Thats my modem: 
VendorID=14F1 : DeviceID=2014
Conexant HSF 56k Data/Fax/Voice Modem

I followed the instructions Method A and until this line:
sudo /usr/sbin/modem-hsf --install 
it worked perfectly.

But that instruction failed. There is not the modem in /dev/
Do you know why? Or how I can fix it?
I hope you can help me!!! I need my modem.

That happend when I write: sudo /usr/sbin/modem-hsf --install 
> root@alexander-desktop:~# sudo /usr/sbin/modem-hsf --install
Removing modules:
&#8222;/etc/hsf/GERMANY&#8220; entfernt
&#8222;/etc/hsf/14F1.2014&#8220; entfernt
Verzeichnis wurde entfernt: &#8222;/etc/hsf&#8220;
make clean -C inf
make[1]: Betrete Verzeichnis '/usr/share/conexant-192-1ubuntu/inf'
rm -rf *.o
rm -rf *.temp
rm -rf *.bin
rm -rf hsfinf2bin
make[1]: Verlasse Verzeichnis '/usr/share/conexant-192-1ubuntu/inf'
make clean -C modules
make[1]: Betrete Verzeichnis '/usr/share/conexant-192-1ubuntu/modules'
make -C /lib/modules/$(uname -r)/build M=/usr/share/conexant-192-1ubuntu/modules
 clean
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
  CLEAN   /usr/share/conexant-192-1ubuntu/modules/.tmp_versions
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
rm -rf *.ko
rm -rf *.o
rm -rf *.O
make[1]: Verlasse Verzeichnis '/usr/share/conexant-192-1ubuntu/modules'

VendorID is 14F1 DeviceID is 2014 Country is GERMANY CountryCode is 04,00

make clean -C inf
make[1]: Betrete Verzeichnis '/usr/share/conexant-192-1ubuntu/inf'
rm -rf *.o
rm -rf *.temp
rm -rf *.bin
rm -rf hsfinf2bin
make[1]: Verlasse Verzeichnis '/usr/share/conexant-192-1ubuntu/inf'
make clean -C modules
make[1]: Betrete Verzeichnis '/usr/share/conexant-192-1ubuntu/modules'
make -C /lib/modules/$(uname -r)/build M=/usr/share/conexant-192-1ubuntu/modules                                                             clean
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
rm -rf *.ko
rm -rf *.o
rm -rf *.O
make[1]: Verlasse Verzeichnis '/usr/share/conexant-192-1ubuntu/modules'
make -C inf
make[1]: Betrete Verzeichnis '/usr/share/conexant-192-1ubuntu/inf'
cc -I../modules/imported/include -I../modules/osspec/include -O2 -Wall   -c -o i                                                            nf2bin.o inf2bin.c
inf2bin.c: In Funktion »ProcessString«:
inf2bin.c:236: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeiche                                                            nbesitz
inf2bin.c: In Funktion »ProcessCtryStruct«:
inf2bin.c:393: Warnung: Zeigerziele in Zuweisung unterscheiden sich im Vorzeiche                                                            nbesitz
cc -o hsfinf2bin inf2bin.o
(./preprocess.sh linux_hsfi-14F1-2014.bin > linux_hsfi-14F1-2014.bin.temp; ./hsf                                                            inf2bin linux_hsfi-14F1-2014.bin.temp linux_hsfi-14F1-2014.bin)
make[1]: Verlasse Verzeichnis '/usr/share/conexant-192-1ubuntu/inf'
make -C modules
make[1]: Betrete Verzeichnis '/usr/share/conexant-192-1ubuntu/modules'
make -C /lib/modules/$(uname -r)/build M=/usr/share/conexant-192-1ubuntu/modules modules
make[2]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/mod_basic2.o
In file included from /usr/share/conexant-192-1ubuntu/modules/mod_basic2.c:51:
/usr/share/conexant-192-1ubuntu/modules/osspec/include/oscompat.h:57:26: error: linux/config.h: No such file or directory
make[3]: *** [/usr/share/conexant-192-1ubuntu/modules/mod_basic2.o] Fehler 1
make[2]: *** [_module_/usr/share/conexant-192-1ubuntu/modules] Fehler 2
make[2]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
make[1]: *** [default] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/share/conexant-192-1ubuntu/modules'
make: *** [all] Fehler 2
cp: Aufruf von stat für &#8222;modules/hsfbasic2.ko&#8220; nicht möglich: No such file or directory
cp: Aufruf von stat für &#8222;modules/hsfengine.ko&#8220; nicht möglich: No such file or directory
cp: Aufruf von stat für &#8222;modules/hsfich.ko&#8220; nicht möglich: No such file or directory
cp: Aufruf von stat für &#8222;modules/hsfosspec.ko&#8220; nicht möglich: No such file or directory
cp: Aufruf von stat für &#8222;modules/hsfserial.ko&#8220; nicht möglich: No such file or directory
FATAL: Module hsfserial not found.

Modem driver should be installed and available on /dev/modem.
If not, your modem may not be supported.

root@alexander-desktop:~#                                             


Greetings Alexander

---

### Post by Matchless on 2007-06-03
Guten tag Alexander,
                              I have not updated any of the information since updating to Feisty and have also not used Smartlink for a long time. The Conexant open drivers that you have tried, do not work on the Feisty of Edgy kernel version and fix has not yet been found. The thread has some posts in it if you read them. The only way at the moment is to download and install the free Linuxant driver for your HSF modem at: [COLOR=#000080]_[[FONT=Arial, sans-serif][SIZE=2]http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.60.00.09full/hsfmodem-7.60.00.09full.tar.gz[/SIZE][/FONT]]("http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.60.00.01full/hsfmodem-7.60.00.01full.tar.gz")_[/COLOR]
 These drivers are free, but restricted to 14.4k and can be opened up with a registration code that you get on paying a fee, but at least will allow you to test and get online. they also have a deb file, but i am not sure if it is for the latest Feisty version or not.

---

### Post by alexander1 on 2007-06-04
Guten Tag :D; Hello,

thanks for your answer.That I can't use my modem, is really bad, because Ubuntu and it's nice Package Manager, and Program Manager wants something to download everytime. And without Internet connection, I can't even play my mp3 files, because it needs the plugins for gstreamer.

Regards Alexander


PS: I want to mention, that at my installation of Ubuntu, the Boot Manager Grub, was not installed correctly. I've to change lofs of things (With Knoppix Live CD), until I can start my XP or even Ubuntu. 
Other Linux Destributions all install a correct Boot Manager.

---

### Post by Matchless on 2007-06-04
If you are using a desktop PC and not a laptop, you can change to a Intel536EP or a Smartlink internal modem and quite a few others and if you have a serial port you can use just about any proper external serial modem without installing any drivers
Good luck

---

### Post by alexander1 on 2007-06-09
Hello,

I want buy me a cheap USB Modem.
Which USB 65k Modem does surly support Linux ?

Regards Alexander

---

### Post by Matchless on 2007-06-09
Alexander,
                I cannot help you here as I have not used USB modems to date, but you should note that the actual name of the modem does not really mean much, it is the chipset that the modem uses that determines which can be used, You may have an xyz modem, but it may have a conexant chip, meaning that you would only be able to use the free but limited modem driver from linuxant or pay for full 56k, but it will work on linux. It also seems as if modems that are based on smartlink may also work.
Here is a site that has a post on successfully using an USB modem. [http://www.mepis.org/node/7482](http://www.mepis.org/node/7482)
I suggest you need to google for USB modems on ubuntu and see what people have made to work. You biggest problem will be to determine what chip the USB modem is using and thus then if there are linux drivers for them and then only you may have to do a bit of work to get the drivers installed if required. Visit friends who have USB modems and are using XP and do a modem query to see what type of modem it may be or open the windows drives and have a look at the top, sometimes there are clues, then varify on google and then buy it!
Good luck and let us know what works to help others.

---

### Post by alexander1 on 2007-06-09
Hello,

thanks. I look for a modem, and post the model, if I get one.

Regards Alexander

---

### Post by autocrosser on 2007-06-09
You can be sure that a Zoom/Faxmodem model# 2986L will work--it is called with dev/ttyACM0--a built-in module with most newer kernels. I used one for several years & still have it (with the wvdial.conf) as a backup modem. I'll send you the .conf if you want it--Make sure you get a 2986L modem--others do not work well. I have seen them on eBay in the $25US range.

---

### Post by alexander1 on 2007-06-10
Thank you, but that's to expensive. I want to get something under 10 Euro.
What do you think of this modem:
[http://cgi.ebay.de/ws/eBayISAPI.dll?ViewItem&item=140126976161&ssPageName=ADME:B:EF:DE:2](http://cgi.ebay.de/ws/eBayISAPI.dll?ViewItem&item=140126976161&ssPageName=ADME:B:EF:DE:2)
in ebay.de
(German ebay :D)
The seller says, that it is a "Smart Link Soft Modem" and that Smart Link is now Conexant.
And he says it Linux Kernel 2.4 support it. And what is with Linux Kernel 2.6? I'll ask him this.

Regards Alexander

---

### Post by autocrosser on 2007-06-10
Not too sure--I'd look at:  [http://www.qbik.ch/usb/devices/](http://www.qbik.ch/usb/devices/)
for information on USB devices.

I'm not seeing the Freeway listed there---you could contact the vendor for more info....

---

### Post by Matchless on 2007-06-10
Have a look here [http://www.mandrivauser.de/smf/index.php/topic,5762.0.html](http://www.mandrivauser.de/smf/index.php/topic,5762.0.html)
and here [http://www.treiberupdate.de/treiber-download/download-155575-treiber-Neolec-FreewayUSB.html](http://www.treiberupdate.de/treiber-download/download-155575-treiber-Neolec-FreewayUSB.html)

You may be in luck. if not sure download the XP driver for this modem and have a look ot the top of the files and see what they are reffering to as ich verstehe nicht deutch

---

### Post by alexander1 on 2007-06-11
Hi,

thanks, for your links. The seller wrote, that the readme on the cd says:
"This is Smart Link Soft Modem for Linux version 2.6. It provides full-featured 56K Voice Fax Modem. "

And this is really good:
[http://www.treiberupdate.de/treiber-download/download-155575-treiber-Neolec-FreewayUSB.html](http://www.treiberupdate.de/treiber-download/download-155575-treiber-Neolec-FreewayUSB.html)

I hope thier will be no problems. I'll buy it.

Thanks for your support. I'll write if whether the modem works or not.

Regards Alexander

---

### Post by linus_torvalds_2006 on 2007-06-14
I have what Windows Vista's Device Manager records as a "Conexant D850 PCI V.92 Modem".  In the "Hardware ID" field, I am getting a reading of "PCI\VEN_14F1&DEV_2F20&SUBSYS_200F14F1&REV_00". Since this reading is not entirely identical to the reading you specify, I cannot be so quick as to safely assume that the modem will work with the drivers I fetch from this site.  Are there some special instructions I should follow for a modem of this class?

Brandon Taylor

---

### Post by Matchless on 2007-06-14
14f1:2f20 identifies it as an HSF Conexant modem and if you are running anything later than the Dapper kernel versions you will not be able to use the open source drivers. The only ones that work on Edgy and Feisty will be free throttled one on the linuxant site.

---

### Post by zorkerz on 2007-06-17
Matchless could you perchance update your old thread here saying that this one exists. The scanModem tool still gives the address to you old thread. I did not realize the new one existed for quite some time.

ScanModem gives me this 

PCI ID: 14f1:2f00 
Subsystem ID: 141b:8d88
Communication Controller: Conexant HSF 56k HSFi Modem

I think this means I can only use linuxant speed restricted drivers because im in feisty.
xubuntu 7.04 would not change this would it?
is anyone working on uncrippled drivers for feisty systems?
I guess its time to play the waiting game
thanks

update: I installed the linuxant drivers and entered my dialup information. The modem dials or at least makes all the sounds but i do not get internet. I know the modem and the connection are good because I can  dial up on windows. 

What can I do to get error message or to find out what is going wrong?

---

### Post by Matchless on 2007-06-18
It seems as if you modem is dialing out. This means that your config may not be correct. Try using wvdial and make sure you have it set up correctly. You can also try pon and poff from the terminal. Once wvdial works you can try using gnome-ppp in both Kubuntu or Ubuntu. This is just really a front end for wvdial and should work and is not too finicky to set up. In Kubuntu you can also try Kppp and turn on the log and it will show you what it is doing. If you are logging into your ISP, but are having difficulty browsing, it may be due to you DNS not resolved. There are many tips out there, but I have used Kppp with mostly default settings and then left it online for a good couple of minutes while the browser would not open google and then it would start and be OK thereafter.

---

### Post by zorkerz on 2007-06-18
Hey thanks for the fast response. I have now tried gnome-ppp with moderate success. I now get a connection but it cuts out quickly especially when i begin to use it.  I was hoping to reload my package lists but it cannot get through that.

---

### Post by Matchless on 2007-06-19
In wvdial configuration and in gnome-ppp it is a good idea to have stupid mode=on. you can also use the open DNS

---

### Post by zorkerz on 2007-06-19
I have now turned stupid mode on in gnome-ppp and wvdial. I am not getting any change in modem behaviour.

I have been trying to use open dns but am not sure how to get gnome-ppp to use the right addresses. I set it up in network the way open dns says on their site and I set gnome-ppp to manual DNS with the appropriate DNS address.

However the gnome-ppp log still shows the "primary DNS address 198.68.168.254" and "secondary DNS address 63.166.217.20" instead of the 208.67.222.222 and 208.67.220.220 that it should be.

I have attached my gnome-ppp log file if it helps anyone. There are a couple warnings i do not know about.

The /var/log/messages file does not seem to be very helpful. It says "Modem hangup". I also notice that there are never more than a few kilobyts sent.

---

### Post by Matchless on 2007-06-20
Edit /etc/wvdial.conf :

Comment this line:

#Carrier Check = no

Add this line:

Stupid Mode = yes

Post your contents of the above file.

---

### Post by zorkerz on 2007-06-20
whoops I had stupid mode = on instead of yes (or does that not matter ive seen it referenced both ways). The check carrier line was not there at all. I did not add it as the comment essentially removes it.

Ive been using the wiki a bit it says that gnome-ppp stores its config file at $HOME/.wvdial.conf and wvdial stores at /etc/wvdial.conf. I checked this, each time I check "Ignore terminal strings (stupid mode)" it edits /home/dave/.wvdial.conf not /etc/wvdial.conf

Also noticeably this sets stupid mode to on not yes. I am now assuming that both on and yes are equivalent.

Should I worry about the conf file in my home.

both wvdial and gnome-ppp have the same problem of being unable to stay connected for long.

The gnome-ppp log is different now at some point it attempts to use my username and password I have stared these out in the attachment.

thanks as always.

---

### Post by Matchless on 2007-06-21
Maybe this will help a bit, also have a look at your default modem speed it should really be 115k not 460K, I am not sure if this will affect anything.
The procedure below has worked for me on many new clean installs. Just check it out and see if you have anything different. In Feisty Kubuntu I now have Kppp working perfectly, but had problems in Edgy

Setting up WVdial and gnome-ppp

  	 	 	 	 	 	 	 	 	  After finding it just about impossible to get Kppp to work properly. I have found that Gnome-ppp is very stable in Kubuntu. The suggestion is to set up wvdial properly and then install Gnome-ppp from the repositories, which is actually a front end for wvdial. It lacks all the bells and whistles that kppp has, but it works. Only use kppp to query the modem as this will always work.
Here are the details for those new to this:
[COLOR=#000000][SIZE=3]_**Tried and tested good old wvdial:**_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]The most reliable way to get dialed up is via [/SIZE][/COLOR][COLOR=#000000][SIZE=3]**wvdial**[/SIZE][/COLOR][COLOR=#000000][SIZE=3] from the konsole, but this means you need to keep the konsole open while you are connected to make sure that you are able to disconnect the modem by typing CTRL+C to disconnect from the telecom line and get back to your normal prompt. If you happen to close the konsole before disconnecting, you may have to reboot your PC to get the modem to disconnect or you may not be aware that you are still connected and run up an account! This can be solved by installing a dial up dialer gui. Some problems may also be picked up when initially configuring wvdial, such as detection of modem.[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_In the konsole type:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]sudo wvdialconf /etc/wvdial.conf[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]If this fails due to not finding a modem, it means the modem drivers are not properly installed, but if you can query the modem successfully in Kppp, then it may mean that wvdial cannot see /dev/modem to set itself up properly. In all cases you may have to open up the file:[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]In Konqueror navigate to /etc/wvdial.conf, Right click, Actions, Edit as root and change or add the following lines so that the file looks like this below and save:[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3][Dialer Defaults][/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Init1 = ATZ[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Modem Type = Analog Modem[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]ISDN = 0[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Phone = xxxxxxxxxxx [/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]New PPPD = yes[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Modem = /dev/modem[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Username = yyyyyyyyyyyyy[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Password = zzzzzzzzz[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Baud = 115200[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Stupid mode = on[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]# Carrier Check = no[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]xxxxxxxxx = the number to dial up your ISP[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]yyyyyyyyy = your username supplied by your ISP[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]zzzzzzzzz = your ISP access password[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]In the last line remove the comment # to enable Carrier Check = no if you are using a Smartlink internal modem.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]You can also add W2 to the Init2 line to show the connection speed if required[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_Now go to the console and type:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]sudo wvdial[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Once connected see if you can open your browser[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Remember to keep the konsole open while you are connected, you can minimise it if it is in your way.[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_To disconnect line while in konsole type:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]CTRL+C to end the connection[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_Some hints:_[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]If you find that you lose the connection after 30 sec to 3 minutes, then edit pppd.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Right click on /etc/ppp/options, actions, Edit as root[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Find lcp-echo-interval 30 and lcp-echo-failure 4 and comment both out by adding a # at the beginning of the lines.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]If you find that you connect successfully, but cannot open any webpages in Firefox then add line default route to /etc/ppp/peers/wvdial[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_Adding a gui to wvdial:_[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]The good news is that there is a nice simple gui for wvdial called Gnome-ppp. This is normally only used in Ubuntu and the name Gnome tends to keep KDE die-hards from installing it on Kubuntu, but it installs straight from the repositories. So once you have wvdial working and you can connect to the internet, enable and update your repositories, use your package manager to download and install Gnome-ppp, right click on the menu icon and create an icon on your desktop. Now rename it so as not to embarrass you as Kubuntu user! to e.g. “Dial up ISP” and it should work very nicely and is definitely more bullet proof than Kppp, even on KDE.[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]_**Configuring Gnome-ppp:**_[/SIZE][/COLOR]


[COLOR=#000000][SIZE=3]Open Gnome-ppp and click on Setup[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Modem tab, Device, you can click detect to have Gnome-ppp detect your modem, but as under the wvdial setup this would maybe not work and you will have to type in your modem device. This could be /dev/modem or /dev/ttyS0 if you have an external modem connected to Com1 or /dev/ttyS1 if on Com2. Here I would suggest using Kppp (the only reliable function that will always work) to Query the modem if you are having problems.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Type select Analogue modem[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Speed 115200[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Phone line Tone[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Volume Hi (speaker volume)[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Dial attempts 1[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Wait for Dial tone checked[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Initstrings and phone number to dial should be picked up from your wvdial configuration, but if not enter them. (see wvdial)[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Networking tab[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Leave Dynamic IP Address and Automatic DNS enabled[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Under Options tab[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Check the following items as on, Abort connecting if no dial tone, Check carrier line, Check default route, Ignore terminal strings(Stupid mode). Leave the rest disabled or change any of the settings as your preferences once all is working.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Close and reopen Gnome-ppp[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Type in your ISP username[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Type in your ISP password[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Check remember password[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Select the number to dial up or type in.[/SIZE][/COLOR]
[COLOR=#000000][SIZE=3]Now click connect and you should be on.[/SIZE][/COLOR]

Hope this makes life more bearable if you are a dialup user.

---

### Post by zorkerz on 2007-06-21
Thanks for that post im afraid im still having the same problem. Cannot stay online for more than a couple of seconds. It stays connected fine until i try and use the internet then it disconnects. In firefox i can usually navigate through a couple links before the internet kicks out.
Any other ideas on how to fix this or where i can go to look. Im close to giving up since even if i get it to work it will be the crippled linuxant driver.

Also It tries to dialup when the computer starts which is rather annoying.

cheers

---

### Post by Matchless on 2007-06-22
All I can think of is that with all the experimenting you may have changed some config somewhere.... or could your modem be faulty? Have you tried a complete uninstall and tidy up and a new clean install of the drivers and related? At worst how about a clean install, of Ubuntu? I recall seeing some post on a modem dialling problem on startup a while back, have a search in the forum maybe they have some answer. I have 2 installs running happily and have not had that problem at all.

---

### Post by zorkerz on 2007-06-23
Only config files ive messed with unfortunately are /etc/wvdial.conf /home/davd/.wvdial.conf and /etc/ppp/options

The modem works in win 98 fine. It does have a tendency to disconnect when it should not but thats in the range of once ever 15-30 min not every 15-30 seconds.

Its and old computer and not woth too much work. Im running xubuntu right now. Someday i may get around to reinstalling it to see if that helps but im not too confident that it will.

Thanks for all the help I may start trying to find a new modem to steel out of some old computer. With a little luck i can find one that is more open source friendly.

Cheers and thanks for all the help

---

### Post by megahead13 on 2007-06-25
Hi! I can confirm that the method described in the original post worked flawlessly on a Dell Inspiron 1501 (Kubunutu 64bit installed). The modem used on this laptop is a Conexant HDA D110 MDC V.92 (HSF softmodem). I haven't "played" with the AT initialization commands through KPPP, but everything seems fine, at least at the moment... :P I suppose that there will be no problem for my Dell Latitude D820, since it uses the same softmodem....

---

### Post by zorkerz on 2007-06-25
Well I have given up with this modem for the time being. I found a lucent modem that  I have been messing around with but it is coming up with a very similar problem im now trying to solve [here.]("http://ubuntuforums.org/showthread.php?p=2910795#post2910795")
Thanks for all your help

---

### Post by megahead13 on 2007-06-27
> **megahead13 said:**
> Hi! I can confirm that the method described in the original post worked flawlessly on a Dell Inspiron 1501 (Kubunutu 64bit installed). The modem used on this laptop is a Conexant HDA D110 MDC V.92 (HSF softmodem). I haven't "played" with the AT initialization commands through KPPP, but everything seems fine, at least at the moment... :P **I suppose that there will be no problem for my Dell Latitude D820, since it uses the same softmodem....**
It seems that there is a problem in the Latitude D820! When I run the **"sudo /usr/sbin/modem-hsf --install"** command I get the following error:

```
make[2]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /usr/share/conexant-192-1ubuntu/modules/mod_basic2.o
In file included from /usr/share/conexant-192-1ubuntu/modules/mod_basic2.c:51:
/usr/share/conexant-192-1ubuntu/modules/osspec/include/oscompat.h:57:26: error: linux/config.h: No such file or directory
make[3]: *** [/usr/share/conexant-192-1ubuntu/modules/mod_basic2.o] Error 1
make[2]: *** [_module_/usr/share/conexant-192-1ubuntu/modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/modules'
make: *** [all] Error 2
cp: cannot stat `modules/hsfbasic2.ko': No such file or directory
cp: cannot stat `modules/hsfengine.ko': No such file or directory
cp: cannot stat `modules/hsfich.ko': No such file or directory
cp: cannot stat `modules/hsfosspec.ko': No such file or directory
cp: cannot stat `modules/hsfserial.ko': No such file or directory
FATAL: Module hsfserial not found.

Modem driver should be installed and available on /dev/modem.
If not, your modem may not be supported.
```

Any ideas?

---

### Post by Jasman on 2007-07-04
> **entropic_existence said:**
> Hi folks,

I've sort of followed this thread because I had been attempting to install the Conexant modems so I could use linux on my laptop while at my parents place over the holidays, where only dial-up is available. Of course like many of you I have had problems (and am still unable to get the driver to install) but right now I actually don't care if I have it installed or not.

My problem now is that the Conexant module is sitting here half-configured which has broken apt on my system. I have not been able to remove Conexant using dpkg or apt because the various modules are not installed. Anyone have any suggestions on how to remove it?

Did anyone ever give an answer to this question, because I can't find one. My apt is entirely frozen because of this conexant package sitting in limbo. I was stupid to try to install it on Feisty, but it installed itself, and it seems it will remain there forever. Thanks.

Oh, forget it, I just found some answers here: [http://ubuntuforums.org/showthread.php?t=356495&highlight=conexant+uninstall+force](http://ubuntuforums.org/showthread.php?t=356495&highlight=conexant+uninstall+force)

---

### Post by andrikos on 2007-07-08
I tried to make a port of the driver to the new (2.6.20) kernel.
I have no idea if my work is finished but it seems that it at least passes compile.

You can find the new versions attached. The changes made were (file : lines) :

/usr/share/conexant-192-1ubuntu/modules/osspec/include/oscompat.h	: 57
/usr/share/conexant-192-1ubuntu/modules/osspec/include/osstdio.h	: 64 - 68
/usr/share/conexant-192-1ubuntu/modules/osspec/ostime.c	: 205
/usr/share/conexant-192-1ubuntu/modules/serial_hsf.c.orig	: 66, 184-215, 611, 688, 692

The files were changed after the installation of the modem-hsfpci_0.1-0ubuntu1_i386.deb package, so we need someone to update them in the original package.  Until then, can someone substitute his files with these ones (please backup the original first), try  sudo /usr/sbin/modem-hsf --install and  tell me if the driver works like in the previous kernel versions?

Hope I helped a bit

---

### Post by Matchless on 2007-07-09
andrikos,
 Thanks for this great attempt! It seems as if the changes you made work mostly, but the modem seems to be seized after a reboot and does not want to dial out, although dialling does take place (dial tones). The modem query also fails due to the same. Thereafter the modem only releases during a reboot but is again seized just when Kubuntu loads. It seems as if something is still not exactly right.
I have a question - you show file **serial_hsf.c.orig** , but there is no such file only **serial_hsf.c**  So I am not sure is this one added or is it supposed to replace the existing one?
Then I also tried the same changes to the conexant_192-1ubuntu-1.tar.gz file and it seems to install and compile with only a few errors. This one on its own installed and ran properly up to Dapper and just needs the changes for Kernel version 2.6.18 upwards and should then run on Feisty. It would be much appreciated if you could have a look at this one for us. There are a few errors when running make. You will most probably get a million thankyou's from everyone!!!

Thanks

---

### Post by andrikos on 2007-07-10
First of all, I would like to start from a version working in a previous Ubuntu version (Dapper you said, right?). Can you tell me exactly the Ubuntu version and the packages you used?
Also, the whole procedure of installing it and working? (A full console trace would be nice)

I need these to see what are the changes and try to deal with them. I know there are some warnings during the compile in *sudo /usr/sbin/modem-hsf --install* so maybe it is their fault. I cannot be sure if I don't look at a working trace first (sorry I don't have dapper to test it).

The *serial_hsf.c.orig* in my machine is located in */usr/share/conexant-192-1ubuntu/modules/serial_hsf.c.orig*
Actually, during *modem-hsf --install* it is copied to */usr/share/conexant-192-1ubuntu/modules/serial_hsf.c* so if you don't have the first one, just change the second one, but make sure the changes remain after any invocation of the install procedure.

---

### Post by Matchless on 2007-07-10
andrikos,
            The method below worked in Kubuntu Dapper while the kernel version was below 2.6.18. When we moved to Edgy it would not work anymore as the compilation started failing. I have upgraded to Feisty Kubuntu and cannot test on Dapper again. I have a feeling that your proposed changes in the file below could be the solution. Let me have a pm with your mail and I will email what I have. Then we can communicate without bloating the forum too much, unless you prefer keeping it on the forum. I will also save the files tomorrow so that you can see the results of the compile. I will be a bit slow as I only go online (via dialup) in the evenings here.


1.Put the downloaded file conexant_192-1ubuntu-1.tar.gz from here [http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/) on your Desktop and right click “Extract Here” and a folder “conexant” will be created on your Desktop.
2.Read the txt files in the folder for more info.
3.Open the folder “conexant/modules/makefile”, right click on makefile, click Actions, then Edit as Root and Kwrite should open the file /conexant/makefile. Now find the 2 lines that start with # KERNELDIR? = /lib/modules..... etc. and KERNELDIR?= /usr/src... etc Remove the comment # in the first line and insert comment # on second line and save changes.
4.Now open the /conexant/makefile in the same way and find the commented line # rm -rf $$DESTDIR/dev/ttySHFS0. Remove the comments from the mentioned line and the following 3 lines up to “update modules” and save changes
5.cd Desktop/conexant
6.make
7.sudo make install
8.sudo modprobe hsfserial     (you should get no result report if OK)
9.dmesg | grep hsfserial         ( you should get no result report if OK)
10.The /dev/ttySHFS0 is created for the modem
11.To test, use the query modem on Kppp

---

### Post by amaurynieto on 2007-07-22
Actually, for Dell's conexant modem (integrated with the audio chipset) the folks over at dell Support have come up with a DEB file with the appropriate conexant drivers. Granted, only "official" for the 1505n model, but when looking into the chipset on either model (1501 and 1505n), we find it's the same D110 chipset. You run the DEB file, it installs, you reboot. Viola! 

Link: [http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en](http://support.dell.com/support/downloads/driverslist.aspx?os=UBLN&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=INSPIRONI6400%2FE1505&hidos=WW1&hidlang=en)

---

### Post by tiwag on 2007-09-30
> **zorkerz said:**
> Thanks for that post im afraid im still having the same problem. Cannot stay online for more than a couple of seconds. It stays connected fine until i try and use the internet then it disconnects. In firefox i can usually navigate through a couple links before the internet kicks out.
 ... 

i'm suffering with the same problem - no advice seems to work!

my troubles are with a Dell D820 notebook, the modem is a Conexant D110 hsf-modem.
i tried it with the linuxant drivers, which are provided at the Dell-support homepage.

it basically connects to my isp, DNS etc. all is working.
also browsing to one website e.g. with firefox is ok,
but when i try to browse to a second url, the modem hangs up and the connection dies. 
sometimes it hangs up when i browse on the same website just to another page.

***grrrrrrrrr, ****

---

### Post by tiwag on 2007-10-13
after studying the syslog messages, i found out after a while, 
that my lost connection was caused by a pppd "Lost compression sync" error

from the **syslog**
> 
Oct 13 09:27:54 DB pppd[6329]: Lost compression sync: disabling compression
Oct 13 09:27:54 DB pppd[6329]: sent [CCP TermReq id=0x2"Lost compression sync"]
Oct 13 09:27:54 DB pppd[6329]: rcvd [Compressed data] 00 15 c4 56 5d 4f c2 30 ...
Oct 13 09:27:55 DB pppd[6329]: rcvd [CCP TermAck id=0x2]
Oct 13 09:27:56 DB pppd[6329]: Modem hangup



the solution for this problem, was to disable deflate compression in pppd options

by adding the line 
```
nodeflate
```
to the file **/etc/ppp/options**

---

### Post by eeried on 2007-12-04
Hello every body,

Nice endeavour with the blasted conexant drivers. Smartlink is another kettle of fish since they do provide a decent driver for no cost, and linmodem has all the info.

1. I really can't see Linuxant point that we should pay for a driver for a  little bit of cheap component  as conexant winmodems are. 

2. As someone in this thread has noticed, why has the developement of the conexant free driver stopped? Laptops still sell with conexant stuff,  Acer aspire 7720Z is an example. So we'd need some help with Gutsy.
The problem seems to be that nobody understands what to change exactly in the code to make the driver work on a new kernel. I wouldn't be able to help with that though.

:mad:

3. Could we use the DELL deb file? or again is it a closed driver for those who bought a dell machine? [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/New_Conexant_Modem_Driver)

---

### Post by kls_user on 2008-05-05
linuxant support usb modem.

wonder if dapper version support usb modem...
I use prolink 1456U using connexant too.
don't remember the chip

not spot any usb modem @ support list

thx in advance

---

### Post by eeried on 2008-05-05
the problem with Connexant (Linuxant) is they make you pay for the driver and you need to buy a new one after each kernek upgrade. (unless you're happy with the slow free version whihc is a joke, just to test if the driver works at all.

Conclusion: connexant winmodem to the dustbin.

---

### Post by Matchless on 2008-05-14
Hi Dell has Conexant drivers available for Hardy for download at [http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb)
Enjoy

---

### Post by eeried on 2008-05-14
Are you sure this package works on other computers than Dell? I undesrtand Dell has a modified Ubuntu version.

---

### Post by Green_Star on 2008-05-14
@Matchless

I think these drivers are just a free drivers from Linuxant, these drivers doesnt support 56kbps (i guess it supports 14kbps?)speed and doesnt support fax. 

Can some one confirm? 

By the way if some one successfully compiled and installed these drivers (as explained in tutorial), can you please give me deb package for Ubuntu 7.10. I am not able to compile without errors. 

Thanks in advance.

---

### Post by kb3hns on 2008-05-14
I just installed on a new system.  From the forum at linuxant, they say using ATW1 makes the modem go at full speed.  Using a teletone (telephone simulator) going between 2 linux boxes (the other with a Rockwell ISA hardware modem) I get this on the other modem:

AT 7=4S0= 1 X4  Q
OK
atw1
ERROR

RING
ata
CONNECT 33600/ARQ/V34/LAPM/V42BIS


and this on the HSFi:
AT S7=45 S0=0 L1 V1 X4 &c1 E1 Q0
OK
atw1
OK
atdt 101
+MCR: V34

+MRR: 33600, 33600

+ER: LAPM

CONNECT 115200

It looks like V.34BIS 33.6kbps, which is exactly what I should be getting going modem to modem.  

FYI.  

Andrew Buettner

---

### Post by Matchless on 2008-05-25
OK just tested the Smartlink drivers from the Ubuntu Repositories for Hardy and they work well. So it seems as if both Conexant and Smartlink are working for Hardy. If anyone can confirm this to help others it will be appreciated as I personally am on ADSL and not experimenting with the modems any more.

---

### Post by JoshuaJamZ on 2008-06-16
I've tried both methods A and B and get the same error:

```
Desktop/conexant/modules/osspec/include/oscompat.h:57:26: error: linux/config.h: No such file or directory
```

Have installed all dependencies and am stumped... would appreciate any help :)

EDIT:

Also, lspci reports:

```
00:09.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
```

and lspci -n :

```
00:00.0 0600: 1106:0691 (rev 44)
00:01.0 0604: 1106:8598
00:07.0 0601: 1106:0596 (rev 12)
00:07.1 0101: 1106:0571 (rev 06)
00:07.2 0c03: 1106:3038 (rev 08)
00:07.3 0600: 1106:3050 (rev 20)
00:09.0 0780: 14f1:2f00 (rev 01)
00:0b.0 0200: 10ec:8139 (rev 10)
00:0c.0 0401: 1274:5880 (rev 02)
01:00.0 0300: 1002:4742 (rev 5c)
```

and changed appropriately modem-hsfpci.conf following method A instructions...

One more thing to mention is that this is a new install of Gutsy on a PIII... wanting to setup Vgetty as an answering machine/callerid... did have Win Sever 2003 on here, but would much rather use Linux... but really do need this to work for the callerid stuff... so, again, any help would be greatly appreciated...

---

### Post by Matchless on 2008-06-19
This is an very old thread and I suggest you read backwards from the last post and you should find a method that works.

---

### Post by mickeyWD on 2008-06-24
...finding the method works for me. 

slmodem is mine, just removed from restricted driver. Arg...
Thank you.

---

### Post by mickeyWD on 2008-07-04
Hi,:(
I need some tips to make my modem work again.
I've installed slamr-2.6.24-19-generic.tar.gz package the same way its described in the slamr_Read.txt and now I've```
laj@little:~$ lspci | grep Modem
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
laj@little:~$ lsmod | grep winmodem
ungrab_winmodem         3584  0 
laj@little:~$ lsmod | grep amr
slamr                 433448  2 
laj@little:~$ dmesg  | grep amr
[   25.352265] slamr: module license 'Smart Link Ltd.' taints kernel.
[   25.407763] slamr: SmartLink AMRMO modem.
[   25.407813] slamr: probe 8086:266d ICH4 card...
[   26.412824] slamr: mc97 codec is SIL2f
[   26.412915] slamr: slamr0 is ICH4 card.
laj@little:~$ 

```
and the bad things is that ttySL0 -> pts/0 is a modem device also```
laj@little:~$ ls -la  /dev/slamr0 
crw-rw---- 1 root dialout 242, 0 2008-07-04 13:53 /dev/slamr0
laj@little:~$ less /etc/wvdial.conf
laj@little:~$ ls -la  /dev/modem
lrwxrwxrwx 1 root root 6 2008-07-04 13:53 /dev/modem -> ttySL0
laj@little:~$ ls -la  /dev/ttyS
ttyS0   ttyS1   ttyS2   ttyS3   ttySL0  
laj@little:~$ ls -la  /dev/ttySL0 
lrwxrwxrwx 1 root root 10 2008-07-04 13:53 /dev/ttySL0 -> /dev/pts/0
laj@little:~$ ls -la  /dev/pts/0 
crw-rw---- 1 root dialout 136, 0 2008-07-04 13:58 /dev/pts/0
laj@little:~$
```and wvdialconf found it but not the first```
laj@little:~$ wvdialconf 
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0 .....
```with  dmesg | grep pts only reporting about interru[COLOR="Red"]pts[/COLOR]:)

Instead, with the first ```
laj@little:~$ ps aux | grep dem
root      2018  0.0  0.0      0     0 ?        S<   14:45   0:00 [knodemgrd_0]
root      4799  0.1  0.0      0     0 ?        S<   14:45   0:00 [kondemand/0]
Slmodemd  5006  0.0  0.3   3968  3968 ?        SL   14:45   0:00 /usr/sbin/slmodemd -c ITALY /dev/slamr0
laj       6601  0.0  0.0   3012   776 pts/1    S+   14:55   0:00 grep dem
laj@little:~$ less /etc/wvdial.conf
laj@little:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/slamr0: Device or resource busy
--> Cannot open /dev/slamr0: Device or resource busy
--> Cannot open /dev/slamr0: Device or resource busy
laj@little:~$ 
```
What is appening? Which device I've to refer to?

---

### Post by anurags85 on 2008-07-06
Hi

I am running Ubuntu 8.04 [AMD 64 bit version] on my Compaq Presario V3611AU. When I type lspci in the terminal, following is the output which i get: 

00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
04:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

OK so as you can see, it does not show my Modem, which I actually have. 
Are there any links for downloading the 64 BIT drivers for the modem. My Modem is the same which is being discussed. 

Thanks in Advance. 

Anurag

---

### Post by palimmo on 2008-07-23
Help me, please.

I've this modem:

Conexant HSF 14F1:2F00

on Ubuntu 8.04.

I've followed the method A.... apparently with no errors.

But, finally, in the director 
/dev 
there is no "modem" or something similar....:(


How can I know if the modem is (correctly) installed on my pc?


Thanks!

---

### Post by gunfus on 2008-08-03
> **JoshuaJamZ said:**
> I've tried both methods A and B and get the same error:

```
Desktop/conexant/modules/osspec/include/oscompat.h:57:26: error: linux/config.h: No such file or directory
```

Have installed all dependencies and am stumped... would appreciate any help :)

...


Since we are all trying to get this working I wanted to pass along some new information. I haven't completed the port yet of the drivers into my ubuntu-server 8.04 but will see how far I can get.

So in regards to:

```
Desktop/conexant/modules/osspec/include/oscompat.h:57:26: error: linux/config.h: No such file or directory
```

What you can do is create the missing file. I am using teh 24-19 headers as that is the latest and greatest at the time of this post. So path of file that we need to create would be: 

```

sudo vi /usr/src/linux-headers-2.6.24-19-server/include/linux/config.h

```

Paste the following content inside of the file:

```

#ifndef _LINUX_CONFIG_H
#define _LINUX_CONFIG_H
/* This file is no longer in use and kept only for backward compatibility.
 * autoconf.h is now included via -imacros on the commandline
 */
#include &ltlinux/autoconf.h&gt

#endif

```

After that you get other problems.. which I haven't had time to look into: 

```

usr/share/conexant-192-1ubuntu/modules/osspec/ostime.c:205:81: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/usr/share/conexant-192-1ubuntu/modules/osspec/ostime.c: In function âcnxthsf_OSCreatePeriodicTimeOutâ:
/usr/share/conexant-192-1ubuntu/modules/osspec/ostime.c:205: error: âINIT_WORKâ undeclared (first use in this function)
/usr/share/conexant-192-1ubuntu/modules/osspec/ostime.c:205: error: (Each undeclared identifier is reported only once
/usr/share/conexant-192-1ubuntu/modules/osspec/ostime.c:205: error: for each function it appears in.)
make[3]: *** [/usr/share/conexant-192-1ubuntu/modules/osspec/ostime.o] Error 1
make[2]: *** [_module_/usr/share/conexant-192-1ubuntu/modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-server'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/share/conexant-192-1ubuntu/modules'
make: *** [all] Error 2
cp: cannot stat `modules/hsfbasic2.ko': No such file or directory
cp: cannot stat `modules/hsfengine.ko': No such file or directory
cp: cannot stat `modules/hsfich.ko': No such file or directory
cp: cannot stat `modules/hsfosspec.ko': No such file or directory
cp: cannot stat `modules/hsfserial.ko': No such file or directory

```

---

### Post by gunfus on 2008-08-04
I continue doing the porting.. quite a bit of work I must say. Tonight I was able to move forward but I later got stuck again with a bunge of errors in /serial_hsf.c

I have the steps to get to this point it but the solution to get my modem working is still not completed. Let me know if someone wants them.

---

### Post by jtsop on 2009-03-29
I want them and  I can try to help if you need anything.

---

### Post by Trespasser on 2009-04-23
First off, thanks Matchless for starting this thread.

Just wanted to say that the Dell hsf deb for Hardy works fine. But of course I had to revert to using Hardy 8.04.2 to get it to work which is alright...seems to run great. I'm doing this not for myself (I'm on DSL running Jaunty) but for my brother, and hopefully for my Dad at some future date, who are both restricted to using dial-up. The download speed varies between 4.4-6.2 kilobytes per second (which is 35.2-49.6 kilobits per second). About what I got when I had dial-up so it seems to be a full speed driver. The only other problem I had was even though I was connecting alright Firefox would always start up Offline. It seems Firefox is getting its cue from Network Manager. You can correct this by going into about:config and search for toolkit.networkmanager.disable
and toggle it to true.

BTW, this is for a Conexant HSF with Vendor/Device ID 14f1:2f00.

---

### Post by Jose Catre-Vandis on 2009-09-21
I am a bit late to the party on this one, and for me the beer seems to have run out!

Just installed Xubuntu 9.04 on an oldish Fujitsu-Siemens Amilo Pro laptop. This has a built-in smartlink modem, evidenced by the fact that xubuntu offered proprietary hardware drivers for it on initial reboot. I installed these and this has provided the slmodemd daemon in my processes.

Xp identifies the modem as Agere Systems and works on dial up no problems.

I tried gnome-ppp to start with but as this failed moved back to wvdial for testing. Using the standard init strings generated by wvdail, the modem is recognised and is initialised, but then stops at:
```
Waiting for carrier
```
then goes into a "Trying again" loop which I have to CTRL+C out of.

I don't get any sounds from the modem, so guess it is not firing up. I have tried all sorts of init string settings following exhaustive searches about this on the net and forum, but always get the same result. I have edited the sl-modem-daemon file for my country - UK.

Am able to reset the modem after each failure using:
```
sudo /etc/init.d/sl-modem-daemon restart
```

Can any one advise on my missing link to get this thing working? Am not by the laptop at present so can't issue wvdial.conf info for another 10 hours or so, but all advice will be gratefully received.

---

### Post by _duncan_ on 2009-09-21
A couple of things you can check:

1. There are many variants of smartlink chipsets, but most of them require the following parameters to be set in the wvdial configuration file to dial out properly:
```
Carrier Check = off
Stupid Mode = on

```
2. Starting with intrepid (8.10) and now jaunty (9.04), user ids are no longer automatically added to the 'dip' group. This results in pppd (ppp daemon) permissions problem when using dialers without sudo. This problem can be solved by adding the user id to the 'dip' group explicity, as follows:
```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```
replace [COLOR="Blue"]userID[/COLOR] with the actual user ID.

-------------------------

BTW, my grasp of dial-up modems are not as good as it was before I moved up to broadband. It's just something I dabble with occasionally.

If you're running out of options with Xubuntu, you may want to consider trying out Puppy Linux 4.3. It's probably the most dial-up friendly distro. It's also more lightweight than Xubuntu, which ought to be a bonus since we're dealing with an old laptop.

---

### Post by Jose Catre-Vandis on 2009-09-21
> **_duncan_ said:**
> A couple of things you can check:

1. There are many variants of smartlink chipsets, but most of them require the following parameters to be set in the wvdial configuration file to dial out properly:
```
Carrier Check = off
Stupid Mode = on

```
2. Starting with intrepid (8.10) and now jaunty (9.04), user ids are no longer automatically added to the 'dip' group. This results in pppd (ppp daemon) permissions problem when using dialers without sudo. This problem can be solved by adding the user id to the 'dip' group explicity, as follows:
```
sudo adduser [COLOR="Blue"]userID[/COLOR] dip
```
replace [COLOR="Blue"]userID[/COLOR] with the actual user ID.

-------------------------

BTW, my grasp of dial-up modems are not as good as it was before I moved up to broadband. It's just something I dabble with occasionally.

If you're running out of options with Xubuntu, you may want to consider trying out Puppy Linux 4.3. It's probably the most dial-up friendly distro. It's also more lightweight than Xubuntu, which ought to be a bonus since we're dealing with an old laptop.

Hi Duncan

Thanks for the tips. Have already added user to the dip group, and done the stupid and carrier settings (tried both on and off).

I'll give Puppy a run, and see if that works :)

EDIT: Tried Puppy, it can't find the modem at all

---

### Post by _duncan_ on 2009-09-22
Did you use the [[COLOR="Red"]_scanModem_[/COLOR]]("http://132.68.73.235/linmodems/packages/scanModem.gz") tool to identify the chipset? It might also be interesting to look at what lspci has to say about the modem.

IIRC, not all smartlink chipsets are supported by the open source driver from linmodems.org.

----------

Does your laptop have a serial port? PCMCIA slot? USB slot? The reason I'm asking is if the softmodem turned out to be totally unusable for linux, your best bet might be to purchase a full hardware modem attached to one of those slots I mentioned.

---

### Post by Jose Catre-Vandis on 2009-09-22
Yes, scanModem suggested to install the same driver (slmodemd) as Xubuntu.

I can use an external modem via USB, however the end user won't be too impressed to find what worked OK on XP doesn't with Xubuntu.

I note in some places it is recommended to install linux-headers. Would this make a difference?

The laptop has gone back to owner now, so i will have to wait til she messes up XP again :)

---

### Post by _duncan_ on 2009-09-22
> I note in some places it is recommended to install linux-headers. Would this make a difference?

Only if you need to compile the driver (slamr) from linmodems.org. Some smartlink chipsets don't need slamr and can use ALSA instead. However, I've seen reports that computers with intel sound cards may be difficult to work with using ALSA-based modem chipsets.

I'm surprised Puppy didn't work out. I must've tried 7 or 8 different modems with it (smartlink, pctel, ess, etc) and most work out of the box using the live CD. Of course my sample is small considering the hundreds of different modem chipsets available. Smartlink alone has 10+ varieties.

> The laptop has gone back to owner now, so i will have to wait til she messes up XP again


I'm hoping it doesn't happen, but if it does and you feel like experimenting with the modem again, PM me with the link to the thread.

---

### Post by vayira on 2010-01-04
I'm going to try to get Ubuntu 9.10 64 bit to recognise my Conexant HSF 56k HSFi Modem (for sending faxes). 

If anyone knows any up to date info about these instructions I'd be grateful. Otherwise I'll start following this howto from the earliest posts. 

-

---

