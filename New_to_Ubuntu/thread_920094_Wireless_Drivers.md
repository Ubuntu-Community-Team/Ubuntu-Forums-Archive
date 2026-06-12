---
title: "Wireless Drivers"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by atmu5fear on 2008-09-14
Hi, I've read all the tutorials and other posts about this, even a few regarding the same network adapter (TEW-421PC). First off I have no internet connection to start with, so sudo apt-get install ndiswrapper-utils, would not work. I would get the message could not find package E:. I tried all the solutions for this and found none, but did manage to install ndiswrapper-common and ndiswrapper-utils-1.9 from within the synaptics packet manager (add/remove had no affect, i could see the package, but could not apply it without internet). after installing ndiswrapper i tried applying the drivers sudo ndiswrapper -i ~media/pearl/driver/driver/win2000/net8185.inf, and I get just another message about this directory cannout be located in /usr/???/ndiswrapper-1.9 ?? (? = can't remember specifics). I have tried with the 2000 and XP drivers, from directly off the cd, and downloaded, off a usb, directly off the desktop, but i alway get the same message. any help would be appreciated, thanks

also i am brand new to this linux bit, so i have no idea what i'm doing wrong

also the os is xubuntu 8.04.1
and the system is IBM thinkpad PII333mhz, 128mb RAM, 80Gb HDD

---

### Post by echo314 on 2008-09-14
I've muddled my way through ndiswrapper before...try copy/pasting the commands you type in, as well as the results. Save it to a jump drive or w/e, then post back on the forum.

There are instructions for ndiswrapper [here]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")

Go to the Installing Windows Driver section, and go from there. post back here if you get stuck, and please provide what you typed in and the output so I can troubleshoot it.

Good luck!

---

### Post by InfinityCircuit on 2008-09-14
I think you have the wrong path.  ~media is just a directory named that.  If you want to install something off of a CD, then change it to /media/whatever, not ~media/whatever.

---

### Post by atmu5fear on 2008-09-15
These were the [instructions]("http://ubuntuforums.org/showthread.php?t=201673") I was following. They are for the exact same card as mine.

 This was copied off the laptop I'm doing this on:

chris@chris-desktop:~$ sudo apt-get install ndiswrapper-utils
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate
chris@chris-desktop:~$ sudo apt-get install ndiswrapper-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-desktop:~$ sudo ndiswrapper
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
chris@chris-desktop:~$ sudo ndiswrapper -i ~chris/desktop/net8185.inf
couldn't open /home/chris/desktop/net8185.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


I have also tried using ~media/pearl/net8185.inf,  /media/pearl/net8185.inf, ~media/cdrom/drivers/winxp/net8185.inf and /media/cdrom/drivers/winxp/net8185.inf, /desktop/net8185.inf, ~desktop/net8185.inf, ~chris/drivers/net8185.inf, /chris/drivers/net8185.inf (all of which are areas that I have copies of this driver)...

The first one (~chris) is the driver that was copied off the cd to my desktop, the second one (~media/pearl, /media/pearl) is the same driver downloaded from trendnet's website and is stored on a usb drive, and the last one (/cdrom) is the cd included with the card. I know I'm doing something wrong, but can't figure out what. Thanks for the help

---

