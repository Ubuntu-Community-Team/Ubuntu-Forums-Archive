---
title: "Please HELP!"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by atmu5fear on 2008-09-15
Re: Wireless Drivers 

--------------------------------------------------------------------------------

I can't get the drivers for my wireless card installed. The laptop has no other internet connection, or network connection.

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
-i inffile install driver described by 'inffile'
-a devid driver use installed 'driver' for 'devid' (dangerous)
-r driver remove 'driver'
-l list installed drivers
-m write configuration for modprobe
-ma write module alias configuration for all devices
-mi write module install configuration for all devices
-v report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
chris@chris-desktop:~$ sudo ndiswrapper -i ~chris/net8185.inf
couldn't open /home/chris/net8185.inf: No such file or directory at /usr/sbin/ndiswrapper-1.9 line 219.


I have also tried using ~media/pearl/net8185.inf, /media/pearl/net8185.inf, ~media/cdrom/drivers/winxp/net8185.inf and /media/cdrom/drivers/winxp/net8185.inf, /desktop/net8185.inf, ~desktop/net8185.inf, ~chris/drivers/net8185.inf, /chris/drivers/net8185.inf (all of which are areas that I have copies of this driver)...

The first one (~chris) is the driver that was copied off the cd to my desktop, the second one (~media/pearl, /media/pearl) is the same driver downloaded from trendnet's website and is stored on a usb drive, and the last one (/cdrom) is the cd included with the card. I know I'm doing something wrong, but can't figure out what. Thanks for the help

---

### Post by ajmorris on 2008-09-16
hi there,
can you open up /usr/sbin/ndiswrapper-1.9  and paste line 219 here.
 
AJ

---

### Post by cardinals_fan on 2008-09-16
In the future, please use a more descriptive title, such as "help with TRENDnet tew-421pc PCMCIA card" rather than "Please HELP!"

Thanks!

EDIT: I understand that it's hard to get used to a new system, but please refrain from posting multiple threads.

---

### Post by Sef on 2008-09-16
Locked. [Duplicate]("http://ubuntuforums.org/showthread.php?p=5796146#post5796146").

---

