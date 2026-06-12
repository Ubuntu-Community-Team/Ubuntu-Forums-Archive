---
title: "HowTo: Epson Scanners"
date: 2009-05-09
forum: Outdated Tutorials &amp; Tips
---

### Post by DoctorMO on 2009-05-09
I have an Epson Perfection v500 Photo and wanted to get it working...

For certain Epson scanners you'll need to install iscan and a specific iscan plugin for your scanner. And if your like me and using Ubuntu 9.04 (jaunty) then you'll notice that the deb file for iscan provided by Epson doesn't work (they are made for Debian not Ubuntu).

So I have provided everyone with an easier way to get their epson scanner working:

Step 1) Add my PPA to your sources, following the guide lines: [https://launchpad.net/~doctormo/+archive/ppa](https://launchpad.net/~doctormo/+archive/ppa)
Step 2) run `sudo apt-get install iscan iscan-plugins`
Step 3) Restart computer (should be required, but hey, might help)

There you go, this won't support all Epson scanners, but it does support a number of tricky ones that aren't supported by the libsane-extras package, it has the added benefit of adding an fdi file to allow access to normal users (not just root). (should work for i386 and amd64)

Please report any problems.

---

### Post by ron_jeremy on 2009-05-10
Finally my 4490 is working. THANK YOU THANK YOU THANK YOU!!!

---

### Post by ron_jeremy on 2009-05-10
Oh, one other thing: my friend has a 4490 like me but could not manage to get his working. After phoning him I found that he was stuck on Step 1. So, to simplify things for other total newbies like us, to complete "Step 1" all you have to do is copy/paste the following 2 lines to your sources list. Don't click the links, just copy/paste each entire line (you will "+Add" 2 times):
[FONT=monospace]
[/FONT]deb [http://ppa.launchpad.net/doctormo/ppa/ubuntu](http://ppa.launchpad.net/doctormo/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/doctormo/ppa/ubuntu](http://ppa.launchpad.net/doctormo/ppa/ubuntu) jaunty main

To find your sources list, go to:

SYSTEM > ADMINISTRATION > SOFTWARE SOURCES > THIRD-PARTY SOFTWARE > +ADD

Then follow Step 2 as DoctorMo prescribed :) I did not have to restart Ubuntu but your mileage may vary.

Now you will see the "Image Scan" icon under APPLICATIONS > GRAPHICS :)

---

### Post by leopoldb on 2009-05-12
Oh so very cool.  I've been using the Epson software in a vbox but regretting every time I had to run WinXP.   
Thank you DoctorMo and Ron (love your movies).

Leopold B.

---

### Post by xakira on 2009-07-25
I went to install these iscan files but they seem to have been deleted from DoctorMO's PPA ... can you confirm this DoctorMO?

---

### Post by xakira on 2009-07-25
Finally got my EPSON 4490 working in Ubuntu 8.10.  It was very easy in the end.  Looks like the peeps at Avasys have updated their software to install properly (for me any-way).  I went here:-

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

and chose my scanner and answered the OS questions.

I found I only needed the core DEB 32bit core package [libltdl7] - "iscan_2.20.0-6.ltdl7_i386.deb" and the DEB 32bit package - "iscan-plugin-gt-x750_2.1.0-5_i386.deb".  The "iscan_2.20.0-6_i386.deb" package was already in the core package so I didn't need to install it.

Basically I installed the following packages in the following order by double clicking on them (after they were downloaded of course):-

iscan_2.20.0-6.ltdl7_i386.deb
iscan-plugin-gt-x750_2.1.0-5_i386.deb

I started up XSane and away the scanner went :D
Remember to be patient with the scanner the first time as it takes awhile for it to warm up/initialise.

I also tried the IScan program and that works ok too.

---

