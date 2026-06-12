---
title: "problems with NDISwrapper-1.53"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by saskatchewan on 2008-05-29
I downloaded and extracted the ndiswrapper-1.53 but I do not know how to install these drivers.

I am running a  broadcom 54g 802.11 blg WLAN with 125hsm/speed booster.

How do I install the drivers?
what commands to I run?
do I have to cd the folder?

---

### Post by saskatchewan on 2008-05-29
I tried doing the following from the instructions but I get the following.

allan@allan-laptop:~$ tar zxvf ndiswrapper-1.53.tar.gz
tar: ndiswrapper-1.53.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
allan@allan-laptop:~$ tar zxvf ndiswrapper-version.tar.gz

---

### Post by alpage2 on 2008-05-29
From Ubuntu 7.10, an open source Broadcom driver is included in the Ubuntu repositories, so you should not need to resort to ndiswrapper.

There is an additional complication with Broadcom wireless adapters. Firmware, which is not open source, has to be available to load into the adapter at boot time. The good news is that all the necessary packages are also included in the ubuntu repositories, but to download and install them, you will need an alternative working internet connection, such as ethernet or dial-up.

With a working connection, the downloading and installation of the firmware is automated - just follow the prompts.

Hope that helps.

Alan

---

### Post by saskatchewan on 2008-05-29
Thanks
Can  you give me a little more information on how I find this ins the ubuntu repositories?  I have a wired connection so there should be no problems.

Also, I am running an AMD 64 so I installed the Ubuntu 64 bit.  There have been issues installing skype with this version so any tips with that would be really helpful/

---

### Post by alpage2 on 2008-05-29
With my BCM4306 broadcom adapter connected, I have always found detection and download to be automated. But running synaptic, I see that I have the b43-fwcutter package installed - this is the firmware for the b43 chipset. A b43xx-fwcutter is also available.

This and the above only applies to the b43 or b43xx chipset - if you have a different chipset then things may be different.

Do you know which chipset you have?

At a terminal prompt, type

lspci

to list all your pci devices, or

lsusb

for all the usb devices.

For a Broadcom 4311 [14e4:4311]) adapter, there is a detailed HOWTO for using ndiswrapper to achieve higher speeds than is possible with the native linux driver, here:

[http://ubuntuforums.org/showthread.php?t=760568&highlight=Dell+WLAN+1390](http://ubuntuforums.org/showthread.php?t=760568&highlight=Dell+WLAN+1390)

Alan

---

### Post by saskatchewan on 2008-05-29
Thanks for the help.

I am not sure what chipset that I have, can you tell me what information that you need?

I am reformatting the disk to install the 32 bit version of Ubuntu since the 64 bit does not seem to work very well.

Any more suggestions on getting this wireless to work are certainly welcome.

---

### Post by alpage2 on 2008-05-29
As in my previous post - in a terminal window - if it is a pci device, type lspci, or if it is a usb device, type lsusb, and copy the output here. If you can, just copy the part relating to your broadcom card.

Alan

---

### Post by saskatchewan on 2008-05-29
Here is my chipset:

Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


What should I do next?

---

### Post by alpage2 on 2008-05-29
Looks promising - you seem to have the b43xx chipset.

Let's check first of all that it is not already installed.

1. What version of Ubuntu are you using?

2. In a terminal window, type the command: iwconfig
and copy the output here.

Alan

---

### Post by saskatchewan on 2008-05-29
I am using Ubuntu 8.04.

This is the response I got from the terminal window.

allan@allan-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

allan@allan-laptop:~$

---

### Post by RequinB4 on 2008-05-29
Not only does this work, this also will give you twice as fast performance as using the repostiroy bcm43xxfwcutter.

[http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

---

### Post by alpage2 on 2008-05-29
OK - it looks like the Broadcom card does not yet have a driver.

Go to System.....Hardware Drivers

- or similar - I am using xubuntu with Xfce 4 window manager, and there are some differences in the menu system.

The hardware manager should be listing the Broadcom card, but it will not be activated. Click on the check-box to activate it, and at this point you should find that it starts to download and install the packages that it needs - just follow the prompts.

Once installed, it will just be a case of configuring your wireless network.

As mentioned by RequinB4, you will probably get better speeds with the use of ndiswrapper, but the set up is a bit more elaborate.

Alan

---

