---
title: "Gaining Internet Connection"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by NanoGoner on 2012-12-16
I installed ubuntu along side Windows 7 and can not get an internet connection.  I have searched the for solutions to my problem with no joy. I have gone into System Settings and found no additional drivers available for my wireless connection.  Many of the suggestions seem to assume I have an internet connection.  I do, but it is in the Windows partition and reading the suggestions there, copying the code and rebooting in Ubuntu has made it a slow process, with no results so far.  The code that has been suggested to run in a terminal window has also failed to run.
 
I'll try to give as complete a system description as possible to see if I can get some directly applicable help with this.
 
The system is a Dell Inspiron 2.2GHz dual core CPU.  The wireless drivers are for a Dell Wireless 1397 WLAN Minicard; Marvell Yukon 8E8040 PCI-E Fast Ethernet Controller, and Microsoft Virtual WiFi Miniport Adaptor.
 
I'm not sure, even if this is a driver problem, and if I am directed to the right one, how I'm going to install it.
 
I hope the community can indulge another Windows defector to help me get on

---

### Post by TheFu on 2012-12-16
Google found this: [http://forum.linuxmint.com/viewtopic.php?f=109&t=55860](http://forum.linuxmint.com/viewtopic.php?f=109&t=55860)
In the meantime, I strongly suggest that you use a wired ethernet connection, not wifi, while working this issue.

It isn't clear to me, does the wired connection work under Ubuntu or not?

---

### Post by NanoGoner on 2012-12-16
I have tried that by plugging the Ethernet that goes to the wireless router to the computer ethernet plug, but I appear to need a ISP Name and password to access that.  I'll need to call the ISP to get that

---

### Post by TheFu on 2012-12-16
> **NanoGoner said:**
> I have tried that by plugging the Ethernet that goes to the wireless router to the computer ethernet plug, but I appear to need a ISP Name and password to access that.  I'll need to call the ISP to get that

Your router has the connection information for your ISP inside the  settings somewhere.  My ISP doesn't do this, so I can only guess that  you are on DSL with PPOE.  That really shouldn't matter, since you  really want to connect the PC to the router.

Most wifi routers that I've seen have 4 or 5 ports. One is labeled "WAN" and the 4 others are are labeled "LAN".  You want to leave the router connected to the internet and plug your PC into a LAN port using an ethernet cable.  It is not a good idea to directly connect a non-hardened computer running any operating system directly into an internet connection.

If it best if after you make these connections, then you reboot into Ubuntu. It isn't strictly necessary, but the easiest answer for you, today.

---

### Post by GordThompson on 2012-12-16
@NanoGoner:

Did you start the install by booting your computer from a Ubuntu CD/DVD?

---

### Post by NanoGoner on 2012-12-16
I have gained access to the internet through a hardwired ethernet connection.  I followed the the link offered by TheFu above and located my BCM chipset which is BCM4312.  I then followed the directions for installation using the following code in a terminal window:

sudo apt-get update 
sudo apt-get install bcmwl-kernel-source

The update did fine, but the reaction to the second command was

bruce@ubuntu:~$ sudo apt-get install bcmw1-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmw1-kernal-source

More guidance please!

---

### Post by GordThompson on 2012-12-16
> **NanoGoner said:**
> I have gained access to the internet through a hardwired ethernet connection.  I followed the the link offered by TheFu above and located my BCM chipset which is BCM4312.  I then followed the directions for installation using the following code in a terminal window:

sudo apt-get update 
sudo apt-get install bcmwl-kernel-source

The update did fine, but the reaction to the second command was

bruce@ubuntu:~$ sudo apt-get install bcmw1-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcmw1-kernal-source

More guidance please!
Check your spelling: it's...  'bcmw**l**-kern**e**l-source'

---

### Post by NanoGoner on 2012-12-16
Yes, my spelling is attrocious.  I fixed it and an installation seemed to be well underway when it ended with the following output:

Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.5.0-17-generic/updates/dkms/

depmod......

DKMS: install completed.
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
update-initramfs: deferring update (trigger activated)
Setting up fakeroot (1.18.4-2) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-17-generic
Warning: No support for locale: en_US.utf8


That seems to me to mean something is still not correct.  It appears that some of the driver files are not where they ought to be.

Any more help will be appreciated!

---

### Post by NanoGoner on 2012-12-17
I don't know what happened, but without doing anything else the wireless connection just started working.  Who am to question a miracle?

---

