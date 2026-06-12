---
title: "Howto: Feisty Smartlink Modem"
date: 2007-06-23
forum: Outdated Tutorials &amp; Tips
---

### Post by Matchless on 2007-06-23
Hi all,
        I have revised my Smartlink Modem installation howto and have decided to rather publish it as a new thread as the older ones are just becoming more bloated and becomes very confusing. I will appreciate any feedback and varifications.
Recognition to Marv Stodolsky at linmodems for his work which I am only summarizing so that us mere mortals can understand it better!

                                                [COLOR=#000000][SIZE=2]_**Howto get Smartlink winmodem working in Feisty**_[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]These drivers have been tested on a LG modem which is a Smartlink modem using a Netodragon chip with device number 2003:8800. It has also been tested on a LG modem with a Netodragon chip MDV92XP that has a device number 10b9:5459 and acually shows it to be Acer Labs Incorporated Ali/Uli, [/SIZE][/COLOR]                                                 [COLOR=#000000][SIZE=2]using Kubuntu kernel 2.6.20.16-generic and may also work of different ,versions of kernel, flavours of Ubuntu and modems.[/SIZE][/COLOR]
 
 

 [COLOR=#000000][SIZE=2]Just some recognition to linmodems and specifically Marv Stodolsky &#8211; I hope someone is cloning you and making sure there are many of you around! Your work is much appreciated![/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]Marv's documentation states: The slamr-KernelVersion. Files provide drivers supporting Smartlink PCI card modems and USB modems sold under a variety of brand names.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Soft modems requiring ALSA modem drivers cannot be supported by the included slamr.ko driver. However the slamr.ko does provide a usefull diagnostic readout by:[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]sudo modprobe slamr[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]demsg | grep slamr[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]Important:[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2](A)Firstly - Before starting, identify your modem properly. Use lspci or lsusb or scan-modem at   [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/scanModem.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/scanModem.gz")_[/COLOR][COLOR=#000000][SIZE=2] You can also identify it in windows with the windows modem diagnostics or any windows program such as Astra32 or Aida32, even test your modem to make sure it is working. Or sneak a peek at the windows drivers that came with the modem.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2](B) Secondly - Clean out your pc - If you have been experimenting with drivers, rather clean out all the dreggs and changes to configs you may have made or rather start with a new and clean Ubuntu install, otherwise you may get stuck with weird results that take longer to fix than a new reinstall.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]Smartlink soft modems work very well in Ubuntu, the slamr-KernelVersion.tar.gz files have been specifically compiled for Ubuntu by Marv Stodolsy at Linmodem [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/[/SIZE]]("http://linmodems.technion.ac.il/")_[/COLOR][COLOR=#000000][SIZE=2] and can be found at [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/[/SIZE]]("http://linmodems.technion.ac.il/packages/")_[/COLOR][COLOR=#000000][SIZE=2] you can use these but can also compile your own from the latest source files also found there if you are adventurous.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]If you intend compiling your own drivers (see method B) then use Synaptic or Adept to first ensure that you have all the necessary packages installed for compiling your drivers. This includes build-essential, linux-headers-ARCH (where ARCH is your kernel version  and can be found with uname -r in the terminal), fakeroot, module-assistant and debhelper. [/SIZE][/COLOR][COLOR=#000000][SIZE=2]Basically the sl-modem-source has to be installed first and then the sl-modem-daemon. The latest daemon also looks for ungrab-winmodem so download and you will have to also install this from the linmodem website.[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]Please note that you may have to do this(recompile) after every update of your kernel if your modem stops working after an update.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2][U][B]Method A:

[/B][/U][/SIZE][/COLOR][COLOR=#000000][SIZE=2]This method id the easiest method uses the latest packages from linmodems which are complete and contain all the files you may need.[/SIZE][/COLOR][LIST=1]
[*][COLOR=#000000][SIZE=2]Determine     you kernel version by typing uname -r in a terminal[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Go     to [http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/](http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/)     and download the latest package that has already been compiled for     your kernel version i.e. [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]slamr-2.6.20-16-generic.tar.gz     [/SIZE]]("http://phep2.technion.ac.il/linmodems/packages/smartlink/Ubuntu/slamr-2.6.20-16-generic.tar.gz")_[/COLOR]
[*][COLOR=#000080][COLOR=#000000][SIZE=2]This     package contains all the files you will need for installing the     driver.[/SIZE][/COLOR][/COLOR]
[*][COLOR=#000000][SIZE=2]Copy     the slamr-2.6.20-16-generic.tar.gz to your Desktop and right click     on it and select &#8220;Extract here&#8221; and a folder wth a similar name     will be created with the extracted files on your Desktop.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Now     rename the folder to an easier name such as &#8220;slmodem&#8221;[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Open     a terminal and cd in to the slmodem folder[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]For     details you can read the file 1st_Read.txt for more insight[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type     sudo ./setup and the install should start and complete successfully[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type     sudo modprobe ungrab_winmodem no results given shows success[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type     sudo modprobe slamr no results given shows success[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type     sudo /etc/init.d/sl-modem-daemon restart    to restart modem ot just     reboot[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Type     dmesg | grep slamr[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Use     Kppp to query the modem on /dev/modem, if this works you are there!     If you are not using Kubuntu then just see if it works from     Gnome-ppp (wvdial must first be set up)[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Edit      /etc/default/sl-modem-daemon to change the line SLMODEMD_COUNTRY=     USA to i.e SOUTHAFRICA or your country[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]If     you do a Query modem in Kppp you will see that your country has     changed[/SIZE][/COLOR][/LIST]
 

 [COLOR=#000000][SIZE=2]_**Method B:**_[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]This is the ideal way if you feel strongly about using linux "properly" go to the linmodem sites shown above and download the latest .[/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20070505.tar.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20070505.tar.gz")_[/COLOR][COLOR=#000000][SIZE=2] and  [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/ungrab-winmodem-20070505.tar.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/ungrab-winmodem-20070505.tar.gz")_[/COLOR][COLOR=#000000][SIZE=2]  and then the ubuntu file above [/SIZE][/COLOR][COLOR=#000080]_[[SIZE=2]http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.20-16-generic.tar.gz[/SIZE]]("http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/slamr-2.6.20-16-generic.tar.gz")_[/COLOR][COLOR=#000000][SIZE=2] that contains a working copy of the daemon. You can also try using Synaptic or adept to install sl-modem daemon and sl-modem-source as well as ungrab-winmodem(from linmodem website) as a dependancy from the repositories [/SIZE][/COLOR] 
 [LIST=1]
[*][COLOR=#000000][SIZE=2]Also     download and install the ungrab-winmodem from the [/SIZE][/COLOR][COLOR=#000000][SIZE=2]     linmodem website. Install with, extract, make, sudo make install.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Download     slmodem-2.9.11-20070505.tar.gz from the linmodem website. Install     with extract, make, sudo make install.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Download     and open  slamr-2.6.20-16-generic.tar.gz. Extract and install the     sl-modem-daemon xxx.deb file you find in there.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Now     go to /etc/default/sl-modem-daemon, right click, Action, Edit as     Root, find the line SLMODEMD_COUNTRY=USA and change the USA to     SOUTHAFRICA or your country name.[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Go     to the konsole: [/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]sudo      modprobe slamr[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]sudo      /etc/init.d/sl-modem-daemon  restart[/SIZE][/COLOR]
[*][COLOR=#000000][SIZE=2]Now     go to Kppp and select /dev/modem and use the Query Modem to test you     modem. Now setup Kppp and go on line![/SIZE][/COLOR][/LIST] [COLOR=#000000][SIZE=2]_**Note:**_[/SIZE][/COLOR][COLOR=#000000][SIZE=2] If you are going to use Kppp it is advisable that you check that the line noauth is not commented out with a # in  /etc/ppp/peers/kppp-options this may only be in older versions than Feisty.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]To[/SIZE][/COLOR][COLOR=#000000][SIZE=2]** release a locked up Smartlink modem**[/SIZE][/COLOR][COLOR=#000000][SIZE=2] use  sudo modprobe ungrab-winmodem, then sudo modprobe slamr, then restart the daemon with sudo /etc/init.d/sl-modem-daemon restart. This may help you from rebooting.[/SIZE][/COLOR]
 
_**Additional info added:**_ If you find that the modem does not seem to initialise after a new boot, but does if Ubuntu is restarted, the try sudo /etc/init.d/sl-modem-daemon restart. If this has to be done at times after a new start then it seems to be eliminated by replacing the sl-modem-daemon that was installed above with the latest one from the Debian site. Download at [http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fnon-free%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.9d%2Be-pre2-7etch2_i386.deb&md5sum=1ec1173fe1c2def73fc842bda93526a6&arch=i386&type=main]("http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fnon-free%2Fs%2Fsl-modem%2Fsl-modem-daemon_2.9.9d%2Be-pre2-7etch2_i386.deb&md5sum=1ec1173fe1c2def73fc842bda93526a6&arch=i386&type=main") 
, uninstall the old one with Synaptic or Adept and right click on the new downloaded version and install.

 [COLOR=#000000][SIZE=2]_**Footnote:**_[/SIZE][/COLOR]
 [COLOR=#000000][SIZE=2]There are packages in the Ubuntu Feisty repository that can be tried, but they may be outdated in reference to the kernel version. We actually need Marv's version as well as ungrab-winmodem to be put in the repos.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]To remove any installation go to Synaptic, search for sl-modem, slmodem and  uninstall completely. Then use Krusader or your file manager in root mode to search for sl-modem and slmodem. Double click on any found (except those in your repository or download folder) and right click for delete. Usually the date created should give you an indication if this is one you put there. This clears all dreggs and leftovers of a previous installation that may be causing a problem with a new sl-modem install. Be very carefull before you delete anything in this way. Remember to reboot if you are picking up problems and also to re-extract a new folder of files if a compilation failed, as there are changes made during compilation that may cause issues if you just compile again with the failed one.[/SIZE][/COLOR]
 

 [COLOR=#000000][SIZE=2]Final note:  when adding your init string i.e.  [/SIZE][/COLOR][COLOR=#000000][SIZE=2]Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 do not include W2 in the line for a Smartlink modem, only include to show connection speed for a Conexant modem![/SIZE][/COLOR]

---

### Post by RavanH on 2007-07-11
Finally a HOW TO for modem installation on Feisty! :)

Sadly, in my case I get errors installing sl-modem during both method A and B. I suspect it is because I have a 64bit version?

During method A after step 8:
```
driver=slamr
When asked about your country, Enter:
        USA

Installing the Debian packages supporting autoloading
dpkg: fout bij afhandelen van sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb (--install):
 pakket-architectuur (i386) komt niet overeen met het systeem (amd64)
Fouten gevonden tijdens behandelen van:
 sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb

Copying over newer files
cp: kan de rechten van `sl-modem-daemon.modutils' niet veranderen: Bestand of map bestaat niet
Making folder /lib/modules/2.6.20-16-generic/extra
Copying drivers to /lib/modules/2.6.20-16-generic/extra
Checking driver install
slamr.ko  slusb.ko  ungrab-winmodem.ko
Finished installs.
Informing the System

Starting function tests, loading drivers:
FATAL: Error inserting ungrab_winmodem (/lib/modules/2.6.20-16-generic/extra/ungrab-winmodem.ko): Invalid module format
FATAL: Error inserting slamr (/lib/modules/2.6.20-16-generic/extra/slamr.ko): Invalid module format
Running diagnostic:


ports should be created by:
slmodemd -c USA /dev/slamr0
./setup: 45: /usr/sbin/slmodemd: not found
Checking for success
Port creation with slmodemd failed.
Read the Slamr.txt record, other 1st_Read.txt CountryList.txt Smartlink.txt wvdial.txt files and the sample wvdial.conf.

ravan@ravan-laptop:~/Desktop/slmodem$ sudo modprobe ungrab_winmodem
FATAL: Error inserting ungrab_winmodem (/lib/modules/2.6.20-16-generic/extra/ungrab-winmodem.ko): Invalid module format

```

Anyone know how to get this working on a AMD64 installation?

--ravan

---

### Post by Matchless on 2007-07-11
I have not tried 64 bit working, but read this [http://linmodems.technion.ac.il/archive-fourth/msg02594.html](http://linmodems.technion.ac.il/archive-fourth/msg02594.html) or maybe you can talk to the guys at linmodems and see what they suggest.

---

### Post by m2montazari on 2007-08-08
in ubuntu feist 7.04:
I had install sl-modem-daemon package and then download slmodemd.gcc4.1.tar.gz and extract it theni went to terminal:
mh@mh-laptop:~$ su
Password: 
root@mh-laptop:/home/mh# modprobe snd_intel8x0m
root@mh-laptop:/home/mh# slmodemd --alsa modem:0
SmartLink Soft Modem: version 2.9.9e-pre1 Mar 20 2007 14:45:09
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `modem:0' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

and then i tried to dial with administration>networking and GPPP but both return an error in terminal:

error: period size 48 is not supported by playback (64).

i do'nt know what is the problem. i mention that GPPP can Detect modem with no error; all the problem is to dial!!

---