### Post by DoctorMO on 2009-07-25
[https://launchpad.net/~doctormo/+archive/doctormo-epson-scanners](https://launchpad.net/~doctormo/+archive/doctormo-epson-scanners)

The PPA changed in order to be more specific. New PPA rules and all that. Glad the software directly from Avasys is now working.

---

### Post by buster2 on 2009-07-26
keep getting , can't find iscan

---

### Post by DoctorMO on 2009-07-26
did you add the repository?

---

### Post by buster2 on 2009-07-27
found the new repository, down loaded iscan ok and plug in
now i get iscan cant find scanner, mine is a dx4400

---

### Post by DoctorMO on 2009-07-27
Is dx4400 supported by iscan? Can you post more information, such as lsusb results and other info.

---

### Post by buster2 on 2009-07-27
> **DoctorMO said:**
> Is dx4400 supported by iscan? Can you post more information, such as lsusb results and other info.

I had this scanner working in xandros after downloading iscan plugin
using kooka. i have checked sane and its supported.


 Bus 001 Device 002: ID 07ab:fcfe Freecom Technologies 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 04b8:083f Seiko Epson Corp. Stylus DX4450
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

i'm new to Ubuntu and linux
Thanks for any help

---

### Post by DoctorMO on 2009-07-27
And what happens when you run 

```

sudo scanimage -L

```

Does the scanner appear in that list?

What about without sudo? can you try both?

---

### Post by buster2 on 2009-07-27
no sane devices found on both

---

### Post by M&amp;StL on 2009-09-07
Old Pentium 4 machine. Version 9.04 Ubuntu.
Did the downloads as instructed. It showed everything downloaded. Did update. Did restart. 
Epson 4490 not responding on Xsane, nor scanner utility.

Solved. Avays correct driver link finally found.

---

### Post by ken300 on 2009-10-04
Mmmmmm,

I've got an Epson V300 and am using Jaunty, the scanner's been working fine since I moved to Jaunty when it was first released and used this how-to & DoctorMO's PPA (the method in post #1) to get the thing working. 

Today I replaced my hard drive & did a clean install of Jaunty, initially I was getting installation errors when I ran through exactly the same procedure as before, not surprising when the PPAs have been updated (I'm now using the link on post #7 of this thread).

It's still not working. It seems to install ok but whether I run as a normal user or use sudo, in the terminal or through Gnome, the result seems the same. When I try and launch IScan the scanner starts whirring like it always does (like it's getting itself ready), the main IScan window then appears but when you click on 'Preview' or 'Scan' the 'warming up' message appears but it comes up with the error message 'Could not send command to the scanner. Check to scanners status' before it actually scans anything. Once (out of about 30 attempts to get it to work) it finished the 'Preview' scan ok but froze when I asked it to actually scan!

The green light next to the power button on the scanner is steady until the error message appears at which point it starts flashing. When I unplug the scanners USB from the computer it whirrs some more as if returning to it's rest position.

Opening a terminal & doing lsusb gives (the same result for both 'lsusb' and 'sudo lsusb'):

Bus 001 Device 007: ID 04b8:0131 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 056a:0017 Wacom Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

'sudo scanimage -L' gives one line:

device `epkowa:interpreter:001:007' is a Epson Perfection V300 flatbed scanner

If I can't get the thing working again it'll force me back to Windows after over 2 years of staying away from it totally, please help!

Thanks!

---

### Post by DoctorMO on 2009-10-04
Hey Ken,

OK first things first, Don't Panic! There is no need to jump off buildings when things get tough, and no reason to jump back in bed with Windows because of one problem.

Some people just tend to mention that they'll go back to windows, just to scare helpers into helping. Please don't do that, I don't need your computer as a hostage, you'll use Ubuntu because it's awesome, not because someone helped you.

OK now that that is out of the way. Because the device is scanning some of the time, and it detects the scanner; my guess is that the driver in my PPA is working correctly as designed. It's possible that your installation isn't quite right or there is a remote possibility that the hardware has somehow been damaged (remote!).

So long as the driver was detected and the driver used is the correct one, then the people you really need to ask for help from are Epson and the driver developers Avasys (because it's not open source, so we (the community) can't fix it).

[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

Good luck!

---

### Post by ken300 on 2009-10-05
DoctorMO,

thankyou for the quick reply!

I know some people use the 'I'm going back to Windows' as some sort of threat, I sincerely appologise for sounding like I was doing that!

I agree TOTALLY that Ubuntu is great I really don't want to be forced back to the closed-source world of windows, I'll do anything I can to keep using Ubuntu but I use this scanner every day so really NEED it to work!

I've realised that my best option may be to sell the Epson if I can't get it working & just buy different scanner!

Thanks again for your advice!

Ken

---

### Post by ken300 on 2009-10-05
Hi,

After much searching & trying different things (& trying the same things over & over again) I read something to do with Canon scanners that should work ok on Ubuntu (they're supported by sane) not working. One post mentioned that things got better when a USB cable with ferrites was used.

My USB cable was 5m long with no ferrites so thought I've got nothing to loose & swapped it for a shorter one with ferrites and, yay, Iscan worked perfectly! There SEEMS to be some reason why the USB cable/signal is more vulnerable to interference in Ubuntu than in Windows (all of the posts I read said 'things are fine in windows')

What I did was just followed post #1 in this thread (with the PPA link in post #7) and swapped the cable!

Hope this helps someone, thanks,

Ken

---

### Post by DoctorMO on 2009-10-13
Thanks for letting us know how you got it solved.

My only guess about windows would be that it resends and resends the usb signal until it gets through. But I can't know that for sure.

---

### Post by Phil Urich on 2009-11-15
**ken300:** In the future, another option, if you're REALLY forced to use Windows for something like this, is VirtualBox; apparently Epson's scanning utilities work fine in VirtualBox, so if you have a copy of XP (keep it legal, kids!) or Win7 or whatever you could always install that in VirtualBox, install the Epson utilities and run VirtualBox in seamless mode.  That way you're just basically using Windows as a backend to run your scanning program; no need to boot into it and loose all the Ubuntu/Linux goodness!

**DoctorMO:** I came across this thread because I was setting up an Epson V500 for my father, and your PPA did the trick; I went the simple way and "add-apt-repository ppa:doctormo/doctormo-epson-scanners"'d it, but then of course I had to go into /etc/apt/sources.list.d/ and edit the repository info to change "karmic" to "jaunty".  I know it's just a minor thing, but maybe for the sake of people who aren't veterans of Ubuntu, could you update it to add karmic to the list?  It does seem to work perfectly with the same packages.

---

### Post by DoctorMO on 2009-11-16
Hey Phil,

Thanks for the update, glad it worked well :-) happy people are so hard to find because they never seem to complain.

Could you send me an email about updating the packages to karmic? I'm at UDS right now so I'm a little caught up in things, but will get to it if I have something I can pin on my todo.

---

### Post by coskierken on 2009-11-16
Just a note:  I have an Artisan 700 epson.  I had problem getting it working at first.  I referred back to getting an Artec flatbed working and having the correct USB address for it.  If you list all the attached USB devices (lsusb) in a terminal and the scanner shows up, which in my case it did, you should be able to see it in the list.  With that, all you have to do is go to (etc/sane.d), open the epson.conf, look for the line (usb 0x4b8 -x..., and then just edit it to the address you got from the lsusb command.  It was relatively simple and Xsane or Quiteinsane will see the scanner and it will work.  No drivers to download or other programs and it works, at least for me. This is with 9.04.  All you really need in the file is the usb line and that is it.  Hope this helps.  

# epson.conf
#
# here are some examples for how to configure the EPSON backend
#
# SCSI scanner:
scsi EPSON
# for the GT-6500:
scsi "EPSON SC"
#
# Parallel port scanner:
#pio 0x278
#pio 0x378
#pio 0x3BC
#
# USB scanner:
# There are two different methods of configuring a USB scanner: libusb and the kernel module
# For any system with libusb support (which is pretty much any recent Linux distribution) the
# following line is sufficient. This however assumes that the connected scanner (or to be more
# accurate, it's device ID) is known to the backend. 
usb
# For libusb support for unknown scanners use the following command
# usb <product ID> <device ID>
# e.g.:
usb 0x4b8 0x846
# And for the scanner module, use the following configuration:
#usb /dev/usbscanner0
#usb /dev/usb/scanner0

---

### Post by sawanishi on 2009-12-08
hi guys..

i m still newbie with ubuntu currently using the ubuntu 9.10

having problem to install scanner epson perfection v500 photo..keep getting error and so on..can someone help me?i already try lsusb and a few tricks..but still fail avail...kinda hate to switch to window juz to scan

---

### Post by DoctorMO on 2009-12-08
sawanishi: If you need some help, the best thing to do is explain exactly what you've done so far and what error your getting.

---

### Post by sawanishi on 2009-12-09
Hi i try this link to add 
[https://launchpad.net/~doctormo/+archive/doctormo-epson-scanners]("https://launchpad.net/%7Edoctormo/+archive/doctormo-epson-scanners")

but when i try to key in the key the error was

gpg: requesting key 113659DF from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error


did i missing the steps or did i forgot something?

currently using 9.10

---

### Post by DoctorMO on 2009-12-09
Try it again, sometimes the key server can be down and sometimes your computer might be offline.

---

### Post by sawanishi on 2009-12-10
ok i already manage to get my epson perfection v500 work..

1. i go to avasys.jp/eng to install the driver
2. lsusb
3. sudo chmod 666 /dev/bus/usb/002/002 ...change the bus and device num accordingly

and it works..yea..finally.

thanks again though.

---

### Post by DoctorMO on 2009-12-10
sawanishi, you know it'll stop working when you reset the computer?

One of the reasons I created the deb files I did, was to provide a way of telling the computer to put the scanner into the scanners group, so you didn't have to set the permission every time you plugged in the scanner or reset the computer.

FYI.

---

### Post by breek on 2010-08-02
the epson v500 is an interesting scanner and i'm thinking of buying it.
i've read this >[link](http://ubuntuforums.org/showthread.php?t=1087787)< but before buying, could please someone provide a screenshot of "image scan!" software to see how much basic it is?
color profiles are supported? scanners profiles are provided? and then, xsane still can't reach 9600dpi? someone experiencing some issues on lucid lynx 64 bit?

thanx for help

---

### Post by ramnarayan on 2010-10-05
> **xakira said:**
> Finally got my EPSON 4490 working in Ubuntu 8.10.  It was very easy in the end.  Looks like the peeps at Avasys have updated their software to install properly (for me any-way).  I went here:-

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

and chose my scanner and answered the OS questions.

I found I only needed the core DEB 32bit core package [libltdl7] - "iscan_2.20.0-6.ltdl7_i386.deb" and the DEB 32bit package - "iscan-plugin-gt-x750_2.1.0-5_i386.deb".  The "iscan_2.20.0-6_i386.deb" package was already in the core package so I didn't need to install it.

Basically I installed the following packages in the following order by double clicking on them (after they were downloaded of course):-

iscan_2.20.0-6.ltdl7_i386.deb
iscan-plugin-gt-x750_2.1.0-5_i386.deb

I started up XSane and away the scanner went :D
Remember to be patient with the scanner the first time as it takes awhile for it to warm up/initialise.

I also tried the IScan program and that works ok too.

Wow

every time i go to the avasys site and follow the instructions i am unable to get 
iscan-plugin-gt-x750_2.1.0-5_i386.deb

so how does one exactly get these files

the only ones i see are as below (bolded ones are the relevant ones for me)

> 
Download for Perfection 4990 PHOTO data package
RPM package 	
iscan-data-1.3.0-2.noarch.rpm 	32,027 bytes

	
[B]deb package 	
iscan-data_1.3.0-2_all.deb 	23,536 bytes[/B]

	
Source file 	
iscan-data_1.3.0-2.tar.gz 	84,106 bytes
iscan-data_1.3.0-2.dsc 	279 bytes

	
checksum file 	
iscan-data-1.3.0-2.md5 	242 bytes
 
Download for Perfection 4990 PHOTO Latest Version
RPM 32bit package 	
iscan-2.26.0-3.i386.rpm 	491,721 bytes

	
RPM 32bit package [libltdl7] (for Fedora 11 or later) 	
iscan-2.26.0-3.ltdl7.i386.rpm 	494,154 bytes

	
DEB 32bit package 	
iscan_2.26.0-3_i386.deb 	354,168 bytes

	
[B]DEB 32bit package [libltdl7] (for Ubuntu 8.10 or later) 	
iscan_2.26.0-3.ltdl7_i386.deb 	350,686 bytes
[/B]
	
RPM 64bit package 	
iscan-2.26.0-3.x86_64.rpm 	375,821 bytes

	
RPM 64bit package [libltdl7] (for Fedora 11 or later) 	
iscan-2.26.0-3.ltdl7.x86_64.rpm 	512,536 bytes

	
DEB 64bit package 	
iscan_2.26.0-3_amd64.deb 	362,156 bytes

	
DEB 64bit package [libltdl7] (for Ubuntu 8.10 or later) 	
iscan_2.26.0-3.ltdl7_amd64.deb 	365,154 bytes

	
Source file 	
iscan_2.26.0-3.tar.gz 	1,072,126 bytes
iscan_2.26.0-3.dsc 	400 bytes

	
checksum file 	
iscan-2.26.0-3.md5 	603 bytes

	
Installation method 	
Please refer to the userg_revL_e.pdf 	574,224 bytes
 
Back to Download [Scanner]



**So where is iscan-plugin-gt-x750_2.1.0-5_i386.deb**

will be grateful as i am desperate to get this scanner working in Ubuntu 9.10

thanks
ram

---

