---
title: "How TO - Zydas ZD1211 - Sitecom WL 113 on Edgy-powerpc"
date: 2006-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by giobatta on 2006-11-09
Note: this is just an amended version of the great [HOW TO: Zydas ZD1211 wireless with automatic WPA]("http://ubuntuforums.org/showthread.php?t=288753") (thanks a lot shof2k), in order to have a working wireless network with a macmini running Ubntu Edgy

Aim
This guide, based on shof2k's Howto, is supposed to help setting up a wireless network using a Sitecom WL 113 usb wireless dongle, on a macmini running Ubuntu Edgy.
As I still haven't made any experiment with Wpa, it comes with no instructions for encryption.

User level
Intermedidate. This isn't meant to be a simple list of commands to type in to a terminal because networking has too many options for any one script to cover. You may need to tweak some of the commands or files to your own system settings.

Prerequisites
You can navigate around the file system using the terminal
You can copy and move files using the terminal
You can edit files from the terminal.
You can untar packages
You can follow bad how to's
All downloaded files are assumed to be in /usr/src.

Installing the module

1) Even with Edgy, there was no way to make the built-in zd1211rw module to work. 
I therefore followed the howto instructions, with some tweaks.

To remove the module, open a terminal and type

sudo modprobe -r zd1211rw

2)To stop the module from loading up on a reboot, blacklist this module:

sudo gedit /etc/modprobe.d/blacklist

Enter a new line:
blacklist zd1211rw

3) The following may not be essential, but it's worth installing to ensure better success with this and any future projects you might do. In a terminal type:

sudo apt-get install build-essential kernel-package gcc libncurses5 libncurses5-dev libqt3-mt-dev wireless-tools libssl-dev

4) Work out which version of the kernel you have by typing:
Code:

uname -r

5) Obtain the correct headers and source for the kernel. In my case I'm running 2.6.17-10-generic, so I need to get:


sudo apt-get install linux-headers-2.6.17-10 linux-headers-2.6.17-10-powerpc linux-headers-powerpc linux-headers-generic linux-source


6) Make sure you have a link in /lib/modules/2.6.17-10-powerpc/build pointing to /usr/src/linux-headers-2.6.17-10-powerpc. This should be already present, but if not type:

sudo ln -s /usr/src/linux-headers-2.6.17-10-powerpc /lib/modules/2.6.17-10-powerpc/build


7.) In /usr/src, download a working version of the ZD1211 driver from [http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/).
There are multiple versions of the driver and you may need to experiment with different drivers to get one that works for your particular dongle and kernel. For me, the r83 did not work, while the r80 did the trick.

8) In /usr/src, untar the source package you selected and edit the Makefile to have the following options:
KERNEL_SOURCE=/usr/src/linux
ZD1211REV_B=0 (set this to 1 if you have a ZD1211B - I used this option as I have a Sitecom WL 113)

9) Compile the module by typing:

sudo make 
sudo make install

10) Copy the resulting zd1211.ko (or zd1211b.ko, if you set B=1) by typing

sudo cp /usr/src/zd1211-driver-r80/zd1211.ko /lib/modules/2.6.17-10-powerpc/build/drivers/usb/net/

or 

sudo cp /usr/src/zd1211-driver-r80/zd1211b.ko /lib/modules/2.6.17-10-powerpc/build/drivers/usb/net/

if you set B=1


11) Install the module using

sudo depmod sudo modprobe -v zd1211

12) Now connect the dongle and type

dmesg

You should take a look at the output, and if you get any error codes here, you will need to go back to 7.) and use another driver package.

13) If you have an unsecured network, you should be able to start browsing. To check type:

sudo ifconfig

to list all the active network connections


sudo iwconfig

14) To configure WEP encryption, I used the graphical network interface to enter ESSID and the key, but everything could be done manually as well.

Now my macmini is happyly surfing, without any cable, and without any airportexpress either !!

Let the penguin roar!! 

:) :) 

Cheers 

Giobatta

---

### Post by Mitsuko on 2006-11-15
I'll try this later :) Just posting in it so that I don't lose it when I come home ;)

Looks good! I'll post comments once I get it sorted :)

---

### Post by mrgumble on 2006-11-30
This HowTo is great, but I've got one problem I cannot understand.

My Sitecom WL-113 works fine, after rebooting or modprobing the zd1211. But after a while(1-5 hours), my nettraffic crashes. dmesg reports something like this:

```

[17186112.172000] zd1211: failed reg_urb
[17186112.172000] zd1211:USB ST Code = -19
[17186112.172000] 1211_readl failed for 5 attempts...Very Serious<3>zd1211: failed reg_urb

```

I tried it with the r83 and r80 Both same problem. Now I am trying the r77, but I have the assumption, that this is not working neither.

Anybody there who could help me?

---

### Post by logos382 on 2006-12-29
Hi!
I've same problem of mrgumble! on Linux ubuntu 2.6.17-10-386 
I use a zyair g-220!
any solution??

---

