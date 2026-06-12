---
title: "How-To: Dell 1390 WLAN (Broadcom 4311 [14e4:4311]) for Laptops using ndiswrapper"
date: 2008-04-20
forum: Outdated Tutorials &amp; Tips
---

### Post by jw5801 on 2008-04-20
This How-To describes how to get WiFi working with the Broadcom 1390 WLAN offered in many Dell and HP laptops using ndiswrapper. Many of us use ndiswrapper as an alternative to the native drivers (b43), as we feel the native drivers have not quite reached a point where they compare with ndiswrapper, usually this relates to only being able to use 802.11b connections (11Mbps) as opposed to 802.11g (54Mbps).

The how-to has been tested and found to work on both AMD64 and i386 installs of Ubuntu Hardy Heron, and should also work on all future versions. If you have any troubles, leave a post and I'll do my best to sort them out.

[color=red]NOTICE: There is no 'linux-ubuntu-modules' meta-package that can be used to install new versions of this package whenever a kernel update is pushed through. Therefore, everytime you install a new kernel, make sure to also install the corresponding linux-ubuntu-modules package, for example:
```
sudo apt-get install linux-ubuntu-modules-2.6.24-19-generic
```[/color]

The How-To is loosely based on Paperdiesel's How-To for earlier versions of Ubuntu which can be found [here](http://ubuntuforums.org/showthread.php?t=297092). If you are running a version older than Hardy, you should refer to [paperdiesel's How-To](http://ubuntuforums.org/showthread.php?t=297092).

[color=red]DISCLAIMER[/color] It's important to note that many people struggle to get wireless working simply because they have unsuccessfully tried a variety of methods and left their system in a shambles. If you've been playing around with alternative methods there's a good chance you won't be able to get this to work until you reverse any previous changes you may have made. It's perhaps best to come straight to this How-To after a fresh install.

To check that you have the same card that this how-to is written for, run the following command:
```
lspci -nn | grep 14e4
```
and you should see something similar to the following:
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI **[14e4:4311]** (rev 01)
```
The section in bold is the important part. If that part doesn't match then you will need a different driver to use with ndiswrapper. The how-to should still be valid however! If you don't have the same WiFi card, have a look at the list of supported cards [here](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/), and it should point you in the right direction for a driver to use.

**STEP 1: OBTAINING THE REQUIRED PACKAGES**
Thankfully, Hardy (and onwards) includes a new enough version of ndiswrapper to remove the need for installing it from source. This saves a lot of trouble during the install process.

For the install process I find it best to create a separate working directory to get all this done in. You can use whatever directory you'd like so long as you're consistent, if you're unsure copy the way I've done it. 

Most of the work from here on will be done from the command-line, so open up a terminal (Applications > Accessories > Terminal), and use it to create your working directory:
```
mkdir wireless-install
cd wireless-install
```

First we need to obtain the correct XP driver (Vista drivers WILL NOT WORK with ndiswrapper) for this chipset, and also install some extra packages. This is easy if you have access to the internet (via a wired connection or otherwise):
```
wget http://ftp.us.dell.com/network/R151519.EXE
```
_NOTE:_ If lspci above showed that you had a different chipset, this driver won't work. You're welcome to try using a different driver, however ndiswrapper is a temperamental thing, so I can't guarantee it will work with just any driver. A google search for the number relating to your card, ie. 14e4:4315 or 14e4:4318, and ndiswrapper should return a driver you can use quite quickly.

Next install ndiswrapper. The latest version is available from the repositories which is a rather nice change for those of us who are used to the need to recompile ndiswrapper on every kernel change! Although, on that note, the most recent kernel update didn't install the modules that were needed alongside it, so I'll include the installation here.
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

If you have no internet access on your Ubuntu machine then you'll need to get the appropriate driver from [here](http://ftp.us.dell.com/network/R151519.EXE) and copy it to your working directory (~/wireless-install). The packages can be installed from your trusty LiveCD: 
```
sudo mount /dev/cdrom /cdrom
sudo apt-cdrom add -m
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils linux-ubuntu-modules-$(uname -r)
```


**STEP 2: PREVENTING THE NATIVE MODULES FROM INTERFERING WITH NDISWRAPPER**

**NOTE FOR ANYONE WHO IS NOT USING A FRESH INSTALL**
If you used ndiswrapper in Gutsy and upgraded directly to Hardy (or tried another method before coming here), odds are good that you'll have a line in the /etc/modules file that loads ndiswrapper, in order for this part of the how-to to work you'll need to remove that line:
```
gksudo gedit /etc/modules
#if under KDE, replace gksudo with kdesudo and gedit with kedit
```
And delete any line(s) that contain "ndiswrapper"
**END NOTE**

This process is not quite as simple as it has been in the past due to the different native modules and how they interact with each other. So firstly we're going to blacklist a few things by adding them to the /etc/modprobe.d/blacklist file:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```
_NOTE:_ You can do this with a text editor, using "gksudo gedit /etc/modprobe.d/blacklist" for example. I like the fancy way because it means you can copy and paste just one command and removes the chance of typos.

_NOTE II:_ The wl module is a new addition and is intended for the 4315 chipset, but there have been reports of it also being loaded for the 4311 chipset (it doesn't appear to work at all, however). If anyone is interested, b43 (and b43legacy) are the in-kernel drivers, these are the supported open source drivers (which I've never found to work particularly well). wl however appears to be Ubuntu only and is found in ubuntu-restricted-extras, so if you don't have this package installed, there's no need to blacklist this module, however doing so can't harm anything.

We also need to add a bootscript to load a couple of modules in an order that suits us. The reason being that the ssb module takes control of our card, thus preventing ndiswrapper from controlling it, however ssb is required by the b44 driver, which handles wired broadcom cards, so we can't just blacklist it. If you would like (and know how to), you can easily use a new script to do this, however the easiest way I find is to add it to /etc/rc.local. To do this we need to edit the file:
```
gksudo gedit /etc/rc.local
#if under KDE, replace gksudo with kdesudo and gedit with kedit
```
Feel free to replace gedit with the text editor of your choice (kate, mousepad, emacs, nano, vi, bluefish, etc), then add the following to lines to the end of the script, just before the "exit 0":
```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```

To give you an idea, my /etc/rc.local now looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
```


**STEP 3: INSTALLING THE DRIVER WITH NDISWRAPPER**

Now we're going to use the driver we downloaded from the Dell website (note that it doesn't matter if your laptop is not a Dell, this driver should still work if you have the same chipset) to give ndiswrapper all it needs to access our card:
```
cd ~/wireless-install/
unzip -a R151519.EXE -d R151519/
cd R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
```
_NOTE:_ Make sure you use the right case, in Linux driver and Driver are very different to DRIVER.
_NOTE II:_ For those of you who have funky fonts in the forum, the driver is a lower caps BCMWL5.inf. Some confusion has occurred as to whether the "L" is a "1" or an "I", hopefully that clarifies!

And that's it! You should be just a reboot away from having a working wireless card:
```
sudo shutdown -r now
```

If you'd like to verify it's working properly without the need for a reboot, try the following series of commands. If your laptop has a wifi-light it should light up after you "modprobe ndiswrapper".
```
sudo rmmod b43 b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```
_NOTE:_ This is essentially what the script we added to /etc/rc.local does, only that script doesn't need to remove the b43 module as it is blacklisted and should not be loaded to start with.


**CLEANING UP**

Once you're happy everything is working well, you can safely remove the working directory:
```
rm -r ~/wireless-install
```
Or you could keep it on hand for future reference!


**TROUBLESHOOTING**
If you have any trouble with the How-To or it doesn't work as expected please post in the thread. I check the thread quite often and I'm always happy to help. It's also possible there's something I've missed which I can then incorporate into the How-To for everyone else to benefit from. If you're posting seeking help, please include the outputs of the following commands:
```
lspci -nn | grep 14e4
ndiswrapper -l
ndiswrapper -v
lsmod | grep b43
lsmod | grep ndiswrapper
ls -l /etc/rc.local
cat /etc/rc.local
lshw -C network
```
as well as anything else you think is relevant. Please include long code outputs in ```
 tags (the # button in the advanced edit view) so they're easier to read.


**UNINSTALLING**

If for some reason you'd like to remove everything that this how-to has done, it's rather simple:
Undo the file changes we made:
[code]gksudo gedit /etc/modprobe.d/blacklist
# Remove the line we added: "blacklist b43"
gksudo gedit /etc/rc.local
# Remove the four modprobe lines we added
```

Remove the driver we told ndiswrapper to use:
```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwl5
```
Remove ndiswrapper:
```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils
```



Changelog:
21/04/08: Made minor clarifications to layout
22/04/08: Added Troubleshooting section
26/04/08: Added redundancy for users with no broadcom wired card
26/04/08: Added note for Gutsy upgraders
01/05/08: Added blacklist for b43legacy
10/05/08: Fixed old link
11/05/08: Added link to NDISwrapper wiki (list of supported cards)
04/06/08: Added extra package to install
08/07/08: Updated troubleshooting
24/07/08: Added redundancy for KDE users
09/09/09: Added code to blacklist wl (meant for 4315 chipset and included in ubuntu-restricted-extras)
11/11/09: Cleaned up the introduction a bit

---

### Post by Krovas on 2008-04-21
Worked like a charm on my Compaq/HP lappy. :guitar:

---

### Post by Champers on 2008-04-21
Didn't work for my on Dell e1505.

---

### Post by Champers on 2008-04-22
Well, after running 

```
modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
```

my internet finally worked after 3 days of googling tutorials lol

---

### Post by jw5801 on 2008-04-22
> **Champers said:**
> Well, after running 

```
modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
```

my internet finally worked after 3 days of googling tutorials lol

That's exactly what the startup script in /etc/rc.local does, only without removing b43 since b43 is blacklisted and won't be loaded anyway. Does it still work on reboot, or do you need to manually run those commands each time you log in?

---

### Post by Cheburator on 2008-04-22
thanks a lot! works on BCM94311MCG

---

### Post by davidefergnani on 2008-04-22
i followed all the instructions but the wireless card is not workin yet.
I have a Hp pavillion dv9410us with hardy 64 bit
My card is a [14e4:4311] (rev 02).
this is the result of the command in the troubleshooting section:


davidefergnani@davidefergnani-laptop:~$ lscpi -nn | grep 14e4
bash: lscpi: command not found
davidefergnani@davidefergnani-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
davidefergnani@davidefergnani-laptop:~$ lsmod | grep b43
davidefergnani@davidefergnani-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
davidefergnani@davidefergnani-laptop:~$ ls -l /etc/rc.local



i dont understand why is not working. i followed all the instructions

---

### Post by jw5801 on 2008-04-23
> **davidefergnani said:**
> i followed all the instructions but the wireless card is not workin yet.
I have a Hp pavillion dv9410us with hardy 64 bit
My card is a [14e4:4311] (rev 02).
this is the result of the command in the troubleshooting section:


davidefergnani@davidefergnani-laptop:~$ lscpi -nn | grep 14e4
bash: lscpi: command not found
davidefergnani@davidefergnani-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
davidefergnani@davidefergnani-laptop:~$ lsmod | grep b43
davidefergnani@davidefergnani-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
davidefergnani@davidefergnani-laptop:~$ ls -l /etc/rc.local



i dont understand why is not working. i followed all the instructions

Ok, can you include the output from the last command? Also what happens when you try the commands to load ndiswrapper:
```
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe ndiswrapper
```
Does that make your wifi light come on? What happens when you run:
```
iwlist scan
ifconfig
```

---

### Post by elnigno on 2008-04-23
> **jw5801 said:**
> This How-To describes how to get WiFi working with the Broadcom 1390 WLAN offered in many Dell and HP laptops using ndiswrapper. Many of us use ndiswrapper as an alternative to the native drivers (b43), as we feel the native drivers have no quite reached a point where they compare with ndiswrapper, usually this relates to only being able to use 802.11b connections (11Mbps) as opposed to 802.11g (54Mbps).

The how-to has been tested on an AMD64 install of the Hardy Heron Release Candidate (and I'm sure will soon be tested on an i386 install).

**THIS HOW-TO IS FOR UBUNTU HARDY HERON (8.04) ONLY.** The How-To is loosely based on Paperdiesel's How-To for earlier versions of Ubuntu which can be found [here](http://ubuntuforums.org/showthread.php?t=297092). If you are not running Hardy, then this How-To will not work. You should refer to [paperdiesel's How-To](http://ubuntuforums.org/showthread.php?t=297092).

[color=red]DISCLAIMER[/color] It's important to note that many people struggle to get wireless working simply because they have unsuccessfully tried a variety of methods and left their system in a shambles. If you've been playing around with alternative methods there's a good chance you won't be able to get this to work until you reverse any previous changes you may have made. It's perhaps best to come straight to this How-To after a fresh install.

To check that you have the same card that this how-to is written for, run the following command:
```
lspci -nn | grep 14e4
```
and you should see something similar to the following:
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI **[14e4:4311]** (rev 01)
```
The section in bold is the important part. If that part doesn't match then you will need a different driver to use with ndiswrapper. The how-to should still be valid however!


**STEP 1: OBTAINING THE REQUIRED PACKAGES**
Thankfully, Hardy includes a new enough version of ndiswrapper to remove the need for installing it from source. This saves a lot of trouble during the install process.

For the install process I find it best to create a separate working directory to get all this done in. You can use whatever directory you'd like so long as you're consistent, if you're unsure copy the way I've done it. 

Most of the work from here on will be done from the command-line, so open up a terminal (Applications > Accessories > Terminal), and use it to create your working directory:
```
mkdir wireless-install
cd wireless-install
```

First we need to obtain the correct XP driver (Vista drivers WILL NOT WORK with ndiswrapper) for this chipset, and also install some extra packages. This is easy if you have access to the internet (via a wired connection or otherwise):
```
wget http://ftp.us.dell.com/network/R151519.EXE
```
NOTE: If lspci above showed that you had a different chipset, this driver won't work. You're welcome to try using a different driver, however ndiswrapper is a temperamental thing, so I can't guarantee it will work with just any driver. A google search for the number relating to your card, ie. 14e4:4315 or 14e4:4318, and ndiswrapper should return a driver you can use quite quickly.

Next install ndiswrapper. The latest version is available from the Hardy repositories which is a rather nice change for those of us who are used to the need to recompile ndiswrapper on every kernel change!
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

If you have no internet access on your Ubuntu machine then you'll need to get the appropriate driver from [here](http://ftp.us.dell.com/network/R151517.EXE) and copy it to your working directory (~/wireless-install). The packages can be installed from your trusty Hardy LiveCD (a Gutsy, or any other, LiveCD WILL NOT WORK): 
```
sudo apt-cdrom add
#When prompted, insert your Hardy CD and press enter
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
NOTE: Hardy behaved oddly with this so I had to work around a bit to get the above to work, it wasn't as simple as it should be. If anyone else has this issue I'll edit the above to use my workaround and post a bug report (I'll probably do the second anyway).


**STEP 2: PREVENTING THE NATIVE MODULES FROM INTERFERING WITH NDISWRAPPER**
This process is not quite as simple as it has been in the past due to the different native modules and how they interact with each other. So firstly we're going to blacklist a few things by adding them to the /etc/modprobe.d/blacklist file:
NOTE: You can do this with a text editor, using "gksudo gedit /etc/modprobe.d/blacklist" for example. I just like to do it the fancy way! So if you copy and paste the line below, you can't go wrong!
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
```

We also need to add a bootscript to load a couple of modules in an order that suits us. The reason being that the ssb module takes control of our card, thus preventing ndiswrapper from controlling it, however ssb is required by the b44 driver, which handles wired broadcom cards, so we can't just blacklist it. If you would like (and know how to), you can easily use a new script to do this, however the easiest way I find is to add it to /etc/rc.local. To do this we need to edit the file:
```
gksudo gedit /etc/rc.local
```
Feel free to replace gedit with the text editor of your choice (kate, mousepad, emacs, nano, vi, bluefish, etc), then add the following to lines to the end of the script, just before the "exit 0":
```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```
To give you an idea, my /etc/rc.local now looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
```


**STEP 3: INSTALLING THE DRIVER WITH NDISWRAPPER**

Now we're going to use the driver we downloaded from the Dell website (note that it doesn't matter if your laptop is not a Dell, this driver should still work if you have the same chipset) to give ndiswrapper all it needs to access our card:
```
cd ~/wireless-install/
unzip -a R151519.EXE -d R151519/
cd R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
```
NOTE: Make sure you use the right case, in Linux driver and Driver very different to DRIVER.

And that's it! You should be just a reboot away from having a working wireless card:
```
sudo shutdown -r now
```

If you'd like to verify it's working properly without the need for a reboot, try the following series of commands:
NOTE: This is essentially what the script we added to /etc/rc.local does, only that script doesn't need to remove the b43 module as it is blacklisted and should not be loaded to start with.
```
sudo rmmod b43 b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```
If your laptop has a wifi-light it should light up after you modprobe ndiswrapper.


**CLEANING UP**

Once you're happy everything is working well, you can safely remove the working directory:
```
rm -r ~/wireless-install
```
Or you could keep it on hand for future reference!


**TROUBLESHOOTING**
If you have any trouble with the How-To or it doesn't work as expected please post in the thread. I check the thread quite often and I'm always happy to help. It's also possible there's something I've missed which I can then incorporate into the How-To for everyone else to benefit from. If you're posting seeking help, please include the outputs of the following commands:
```
lscpi -nn | grep 14e4
ndiswrapper -l
lsmod | grep b43
lsmod | grep ndiswrapper
ls -l /etc/rc.local
```
as well as anything else you think is relevant. Please include long code outputs in ```
 tags (the # button in the advanced edit view) so they're easier to read.


**UNINSTALLING**

If for some reason you'd like to remove everything that this how-to has done, it's rather simple:
Undo the file changes we made:
[code]gksudo gedit /etc/modprobe.d/blacklist
# Remove the line we added: "blacklist b43"
gksudo gedit /etc/rc.local
# Remove the four modprobe lines we added
```
Remove the driver we told ndiswrapper to use:
```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwl5
```
Remove ndiswrapper:
```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils
```



Changelog:
21/04/08: Made minor clarifications to layout
22/04/08: Added Troubleshooting section

I love you, really! It worked!

---

### Post by Champers on 2008-04-23
> **jw5801 said:**
> That's exactly what the startup script in /etc/rc.local does, only without removing b43 since b43 is blacklisted and won't be loaded anyway. Does it still work on reboot, or do you need to manually run those commands each time you log in?

I made a script with the commands in it and added it to the /etc/init.d so that it would run everytime I turn on the computer, all by itself

---

### Post by jw5801 on 2008-04-23
> **Champers said:**
> I made a script with the commands in it and added it to the /etc/init.d so that it would run everytime I turn on the computer, all by itself

That's what /etc/rc.local does. It's a script that is called by another script in /etc/init.d/, so if you followed the how-to correctly you would have wound up at the same point.

---

### Post by davidefergnani on 2008-04-23
> **jw5801 said:**
> Ok, can you include the output from the last command? Also what happens when you try the commands to load ndiswrapper:
```
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe ndiswrapper
```
Does that make your wifi light come on? What happens when you run:
```
iwlist scan
ifconfig
```


the light will not come on
an this is the result of running the second code


```
davidefergnani@davidefergnani-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

davidefergnani@davidefergnani-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:6a:48:f6  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe6a:48f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9441891 (9.0 MB)  TX bytes:462384 (451.5 KB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54933 (53.6 KB)  TX bytes:54933 (53.6 KB)

```

i hope that this will help to solve the problem

---

### Post by jw5801 on 2008-04-23
> **davidefergnani said:**
> the light will not come on
an this is the result of running the second code


```
davidefergnani@davidefergnani-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

davidefergnani@davidefergnani-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:6a:48:f6  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe6a:48f6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7252 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4614 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9441891 (9.0 MB)  TX bytes:462384 (451.5 KB)
          Interrupt:20 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54933 (53.6 KB)  TX bytes:54933 (53.6 KB)

```

i hope that this will help to solve the problem

It appears as though you don't have the ndiswrapper module installed. Can you ```
sudo modprobe ndiswrapper
dmesg | tail -n10
```
And post everything that comes out here, regardless of whether it appears relevant or not. You need to make sure you read the output after each command in case it reports errors or anything along those lines. Post everything here so I can have a look at it.

---

### Post by davidefergnani on 2008-04-23
> **jw5801 said:**
> It appears as though you don't have the ndiswrapper module installed. Can you ```
sudo modprobe ndiswrapper
dmesg | tail -n10
```
And post everything that comes out here, regardless of whether it appears relevant or not. You need to make sure you read the output after each command in case it reports errors or anything along those lines. Post everything here so I can have a look at it.



this is waht came out:

davidefergnani@davidefergnani-laptop:~$ sudo modprobe ndiswrapper
davidefergnani@davidefergnani-laptop:~$ dmesg | tail -n10
[35556.199328]  domain 0: span 03
[35556.199330]   groups: 01 02
[35556.199334]   domain 1: span 03
[35556.199335]    groups: 03
[35556.199338] CPU1 attaching sched-domain:
[35556.199339]  domain 0: span 03
[35556.199341]   groups: 02 01
[35556.199343]   domain 1: span 03
[35556.199345]    groups: 03
[35812.819060] ACPI: PCI interrupt for device 0000:03:00.0 disabled
davidefergnani@davidefergnani-laptop:~$

---

### Post by jw5801 on 2008-04-24
> **davidefergnani said:**
> this is waht came out:

davidefergnani@davidefergnani-laptop:~$ sudo modprobe ndiswrapper
davidefergnani@davidefergnani-laptop:~$ dmesg | tail -n10
[35556.199328]  domain 0: span 03
[35556.199330]   groups: 01 02
[35556.199334]   domain 1: span 03
[35556.199335]    groups: 03
[35556.199338] CPU1 attaching sched-domain:
[35556.199339]  domain 0: span 03
[35556.199341]   groups: 02 01
[35556.199343]   domain 1: span 03
[35556.199345]    groups: 03
[35812.819060] ACPI: PCI interrupt for device 0000:03:00.0 disabled
davidefergnani@davidefergnani-laptop:~$

Ok, well it looks as though ndiswrapper is being loaded correctly (from what I can see). Have a look in your laptops bios and have a play with the wireless hotkey settings there. I sometimes find that if the wireless has been toggled off it needs to have the wireless hotkey turned off in the bios, or turned on again, or something along those lines.

---

### Post by hopcroft on 2008-04-24
omg i think i love you!

worked a dream on HP dv6552ea which is the BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)

great fix.

i should add that i did this on hardy.

---

### Post by adrian.mowrey on 2008-04-24
Oh, I see. I apologize because I didn't see this post earlier before I posted my previous question about "How To" on Ubuntu 8.04 Hardy Heron. Thank you for your understanding, and I really appreciate the help.

Sincerely,

Adrian G. Mowrey

---

### Post by davidefergnani on 2008-04-24
> **jw5801 said:**
> Ok, well it looks as though ndiswrapper is being loaded correctly (from what I can see). Have a look in your laptops bios and have a play with the wireless hotkey settings there. I sometimes find that if the wireless has been toggled off it needs to have the wireless hotkey turned off in the bios, or turned on again, or something along those lines.

i`ve checked on my bios but there is nothing about my wireless card,i cant get this fixed. What else could be?

---

### Post by raj83168 on 2008-04-25
Hello everyone, this is my first ever day with linux and Hardy Heron, and loving every moment of it! I did exactly as mentioned in the "how to" but I get this error

> FATAL: Could not open '/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory


Need help! thanks in advance

Raj

---

### Post by RiseAgainst540 on 2008-04-25
Works like a charm on my e1505. Only question, will it auto detect every time I boot up?

---

### Post by RiseAgainst540 on 2008-04-25
Nevermind, answered it myself, dude I love you!

This version of ubuntu rocks! FAST boot times, and now wireless! All I need now is the ATI instructions....

---

### Post by raj83168 on 2008-04-25
Now i get this new error! 

> root@raj:/# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


here are some details i have: 

> root@raj:/# lspci -nn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
root@raj:/# ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)


Help help! 

RAj:(

---

### Post by mpgarate on 2008-04-25
> **raj83168 said:**
> Now i get this new error! 



here are some details i have: 



Help help! 

RAj:(

Same here.

---

### Post by jw5801 on 2008-04-25
> **raj83168 said:**
> Now i get this new error! 



here are some details i have: 



Help help! 

RAj:(

> **mpgarate said:**
> Same here.

It appears as though you don't have the ndiswrapper-utils-1.9 package installed, try ```
sudo aptitude install ndiswrapper-utils-1.9
```

---

### Post by jw5801 on 2008-04-25
> **RiseAgainst540 said:**
> Works like a charm on my e1505. Only question, will it auto detect every time I boot up?

That's what the commands the how-to adds to /etc/rc.local are all about, those are the commands you need to use to add the ndiswrapper module and get your wireless rolling, so that runs them at startup!

---

### Post by jw5801 on 2008-04-25
> **davidefergnani said:**
> i`ve checked on my bios but there is nothing about my wireless card,i cant get this fixed. What else could be?

After you run the commands to add ndiswrapper to the kernel:
```
sudo rmmod b44 ssb
sudo modprobe ndiswrapper
```

Does ```
iwlist scan
```
report a wlan0 interface? So run those three commands and post the output here.

---

### Post by SoulSmasher on 2008-04-25
worked like a charm on acer aspire 5104 (which has the same chipset)

now i'm typing this over a wireless network, 

thanks soo much :)

---

### Post by 0004tom on 2008-04-25
I'm getting this error code while running this command, and can't make heads or tails of it

tom@PCNO1Linux:~/wireless-install$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules

I've followed the guide, with every detail, and still my Wifi light remains orange, for off.

Any idea's ?

I'm on a HPG6030EA with a rev 02 of the WIFI card

---

### Post by jw5801 on 2008-04-25
> **0004tom said:**
> I'm getting this error code while running this command, and can't make heads or tails of it

tom@PCNO1Linux:~/wireless-install$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules

I've followed the guide, with every detail, and still my Wifi light remains orange, for off.

Any idea's ?

I'm on a HPG6030EA with a rev 02 of the WIFI card

That output is ok, just means that when you're trying to remove the modules, they're not added anyway so it can't remove them. What happens when you run ```
sudo modprobe ndiswrapper
```

---

### Post by adam15c on 2008-04-25
I want to try this on my HP Compaq Lappy which has the same specs as mentioned. If I upgrade my system rather than do a new install is anything different? Also when I upgrade I will lose my wireless connection. Any further advice would be very much appreciated. Thanks.

---

### Post by jw5801 on 2008-04-25
> **adam15c said:**
> I want to try this on my HP Compaq Lappy which has the same specs as mentioned. If I upgrade my system rather than do a new install is anything different? Also when I upgrade I will lose my wireless connection. Any further advice would be very much appreciated. Thanks.

It all depends on how you got your wireless working to begin with. If you changed anything that will persist into this install, like adding ndiswrapper to /etc/modules, then you'll need to undo that for this to work properly.

If you have the how-to you followed for Gutsy, or you can remember how you got it working, then doing the opposite of whatever you did that time ought to be enough to fix any issues it might cause. It will still be a little bit more difficult and require some more ground work on your part.

---

### Post by 0004tom on 2008-04-25
sorry for the long repply, forums are going slow for me :s

anyway, when i run the command, sudo modprobe ndiswrapper

This is what i get back

tom@PCNO1Linux: sudo modprobe ndiswrapper
tom@PCNO1Linux:

---

### Post by adam15c on 2008-04-25
> **jw5801 said:**
> It all depends on how you got your wireless working to begin with. If you changed anything that will persist into this install, like adding ndiswrapper to /etc/modules, then you'll need to undo that for this to work properly.

If you have the how-to you followed for Gutsy, or you can remember how you got it working, then doing the opposite of whatever you did that time ought to be enough to fix any issues it might cause. It will still be a little bit more difficult and require some more ground work on your part.

For Gutsy I am using the Restricted Drivers Manager (firmware for Broadcom 43xx) with fwcutter. Which was very easy to set up.

---

### Post by 0004tom on 2008-04-25
Right, quick update, i wiped Ubuntu and installed it again,

Started from the very start, whent though the How to, with a fine hair combe.

got to the end, and where you say do command lines to check if it works before rebooting, i did... SUCESS, light went blue !!!

Reboot, nothing, orange light...

What could have gone wrong ?

this is what i have to do, to enable my card after a restart

tom@PCNO1Linux:~$ sudo modprobe -r ndiswrapper
tom@PCNO1Linux:~$ sudo ndiswrapper -e bcmwl5
tom@PCNO1Linux:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
tom@PCNO1Linux:~$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
tom@PCNO1Linux:~$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
tom@PCNO1Linux:~$ cd ~/wireless-install/
tom@PCNO1Linux:~/wireless-install$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
tom@PCNO1Linux:~/wireless-install$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
tom@PCNO1Linux:~/wireless-install$ sudo modprobe ndiswrapper
tom@PCNO1Linux:~/wireless-install$ 

after the last command, the wireless card works.

is it i at vault, or my installion, as i'm doing everythin in your guide ?

---

### Post by EastBayAnt on 2008-04-25
Ahhh! Thank you so much! Finally got my wireless up and running! :)

---

### Post by jw5801 on 2008-04-25
> **adam15c said:**
> For Gutsy I am using the Restricted Drivers Manager (firmware for Broadcom 43xx) with fwcutter. Which was very easy to set up.

You can use the same thing again. That's a different method to this one. The reason many of us use ndiswrapper as opposed to the open source driver for this chipset (bcm43xx in earlier kernels, b43 in this one), is because the older drivers only support 802.11b connections (11Mb/s) as compared to 802.11g (54Mb/s). It's really just a matter of preference though, if you're not going to be copying files over your local network, then you probably won't notice a difference.

---

### Post by jw5801 on 2008-04-25
> **0004tom said:**
> Right, quick update, i wiped Ubuntu and installed it again,

Started from the very start, whent though the How to, with a fine hair combe.

got to the end, and where you say do command lines to check if it works before rebooting, i did... SUCESS, light went blue !!!

Reboot, nothing, orange light...

What could have gone wrong ?

this is what i have to do, to enable my card after a restart

tom@PCNO1Linux:~$ sudo modprobe -r ndiswrapper
tom@PCNO1Linux:~$ sudo ndiswrapper -e bcmwl5
tom@PCNO1Linux:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
tom@PCNO1Linux:~$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
tom@PCNO1Linux:~$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
tom@PCNO1Linux:~$ cd ~/wireless-install/
tom@PCNO1Linux:~/wireless-install$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
tom@PCNO1Linux:~/wireless-install$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
tom@PCNO1Linux:~/wireless-install$ sudo modprobe ndiswrapper
tom@PCNO1Linux:~/wireless-install$ 

after the last command, the wireless card works.

is it i at vault, or my installion, as i'm doing everythin in your guide ?

So after you reboot you have no wireless until you run:
```
sudo modprobe ndiswrapper
```
Correct?

In that case have a look at the output from ```
cat /etc/modules
```
Should be something like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
ndiswrapper
```
If that last line isn't there (or it's on the same line as something else) then you'll need to edit the file and make sure ndiswrapper is on the last line (or on it's own line somewhere in the file).
```
gksudo gedit /etc/modules
```

---

### Post by Bandit09 on 2008-04-25
Hi, I just upgrade to 8.04 Hardy from 7.10 Gutsy. I followed paperdiesel's guide and successfully got my wireless working with ndiswrapper. Now after the upgrade, it no longer worked, so I tried this guide. Everything seems to be fine, but I cannot successfully connect to my network encrypted with WPA. It can connect to unencrypted open networks fine, but not my home network, which is encrypted. Is there some kind of conflict with the new version of ndiswrapper and the new Dell drivers, or perhaps the new linux kernel? Any help would be appreciated. Here is a log of some of my commands:

```
bandit@Obsidian:~$ lscpi -nn | grep 14e4
bash: lscpi: command not found
bandit@Obsidian:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
bandit@Obsidian:~$ lsmod | grep b43
bandit@Obsidian:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
bandit@Obsidian:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 557 2008-04-25 21:18 /etc/rc.local
bandit@Obsidian:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
#tunndiswrapper
ndiswrapper
bandit@Obsidian:~$  
```

Here is the important stuff in my rc.local:

```
modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

exit 0

```

My Blacklist: 

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43

```

Thanks!

Bandit

---

### Post by i speak in math on 2008-04-25
Got stuck at one point -- "sudo ndiswrapper -i bcmwl5.inf"

The l looks an awful lot like a 1 on my computer. It looks like bcmw*FIFTEEN*.inf instead of bcmw*EL*5.inf

Overall, very easy to follow guide for a newbie like me. I thank you very much for getting my wireless working!

---

### Post by Bandit09 on 2008-04-26
UPDATE: I finally fixed it via another method. For those of you who are still having difficulties with the ndiswrapper solution, check out:

[http://paste.ubuntu-nl.org/64457/](http://paste.ubuntu-nl.org/64457/)

Use those commands, reboot and it works like a charm. Please note I am using Hardy 8.04, not sure if it will work with other versions.

For you lazy people who don't feel like clicking, here are the commands (copy and paste them to reduce the room for error)  :)

```
 
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

```

Hope this helps some people out!

Bandit

---

### Post by jw5801 on 2008-04-26
> **Bandit09 said:**
> Hi, I just upgrade to 8.04 Hardy from 7.10 Gutsy. I followed paperdiesel's guide and successfully got my wireless working with ndiswrapper. Now after the upgrade, it no longer worked, so I tried this guide. Everything seems to be fine, but I cannot successfully connect to my network encrypted with WPA. It can connect to unencrypted open networks fine, but not my home network, which is encrypted. Is there some kind of conflict with the new version of ndiswrapper and the new Dell drivers, or perhaps the new linux kernel? Any help would be appreciated. Here is a log of some of my commands:

```
bandit@Obsidian:~$ lscpi -nn | grep 14e4
bash: lscpi: command not found
bandit@Obsidian:~$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)
bandit@Obsidian:~$ lsmod | grep b43
bandit@Obsidian:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
bandit@Obsidian:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 557 2008-04-25 21:18 /etc/rc.local
bandit@Obsidian:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
#tunndiswrapper
ndiswrapper
bandit@Obsidian:~$  
```

Here is the important stuff in my rc.local:

```
modprobe -r b44
modprobe -r b43
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

exit 0

```

My Blacklist: 

```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43

```

Thanks!

Bandit

Hmm... well I'm not aware of any conflict between the new kernel and WPA, and this is the same version of ndiswrapper and the same driver as in paperdiesel's howto, so it can't be between ndiswrapper and WPA. That being said, I don't know all that much about WPA. If you can connect to an unecrypted (or WEP) network then the driver and ndiswrapper install all went correctly. What are you using for WPA? wpa_supplicant?

---

### Post by jw5801 on 2008-04-26
> **Bandit09 said:**
> UPDATE: I finally fixed it via another method. For those of you who are still having difficulties with the ndiswrapper solution, check out:

[http://paste.ubuntu-nl.org/64457/](http://paste.ubuntu-nl.org/64457/)

Use those commands, reboot and it works like a charm. Please note I am using Hardy 8.04, not sure if it will work with other versions.

For you lazy people who don't feel like clicking, here are the commands (copy and paste them to reduce the room for error)  :)

```
 
wget http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd ..
export FIRMWARE_INSTALL_DIR="/lib/firmware"
wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2
tar xjf broadcom-wl-4.80.53.0.tar.bz2
cd broadcom-wl-4.80.53.0/kmod
sudo ../../b43-fwcutter-011/b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

```

Hope this helps some people out!

Bandit

That would be for b43, the open source driver for these cards. There are reasons for and against using it as I've discussed on numerous occasions. Just be aware that the two solutions are mutually exclusive, you'll need to undo pretty much everything done in Step 2 of this how-to if you want to get b43 working. That being said from a fresh install, b43-fwcutter is in the repos, so it should be necessary to get it externally and compile it. You should also be able to use the restricted drivers manager to do all of this for you, with one click. This how-to is primarily an alternative to b43, for those of us who feel that the open source drivers aren't quite up to the same standard yet.

---

### Post by 0004tom on 2008-04-26
> **jw5801 said:**
> So after you reboot you have no wireless until you run:
```
sudo modprobe ndiswrapper
```
Correct?

If i run that command, nothin happens, I have to remove the Driver, and reinstall it.

Come to think about it, I'm using Vista Drivers, but i can't see why thats stopping the Card starting on boot up ?

The Vista Drivers are working, as i'm writing this to you now, From Ubuntu, on a wireless network. i didn't realise untill a few moments ago.
I'll tottle of and try with XP drivers #-o

Edit, same happens with XP drivers, not working after restart.

This is my output from cat /etc/modules

```
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
```

:confused:

could it be the line thats missing ?

---

### Post by jw5801 on 2008-04-26
> **0004tom said:**
> If i run that command, nothin happens, I have to remove the Driver, and reinstall it.

Come to think about it, I'm using Vista Drivers, but i can't see why thats stopping the Card starting on boot up ?

The Vista Drivers are working, as i'm writing this to you now, From Ubuntu, on a wireless network. i didn't realise untill a few moments ago.
I'll tottle of and try with XP drivers #-o

Edit, same happens with XP drivers, not working after restart.

This is my output from cat /etc/modules

```
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
ndiswrapper
```

:confused:

could it be the line thats missing ?

Well you can probably remove all the redundant lines! You only need one ndiswrapper. What's in /etc/rc.local?:
```
cat /etc/rc.local
```

Let's try and narrow down what it's requiring you to do on each boot. What happens if you run: ```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
```
As soon as you boot up?

---

### Post by 0004tom on 2008-04-26
> **jw5801 said:**
> Well you can probably remove all the redundant lines! You only need one ndiswrapper. What's in /etc/rc.local?:

```

# By default this script does nothing.

modprobe -r b43
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44


exit 0
```

I added the -r b43 line to see if that worked, no joy :(


> **jw5801 said:**
> Let's try and narrow down what it's requiring you to do on each boot. What happens if you run: ```
sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo modprobe ndiswrapper
```
As soon as you boot up?

Nothing, i if i don't start from, 

```
sudo modprobe -r ndiswrapper
```

and work my way though the guide again i can't get the light to go blue.

```
tom@PCNO1Linux:~$ sudo modprobe -r ndiswrapper
tom@PCNO1Linux:~$ sudo ndiswrapper -e bcmwl5
tom@PCNO1Linux:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
tom@PCNO1Linux:~$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
tom@PCNO1Linux:~$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
tom@PCNO1Linux:~$ cd ~/wireless-install/
tom@PCNO1Linux:~/wireless-install$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
tom@PCNO1Linux:~/wireless-install$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
tom@PCNO1Linux:~/wireless-install$ sudo modprobe ndiswrapper
```

If i do this, on the final command, light goes blue, and i'm wireless :)

just a little ball ache, having to do this everytime i wanna use Ubuntu

---

### Post by st33med on 2008-04-26
The b43 proprietary driver works fine for me, I just need to undo these steps for blacklisting it on startup...

This method did not work for me. Thank you for the effort of filling in the missing spaces for paperdiesel's howto, however.

---

### Post by adam15c on 2008-04-26
> **jw5801 said:**
> You can use the same thing again. That's a different method to this one. The reason many of us use ndiswrapper as opposed to the open source driver for this chipset (bcm43xx in earlier kernels, b43 in this one), is because the older drivers only support 802.11b connections (11Mb/s) as compared to 802.11g (54Mb/s). It's really just a matter of preference though, if you're not going to be copying files over your local network, then you probably won't notice a difference.

Thank you for your assistance with this. I followed your tutorial and I have wireless on my Compaq lappy with a Broadcom card. What would we do without help such as yours? Excellent, thank you :popcorn:

---

### Post by gulgulguru on 2008-04-26
> **jw5801 said:**
> That's what /etc/rc.local does. It's a script that is called by another script in /etc/init.d/, so if you followed the how-to correctly you would have wound up at the same point.

Hi jw5801,

Thank you for taking the time to write such a clear guide. I got it working but after a minor(?) alteration to /etc/rc.local.

Champers pointed out that he needed to create a script to run:

```
modprobe -r b44
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
```

These lines worked for me straight away in /etc/rc.local - no extra script needed.

The problem I had at first was that your version of this was

```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```

The above didn't work for me after booting up but it did once I added 

```
modprobe -r ndiswrapper
```

before 

```
modprobe ndiswrapper
```

Hope that helps others!

---

### Post by jw5801 on 2008-04-26
> **0004tom said:**
> ```

# By default this script does nothing.

modprobe -r b43
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44


exit 0
```

I added the -r b43 line to see if that worked, no joy :(




Nothing, i if i don't start from, 

```
sudo modprobe -r ndiswrapper
```

and work my way though the guide again i can't get the light to go blue.

```
tom@PCNO1Linux:~$ sudo modprobe -r ndiswrapper
tom@PCNO1Linux:~$ sudo ndiswrapper -e bcmwl5
tom@PCNO1Linux:~$ sudo rmmod b44
ERROR: Module b44 does not exist in /proc/modules
tom@PCNO1Linux:~$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
tom@PCNO1Linux:~$ echo ndiswrapper | sudo tee -a /etc/modules
ndiswrapper
tom@PCNO1Linux:~$ cd ~/wireless-install/
tom@PCNO1Linux:~/wireless-install$ sudo ndiswrapper -i bcmwl5.inf
installing bcmwl5 ...
tom@PCNO1Linux:~/wireless-install$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
tom@PCNO1Linux:~/wireless-install$ sudo modprobe ndiswrapper
```

If i do this, on the final command, light goes blue, and i'm wireless :)

just a little ball ache, having to do this everytime i wanna use Ubuntu

Hmm... ok, so I notice that b43, b44 and ssb are all not loaded on start up, that's ok, in fact it's a good thing. Do you have a line for ndiswrapper in both /etc/rc.local and in /etc/modules? If you do you can probably remove everything from /etc/rc.local (other than the "exit 0" that was there to start with) and that might make a difference.

One last test, after you've booted up simply try removing the module and adding it again:
```
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
```

And see if that does it.
By the way, "rmmod" and "modprobe -r" are equivalent, just to alleviate any confusion the use of the two may have caused. They both remove a module from the kernel.

---

### Post by jw5801 on 2008-04-26
> **gulgulguru said:**
> Hi jw5801,

Thank you for taking the time to write such a clear guide. I got it working but after a minor(?) alteration to /etc/rc.local.

Champers pointed out that he needed to create a script to run:

```
modprobe -r b44
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44
```

These lines worked for me straight away in /etc/rc.local - no extra script needed.

The problem I had at first was that your version of this was

```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```

The above didn't work for me after booting up but it did once I added 

```
modprobe -r ndiswrapper
```

before 

```
modprobe ndiswrapper
```

Hope that helps others!

Ok, I notice that this appears to be a recurring problem. If you've upgraded straight from Gutsy, odds are you will have a line in /etc/modules that loads ndiswrapper. Removing this line will solve this issue!

---

### Post by 0004tom on 2008-04-26
:guitar:

I LOVE YOU

Sucesss.

After removing the Nidswrapper lines from /etc/modules and adding the lines back to /etc/rc.local

I have a Wireless Card after rebooting, with out having to go into the terminal.

Thanks for your help in this funky issue with HP laptops :)

---

### Post by ibun2 on 2008-04-26
jw5801, I just wanted to say thank you so much for this guide; I had no problems getting my card working because of it. I made a simple walkthrough based on your guide to help people with similar hardware: [http://ubuntuforums.org/showthread.php?p=4806247](http://ubuntuforums.org/showthread.php?p=4806247)

Thanks so much!

---

### Post by SoulRyuu on 2008-04-26
jw5801 thanks a lot mate, This worked like a charm.

Starts and connects nice and quickly as soon as i start the laptop and it's a nice solid signal all the time also.

I signed up to the forum just so i can post this thank you, much like most linux users the wireless has been the biggest pain in the butt for years, but thanks to you i can say bye bye to my xp once and for all :)

P.S : My Laptop is an Acer Aspire 3690 Running a clean install of Hardy Heron Full Release.

---

### Post by Rocky37 on 2008-04-27
Hi jw --Am also new to linux but have been looking comfortable and got hooked on Hardy beta 5 some 3 weeks ago.  Have to tell you I love Hardy!!

I am working with a Dell Vostro 1500 w/1390 wlan.  Needless to say, it seems I have joined the ranks with my wireless problem.  Sorry for the following dump but have been reading and writing and saving for a few hours.

My wired connection runs well but not the wired connection.

root@ralph-a5y6s5m6e:/home/ralph# lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

root@ralph-a5y6s5m6e:/home/ralph# ndiswrapper -l
bcmwl5 : invalid driver!


ot@ralph-a5y6s5m6e:/home/ralph# lsmod | grep b43


root@ralph-a5y6s5m6e:/home/ralph# lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  8 lmpcm_usb,ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd


root@ralph-a5y6s5m6e:/home/ralph# ls -l /etc/rc.local
-rwxr-xr-x 1 root root 372 2008-04-26 21:23 /etc/rc.local
root@ralph-a5y6s5m6e:/home/ralph# 



root@ralph-a5y6s5m6e:/etc# modprobe -r b44
root@ralph-a5y6s5m6e:/etc# modprobe -r ssb
root@ralph-a5y6s5m6e:/etc# modprobe ndiswrapper


root@ralph-a5y6s5m6e:/etc# iwlist scan
lo        Interface doesn't support scanning.

root@ralph-a5y6s5m6e:/etc# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75300 (73.5 KB)  TX bytes:75300 (73.5 KB)

root@ralph-a5y6s5m6e:/etc#

---

### Post by jw5801 on 2008-04-27
> **Rocky37 said:**
> Hi jw --Am also new to linux but have been looking comfortable and got hooked on Hardy beta 5 some 3 weeks ago.  Have to tell you I love Hardy!!

I am working with a Dell Vostro 1500 w/1390 wlan.  Needless to say, it seems I have joined the ranks with my wireless problem.  Sorry for the following dump but have been reading and writing and saving for a few hours.

My wired connection runs well but not the wired connection.

```
root@ralph-a5y6s5m6e:/home/ralph# lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

root@ralph-a5y6s5m6e:/home/ralph# ndiswrapper -l
bcmwl5 : invalid driver!


ot@ralph-a5y6s5m6e:/home/ralph# lsmod | grep b43


root@ralph-a5y6s5m6e:/home/ralph# lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  8 lmpcm_usb,ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd


root@ralph-a5y6s5m6e:/home/ralph# ls -l /etc/rc.local
-rwxr-xr-x 1 root root 372 2008-04-26 21:23 /etc/rc.local
root@ralph-a5y6s5m6e:/home/ralph# 



root@ralph-a5y6s5m6e:/etc# modprobe -r b44
root@ralph-a5y6s5m6e:/etc# modprobe -r ssb
root@ralph-a5y6s5m6e:/etc# modprobe ndiswrapper


root@ralph-a5y6s5m6e:/etc# iwlist scan
lo        Interface doesn't support scanning.

root@ralph-a5y6s5m6e:/etc# ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75300 (73.5 KB)  TX bytes:75300 (73.5 KB)

root@ralph-a5y6s5m6e:/etc#
```

Ok, the issue is in your output from "ndiswrapper -l". See how it says "invalid driver"? That means the driver didn't get installed properly. So remove the one that's there:
```
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
```
Then you'll need to go to the directory where you have your driver, if you followed the how-to exactly this will be:
```
cd ~/wireless-install/R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
```

Make sure none of those commands give you nasty errors. Once that's done, give it another whirl:
```
sudo rmmod b44
sudo rmmod ssb
sudo rmmod b43
sudo modprobe ndiswrapper
sudo morprobe b44
```

---

### Post by mpgarate on 2008-04-27
this worked perfectly for me, except what I think is just a general ubuntu problem. Connecting to the network takes several tries and retypes of the password, maybe 15 failed attempts before an actual connection.

---

### Post by jw5801 on 2008-04-27
> **mpgarate said:**
> this worked perfectly for me, except what I think is just a general ubuntu problem. Connecting to the network takes several tries and retypes of the password, maybe 15 failed attempts before an actual connection.

Hmm... that's interesting. Try a different network manager, wifi-radar and wicd would be my suggestions.

---

### Post by mpgarate on 2008-04-27
are there any terminal-based wifi tools? I would feel more secure with what im doing, maybe identify when the problem occurs?

---

### Post by jw5801 on 2008-04-27
> **mpgarate said:**
> are there any terminal-based wifi tools? I would feel more secure with what im doing, maybe identify when the problem occurs?

Pretty much everything is a frontend for the basic networking tools. Kevdog has a great tutorial for connecting to a network using the commandline:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by andrewbrown22 on 2008-04-27
Followed the tutorial, worked great! However, annoying enough, the damn WiFi light on the laptop does not come on. It is working, but the light doesn't come on and it is very frustrating.. 

Any ideas?

---

### Post by devotia on 2008-04-27
I just got a new laptop and decided it was finally time to try out this crazy *nix I've heard so much about.

So I followed the guide, and got my wireless light to turn on, but after I rebooted, not only did my wireless light not go back on, but my card stopped showing up in the network manager.  :(  Anyone who can figure this one out gets to be my hero :D  Here's the output op asked for:

```
lspci -nn | grep 14e4

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)


ndiswrapper -l

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

lsmod | grep b43: No output

lsmod | grep ndiswrapper:  No output

ls -l /etc/rc.local:  rwxr-xr-x 1 root root 373 2008-04-27 15:17 /etc/rc.local

```

So the question is (are?), what did I screw up, how badly, and how's it get fixed? :)

---

### Post by Rocky37 on 2008-04-27
> **jw5801 said:**
> Ok, the issue is in your output from "ndiswrapper -l". See how it says "invalid driver"? That means the driver didn't get installed properly. So remove the one that's there:
```
sudo rmmod ndiswrapper
sudo ndiswrapper -e bcmwl5
```
Then you'll need to go to the directory where you have your driver, if you followed the how-to exactly this will be:
```
cd ~/wireless-install/R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
```

Make sure none of those commands give you nasty errors. Once that's done, give it another whirl:
```
sudo rmmod b44
sudo rmmod ssb
sudo rmmod b43
sudo modprobe ndiswrapper
sudo morprobe b44
```

COMPUTERS!!!!! Dang ---- Problem solved.
I went into XP this morning and after some rooting around I discovered that XP had swapped out my bcmwl5.inf for a bcmwl5.SYS.  I tried to exchange it but it wouldn't budge.  I did uninstall it and went back to hardy and wireless was nowhere to be found.  I did remove and reinstall hardy after reinstalling the bcmwl5.sys. After it finished with more upgrades there were 2 more drivers included -- Broadcom B43 FWcutter & Broadcom B43 wireless driver. I don't remember them coming through during the first install.  Maybe that corrected the problem.

After the reboot wired and wireless were up and running!! :) ](*,)  I know not why :confused:

JW, you are truly a Saint.  Thanks soooooo much!!!

---

### Post by jw5801 on 2008-04-27
> **devotia said:**
> I just got a new laptop and decided it was finally time to try out this crazy *nix I've heard so much about.

So I followed the guide, and got my wireless light to turn on, but after I rebooted, not only did my wireless light not go back on, but my card stopped showing up in the network manager.  :(  Anyone who can figure this one out gets to be my hero :D  Here's the output op asked for:

```
lspci -nn | grep 14e4

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)


ndiswrapper -l

bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

lsmod | grep b43: No output

lsmod | grep ndiswrapper:  No output

ls -l /etc/rc.local:  rwxr-xr-x 1 root root 373 2008-04-27 15:17 /etc/rc.local

```

So the question(s) is (are?), what did I screw up, how badly, and how's it get fixed? :)

Ok, after you boot up, can you give me the output of these:
```
sudo rmmod ndiswrapper b43 b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
cat /etc/rc.local
cat /etc/modules
```

The first three commands should switch your wireless back on, and the output of all 5 will tell us what you need to do to make it run at startup.

---

### Post by devotia on 2008-04-27
I just did a fresh install and went through the guide again, and now the wireless light is on, but still no luck getting the network manager to work the wireless.

```
sudo rmmod ndiswrapper b43 b44 ssb:

ERROR: Module ndiswrapper does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules

sudo modprobe ndiswrapper:

FATAL: Could not open '/lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko': No such file or directory

sudo modprobe b44:

No output

cat /etc/rc.local:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

cat /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ndiswrapper



```

---

### Post by jw5801 on 2008-04-28
> **devotia said:**
> I just did a fresh install and went through the guide again, and now the wireless light is on, but still no luck getting the network manager to work the wireless.

```
sudo rmmod ndiswrapper b43 b44 ssb:

ERROR: Module ndiswrapper does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules

sudo modprobe ndiswrapper:

FATAL: Could not open '/lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko': No such file or directory

sudo modprobe b44:

No output

cat /etc/rc.local:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0

cat /etc/modules:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp...
sbp2
ndiswrapper



```

You've followed the wrong part of Step 2. So:```
gksudo gedit /etc/modules
```
And remove the ndiswrapper line from /etc/modules.

Then you need to add the lines to /etc/rc.local as in Step 2. That will allow it to work again after you reboot. To get it working at all however you need to install ndiswrapper-utils-1.9:
```
sudo aptitude install ndiswrapper-utils-1.9
```
Will do that if you're connected to the internet by a wired connection or otherwise. If you can't get the internet on your laptop without wireless then you'll need to use your Hardy LiveCD to get the package, as detailed in Step 1 of the how-to.

---

### Post by gunninks on 2008-04-28
I have a dell vostro w/1390 wlan and i am having a terible time getting it to to. I am pretty sure i followed your guide right but i the wifi light does not come on nor is there any indication if the wifi bars at the top of the scree. here is some of the code. If you can help it would be greatly appreciated. Thanks.
```
steve@steve-ubuntu:~$ lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
steve@steve-ubuntu:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
steve@steve-ubuntu:~$ lsmod | grep b43
steve@steve-ubuntu:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  7 uvcvideo,hci_usb,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
steve@steve-ubuntu:~$ modprobe -r b44
FATAL: Error removing b44 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/b44.ko): Operation not permitted
steve@steve-ubuntu:~$ modprobe -r ssb
FATAL: Module ssb is in use.
steve@steve-ubuntu:~$ modprobe ndiswrapper
steve@steve-ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

steve@steve-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:9f:38:9b  
          inet addr:192.168.99.199  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe9f:389b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2096614 (1.9 MB)  TX bytes:165787 (161.9 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77300 (75.4 KB)  TX bytes:77300 (75.4 KB)

```
Never mind i am unsure about what i did but it works now. Thanks.

---

### Post by jw5801 on 2008-04-28
> **gunninks said:**
> ...
Never mind i am unsure about what i did but it works now. Thanks.

If you're curious it's because the first time you attempted to remove the b44 and ssb modules you didn't do it as root (either by appending "sudo" or logging in as root). Thus nothing happened.

---

### Post by devotia on 2008-04-28
Ok, switched which step 2 I used, installed ndiswrapper-util-1.9 and got:

```
sudo rmmod ndiswrapper b43 b44 ssb

ERROR: Module ndiswrapper does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules

sudo modprobe ndiswrapper

FATAL: Could not open '/modules/2.6.24-16-generic/misc/ndiswrapper.ko': No such file or directory
```

---

### Post by jw5801 on 2008-04-28
> **devotia said:**
> Ok, switched which step 2 I used, installed ndiswrapper-util-1.9 and got:

```
sudo rmmod ndiswrapper b43 b44 ssb

ERROR: Module ndiswrapper does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules

sudo modprobe ndiswrapper

FATAL: Could not open '/modules/2.6.24-16-generic/misc/ndiswrapper.ko': No such file or directory
```

You need to install ndiswrapper-utils-1.9! That's where the ndiswrapper module comes from, you can't load it and therefore can't have Wireless if you don't have that module! If you have can't get internet access on your laptop, get the package here: [http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9](http://packages.ubuntu.com/hardy/ndiswrapper-utils-1.9)

Click where it says "i386" (unless you're running the AMD64 build) in bold, select a mirror near to you, then copy the .deb file you get to your laptop, double click on it and it should install all by itself!

If you do have internet access on your laptop:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by kevdog on 2008-04-28
Is the rc.local file really necessary?  This is what I'm experimenting with!

If you add  b44, ssb to the /etc/modprobe.d/blacklist file, and then add

ndiswrapper
ssb
b44

in that order to the /etc/modules file does everything then work?

When does the rc.local file get called?    

And if this doesn't work, would it be possible to just add the modprobe statements to the /etc/network/interfaces file just using a series of pre-up commands? -- That way you could reload everything calling sudo /etc/init.d/networking restart.

Just some ideas I'm tossing around -- need others to play with these things to confirm if they work.

---

### Post by jw5801 on 2008-04-28
> **kevdog said:**
> Is the rc.local file really necessary?  This is what I'm experimenting with!

If you add  b44, ssb to the /etc/modprobe.d/blacklist file, and then add

ndiswrapper
ssb
b44

in that order to the /etc/modules file does everything then work?

When does the rc.local file get called?    

And if this doesn't work, would it be possible to just add the modprobe statements to the /etc/network/interfaces file just using a series of pre-up commands? -- That way you could reload everything calling sudo /etc/init.d/networking restart.

Just some ideas I'm tossing around -- need others to play with these things to confirm if they work.

I tried blacklisting the lot of them and then calling them in /etc/modules in the correct order, that didn't work. Didn't think of /etc/network/interfaces, might give it a try. The other option that was floating around was altering /etc/modprobe.d/ndiswrapper so that it removes ssb and readds it after adding itself.

So you suggest adding something like:
```
iface wlan0 inet dhcp
	pre-up rmmod b44 ssb
	pre-up modprobe ndiswrapper
	post-up modprobe b44
```
to /etc/network/interfaces?

EDIT: Well that works, it's effectively doing the same thing though. I guess we could blacklist the lot of them and do it as:
```
iface wlan0 inet dhcp
	pre-up modprobe ndiswrapper
	post-up modprobe b44
```

EDIT2: Blacklisting the lot and running that doesn't work. And using the first alternative there's still the need to add a line somewhere to bring the interface up. Unless we're going to make it auto, which doesn't really work well with roaming.

---

### Post by noiseordinance on 2008-04-28
Hi there. I have a Dell Vostro 1500 with the 1390 wireless adapter. I have XP on one partition and Ubuntu 8.04 on the other partition. I followed all the instructions to a T on this thread and encountered no problems during the install process. However, I can't view wireless networks. Also, when I boot into XP Pro, all of a sudden my wireless adapter [as well as my cat5 adapter] does not resolve DNS. So basically, I get an IP address, subnet and gateway address, but no DNS suffix. Consequently, both adapters attempt to repair constantly.

Here are my questions: 

1. What can I do to attempt to get wireless networking working on Ubuntu 8.04?
2. I made sure to put in the command for bypassing the firmware install for the NDISWrapper; however, it seems like my hardware is going a little nuts in XP now. Is there any chance I messed with the hardware which is causing XP to go on the fritz?

Thank you for the help...

---

### Post by jw5801 on 2008-04-28
> **noiseordinance said:**
> Hi there. I have a Dell Vostro 1500 with the 1390 wireless adapter. I have XP on one partition and Ubuntu 8.04 on the other partition. I followed all the instructions to a T on this thread and encountered no problems during the install process. However, I can't view wireless networks. Also, when I boot into XP Pro, all of a sudden my wireless adapter [as well as my cat5 adapter] does not resolve DNS. So basically, I get an IP address, subnet and gateway address, but no DNS suffix. Consequently, both adapters attempt to repair constantly.

Here are my questions: 

1. What can I do to attempt to get wireless networking working on Ubuntu 8.04?
2. I made sure to put in the command for bypassing the firmware install for the NDISWrapper; however, it seems like my hardware is going a little nuts in XP now. Is there any chance I messed with the hardware which is causing XP to go on the fritz?

Thank you for the help...

What command to "bypass the firmware install" for ndiswrapper? ndiswrapper is not firmware! It uses the same driver you'll use in XP, just wraps it into the linux kernel. So no, you can't have messed with the hardware (especially not with the wired interface as well).

What do you get from the following?
```
ifconfig
iwlist scan
ndiswrapper -l
```

---

### Post by noiseordinance on 2008-04-28
> **jw5801 said:**
> What command to "bypass the firmware install" for ndiswrapper? ndiswrapper is not firmware! It uses the same driver you'll use in XP, just wraps it into the linux kernel. So no, you can't have messed with the hardware (especially not with the wired interface as well).

What do you get from the following?
```
ifconfig
iwlist scan
ndiswrapper -l
```

Ok, for some reason I thought the blacklist command was having me skip a firmware update on the card. You know, I actually did a different driver than the one listed on this thread. I believe the version I did was 151517R.exe and not 151519R.exe. When I get home I will run the lines that you mentioned.

(Still totally confused why my XP network adapters have gone haywire but it must be purely coincidental.)

Thanks your for help, btw.

---

### Post by Lundok on 2008-04-28
Great tutorial! I had a few problems but they were due to me not reading through it first. 

BTW, being pretty new to Linux, why use 'gksudo' instead of 'sudo'? 'Gksudo' didn't allow me to edit modprobe.d and rc.local. Is that a Gnome specific command?

Anyway, thanks again for all the work that was put into it. Well Done!!

---

### Post by jw5801 on 2008-04-28
> **Lundok said:**
> Great tutorial! I had a few problems but they were due to me not reading through it first. 

BTW, being pretty new to Linux, why use 'gksudo' instead of 'sudo'? 'Gksudo' didn't allow me to edit modprobe.d and rc.local. Is that a Gnome specific command?

Anyway, thanks again for all the work that was put into it. Well Done!!

Are you using KDE? Then yeah you should use "kdesudo" I guess I should include that. As to why, you can read about it here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by jw5801 on 2008-04-28
> **noiseordinance said:**
> Ok, for some reason I thought the blacklist command was having me skip a firmware update on the card. You know, I actually did a different driver than the one listed on this thread. I believe the version I did was 151517R.exe and not 151519R.exe. When I get home I will run the lines that you mentioned.

(Still totally confused why my XP network adapters have gone haywire but it must be purely coincidental.)

Thanks your for help, btw.

R151517.EXE is simply an older version of the same driver, I find R151519.EXE to be slightly more stable, but I think that's just a placebo! Both should work equally well.

---

### Post by noiseordinance on 2008-04-29
Ok I reinstalled 8.04 (i know, a little extreme) and followed the updated instructions and it works like a charm. It doesn't seem like it permanently saves my wireless password (it prompts after reboot every other reboot) but I'm happy.

---

### Post by jw5801 on 2008-04-29
> **noiseordinance said:**
> Ok I reinstalled 8.04 (i know, a little extreme) and followed the updated instructions and it works like a charm. It doesn't seem like it permanently saves my wireless password (it prompts after reboot every other reboot) but I'm happy.

Yeah, that's an issue with network-manager, rather than a driver issue.

---

### Post by pavanmaverick on 2008-04-29
Beautiful tutorial. Worked fine for me:

Inspiron 1505
Broadcom ethernet
Dell 1390 wireless card

---

### Post by noiseordinance on 2008-04-29
Would you recommend people do the pam keyring fix to get the password to save? Thanks for your help with all this by the way, your how-to has been very helpful and has prevented me from jumping back over to PCLOS.

---

### Post by jw5801 on 2008-04-29
> **noiseordinance said:**
> Would you recommend people do the pam keyring fix to get the password to save? Thanks for your help with all this by the way, your how-to has been very helpful and has prevented me from jumping back over to PCLOS.

I didn't think the pam-keyring fix was needed from Gutsy onwards? Isn't there a little radar checkbox you can click to tell it to stop bugging you about passwords? I personally don't use the gnome network manager, I tend to alternate between [wicd](http://wicd.sourceforge.net/) and [wifi-radar](http://wifi-radar.systemimager.org/). Wifi-radar is in the repos and wicd has it's own repository.

---

### Post by noiseordinance on 2008-04-29
> **jw5801 said:**
> I didn't think the pam-keyring fix was needed from Gutsy onwards? Isn't there a little radar checkbox you can click to tell it to stop bugging you about passwords? I personally don't use the gnome network manager, I tend to alternate between [wicd](http://wicd.sourceforge.net/) and [wifi-radar](http://wifi-radar.systemimager.org/). Wifi-radar is in the repos and wicd has it's own repository.

I see no checkmark to get it to stop annoying. And it's odd that it doesn't always prompt for password, yet other times it prompts in the midst of an internet session. Which of those two do you recommend, and how do I get it installed?

---

### Post by jw5801 on 2008-04-29
> **noiseordinance said:**
> I see no checkmark to get it to stop annoying. And it's odd that it doesn't always prompt for password, yet other times it prompts in the midst of an internet session. Which of those two do you recommend, and how do I get it installed?

The pam-keyring solution worked quite well last time I used it, there's a how-to around somewhere.

I'm currently using wicd which I find works quite well. If you like having a tray applet then wicd is for you, otherwise wifi-radar is equally as good. wifi-radar is in the normal repositories, wicd you'll need to add a 3rd party repo for.

The choice is basically a matter of preference.

---

### Post by quill7111 on 2008-04-29
Hi all

I'm on a dell inspiron 5100 with a broadcom BCM4306 card. I'm using the drivers I used in feisty (and gutsy) to get ndiswrapper to work rather than the ones listed in the howto. After following the tutorial the network manager can see that I have a wireless card but can't find any networks. Also, my wired connection is unable to properly connect; it tries and tries and ends up with a null address. Unloading and reloading b44 also breaks the wired interface (if I boot having commented out all the changes from the howto). Here are some outputs that were asked for in previous posts:
```

matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:32:37:a4  
          inet6 addr: fe80::20d:56ff:fe32:37a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6607 (6.4 KB)  TX bytes:11642 (11.3 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:4b:2c:b3:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:faffc000-faffe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0d:56:32:37:a4  
          inet addr:169.254.5.96  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91844 (89.6 KB)  TX bytes:91844 (89.6 KB)
```

```

matt@matt-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      No scan results

eth0      Interface doesn't support scanning.

```

```

matt@matt-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

```

Thanks for putting in so much time and effort JW!

---

### Post by jw5801 on 2008-04-30
> **quill7111 said:**
> Hi all

I'm on a dell inspiron 5100 with a broadcom BCM4306 card. I'm using the drivers I used in feisty (and gutsy) to get ndiswrapper to work rather than the ones listed in the howto. After following the tutorial the network manager can see that I have a wireless card but can't find any networks. Also, my wired connection is unable to properly connect; it tries and tries and ends up with a null address. Unloading and reloading b44 also breaks the wired interface (if I boot having commented out all the changes from the howto). Here are some outputs that were asked for in previous posts:
```

matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:32:37:a4  
          inet6 addr: fe80::20d:56ff:fe32:37a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6607 (6.4 KB)  TX bytes:11642 (11.3 KB)
          Interrupt:7 

eth1      Link encap:Ethernet  HWaddr 00:90:4b:2c:b3:e4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Memory:faffc000-faffe000 

eth0:avahi Link encap:Ethernet  HWaddr 00:0d:56:32:37:a4  
          inet addr:169.254.5.96  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:91844 (89.6 KB)  TX bytes:91844 (89.6 KB)
```

```

matt@matt-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      No scan results

eth0      Interface doesn't support scanning.

```

```

matt@matt-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

```

Thanks for putting in so much time and effort JW!

Hmm... well the interface appears to be coming up ok, weird that it's still eth1, mine changed from eth1 to wlan0 with the Hardy upgrade, is there something interesting in your /etc/network/interfaces?

Lets take a look at what happens when you try and load the modules. So try running:
```
sudo rmmod b44 b43 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
dmesg | tail -n25
```

And post the eventual output up here (or have a look at it yourself and see if it sheds any light on what happens when you're reloading the modules).

---

### Post by hmhmhm on 2008-04-30
Hi and thanks for the tutorial.
Unfortunately it doesn't seem to work for me. I use a Compaq Presario C700 and I follow your steps straight after the installation of Hardy has finished. Everything seems to go ok (no error messages) but when I click on the network icon, I don't even get a wireless option.
This is the output:

```
user@hmcompaq804:~$ lspci -nn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)
user@hmcompaq804:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
user@hmcompaq804:~$ lsmod | grep b43
user@hmcompaq804:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
user@hmcompaq804:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 306 2008-04-23 03:49 /etc/rc.local
user@hmcompaq804:~$ 

```

Thanks for your help!

---

### Post by jw5801 on 2008-04-30
> **hmhmhm said:**
> Hi and thanks for the tutorial.
Unfortunately it doesn't seem to work for me. I use a Compaq Presario C700 and I follow your steps straight after the installation of Hardy has finished. Everything seems to go ok (no error messages) but when I click on the network icon, I don't even get a wireless option.
This is the output:

```
user@hmcompaq804:~$ lspci -nn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)
user@hmcompaq804:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
user@hmcompaq804:~$ lsmod | grep b43
user@hmcompaq804:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  6 ndiswrapper,usb_storage,libusual,ehci_hcd,uhci_hcd
user@hmcompaq804:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 306 2008-04-23 03:49 /etc/rc.local
user@hmcompaq804:~$ 

```

Thanks for your help!

Ok, what's in the following files (run the commands and post back)
```
cat /etc/rc.local
cat /etc/modules
```

And what happens when you run:
```
sudo rmmod b44 b43 ssb ndiswrapper
sudo modprobe ndiswrapper
```
Does that switch the light on? If you don't have a light or aren't sure, run:
```
iwlist scan
```
And it should show you whether your wireless interface got set up.

---

### Post by hmhmhm on 2008-04-30
Thank you for the super-fast reply.
I entered line by line what you said and as soon as I enter
> sudo modprobe ndiswrapper
it all of a sudden works (yes!!!)

Is it somehow possible to make this work on start-up, too?

Here is the requested output, just in case it is required:

> user@hmcompaq804:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
user@hmcompaq804:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
ndiswrapper
user@hmcompaq804:~$ sudo rmmod b44 b43 ssb ndiswrapper
[sudo] password for user: 
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
user@hmcompaq804:~$ sudo modprobe ndiswrapper
user@hmcompaq804:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:BD:9F:54
                    ESSID:"wireless"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

user@hmcompaq804:~$ 


---

### Post by jw5801 on 2008-04-30
> **hmhmhm said:**
> Thank you for the super-fast reply.
I entered line by line what you said and as soon as I enter

it all of a sudden works (yes!!!)

Is it somehow possible to make this work on start-up, too?

Here is the requested output, just in case it is required:

Ok, firstly I'll apologize, I've changed the How-To on you! I had made an assumption which turned out to be false.

Anyway, open up /etc/modules:
```
gksudo gedit /etc/modules
```
And remove the line that says "ndiswrapper"

Secondly open up /etc/rc.local:
```
gksudo gedit /etc/rc.local
```
And just before the "exit 0" add the following lines:
```
rmmod ssb
modprobe ndiswrapper
```

That should automate the process during boot.

---

### Post by hmhmhm on 2008-04-30
No need to apologize. It works like a charm now. Thank you so much!!!

---

### Post by Freakeomi on 2008-04-30
I have been trying to get this to work all weekend, and I saw the old thread and didn't see this one, I tried a different method on my E1505 and ran into a problem. 

I had done the method where you install windows gui drivers (can't remember the exact name since I am not on my machine at the moment), I downloaded and used the drivers R151517.EXE from dell's site.  I rebooted it asked to update the b43 and rebooted again after.  My wireless would work, then suddenly it would drop connection, Should I go back and try this method? Or maybe use a different program for my wireless connection? Thanks (I don't get any errors, connection just suddenly stops so I don't have anything to copy/paste, sorry :-( )

---

### Post by quill7111 on 2008-04-30
I realized after posting that I had discovered that a module called b43legacy was being loaded which was using ssb and preventing it from being unloaded. I blacklisted both b43 and b43legacy (although google told me that only one of the two would be used). The outputs from my previous post were all with the rc.local changes from the howto and with both b43 and b43legacy blacklisted. With only b43 blacklisted, I get the following:

```

matt@matt-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1814 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90860 (88.7 KB)  TX bytes:90860 (88.7 KB)

matt@matt-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

eth1      No scan results

matt@matt-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

```

Here's my network interfaces file
```

matt@matt-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

```

Here's the output for the commands you suggested in your recent post, which illustrate the b43legacy issue (which reminded me why I had blacklisted it).
```

matt@matt-laptop:~$ sudo rmmod b44 b43 ssb ndiswrapper
[sudo] password for matt: 
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module ssb is in use by b43legacy
ERROR: Module ndiswrapper does not exist in /proc/modules
matt@matt-laptop:~$ sudo modprobe ndiswrapper
matt@matt-laptop:~$ sudo modprobe b44
matt@matt-laptop:~$ dmesg | tail -n25
[   54.615583] [drm] Initialized drm 1.1.0 20060810
[   54.639161] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   54.639170] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   54.639424] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   55.057939] ppdev: user-space parallel port driver
[   55.292387] audit(1209567184.327:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5197 profile="/usr/sbin/cupsd" namespace="default"
[   55.373888] apm: BIOS not found.
[   55.751720] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   55.751731] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[   55.928206] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   55.928233] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   55.928270] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   57.295865] [drm] Setting GART location based on new memory map
[   57.295920] [drm] writeback test succeeded in 1 usecs
[   57.800853] NET: Registered protocol family 10
[   57.801976] lo: Disabled Privacy Extensions
[   57.804083] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   59.280706] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[  616.397554] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  616.423459] usbcore: registered new interface driver ndiswrapper
[  625.299443] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[  625.358009] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[  625.358051] b44.c:v2.0
[  625.379294] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:32:37:a4
[  625.543959] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

Here's another try with removing both b43 and b43legacy. After running these commands, the gnome network manager was able to see my wireless network, but neither my wired nor wireless interfaces could establish a connection. 
```

matt@matt-laptop:~$ sudo rmmod b44 b43 b43legacy ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
matt@matt-laptop:~$ sudo modprobe ndiswrapper
matt@matt-laptop:~$ sudo modprobe b44
matt@matt-laptop:~$ dmesg | tail -n25
[  616.397554] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  616.423459] usbcore: registered new interface driver ndiswrapper
[  625.299443] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[  625.358009] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[  625.358051] b44.c:v2.0
[  625.379294] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:32:37:a4
[  625.543959] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  802.055880] ACPI: PCI interrupt for device 0000:02:01.0 disabled
[  802.185821] ACPI: PCI interrupt for device 0000:02:02.0 disabled
[  802.195829] usbcore: deregistering interface driver ndiswrapper
[  818.552304] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  819.073927] ndiswrapper: driver bcmwl5 (Broadcom,02/10/2005, 3.100.35.1) loaded
[  819.075225] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[  819.087312] ndiswrapper: using IRQ 11
[  819.521698] wlan0: ethernet device 00:90:4b:2c:b3:e4 using NDIS driver: bcmwl5, version: 0x3642301, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4320.5.conf
[  819.523504] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  819.524774] usbcore: registered new interface driver ndiswrapper
[  819.527626] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[  819.527745] udev: renamed network interface wlan0 to eth1
[  819.563682] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  832.084397] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKB] -> GSI 7 (level, low) -> IRQ 7
[  832.141201] ssb: Sonics Silicon Backplane found on PCI device 0000:02:01.0
[  832.141237] b44.c:v2.0
[  832.162481] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:0d:56:32:37:a4
[  832.325295] ADDRCONF(NETDEV_UP): eth0: link is not ready

```

I'm pretty confounded. I'm almost tempted to think this is also related to the gnome network manager, so I think I'll try wicd and see if that helps.

---

### Post by Cinnander on 2008-04-30
Hi! Thanks a lot for this guide :)
I'd been staring into a terminal for most of the afternoon, and firefox was choking under the weight of so many tabs open while I tried to fix this.

It *definitely* works so much better on a fresh install -- if you have /home on a separate partition reinstalling is a fairly trivial task so I can't recommend that enough.

My laptop is a **Dell Inspiron 1300** so slightly different -- the card is a **4318**, ```
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

And I used a different driver pack from HP. Despite not being Dell drivers, it works. I suspect the exact Dell driver pack for this laptop and card (R115321) would work too.

I've tried this so many times this afternoon that I can't figure out why this guide worked and all the other similar ones didn't, heh :)

-x-

The driver pack I used was: **[ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)** (4.2M)
I found it on [this list](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/).

This can be extracted using cabextract, instead of unzip:
```

(make working dir + cd to it)
...
sudo apt-get -y install cabextract
wget ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe
cabextract sp33008.exe
...
(install ndiswrapper, etc)
```

---

### Post by quill7111 on 2008-04-30
So I installed wicd and now neither my wired nor wireless will connect. Weak. Probably shouldn't have introduced another variable. I've tried wicd's one troubleshooting suggestion of limiting the /etc/network/interfaces file to this:
```

auto lo
iface lo inet loopback

```
and it didn't help. I ran through all the howto steps again just to make sure, but still nothing. 
This raises the further problem of not being able to reinstall network-manager since I did the upgrade and don't have a Hardy cd or any blank cds. 
Cinnander, this has definitely been an inspiration to put my /home folders on separate partitions on all my machines. I had high hopes for the upgrade option, and it's a great idea in theory, but a fresh install would be pretty nice right now.

*EDIT 
After following all the howto steps and rebooting then refreshing the network list in wicd it was able to see my wireless network, but it still won't recognize the wired connection or actually connect to the wireless network. The similar behavior of network-manager and wicd seem to confirm that the problem lies elsewhere.

---

### Post by jw5801 on 2008-04-30
> **quill7111 said:**
> So I installed wicd and now neither my wired nor wireless will connect. Weak. Probably shouldn't have introduced another variable. I've tried wicd's one troubleshooting suggestion of limiting the /etc/network/interfaces file to this:
```

auto lo
iface lo inet loopback

```
and it didn't help. I ran through all the howto steps again just to make sure, but still nothing. 
This raises the further problem of not being able to reinstall network-manager since I did the upgrade and don't have a Hardy cd or any blank cds. 
Cinnander, this has definitely been an inspiration to put my /home folders on separate partitions on all my machines. I had high hopes for the upgrade option, and it's a great idea in theory, but a fresh install would be pretty nice right now.

*EDIT 
After following all the howto steps and rebooting then refreshing the network list in wicd it was able to see my wireless network, but it still won't recognize the wired connection or actually connect to the wireless network. The similar behavior of network-manager and wicd seem to confirm that the problem lies elsewhere.

Thanks for the heads up on b43legacy, I'll add that to be blacklisted as well.

Ok, well it appears as though everything is loading nicely and you card is being recognised and finding networks, so the scope of this how-to appears to have been met. Maybe try disabling any encryption you have on the wireless and connecting?

As for the wired try adding to your /etc/network/interfaces:
```
iface eth0 inet dhcp
     pre-up modprobe b44
     post-down rmmod b44 ssb
```
Then you can bring your wired interface up, and take it down with:
```
sudo ifup eth0 #to bring up
sudo ifdown eth0 #to take down
```
I like that approach because it means you can remove the "modprobe b44" from rc.local, and you're only using the ethernet card at all when you want it up, good from a power management perspective.

---

### Post by jw5801 on 2008-04-30
> **Freakeomi said:**
> I have been trying to get this to work all weekend, and I saw the old thread and didn't see this one, I tried a different method on my E1505 and ran into a problem. 

I had done the method where you install windows gui drivers (can't remember the exact name since I am not on my machine at the moment), I downloaded and used the drivers R151517.EXE from dell's site.  I rebooted it asked to update the b43 and rebooted again after.  My wireless would work, then suddenly it would drop connection, Should I go back and try this method? Or maybe use a different program for my wireless connection? Thanks (I don't get any errors, connection just suddenly stops so I don't have anything to copy/paste, sorry :-( )

ndisgtk? Something like that anyway.

If it's installing b43 bits and pieces that means you haven't blacklisted b43 properly, have a look at /etc/modprobe.d/blacklist(gksudo gedit /etc/modprobe.d/blacklist) and make sure there's the following two lines there:
```
blacklist b43
blacklist b43legacy
```

You can check if the module has been loaded with:
```
lsmod | grep b43
```
If it has been, the following should get you working (provided the rest of the ndiswrapper install went correctly):
```
sudo rmmod b43 b44 ssb
sudo modprobe ndiswrapper
```

---

### Post by Freakeomi on 2008-04-30
Thanks for the quick response, I tried to redo everything exactly as listed and added 
> If it's installing b43 bits and pieces that means you haven't blacklisted b43 properly, have a look at /etc/modprobe.d/blacklist(gksudo gedit /etc/modprobe.d/blacklist) and make sure there's the following two lines there:
Code:

blacklist b43
blacklist b43legacy

You can check if the module has been loaded with:
Code:

lsmod | grep b43

If it has been, the following should get you working (provided the rest of the ndiswrapper install went correctly):
Code:

sudo rmmod b43 b44 ssb
sudo modprobe ndiswrapper

This didn't work still, I kept the items on Blacklist and what happened was my normal network card doesn't show up anymore and the wireless card under System --> admin --> network.  I went into System --> admin --> Windows Wireless Drivers and loaded the .inf file and the wireless started working, but I still do not see the network card, also upon reboot, I'd have to go into Windows Wireless Drivers again, uninstall the driver and reinstall it. :-(

---

### Post by jw5801 on 2008-04-30
> **Freakeomi said:**
> Thanks for the quick response, I tried to redo everything exactly as listed and added 


This didn't work still, I kept the items on Blacklist and what happened was my normal network card doesn't show up anymore and the wireless card under System --> admin --> network.  I went into System --> admin --> Windows Wireless Drivers and loaded the .inf file and the wireless started working, but I still do not see the network card, also upon reboot, I'd have to go into Windows Wireless Drivers again, uninstall the driver and reinstall it. :-(

Try following the how-to and use it's method. If it's not working until you reload ndiswrapper, then something in /etc/rc.local or /etc/modules is wrong.

---

### Post by jw5801 on 2008-05-02
If anyone is curious, I have found a much more graceful solution to this issue, it does however remove a small amount of "functionality" from the bootup process. I'm also debating whether to alter the how-to to use this method, as it does present an opportunity for people to put their system in an unbootable state.

The reason 'ssb' gets loaded (even if we blacklist it) and is able to take control of our WiFi card, is because it is contained in the initramfs. That is, the initial RAM image that gets loaded by Grub so that the kernel can have modules available to it immediately. Now, the reason 'ssb' is in the initramfs, is because 'b44' is in the initramfs and 'ssb' is a dependency of 'b44'. 'b44' is there in case you ever want to do a network boot over ethernet, in other words, so the eth0 interface can be up and working before any other boot scripts are run, so that everything else can be booted up from a remote network location. Now, this sort of feature is immensely important in a large scale office/university situation, but really not necessary at all for a regular Joe. *Especially* not on a laptop.

So, the more graceful solution is to remove 'b44' (and thus 'ssb') from our initramfs by doing the following:
```
gksudo gedit /etc/initramfs-tools/initramfs.conf
```
Scroll down to the section that looks like the following:
```
#
# DEVICE: ...
#
# Specify the network interface, like eth0
#

DEVICE=eth0
```
And change the eth0 to an lo:
```
DEVICE=lo
```

Then you'll need to update your initramfs:```
sudo update-initramfs -u
```

Now remove the lines we put in /etc/rc.local:```
gksudo gedit /etc/rc.local
```And remove everything other than the "exit 0".

And finally add ndiswrapper to /etc/modules:```
gksudo gedit /etc/modules
```
and add a line that contains only "ndiswrapper" at the bottom.

Then reboot and *hopefully* your WiFi light will still come one, but much earlier than it did using the previous solution.

I'm unsure whether this will work on unaltered systems, I rarely use my ethernet interface so I have it set up to not load automatically, but to load the modules it needs ('b44' and the nasty 'ssb') when I bring it up, and to unload them when I take it down.

If someone (who is competent enough to undo what is done above and return to the how-to method should it fail) wants to test this for me that would be fantastic. I think I will leave the how-to as is, using the brute force method, for now.

---

### Post by kevdog on 2008-05-03
Very interesting find about the initramfs -- in fact i learned a lot.  However there may be some consequences of removing the ssb module and not reloading it if a USB module depends on ssb.  Again I think some logic is going to have to be employed for a solution.

Just curious about the initramfs -- if you dont have a broadcom wired nic card -- is the ssb module loaded?  Isnt the module only loaded after a hardware detection sequence has finished?

---

### Post by Fernanddo Saenz on 2008-05-03
For davidefergnani: It seems that you just mis-typed the first command. You typed "lscpi", but it should be "lspci" ... That's why you got a "command not found" message.

---

### Post by jw5801 on 2008-05-03
> **kevdog said:**
> Very interesting find about the initramfs -- in fact i learned a lot.  However there may be some consequences of removing the ssb module and not reloading it if a USB module depends on ssb.  Again I think some logic is going to have to be employed for a solution.

Just curious about the initramfs -- if you dont have a broadcom wired nic card -- is the ssb module loaded?  Isnt the module only loaded after a hardware detection sequence has finished?

I use a USB mouse and have an external harddrive permanently attached when I'm at home, as well as a couple of flash drives I use when I'm out and about, so far none of them have required ssb (the mouse uses the ohci_hcd, the harddrive uses usb_storage, I think, both of which use usbcore). I have it blacklisted at the moment along with b44 and b43, I might try unblacklisting ssb and seeing if it still loads. I think if another module needed it it would still be loaded regardless of blacklisting wouldn't it? I'm not sure.

I'll keep b44 blacklisted, I'm loading it and unloading it with pre-up and post-down commands in /etc/network/interfaces (I rarely ever use the interface). Although I think I'll need to verify at what stage b44 gets loaded if it's not blacklisted to see whether ndiswrapper is called prior.

As for systems without a broadcom wired nic, I honestly have no idea. If anyone has a broadcom wireless nic but a different wired nic and wants to have a play around with it, I'd be most curious to find out! I'm thinking it probably wouldn't be loaded in the initramfs, but it possibly is still loaded during boot.

---

### Post by quill7111 on 2008-05-05
> **jw5801 said:**
> 
I'm unsure whether this will work on unaltered systems, I rarely use my ethernet interface so I have it set up to not load automatically, but to load the modules it needs ('b44' and the nasty 'ssb') when I bring it up, and to unload them when I take it down.

If someone (who is competent enough to undo what is done above and return to the how-to method should it fail) wants to test this for me that would be fantastic. I think I will leave the how-to as is, using the brute force method, for now.

Well, after the initramfs.conf changes, b44 and thus ssb are still loading at startup for me.
```

matt@matt-laptop:~$ lsmod | grep b44
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44

```

 and thus my wireless card remains unavailable.

```

matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:32:37:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89360 (87.2 KB)  TX bytes:89360 (87.2 KB)

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Given my problems with the brute-force howto as well, I think it's time for a clean install in the next few days. After that I'll retest both the regular howto as well as the initramfs.conf method again and hopefully get some better restults. If not, I guess it's back to Gutsy for me.

---

### Post by jw5801 on 2008-05-05
> **quill7111 said:**
> Well, after the initramfs.conf changes, b44 and thus ssb are still loading at startup for me.
```

matt@matt-laptop:~$ lsmod | grep b44
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44

```

 and thus my wireless card remains unavailable.

```

matt@matt-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:32:37:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:7 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:89360 (87.2 KB)  TX bytes:89360 (87.2 KB)

matt@matt-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

Given my problems with the brute-force howto as well, I think it's time for a clean install in the next few days. After that I'll retest both the regular howto as well as the initramfs.conf method again and hopefully get some better restults. If not, I guess it's back to Gutsy for me.

Yeah, I have a funny feeling that networking is brought up before /etc/modules is read, which means your eth0 would still be brought up, thus loading b44 and ssb. I have b44 and ssb blacklisted, as well as having eth0 not be auto, which explains why it still works so well for me. You could always try adding ndiswrapper to the initramfs (add ndiswrapper to /etc/initramfs-tools/modules). That would be my next attempt.

It would definitely appear that the How-To method, is by far the most robust solution to this issue.

---

### Post by tvs on 2008-05-06
I've upgraded from Gutsy and it didn't work for me (in Gutsy the wireless worked perfectly). 

Also, the lines you add in /etc/rc.local unconfigures my lan!! (eth0 loses its IP).

BTW, I have a Dell 1505n

---

### Post by jw5801 on 2008-05-06
> **tvs said:**
> I've upgraded from Gutsy and it didn't work for me (in Gutsy the wireless worked perfectly). 

Also, the lines you add in /etc/rc.local unconfigures my lan!! (eth0 loses its IP).

BTW, I have a Dell 1505n

That's the point... your wired card uses the b44 module, which loads the ssb module which prevents your wireless card from working. Thus, we need to unload it and 'unconfigure your LAN' if we want to be able to use wireless.

---

### Post by Larss on 2008-05-08
Okay, have tried this guide several times now, but it just won't work. Even did a fresh install, but still no luck. I get the wireless option in the network-manager in the notification area, but there are none wireless networks in the "Wireless Networks"-list. The wifi-light isn't on either (edit: and doesn't come on with -> sudo rmmod b44 b43 ssb ndiswrapper -> sudo modprobe ndiswrapper). Could it be a problem with my wifi-card (it worked perfectly two days ago in gutsy, but no luck in hardy heron)? Any idea what else could it be? Kinda new to ubuntu, so try to keep it neewbie-friendly =)

Thanks for any help.

Troubleshooting (same before and after a reboot):
```

lars@lars-laptop:~$ lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

lars@lars-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

lars@lars-laptop:~$ lsmod | grep b43

lars@lars-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd

lars@lars-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 373 2008-05-08 13:37 /etc/rc.local

lars@lars-laptop:~$ cat /etc/rc.local
#!/bin/sh -e
# (...)
# By default this script does nothing.
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
exit 0

```

edit:
```

lars@lars-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

lars@lars-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:88:49:99  
          inet addr:129.241.150.129  Bcast:129.241.151.255  Mask:255.255.254.0
          inet6 addr: 2001:700:303:f:219:b9ff:fe88:4999/64 Scope:Global
          inet6 addr: fe80::219:b9ff:fe88:4999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2531715 (2.4 MB)  TX bytes:76143 (74.3 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74500 (72.7 KB)  TX bytes:74500 (72.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:c7:6d:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efdfc000-efe00000 


```

edit2:
```

lars@lars-laptop:~$ sudo rmmod b44 b43 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
lars@lars-laptop:~$ sudo modprobe ndiswrapper
lars@lars-laptop:~$ sudo modprobe b44
lars@lars-laptop:~$ dmesg | tail -n25
[  841.132949] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  844.815180] b44: eth0: Link is up at 100 Mbps, full duplex.
[  844.815186] b44: eth0: Flow control is off for TX and off for RX.
[  844.817170] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1073.123963] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 1071.191752] ndiswrapper: device wlan0 removed
[ 1071.191781] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 1071.191895] usbcore: deregistering interface driver ndiswrapper
[ 1080.643705] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1080.655142] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 1080.656304] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 1080.656991] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[ 1080.664352] ndiswrapper: using IRQ 16
[ 1080.864998] wlan0: ethernet device 00:19:7e:c7:6d:d2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 1080.865248] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1078.865021] usbcore: registered new interface driver ndiswrapper
[ 1080.891256] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1087.130917] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
[ 1085.167618] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 1085.167655] b44.c:v2.0
[ 1085.188383] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:88:49:99
[ 1085.250180] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1088.815796] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1088.815806] b44: eth0: Flow control is off for TX and off for RX.
[ 1088.819917] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

---

### Post by wlee618 on 2008-05-08
[CENTER]it is working!!!! i .. love.. you.. you are awesome!!!  i think this problem is with many laptop users.  i say please goto page 1 and follow the original instruction.  wifi works like c charm.  i even try to reboot... the wifi works just like that after reboot.  no need to do any further tweaking.

i am once again a very happy camper.. [/CENTER]

---

### Post by jw5801 on 2008-05-08
> **Larss said:**
> Okay, have tried this guide several times now, but it just won't work. Even did a fresh install, but still no luck. I get the wireless option in the network-manager in the notification area, but there are none wireless networks in the "Wireless Networks"-list. The wifi-light isn't on either (edit: and doesn't come on with -> sudo rmmod b44 b43 ssb ndiswrapper -> sudo modprobe ndiswrapper). Could it be a problem with my wifi-card (it worked perfectly two days ago in gutsy, but no luck in hardy heron)? Any idea what else could it be? Kinda new to ubuntu, so try to keep it neewbie-friendly =)

Thanks for any help.

Troubleshooting (same before and after a reboot):
```

lars@lars-laptop:~$ lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

lars@lars-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

lars@lars-laptop:~$ lsmod | grep b43

lars@lars-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd

lars@lars-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 373 2008-05-08 13:37 /etc/rc.local

lars@lars-laptop:~$ cat /etc/rc.local
#!/bin/sh -e
# (...)
# By default this script does nothing.
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
exit 0

```

edit:
```

lars@lars-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

lars@lars-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:88:49:99  
          inet addr:129.241.150.129  Bcast:129.241.151.255  Mask:255.255.254.0
          inet6 addr: 2001:700:303:f:219:b9ff:fe88:4999/64 Scope:Global
          inet6 addr: fe80::219:b9ff:fe88:4999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2531715 (2.4 MB)  TX bytes:76143 (74.3 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74500 (72.7 KB)  TX bytes:74500 (72.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:c7:6d:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efdfc000-efe00000 


```

edit2:
```

lars@lars-laptop:~$ sudo rmmod b44 b43 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
lars@lars-laptop:~$ sudo modprobe ndiswrapper
lars@lars-laptop:~$ sudo modprobe b44
lars@lars-laptop:~$ dmesg | tail -n25
[  841.132949] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  844.815180] b44: eth0: Link is up at 100 Mbps, full duplex.
[  844.815186] b44: eth0: Flow control is off for TX and off for RX.
[  844.817170] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1073.123963] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 1071.191752] ndiswrapper: device wlan0 removed
[ 1071.191781] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 1071.191895] usbcore: deregistering interface driver ndiswrapper
[ 1080.643705] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 1080.655142] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 1080.656304] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 1080.656991] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[ 1080.664352] ndiswrapper: using IRQ 16
[ 1080.864998] wlan0: ethernet device 00:19:7e:c7:6d:d2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 1080.865248] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1078.865021] usbcore: registered new interface driver ndiswrapper
[ 1080.891256] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1087.130917] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 22
[ 1085.167618] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[ 1085.167655] b44.c:v2.0
[ 1085.188383] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:19:b9:88:49:99
[ 1085.250180] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1088.815796] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1088.815806] b44: eth0: Flow control is off for TX and off for RX.
[ 1088.819917] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

```

Ok, well the driver install has gone fine, so redoing the how-to ain't going to help. Loading ndiswrapper all works fine. Given the line about "wlan0: link is not ready" and the fact your WiFi light isn't coming on, I'm inclined to thing that the card is being disabled somewhere. Have a look in your bios, there's almost certainly a setting about WiFi, either disabling/enabling a hotkey, or something similar. Also, if you have a WiFi hotkey, it wouldn't hurt to try it. On most Dells it's Fn+F2.

---

### Post by SidStudios on 2008-05-08
> **davidefergnani said:**
> i followed all the instructions but the wireless card is not workin yet.
I have a Hp pavillion dv9410us with hardy 64 bit
My card is a [14e4:4311] (rev 02).
this is the result of the command in the troubleshooting section:


davidefergnani@davidefergnani-laptop:~$ lscpi -nn | grep 14e4
bash: lscpi: command not found
davidefergnani@davidefergnani-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
davidefergnani@davidefergnani-laptop:~$ lsmod | grep b43
davidefergnani@davidefergnani-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,uvcvideo,ohci_hcd,ehci_hcd
davidefergnani@davidefergnani-laptop:~$ ls -l /etc/rc.local



i dont understand why is not working. i followed all the instructions
You're a dolt. Sorry, but you typed in "lscpi" instead of "lspci".

---

### Post by Larss on 2008-05-08
> **jw5801 said:**
> Ok, well the driver install has gone fine, so redoing the how-to ain't going to help. Loading ndiswrapper all works fine. Given the line about "wlan0: link is not ready" and the fact your WiFi light isn't coming on, I'm inclined to thing that the card is being disabled somewhere. Have a look in your bios, there's almost certainly a setting about WiFi, either disabling/enabling a hotkey, or something similar. Also, if you have a WiFi hotkey, it wouldn't hurt to try it. On most Dells it's Fn+F2.

It's the wierdest thing. I've hit Fn+F2 many hundred times the last two days, and I did the same thing like 10 times now and suddenly the light came on and the wireless works perfectly! Thanks for the help! :)

---

### Post by jw5801 on 2008-05-08
> **Larss said:**
> It's the wierdest thing. I've hit Fn+F2 many hundred times the last two days, and I did the same thing like 10 times now and suddenly the light came on and the wireless works perfectly! Thanks for the help! :)

Haha, yeah it'll do that!

---

### Post by jw5801 on 2008-05-08
> **SidStudios said:**
> You're a dolt. Sorry, but you typed in "lscpi" instead of "lspci".

lspci is only a diagnosis tool, so it's not going to make anything start working. Also, I had that typo in the how-to for about a week before I corrected it, so please keep the insults to a minimum!

---

### Post by NMambre on 2008-05-09
I am using Ubuntu Ultimate Edition 1.8 64bit, based on Hardy. 

Paperdiesel's tutorial worked for UUE 1.7 32bit, so I tried it yesterday without luck. After that I found your tutorial.
Two things: in the code you put R151519.EXE but the link you put below that points to R151517.EXE. I guess both should work, but I´m not sure. I already had R151517.EXE and used it in this tutorial, but maybe I didn´t clean everything (ndiswrapper etc) so maybe that´s why it didn´t work the first. Then I just followed every single step of the tutorial, and after rebooting, I had wifi working.


The other thing is that this time I had to reboot, modprobe didn´t help. In In 1.7 I didn´t need to reboot.

Thankz a lot.

---

### Post by jw5801 on 2008-05-09
> **NMambre said:**
> I am using Ubuntu Ultimate Edition 1.8 64bit, based on Hardy. 

Paperdiesel's tutorial worked for UUE 1.7 32bit, so I tried it yesterday without luck. After that I found your tutorial.
Two things: in the code you put R151519.EXE but the link you put below that points to R151517.EXE. I guess both should work, but I´m not sure. I already had R151517.EXE and used it in this tutorial, but maybe I didn´t clean everything (ndiswrapper etc) so maybe that´s why it didn´t work the first. Then I just followed every single step of the tutorial, and after rebooting, I had wifi working.


The other thing is that this time I had to reboot, modprobe didn´t help. In In 1.7 I didn´t need to reboot.

Thankz a lot.

No idea why you should need to reboot, but all's well that ends well! R151519 is essentially the same as R151517, just an updated version, I find it is a little more stable, but R151517 works just as well.

---

### Post by bardu0708 on 2008-05-10
Hei,
Your guide got me further than all of the other ones but I still run into a problem with the driver.
I don't have the one specified in your guide but it's similar and I found xp drivers here: [http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php](http://zh-tw.broadcom.com/support/ethernet_nic/netlink.php)

Because I don't have a clue which one is the right one I just tried all three of them but the b57win32 seems to be the right one (the IA64 one simply stated: driver installed, and the other 64 one stated: driver malfunction or something like that).

The information below states that there is an alternate driver, should I blacklist that one and if so how to? Thanks in advance.

osiris@osiris-laptop:~$ lspci -nn | grep 14e4 
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02) 
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02) 

osiris@osiris-laptop:~$ ndiswrapper -l 
b57win32 : driver installed 
	device (14E4:1693) present (alternate driver: tg3) 

lsmod | grep b57
lsmod 1 grep ndiswrapper

Won't give me anything, neither when I give the command using sudo lsmod....

(I haven't blacklisted anything because it's a fresh install, but just because you asked for it)
osiris@osiris-laptop:~$ ls -l /etc/rc.local 
-rwxr-xr-x 1 root root 306 2008-04-22 19:49 /etc/rc.local

---

### Post by bardu0708 on 2008-05-10
I just realised something, should I get a driver for the 
Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693]
or should I install a driver for the
Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312]
?

(I'm a total newbie at computer things)

---

### Post by jw5801 on 2008-05-11
> **bardu0708 said:**
> I just realised something, should I get a driver for the 
Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693]
or should I install a driver for the
Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312]
?

(I'm a total newbie at computer things)

The second one! The first one is your ethernet (wired) interface and is almost certainly supported out of the box. For the 4312 you can have a try with this driver [here](ftp://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe), follow the same instructions to extract it, and look for the bcmwl5.inf. Everything else should be the same (blacklisting b43 and creating a file to load ndiswrapper properly on bootup).

EDIT: The list of cards supported by NDISwrapper can be found here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by bardu0708 on 2008-05-11
Thanks a lot for your help,

But now I get the following problem:
[I]osiris@osiris-laptop:~/wireless-install$ unzip SP33008.EXE -d SP33008/ 
Archive:  SP33008.EXE 
  End-of-central-directory signature not found.  Either this file is not 
  a zipfile, or it constitutes one disk of a multi-part archive.  In the 
  latter case the central directory and zipfile comment will be found on 
  the last disk(s) of this archive. 
note:  SP33008.EXE may be a plain executable, not an archive 
unzip:  cannot find zipfile directory in one of SP33008.EXE or 
        SP33008.EXE.zip, and cannot find SP33008.EXE.ZIP, period. [/I]
(It's a driver I found at the site you gave me)

---

### Post by bardu0708 on 2008-05-11
I know I missed the '-a' in the command, but it doesn't really matter, tried it again:

[I]osiris@osiris-laptop:~/wireless-install$ unzip -a SP33008.EXE -d SP33008/
Archive:  SP33008.EXE
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  SP33008.EXE may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of SP33008.EXE or
        SP33008.EXE.zip, and cannot find SP33008.EXE.ZIP, period.
[/I]

---

### Post by srdempster on 2008-05-11
> **jw5801 said:**
> This How-To describes how to get WiFi working with the Broadcom 1390 WLAN offered in many Dell and HP laptops using ndiswrapper. Many of us use ndiswrapper as an alternative to the native drivers (b43), as we feel the native drivers have not quite reached a point where they compare with ndiswrapper, usually this relates to only being able to use 802.11b connections (11Mbps) as opposed to 802.11g (54Mbps).

The how-to has been tested and found to work on both AMD64 and i386 installs of Ubuntu Hardy Heron.

**THIS HOW-TO IS FOR UBUNTU HARDY HERON (8.04) ONLY.** The How-To is loosely based on Paperdiesel's How-To for earlier versions of Ubuntu which can be found [here](http://ubuntuforums.org/showthread.php?t=297092). If you are not running Hardy, then this How-To will not work. You should refer to [paperdiesel's How-To](http://ubuntuforums.org/showthread.php?t=297092).

[color=red]DISCLAIMER[/color] It's important to note that many people struggle to get wireless working simply because they have unsuccessfully tried a variety of methods and left their system in a shambles. If you've been playing around with alternative methods there's a good chance you won't be able to get this to work until you reverse any previous changes you may have made. It's perhaps best to come straight to this How-To after a fresh install.

To check that you have the same card that this how-to is written for, run the following command:
```
lspci -nn | grep 14e4
```
and you should see something similar to the following:
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI **[14e4:4311]** (rev 01)
```
The section in bold is the important part. If that part doesn't match then you will need a different driver to use with ndiswrapper. The how-to should still be valid however! If you don't have the same WiFi card, have a look at the list of supported cards [here](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/), and it should point you in the right direction for a driver to use.

**STEP 1: OBTAINING THE REQUIRED PACKAGES**
Thankfully, Hardy includes a new enough version of ndiswrapper to remove the need for installing it from source. This saves a lot of trouble during the install process.

For the install process I find it best to create a separate working directory to get all this done in. You can use whatever directory you'd like so long as you're consistent, if you're unsure copy the way I've done it. 

Most of the work from here on will be done from the command-line, so open up a terminal (Applications > Accessories > Terminal), and use it to create your working directory:
```
mkdir wireless-install
cd wireless-install
```

First we need to obtain the correct XP driver (Vista drivers WILL NOT WORK with ndiswrapper) for this chipset, and also install some extra packages. This is easy if you have access to the internet (via a wired connection or otherwise):
```
wget http://ftp.us.dell.com/network/R151519.EXE
```
_NOTE:_ If lspci above showed that you had a different chipset, this driver won't work. You're welcome to try using a different driver, however ndiswrapper is a temperamental thing, so I can't guarantee it will work with just any driver. A google search for the number relating to your card, ie. 14e4:4315 or 14e4:4318, and ndiswrapper should return a driver you can use quite quickly.

Next install ndiswrapper. The latest version is available from the Hardy repositories which is a rather nice change for those of us who are used to the need to recompile ndiswrapper on every kernel change!
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```

If you have no internet access on your Ubuntu machine then you'll need to get the appropriate driver from [here](http://ftp.us.dell.com/network/R151519.EXE) and copy it to your working directory (~/wireless-install). The packages can be installed from your trusty Hardy LiveCD (a Gutsy, or any other, LiveCD WILL NOT WORK): 
```
sudo mount /dev/cdrom /cdrom
sudo apt-cdrom add -m
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```


**STEP 2: PREVENTING THE NATIVE MODULES FROM INTERFERING WITH NDISWRAPPER**

**NOTE FOR ANYONE WHO IS NOT USING A FRESH INSTALL**
If you used ndiswrapper in Gutsy and upgraded directly to Hardy (or tried another method before coming here), odds are good that you'll have a line in the /etc/modules file that loads ndiswrapper, in order for this part of the how-to to work you'll need to remove that line:
```
gksudo gedit /etc/modules
```
And delete any line(s) that contain "ndiswrapper"
**END NOTE**

This process is not quite as simple as it has been in the past due to the different native modules and how they interact with each other. So firstly we're going to blacklist a few things by adding them to the /etc/modprobe.d/blacklist file:
```
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist
```
_NOTE:_ You can do this with a text editor, using "gksudo gedit /etc/modprobe.d/blacklist" for example. I like the fancy way because it means you can copy and paste just one command and removes the chance of typos.

We also need to add a bootscript to load a couple of modules in an order that suits us. The reason being that the ssb module takes control of our card, thus preventing ndiswrapper from controlling it, however ssb is required by the b44 driver, which handles wired broadcom cards, so we can't just blacklist it. If you would like (and know how to), you can easily use a new script to do this, however the easiest way I find is to add it to /etc/rc.local. To do this we need to edit the file:
```
gksudo gedit /etc/rc.local
```
Feel free to replace gedit with the text editor of your choice (kate, mousepad, emacs, nano, vi, bluefish, etc), then add the following to lines to the end of the script, just before the "exit 0":
```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
```

To give you an idea, my /etc/rc.local now looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
```


**STEP 3: INSTALLING THE DRIVER WITH NDISWRAPPER**

Now we're going to use the driver we downloaded from the Dell website (note that it doesn't matter if your laptop is not a Dell, this driver should still work if you have the same chipset) to give ndiswrapper all it needs to access our card:
```
cd ~/wireless-install/
unzip -a R151519.EXE -d R151519/
cd R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf
```
_NOTE:_ Make sure you use the right case, in Linux driver and Driver very different to DRIVER.
_NOTE II:_ For those of you who have funky fonts in the forum, the driver is a lower caps BCMWL5.inf. Some confusion has occurred as to whether the "L" is a "1" or an "I", hopefully that clarifies!

And that's it! You should be just a reboot away from having a working wireless card:
```
sudo shutdown -r now
```

If you'd like to verify it's working properly without the need for a reboot, try the following series of commands. If your laptop has a wifi-light it should light up after you "modprobe ndiswrapper".
```
sudo rmmod b43 b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```
_NOTE:_ This is essentially what the script we added to /etc/rc.local does, only that script doesn't need to remove the b43 module as it is blacklisted and should not be loaded to start with.


**CLEANING UP**

Once you're happy everything is working well, you can safely remove the working directory:
```
rm -r ~/wireless-install
```
Or you could keep it on hand for future reference!


**TROUBLESHOOTING**
If you have any trouble with the How-To or it doesn't work as expected please post in the thread. I check the thread quite often and I'm always happy to help. It's also possible there's something I've missed which I can then incorporate into the How-To for everyone else to benefit from. If you're posting seeking help, please include the outputs of the following commands:
```
lspci -nn | grep 14e4
ndiswrapper -l
lsmod | grep b43
lsmod | grep ndiswrapper
ls -l /etc/rc.local
```
as well as anything else you think is relevant. Please include long code outputs in ```
 tags (the # button in the advanced edit view) so they're easier to read.


**UNINSTALLING**

If for some reason you'd like to remove everything that this how-to has done, it's rather simple:
Undo the file changes we made:
[code]gksudo gedit /etc/modprobe.d/blacklist
# Remove the line we added: "blacklist b43"
gksudo gedit /etc/rc.local
# Remove the four modprobe lines we added
```

Remove the driver we told ndiswrapper to use:
```
sudo modprobe -r ndiswrapper
sudo ndiswrapper -e bcmwl5
```
Remove ndiswrapper:
```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils
```



Changelog:
21/04/08: Made minor clarifications to layout
22/04/08: Added Troubleshooting section
26/04/08: Added redundancy for users with no broadcom wired card
26/04/08: Added note for Gutsy upgraders
01/05/08: Added blacklist for b43legacy
10/05/08: Fixed old link
11/05/08: Added link to NDISwrapper wiki (list of supported cards).


These are my reports for trying the steps you've said but got nothing no light zilch.I run dell vostro 1000 with ubuntu 8.04

steve@steve-laptop:~$ lspci -nn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
steve@steve-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
steve@steve-laptop:~$ lsmod | grep b43
steve@steve-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           193564  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd
steve@steve-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 372 2008-05-11 20:08 /etc/rc.local
steve@steve-laptop:~$

Can you suggest anything?

Thanks Steve:confused:

---

### Post by jw5801 on 2008-05-11
> **bardu0708 said:**
> Thanks a lot for your help,

But now I get the following problem:
[I]osiris@osiris-laptop:~/wireless-install$ unzip SP33008.EXE -d SP33008/ 
Archive:  SP33008.EXE 
  End-of-central-directory signature not found.  Either this file is not 
  a zipfile, or it constitutes one disk of a multi-part archive.  In the 
  latter case the central directory and zipfile comment will be found on 
  the last disk(s) of this archive. 
note:  SP33008.EXE may be a plain executable, not an archive 
unzip:  cannot find zipfile directory in one of SP33008.EXE or 
        SP33008.EXE.zip, and cannot find SP33008.EXE.ZIP, period. [/I]
(It's a driver I found at the site you gave me)

Ah, sorry. I should have checked that shouldn't I? You'll need to use cabextract rather than unzip:
```
 cabextract SP33008.EXE -d SP33008/
```

---

### Post by jw5801 on 2008-05-11
> **srdempster said:**
> These are my reports for trying the steps you've said but got nothing no light zilch.I run dell vostro 1000 with ubuntu 8.04

steve@steve-laptop:~$ lspci -nn | grep 14e4
05:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
steve@steve-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
steve@steve-laptop:~$ lsmod | grep b43
steve@steve-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           193564  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd
steve@steve-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 372 2008-05-11 20:08 /etc/rc.local
steve@steve-laptop:~$

Can you suggest anything?

Thanks Steve:confused:

Well everything looks to be ok, what happens when you run the commands at the end:
```
sudo rmmod b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n30
sudo modprobe b44
```

Copy and paste the whole lot up to here.

---

### Post by srdempster on 2008-05-12
> **jw5801 said:**
> Well everything looks to be ok, what happens when you run the commands at the end:
```
sudo rmmod b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n30
sudo modprobe b44
```

Copy and paste the whole lot up to here.

steve@steve-laptop:~$ rmmod b43 b44 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
ERROR: Removing 'b44': Operation not permitted
ERROR: Module ssb is in use by b44
ERROR: Removing 'ndiswrapper': Operation not permitted
steve@steve-laptop:~$ sudo rmmod b43 b44 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
steve@steve-laptop:~$ sudo modprobe ndiswrapper
steve@steve-laptop:~$ dmesg | tail -n30
[  914.680278] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  914.685314] ndiswrapper: using IRQ 19
[  915.051633] wlan0: ethernet device 00:1d:d9:36:1b:c2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[  915.053311] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  915.076410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  915.077878] usbcore: registered new interface driver ndiswrapper
[  922.361729] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[  922.388553] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[  922.388581] b44.c:v2.0
[  922.398357] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:a0:8d:42
[  922.552085] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  925.804546] b44: eth0: Link is up at 100 Mbps, full duplex.
[  925.804551] b44: eth0: Flow control is off for TX and off for RX.
[  925.805279] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  946.162050] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  956.811485] wlan0: no IPv6 routers present
[ 1018.012393] eth0: no IPv6 routers present
[ 1077.898620] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[ 1077.967087] ndiswrapper: device wlan0 removed
[ 1077.967106] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[ 1077.967223] usbcore: deregistering interface driver ndiswrapper
[ 1089.923910] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[ 1089.938700] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 1089.939828] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[ 1089.939872] PCI: Setting latency timer of device 0000:05:00.0 to 64
[ 1089.945151] ndiswrapper: using IRQ 19
[ 1090.315393] wlan0: ethernet device 00:1d:d9:36:1b:c2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 1090.317073] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1090.340573] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1090.342219] usbcore: registered new interface driver ndiswrapper
steve@steve-laptop:~$ sudo modprobe b44

Now the funny thing was it did start to work at 54mbs then it now has stopped so I followed it all again and still nowt.It just shows the circling icon and shows waiting for wireless key but nowt.Rebooted router and still nowt, so if this reboot fails might try and re-enter network key in router.

Ta Steve

p.s. It connects if I amend the wireless profile from roaming to manual and then back again!!Every time it connects it keeps asking for the key as if it forgets it too if that helps!

---

### Post by jw5801 on 2008-05-12
> **srdempster said:**
> ```
steve@steve-laptop:~$ rmmod b43 b44 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
ERROR: Removing 'b44': Operation not permitted
ERROR: Module ssb is in use by b44
ERROR: Removing 'ndiswrapper': Operation not permitted
steve@steve-laptop:~$ sudo rmmod b43 b44 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules
steve@steve-laptop:~$ sudo modprobe ndiswrapper
steve@steve-laptop:~$ dmesg | tail -n30
[  914.680278] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  914.685314] ndiswrapper: using IRQ 19
[  915.051633] wlan0: ethernet device 00:1d:d9:36:1b:c2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[  915.053311] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  915.076410] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  915.077878] usbcore: registered new interface driver ndiswrapper
[  922.361729] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 21 (level, low) -> IRQ 21
[  922.388553] ssb: Sonics Silicon Backplane found on PCI device 0000:08:00.0
[  922.388581] b44.c:v2.0
[  922.398357] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:a0:8d:42
[  922.552085] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  925.804546] b44: eth0: Link is up at 100 Mbps, full duplex.
[  925.804551] b44: eth0: Flow control is off for TX and off for RX.
[  925.805279] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  946.162050] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  956.811485] wlan0: no IPv6 routers present
[ 1018.012393] eth0: no IPv6 routers present
[ 1077.898620] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[ 1077.967087] ndiswrapper: device wlan0 removed
[ 1077.967106] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[ 1077.967223] usbcore: deregistering interface driver ndiswrapper
[ 1089.923910] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[ 1089.938700] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 1089.939828] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 18 (level, low) -> IRQ 19
[ 1089.939872] PCI: Setting latency timer of device 0000:05:00.0 to 64
[ 1089.945151] ndiswrapper: using IRQ 19
[ 1090.315393] wlan0: ethernet device 00:1d:d9:36:1b:c2 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 1090.317073] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 1090.340573] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1090.342219] usbcore: registered new interface driver ndiswrapper
steve@steve-laptop:~$ sudo modprobe b44
```

Now the funny thing was it did start to work at 54mbs then it now has stopped so I followed it all again and still nowt.It just shows the circling icon and shows waiting for wireless key but nowt.Rebooted router and still nowt, so if this reboot fails might try and re-enter network key in router.

Ta Steve

p.s. It connects if I amend the wireless profile from roaming to manual and then back again!!Every time it connects it keeps asking for the key as if it forgets it too if that helps!

Ok, well everything in the How-To has worked correctly. This is an issue with how you're connecting to the access point. If it's waiting for wireless key it's waiting for your input. If you're really struggling I'd be inclined to turn off the encryption at the router entirely and see if you can connect then. If that works then turn it back on and have a play with different settings. kevdog's [thread](http://ubuntuforums.org/showthread.php?t=571188) is excellent for debugging network connections from the command line.

---

### Post by samborambo on 2008-05-13
Just a point worth noting....

If your laptop doesn't have a broadcom wired chipset, you shouldn't need the b44 module. This howto works on those laptops without a b44 chipset because the b44 module implies the ssb module. Just modprobe the ssb module instead of the b44 if this is the case.

Sam.

---

### Post by jw5801 on 2008-05-13
> **samborambo said:**
> Just a point worth noting....

If your laptop doesn't have a broadcom wired chipset, you shouldn't need the b44 module. This howto works on those laptops without a b44 chipset because the b44 module implies the ssb module. Just modprobe the ssb module instead of the b44 if this is the case.

Sam.

That's a fair point, I've left it the way it is to try and keep it as simple as possible. That and because I'm not entirely sure what would cause ssb to be loaded if b44 were not being loaded in the initramfs. I don't really want 5 different how-tos combined into one thread, it's long enough as is.

If you don't need b44 however, you can just blacklist b43, b43legacy and ssb, then add ndiswrapper to /etc/modules, there's no need for this annoying script to load things properly. I'm not entirely sure what ssb is used for, apparently it has something to do with USB, but I use many USB devices and I haven't encountered any other modules that need it for anything. It's a much nicer solution and it should help you be connected to a network by the time you reach your desktop (if the rest of it is set up nicely anyway) as it'll load ndiswrapper much earlier in the boot-up sequence.

---

### Post by lifeinoleg on 2008-05-13
> **tvs said:**
> I've upgraded from Gutsy and it didn't work for me (in Gutsy the wireless worked perfectly). 

Also, the lines you add in /etc/rc.local unconfigures my lan!! (eth0 loses its IP).

BTW, I have a Dell 1505n


I believe this post related to my problem, but I may be wrong.

I did the how-to and the wireless light came on perfectly(thank you). But when I restarted, my wired network(the one I usually use) did not start. So after a little scowling and fist-shaking I decided to try:

> 
sudo /etc/init.d/networking restart


...without knowing exactly what it does. But it seems to get my wired connection working. (previously, when I tried to connect to wired connection using wicd, it just kept searching for IP). Is there any less roundabout way to have my wired connection work on start-up than to paste the above commands in terminal every time?

Thanks.

---

### Post by jw5801 on 2008-05-13
> **lifeinoleg said:**
> I believe this post related to my problem, but I may be wrong.

I did the how-to and the wireless light came on perfectly(thank you). But when I restarted, my wired network(the one I usually use) did not start. So after a little scowling and fist-shaking I decided to try:



...without knowing exactly what it does. But it seems to get my wired connection working. (previously, when I tried to connect to wired connection using wicd, it just kept searching for IP). Is there any less roundabout way to have my wired connection work on start-up than to paste the above commands in terminal every time?

Thanks.

So wireless is working perfectly, but your wired interface doesn't come back up? Ok, reboot (don't bring up your wired card) and pass along some outputs (please use ```
 tags):
[code]lshw -C network
cat /etc/rc.local
lsmod | grep b44
cat /etc/network/interfaces
ifconfig
```

Then bring your wired card up using "/etc/init.d/networking restart" and again run:
```
lshw -C network
ifconfig
```

---

### Post by huck416 on 2008-05-13
Thanks very much; it works. I had wifi in Gutsy as well but it would load on boot; now it doesn't in Hardy. I have to manually connect via knetworkmanager each time. I can switch between wired and wireless usually without problem but not having my wifi connect on start is a pain. In Gutsy I had a modified interfaces file with info regarding my wifi however it got dumped with the Hardy upgrade and I can't find the code. Any ideas?

***EDIT***
I got it to auto-connect on boot with 2.6.24.17. I removed ndiswrapper from /etc/modules and ran with the modified rc.local file as described in this thread. That solved it.

---

### Post by lifeinoleg on 2008-05-13
**Here is the output of:**
```
lshw -C network
cat /etc/rc.local
lsmod | grep b44
cat /etc/network/interfaces
ifconfig
```

```

oleg@OlegsCPU:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:1c:80:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:ae:ec:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
oleg@OlegsCPU:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
oleg@OlegsCPU:~$ lsmod | grep b44
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
oleg@OlegsCPU:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp

auto eth1
oleg@OlegsCPU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85600 (83.5 KB)  TX bytes:85600 (83.5 KB)

```

**Output from:**
```
sudo /etc/init.d/networking restart
```

```
[sudo] password for oleg: 
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 4810
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:c5:ae:ec:f7
Sending on   LPF/eth1/00:15:c5:ae:ec:f7
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:c5:ae:ec:f7
Sending on   LPF/eth1/00:15:c5:ae:ec:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPOFFER of 192.168.0.3 from 192.168.0.1
DHCPREQUEST of 192.168.0.3 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.3 from 192.168.0.1
bound to 192.168.0.3 -- renewal in 936749597 seconds.
                                                                         [ OK ]
```

**Finally, here is the output from:**
```
lshw -C network
ifconfig
```

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:1c:80:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:ae:ec:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.3 latency=64 module=ssb multicast=yes
oleg@OlegsCPU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 

eth1      Link encap:Ethernet  HWaddr 00:15:c5:ae:ec:f7  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feae:ecf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1518 (1.4 KB)  TX bytes:5021 (4.9 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85600 (83.5 KB)  TX bytes:85600 (83.5 KB)

```


Thanks for the help.

---

### Post by jw5801 on 2008-05-13
> **huck416 said:**
> Thanks very much; it works. I had wifi in Gutsy as well but it would load on boot; now it doesn't in Hardy. I have to manually connect via knetworkmanager each time. I can switch between wired and wireless usually without problem but not having my wifi connect on start is a pain. In Gutsy I had a modified interfaces file with info regarding my wifi however it got dumped with the Hardy upgrade and I can't find the code. Any ideas?

You could give wicd or wifi-radar a try. I personally use wicd, and I'm almost always connected to my network well before I hit the desktop.

---

### Post by jw5801 on 2008-05-13
> **lifeinoleg said:**
> **Here is the output of:**
```
lshw -C network
cat /etc/rc.local
lsmod | grep b44
cat /etc/network/interfaces
ifconfig
```

```

oleg@OlegsCPU:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:1c:80:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:ae:ec:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
oleg@OlegsCPU:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
oleg@OlegsCPU:~$ lsmod | grep b44
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
oleg@OlegsCPU:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp

auto eth1
oleg@OlegsCPU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85600 (83.5 KB)  TX bytes:85600 (83.5 KB)

```

**Output from:**
```
sudo /etc/init.d/networking restart
```

```
[sudo] password for oleg: 
 * Reconfiguring network interfaces...                                          RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth1.pid with pid 4810
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:c5:ae:ec:f7
Sending on   LPF/eth1/00:15:c5:ae:ec:f7
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.0.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:15:c5:ae:ec:f7
Sending on   LPF/eth1/00:15:c5:ae:ec:f7
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPOFFER of 192.168.0.3 from 192.168.0.1
DHCPREQUEST of 192.168.0.3 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.3 from 192.168.0.1
bound to 192.168.0.3 -- renewal in 936749597 seconds.
                                                                         [ OK ]
```

**Finally, here is the output from:**
```
lshw -C network
ifconfig
```

```
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:1c:80:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:ae:ec:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.3 latency=64 module=ssb multicast=yes
oleg@OlegsCPU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 

eth1      Link encap:Ethernet  HWaddr 00:15:c5:ae:ec:f7  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:feae:ecf7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1518 (1.4 KB)  TX bytes:5021 (4.9 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1712 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:85600 (83.5 KB)  TX bytes:85600 (83.5 KB)

```


Thanks for the help.

That's very interesting! You've had your Wireless card be configured as eth1 and your wireless card as eth0. That's a bug you probably want to report! Your wireless should be wlan0 and your wired should be eth0. Try changing your /etc/network/interfaces to the following:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0
```

Note that I've changed the all eth1s to eth0. The default scripts to configure wired interfaces all generally run on eth0, so if we make eth0 be assigned to the correct place then it should make life a little better. Might also mean that your wireless gets assigned to wlan0 as it should. Try changing that and rebooting and see what happens.

---

### Post by lifeinoleg on 2008-05-14
I edited the 'interfaces' file, restarted and before anything I ran the stack you told me to run before:

```
lshw -C network
cat /etc/rc.local
lsmod | grep b44
cat /etc/network/interfaces
ifconfig
```

Here is the output: 

```

oleg@OlegsCPU:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:1c:80:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:ae:ec:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
oleg@OlegsCPU:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
oleg@OlegsCPU:~$ lsmod | grep b44
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
oleg@OlegsCPU:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0
oleg@OlegsCPU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          inet addr:169.254.7.73  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:efcfc000-efd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90261 (88.1 KB)  TX bytes:90261 (88.1 KB)
```


But I was not able to connect. So I ran the 'restart' command:
```

sudo /etc/init.d/networking restart
```

and got this:

```
[sudo] password for oleg: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6096
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:92:1c:80:be
Sending on   LPF/eth0/00:1a:92:1c:80:be
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:92:1c:80:be
Sending on   LPF/eth0/00:1a:92:1c:80:be
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


```

But the connection did not come back on so I changed 'interfaces' back to the way it was, eth1 instead of eth0 and ran 'restart' command again. Below is the output:


```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:c5:ae:ec:f7
Sending on   LPF/eth1/00:15:c5:ae:ec:f7
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.3 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.3 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.3 from 192.168.0.1
bound to 192.168.0.3 -- renewal in 936742508 seconds.
```


I am now connected.

Are there any other things I can try? ((maybe I can try substituting wlan0 instead of eth0/1 in 'interfaces'?))

---

### Post by jw5801 on 2008-05-14
> **lifeinoleg said:**
> I edited the 'interfaces' file, restarted and before anything I ran the stack you told me to run before:

```
lshw -C network
cat /etc/rc.local
lsmod | grep b44
cat /etc/network/interfaces
ifconfig
```

Here is the output: 

```

oleg@OlegsCPU:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:92:1c:80:be
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:15:c5:ae:ec:f7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
oleg@OlegsCPU:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
oleg@OlegsCPU:~$ lsmod | grep b44
b44                    28432  0 
ssb                    32260  1 b44
mii                     6400  1 b44
oleg@OlegsCPU:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0
oleg@OlegsCPU:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:92:1c:80:be  
          inet addr:169.254.7.73  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:efcfc000-efd00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1781 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:90261 (88.1 KB)  TX bytes:90261 (88.1 KB)
```


But I was not able to connect. So I ran the 'restart' command:
```

sudo /etc/init.d/networking restart
```

and got this:

```
[sudo] password for oleg: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 6096
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:92:1c:80:be
Sending on   LPF/eth0/00:1a:92:1c:80:be
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1a:92:1c:80:be
Sending on   LPF/eth0/00:1a:92:1c:80:be
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]


```

But the connection did not come back on so I changed 'interfaces' back to the way it was, eth1 instead of eth0 and ran 'restart' command again. Below is the output:


```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:15:c5:ae:ec:f7
Sending on   LPF/eth1/00:15:c5:ae:ec:f7
Sending on   Socket/fallback
DHCPREQUEST of 192.168.0.3 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.0.3 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.0.3 from 192.168.0.1
bound to 192.168.0.3 -- renewal in 936742508 seconds.
```


I am now connected.

Are there any other things I can try? ((maybe I can try substituting wlan0 instead of eth0/1 in 'interfaces'?))

Well the interface that should be configuring is your wired interface. For some reason ndiswrapper is claiming eth0, which is very odd indeed. As a temporary workaround (albeit a not very graceful one) you can add /etc/init.d/networking restart to the end of your /etc/rc.local script. I honestly have no idea why ndiswrapper is claiming eth0! It's definitely worthy of a bug report however, and if you do that you'll almost certainly get assistance from someone who knows much more about how interfaces are assigned than most of the forum regulars.

We could try not loading ndiswrapper to start off with and seeing if the problem still occurs. We'll leave our script intact, just make it not executable so it doesn't run on boot:
```
sudo chmod a-x /etc/rc.local
```
When you want it to run again, use:
```
sudo chmod a+x /etc/rc.local
```
Then reboot and see what happens.

---

### Post by Moneyless on 2008-05-14
Ok well in that other How-To you said:

> **jw5801 said:**
> Posting in the other How-To is probably the best idea.

Try taking down the WEP encryption (just for a second) and see if you can connect to an unencrypted network. If you can, it's almost certainly a network manager issue rather than a driver issue.

I can't disable the WEP encryption on my router it comes with it always enabled, the only thing I can do is change the key, also since it's just one of those Modem/Router combo's we got from the ISP... (In case it could be useful it's a SIEMENS Speedstream 6520)

When I get home today I am just going to do a resh install of Ubuntu and start from the right How-To.

---

### Post by Moneyless on 2008-05-14
> **Moneyless said:**
> Ok well in that other How-To you said:



I can't disable the WEP encryption on my router it comes with it always enabled, the only thing I can do is change the key, also since it's just one of those Modem/Router combo's we got from the ISP... (In case it could be useful it's a SIEMENS Speedstream 6520)

When I get home today I am just going to do a resh install of Ubuntu and start from the right How-To.

Ok so I did a fresh install of Ubuntu 8.04 and followed your How-To but it is still doing the same thing... the WLAN light on my laptop comes on and I can see other wireless networks but whenever I try and connect to my network it just keeps asking me for the WEP key over and over... And I can't disable the WEP I can only reset the key.

---

### Post by jw5801 on 2008-05-15
> **Moneyless said:**
> Ok so I did a fresh install of Ubuntu 8.04 and followed your How-To but it is still doing the same thing... the WLAN light on my laptop comes on and I can see other wireless networks but whenever I try and connect to my network it just keeps asking me for the WEP key over and over... And I can't disable the WEP I can only reset the key.

What did you do to fix it last time? The how-to has worked correctly if your light is on and you can see networks. All I can recommend is that you try different applications for connecting, like wicd, wifi-radar or you could go command-line and try kevdog's tutorial:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by Moneyless on 2008-05-15
Ok well when I try and connect using Terminal it gives me this:

```
max@MaxUbuntuLaptop:~$ sudo ifconfig wlan0 down
[sudo] password for max: 
max@MaxUbuntuLaptop:~$ sudo ifconfig wlan0 down
max@MaxUbuntuLaptop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:3a:04:34:c4
Sending on   LPF/wlan0/00:1f:3a:04:34:c4
Sending on   Socket/fallback
max@MaxUbuntuLaptop:~$ sudo ifconfig wlan0 up
max@MaxUbuntuLaptop:~$ sudo iwconfig wlan0 essid "Rawr"
max@MaxUbuntuLaptop:~$ sudo iwconfig wlan0 key 11adde21f1d238fc829e3ebcfb
max@MaxUbuntuLaptop:~$ sudo iwconfig wlan0 mode Managed
max@MaxUbuntuLaptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:3a:04:34:c4
Sending on   LPF/wlan0/00:1f:3a:04:34:c4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
max@MaxUbuntuLaptop:~$ 
```

How do I fix this? Also I tried setting my modem to a static IP instead of a dynamic IP but I don't exactly know what I have to do to change it...

---

### Post by jw5801 on 2008-05-16
> **Moneyless said:**
> Ok well when I try and connect using Terminal it gives me this:

```
max@MaxUbuntuLaptop:~$ sudo ifconfig wlan0 down
[sudo] password for max: 
max@MaxUbuntuLaptop:~$ sudo ifconfig wlan0 down
max@MaxUbuntuLaptop:~$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:3a:04:34:c4
Sending on   LPF/wlan0/00:1f:3a:04:34:c4
Sending on   Socket/fallback
max@MaxUbuntuLaptop:~$ sudo ifconfig wlan0 up
max@MaxUbuntuLaptop:~$ sudo iwconfig wlan0 essid "Rawr"
max@MaxUbuntuLaptop:~$ sudo iwconfig wlan0 key 11adde21f1d238fc829e3ebcfb
max@MaxUbuntuLaptop:~$ sudo iwconfig wlan0 mode Managed
max@MaxUbuntuLaptop:~$ sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1f:3a:04:34:c4
Sending on   LPF/wlan0/00:1f:3a:04:34:c4
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
max@MaxUbuntuLaptop:~$ 
```

How do I fix this? Also I tried setting my modem to a static IP instead of a dynamic IP but I don't exactly know what I have to do to change it...

Do you have any other computers accessing your router? There *should* be a setting somewhere about disabling DHCP on the LAN side (don't do it on the WAN side, that wouldn't be good), then you may need to assign an IP based on MAC address, and tell your install what IP it should be using. I highly doubt that will make much difference though.

Have you quadruple checked the WEP key you're using? Other than that, I'm struggling for ideas. What does ```
iwlist scan
```say about your network? It might be able to tell us if there's anything interesting about it.

---

### Post by brainiac978 on 2008-05-16
Okay, I used my wired connection to get the driver, get the latest packages, etc.

Everything seemed to be going fine until I rebooted.  I rebooted without my wired connection plugged in.  The wireless component was  identified in the networking tool.

I edited the properties with my SSID and WPA encryption key, and set for DHCP.  I click OK and the check mark appears as it is changing the settings.

But afterward, nothing happens.  No connection, nothing.  When I go back to the networking tool, the check mark is gone.

It is almost like it refuses to work with it.

I am on a Dell Inspiron 1520 with the 1390 card.

---

### Post by masterkoppa on 2008-05-16
Thank you for this great How-To. Yet I'm still having a little problem. Sometimes when I boot my computer Ubuntu does not read the wireless card and I have to reboot several times until the wireless indicator turns on. When I boot I try to power the wireless, by pressing the wireless button and sometimes it turns on and sometimes not.
Curious thing is that every time I boot in safe mode it works.

Am I doing anything wrong?
Did I skip a step in the How-To?

I'm currently running fine by booting in safe mode when I need internet but i would really like to solve this.

My Computer:

Dell Latitude 131L
AMD Anthol 64 1.6 GHz
Dell BCM94311MCG wlan mini-PCI

---

### Post by jw5801 on 2008-05-16
> **masterkoppa said:**
> Thank you for this great How-To. Yet I'm still having a little problem. Sometimes when I boot my computer Ubuntu does not read the wireless card and I have to reboot several times until the wireless indicator turns on. When I boot I try to power the wireless, by pressing the wireless button and sometimes it turns on and sometimes not.
Curious thing is that every time I boot in safe mode it works.

Am I doing anything wrong?
Did I skip a step in the How-To?

I'm currently running fine by booting in safe mode when I need internet but i would really like to solve this.

My Computer:

Dell Latitude 131L
AMD Anthol 64 1.6 GHz
Dell BCM94311MCG wlan mini-PCI

That's extremely odd! Try playing with the wireless options in your bios?

---

### Post by jw5801 on 2008-05-16
> **brainiac978 said:**
> Okay, I used my wired connection to get the driver, get the latest packages, etc.

Everything seemed to be going fine until I rebooted.  I rebooted without my wired connection plugged in.  The wireless component was  identified in the networking tool.

I edited the properties with my SSID and WPA encryption key, and set for DHCP.  I click OK and the check mark appears as it is changing the settings.

But afterward, nothing happens.  No connection, nothing.  When I go back to the networking tool, the check mark is gone.

It is almost like it refuses to work with it.

I am on a Dell Inspiron 1520 with the 1390 card.

Well as far as this how-to is concerned your card is working. I've always had issues with the default network-manager, so my suggestions are to try using wifi-radar or doing the whole thing manually following kevdog's tutorial. [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

The other option is to disable WPA and put it back to an open connection, so you can verify you can connect there, then build the security back up to trace where the issue is.

---

### Post by LazyEngineer on 2008-05-19
Thank you so much!!  I followed the instructions in the original post here, and it worked!  I've been battling this for a week, following countless threads claiming to be THE solution - and this is the only one that was.

for the record, I'm running Ubuntu 8.04 on an HP Pavilion TX1000 (TX1308nr) tablet.

---

### Post by stopthewar24 on 2008-05-23
Just another note to say that this *almost* worked for me, and started working completely with one smallish change.  First, a little background: I upgraded my system (a Dell Inspiron 1520 w/1390 card) from Gutsy to Hardy via the automatic internet-based upgrade.  I had followed paperdiesel's tutorial to configure my card with ndiswrapper back when I was using Gutsy, and of course, that stopped working once I put Hardy on.

jw5801, I followed your tutorial for Hardy and it seemed to go great.  When I rebooted at the end, however, I couldn't connect wirelessly -- Network Manager didn't want to acknowledge that I had a wireless card in the computer at all.  However, if I then put the computer into standby and brought it out, the wireless would start working perfectly.  Running 

```
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
```

in the terminal also worked to get the wireless going.  But it didn't work on boot-up -- and I even made sure that ndiswrapper was removed from my /etc/modules (and then I added it back in to see if that somehow made any difference, and it didn't).

I ended up adding 

```
sudo modprobe -r ndiswrapper
```

right before 

```
sudo modprobe ndiswrapper
```

in my rc.local, and that fixed it.  Wireless started working all the time, even on boot-up.  I don't know exactly why I *needed* to add this command to rc.local, even with ndiswrapper removed from /etc/modules, but it was the only thing that seemed to clear up this problem.  I'm relatively new to Linux... maybe ndiswrapper is being loaded during the boot in some other way that I'm not aware of?

Anyway, thought I'd throw this in the mix for other people with similar problems.  Also, for whatever it's worth, the wi-fi light on my Dell is on and working perfectly, and I'm on a WPA1 Personal network, using Network Manager.  My Broadcom wired ethernet also works without a hitch, switching between wired and wireless depending on whether a cable is connected.  Thanks so much, jw5801, for your excellent tutorial!  I would have been clueless otherwise...

---

### Post by jw5801 on 2008-05-24
> **stopthewar24 said:**
> Just another note to say that this *almost* worked for me, and started working completely with one smallish change.  First, a little background: I upgraded my system (a Dell Inspiron 1520 w/1390 card) from Gutsy to Hardy via the automatic internet-based upgrade.  I had followed paperdiesel's tutorial to configure my card with ndiswrapper back when I was using Gutsy, and of course, that stopped working once I put Hardy on.

jw5801, I followed your tutorial for Hardy and it seemed to go great.  When I rebooted at the end, however, I couldn't connect wirelessly -- Network Manager didn't want to acknowledge that I had a wireless card in the computer at all.  However, if I then put the computer into standby and brought it out, the wireless would start working perfectly.  Running 

```
sudo modprobe -r b44
sudo modprobe -r ssb
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
```

in the terminal also worked to get the wireless going.  But it didn't work on boot-up -- and I even made sure that ndiswrapper was removed from my /etc/modules (and then I added it back in to see if that somehow made any difference, and it didn't).

I ended up adding 

```
sudo modprobe -r ndiswrapper
```

right before 

```
sudo modprobe ndiswrapper
```

in my rc.local, and that fixed it.  Wireless started working all the time, even on boot-up.  I don't know exactly why I *needed* to add this command to rc.local, even with ndiswrapper removed from /etc/modules, but it was the only thing that seemed to clear up this problem.  I'm relatively new to Linux... maybe ndiswrapper is being loaded during the boot in some other way that I'm not aware of?

Anyway, thought I'd throw this in the mix for other people with similar problems.  Also, for whatever it's worth, the wi-fi light on my Dell is on and working perfectly, and I'm on a WPA1 Personal network, using Network Manager.  My Broadcom wired ethernet also works without a hitch, switching between wired and wireless depending on whether a cable is connected.  Thanks so much, jw5801, for your excellent tutorial!  I would have been clueless otherwise...

No problems! :)

The fact you need that step at the beginning (of your /etc/rc.local) means that ndiswrapper is being loaded somewhere else during the boot process, most probably from /etc/modules. I'm trying to avoid telling people to remove a module that shouldn't have been loaded at all in their rc.local, it doesn't have a massive impact on anything but it makes this solution just a little bit less graceful.

---

### Post by DougAlder on 2008-05-24
I followed all the steps - note that the file retrieved from Dell was wget [http://ftp.us.dell.com/network/R151519.exe](http://ftp.us.dell.com/network/R151519.exe) not .EXE so the unzip command did not work until I did a list of the files in the directory and saw the case change on the EXE. - and it does not connect to my wireless card. Here are the results you asked for

doug@doug-laptop:~$ lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
doug@doug-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
doug@doug-laptop:~$ lsmod | grep b43
doug@doug-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  12 ndiswrapper,pl2303,usb_storage,usbserial,libusual,hci_usb,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
doug@doug-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 422 2008-05-24 13:04 /etc/rc.local

I'm completely new to Linux so go easy on me please :)

aaaaaarrrrggghh 

Ignore this message - turns out I had a case problem in the WPA2 password for my router - logged in via cable copied the password directly into my wireless network settings and it worked like a charm - I can't thank you enough for this advice!

---

### Post by jw5801 on 2008-05-24
> **DougAlder said:**
> I followed all the steps - note that the file retrieved from Dell was wget [http://ftp.us.dell.com/network/R151519.exe](http://ftp.us.dell.com/network/R151519.exe) not .EXE so the unzip command did not work until I did a list of the files in the directory and saw the case change on the EXE. - and it does not connect to my wireless card. Here are the results you asked for

doug@doug-laptop:~$ lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
doug@doug-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
doug@doug-laptop:~$ lsmod | grep b43
doug@doug-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  12 ndiswrapper,pl2303,usb_storage,usbserial,libusual,hci_usb,snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,uhci_hcd
doug@doug-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 422 2008-05-24 13:04 /etc/rc.local

I'm completely new to Linux so go easy on me please :)

aaaaaarrrrggghh 

Ignore this message - turns out I had a case problem in the WPA2 password for my router - logged in via cable copied the password directly into my wireless network settings and it worked like a charm - I can't thank you enough for this advice!

No probs!

If you run
```
wget http://ftp.us.dell.com/network/R151519.exe
```
Then yes, you will get the lower case .exe, but if you use the URL with the upper case .EXE then that's what you'll get back:
```
wget http://ftp.us.dell.com/network/R151519.EXE
```

---

### Post by thinking2loud on 2008-05-25
I got it to work, eventually.  I had a LOT of trouble with it.  There's something in particular with the modprobe/modprobe -r things that you have to do in a particular order.  I finally got it to work, but it was luck not skill and I was unable to track down what order I did it.  Or it may have been a side effect of the next issue.  But, not to have a negative attitude, thanks.

My current problem is WPA security.  I have a secured wireless router and an unsecured wireless router on different channels.  What happens is the secured one requires several trials before it finally connects.  The unsecured one starts right up first time every time.  It isn't signal strength--the unsecured one also has reduced power.

---

### Post by jw5801 on 2008-05-25
> **thinking2loud said:**
> I got it to work, eventually.  I had a LOT of trouble with it.  There's something in particular with the modprobe/modprobe -r things that you have to do in a particular order.  I finally got it to work, but it was luck not skill and I was unable to track down what order I did it.  Or it may have been a side effect of the next issue.  But, not to have a negative attitude, thanks.

My current problem is WPA security.  I have a secured wireless router and an unsecured wireless router on different channels.  What happens is the secured one requires several trials before it finally connects.  The unsecured one starts right up first time every time.  It isn't signal strength--the unsecured one also has reduced power.

Alot of people seem to have issues with reliably connecting to a WPA network, but it doesn't seem to be specific to any one card or setup. About all the advice I have is to try an alternate network manager or have a look at kevdog's tutorial on commandline connections. kevdog is somewhat of an authority on wpa_supplicant and similar apps so his thread is a good place to ask for help with it. I don't have the link handy but I've referenced it many a time already in this thread.

---

### Post by toastermm on 2008-05-29
JW - first let me say what a wonderful guide and easy to use/read.  I wish all guides were that way.  The wireless card is the last thing I need to configure and I'll be a happy man.  I'm running a HP laptop, tx1000, hardy heron, amd x64.  I believe I have run your guide to a T- even ran it twice.  I'm having an issue with ndiswrapper.  Can't find the module even though I installed the latest version.  (excuse the linux beginner-ness exuding here)

Here is my output as requested in trouble shooting:

[PHP]nick@Hobbes:~$ lspci -nn | grep 14e4
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02)
[/PHP]

[PHP]nick@Hobbes:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
[/PHP]

[PHP]nick@Hobbes:~$ lsmod | grep b43
nick@Hobbes:~$ 
[/PHP]
--no output--

[PHP]nick@Hobbes:~$ lsmod | grep ndiswrapper
nick@Hobbes:~$ 
[/PHP]
--no output--

[PHP]nick@Hobbes:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 580 2008-05-28 21:16 /etc/rc.local
[/PHP]

[PHP]nick@Hobbes:~$ sudo rmmod b43 b44 ssb
[sudo] password for nick: 
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
[/PHP]

[PHP]nick@Hobbes:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
[/PHP]

[PHP]nick@Hobbes:~$ sudo modprobe b44
nick@Hobbes:~$ 
[/PHP]
--no output--


--So I thought I missed the step to install ndiswrapper, and it seemed to go ok:

[PHP]nick@Hobbes:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/PHP]

Which is what I received before. (when I ran the guide)

I also have read the previous posts and you mentioned something about a command had to been run as the root user?  I scanned the guide and didn't see it.  Although it's late right now and I could have missed it.

Any more information you would want, let me know.  Thanks again for your time and dedication to this.



*edit*
Here is my blacklist file

[PHP]nick@Hobbes:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

#blacklist bcm43xx

#blacklist ssb
blacklist b43
blacklist b43legacy
[/PHP]

and my rc.local file:

[PHP]nick@Hobbes:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## TouchKit kernel module section begin ##
rmmod touchkitusb
# This module may be renamed “usbtouchscreen”.
insmod /lib/modules/tkusb.o
# for Kernel 2.6.x only.
## TouchKit kernel module section end ##

modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
[/PHP]

and finally my /etc/modules file:

[PHP]nick@Hobbes:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
[/PHP]

Gosh that's all I can think of.

---

### Post by jw5801 on 2008-05-29
> **toastermm said:**
> JW - first let me say what a wonderful guide and easy to use/read.  I wish all guides were that way.  The wireless card is the last thing I need to configure and I'll be a happy man.  I'm running a HP laptop, tx1000, hardy heron, amd x64.  I believe I have run your guide to a T- even ran it twice.  I'm having an issue with ndiswrapper.  Can't find the module even though I installed the latest version.  (excuse the linux beginner-ness exuding here)

...

[PHP]nick@Hobbes:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
[/PHP]

...

--So I thought I missed the step to install ndiswrapper, and it seemed to go ok:

[PHP]nick@Hobbes:~$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ndiswrapper-common is already the newest version.
ndiswrapper-utils-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
[/PHP]

Which is what I received before. (when I ran the guide)

...

Hmm... very interesting!

I would think this is related to the most recent kernel update from Ubuntu. What do you get from the following:
```
sudo updatedb #will think for a while, but shouldn't return anything
locate ndiswrapper.ko
uname -r
```

I'm thinking that perhaps modules for the newer kernel (2.6.24-17) were installed whilst you're still using the older (2.6.24-16). Or maybe vice versa. If that's the case try:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install linux-restricted-modules
```

This is what I get back from the locate command for your reference:
```
[ ~ ] locate ndiswrapper.ko
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
```

---

### Post by saskatchewan on 2008-05-29
This is the wireless that I have.

allan@allan-laptop:~$ lspci -nn | grep 14e4
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


I can't find any support for the BCM4318.

Any more suggestions?

---

### Post by jw5801 on 2008-05-29
> **saskatchewan said:**
> This is the wireless that I have.

allan@allan-laptop:~$ lspci -nn | grep 14e4
05:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)


I can't find any support for the BCM4318.

Any more suggestions?

[Search](http://www.google.com.au/search?q=ndiswrapper+14e4%3A4318&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a) a little [bit](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/)?

According to the NDISWrapper wiki, you should use this driver:
[http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)

---

### Post by toastermm on 2008-05-29
> **jw5801 said:**
> Hmm... very interesting!

I would think this is related to the most recent kernel update from Ubuntu. What do you get from the following:
```
sudo updatedb #will think for a while, but shouldn't return anything
locate ndiswrapper.ko
uname -r
```

I'm thinking that perhaps modules for the newer kernel (2.6.24-17) were installed whilst you're still using the older (2.6.24-16). Or maybe vice versa. If that's the case try:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install linux-restricted-modules
```

This is what I get back from the locate command for your reference:
```
[ ~ ] locate ndiswrapper.ko
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
```

Here is the output:
```
 nick@Hobbes:~$ sudo updatedb
nick@Hobbes:~$

nick@Hobbes:~$ locate ndiswrapper.ko
/home/nick/ndiswrapper-1.52/driver/.ndiswrapper.ko.cmd
/home/nick/ndiswrapper-1.52/driver/ndiswrapper.ko
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.24-16-server/misc/ndiswrapper.ko
/lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

nick@Hobbes:~$ uname -r
2.6.24-17-server

```

Makes sense about the kernel, so I ran the code you requested:

```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install linux-restricted-modules

```

I got a bunch of updates/upgrades and the install of restricted modules went without a hitch.  The only thing worth noting is that there were a few sites at the end of the first command that didn't get connected to:

[www.getautomatix.com](www.getautomatix.com)
[http://ubuntu.beryl-project.org/dists/hardy/main/binary-amd64/Packages.gz](http://ubuntu.beryl-project.org/dists/hardy/main/binary-amd64/Packages.gz)
[http://exodus.xmms.se/debian/dists/stable/main/binary-amd64/Packages.gz](http://exodus.xmms.se/debian/dists/stable/main/binary-amd64/Packages.gz)

Not sure if I need these, I've had to go manually to sites before and install packages, but I can do that if needed.

After this should I run the guide again?

**edit**

I did run through the guide again... different output for the test:

```

nick@Hobbes:~/wireless-install/R151519/DRIVER$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
nick@Hobbes:~/wireless-install/R151519/DRIVER$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
nick@Hobbes:~/wireless-install/R151519/DRIVER$ sudo modprobe b44
nick@Hobbes:~/wireless-install/R151519/DRIVER$ 

```

Do I need to create something in /proc/modules?

---

### Post by jw5801 on 2008-05-29
> **toastermm said:**
> Here is the output:
```
 nick@Hobbes:~$ sudo updatedb
nick@Hobbes:~$

nick@Hobbes:~$ locate ndiswrapper.ko
/home/nick/ndiswrapper-1.52/driver/.ndiswrapper.ko.cmd
/home/nick/ndiswrapper-1.52/driver/ndiswrapper.ko
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.24-16-server/misc/ndiswrapper.ko
/lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

nick@Hobbes:~$ uname -r
2.6.24-17-server

```

Makes sense about the kernel, so I ran the code you requested:

```

sudo apt-get update && sudo apt-get upgrade
sudo apt-get install linux-restricted-modules

```

I got a bunch of updates/upgrades and the install of restricted modules went without a hitch.  The only thing worth noting is that there were a few sites at the end of the first command that didn't get connected to:

[www.getautomatix.com](www.getautomatix.com)
[http://ubuntu.beryl-project.org/dists/hardy/main/binary-amd64/Packages.gz](http://ubuntu.beryl-project.org/dists/hardy/main/binary-amd64/Packages.gz)
[http://exodus.xmms.se/debian/dists/stable/main/binary-amd64/Packages.gz](http://exodus.xmms.se/debian/dists/stable/main/binary-amd64/Packages.gz)

Not sure if I need these, I've had to go manually to sites before and install packages, but I can do that if needed.

After this should I run the guide again?

**edit**

I did run through the guide again... different output for the test:

```

nick@Hobbes:~/wireless-install/R151519/DRIVER$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
nick@Hobbes:~/wireless-install/R151519/DRIVER$ sudo modprobe ndiswrapper
[COLOR="Red"]FATAL: Module ndiswrapper not found.[/COLOR]
nick@Hobbes:~/wireless-install/R151519/DRIVER$ sudo modprobe b44
nick@Hobbes:~/wireless-install/R151519/DRIVER$ 

```

Do I need to create something in /proc/modules?

The b43 and b44 bits are ok. In fact they're good as it means they're not being loaded (which they shouldn't). The issue is in the fact that you're using the server kernel but there isn't the module available for it (I've highlighted the relevent error message in red). Probably something you'd want to file a bug against, the package should have been upgraded when the kernel was upgraded.

Anyway, the package I think you need is:
```
sudo apt-get install linux-ubuntu-modules-2.6.24-17-server
```

After that's installed just run ```
sudo rmmod b44 ssb ndiswrapper # don't worry if it complains
sudo modprobe ndiswrapper
```
There's no need to rerun anything else in the guide.

---

### Post by TalioGladius on 2008-05-29
I need help, fresh image today on 8.04 and I can't get this working.  Honestly I think it's a little retarded that wifi doesn't work out of the box with heron when it did with the last 3 versions without a single issue.  But that's another story.


Dell XPS M1710 laptop.  Intel PRO/Wireless 3945ABG.  That's R171131 from dell.

uname -a
Linux Fyodor 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

This is what I did:

wget [http://ftp.us.dell.com/network/R171131.exe](http://ftp.us.dell.com/network/R171131.exe)
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist
gksudo gedit /etc/rc.local  -added the lines specified
unzip -a R171131.exe -d R171131/
changed directories
sudo ndiswrapper -i NETw4k32.INF

I then did
sudo rmmod b43 b44 ssb    which returned this:  ERROR: Module b43 does not exist in /proc/modules
 sudo modprobe ndiswrapper
 sudo modprobe b44


I then rebooted.  No wifi light.  When I go to the tray and network to choose the wireless network, only wired network and my vpnc is available.

ifconfig only displays eth0 and lo, and iwconfig does nothing either, obviously.

Please help, this is a heron deal breaker for me.

---

### Post by toastermm on 2008-05-29
> **jw5801 said:**
> The b43 and b44 bits are ok. In fact they're good as it means they're not being loaded (which they shouldn't). The issue is in the fact that you're using the server kernel but there isn't the module available for it (I've highlighted the relevent error message in red). Probably something you'd want to file a bug against, the package should have been upgraded when the kernel was upgraded.

Anyway, the package I think you need is:
```
sudo apt-get install linux-ubuntu-modules-2.6.24-17-server
```

After that's installed just run ```
sudo rmmod b44 ssb ndiswrapper # don't worry if it complains
sudo modprobe ndiswrapper
```
There's no need to rerun anything else in the guide.


I ran the code... it works!!!
You are my hero- thanks again!

---

### Post by gimmerealroot on 2008-05-29
I see everybody here is using ndiswrapper for for the 4311.  

Is anybody using the in kernel modules successfully with bcm43xx firmwarecutter on a 2.6.24 kernel?  I know I had problems on another OS using the b43 drivers in this manner(didn't want to bother with ndiswrapper so haven't tried it).

I have been for over 1-1/2 years now been using the in kernel bcm43xx modules thats been available for quite a few kernels prior to 2.6.24.  No problems.  I'll past the appropriate section of my kernel config.

From 2.6.23 r10 kernel

[PHP]# Wireless
#
CONFIG_CFG80211=y
CONFIG_WIRELESS_EXT=y
# CONFIG_MAC80211 is not set
CONFIG_IEEE80211=y
CONFIG_IEEE80211_DEBUG=y
CONFIG_IEEE80211_CRYPT_WEP=y
CONFIG_IEEE80211_CRYPT_CCMP=y
CONFIG_IEEE80211_CRYPT_TKIP=y
CONFIG_IEEE80211_SOFTMAC=m
CONFIG_IEEE80211_SOFTMAC_DEBUG=y
CONFIG_RFKILL=m
CONFIG_RFKILL_INPUT=m
.
.
.
Under Device Drivers
.
# Wireless LAN
#
# CONFIG_WLAN_PRE80211 is not set
CONFIG_WLAN_80211=y
# CONFIG_PCMCIA_RAYCS is not set
# CONFIG_IPW2100 is not set
# CONFIG_IPW2200 is not set
# CONFIG_LIBERTAS is not set
# CONFIG_AIRO is not set
# CONFIG_HERMES is not set
# CONFIG_ATMEL is not set
# CONFIG_AIRO_CS is not set
# CONFIG_PCMCIA_WL3501 is not set
# CONFIG_PRISM54 is not set
# CONFIG_USB_ZD1201 is not set
CONFIG_HOSTAP=y
# CONFIG_HOSTAP_FIRMWARE is not set
# CONFIG_HOSTAP_PLX is not set
# CONFIG_HOSTAP_PCI is not set
# CONFIG_HOSTAP_CS is not set
CONFIG_BCM43XX=m
CONFIG_BCM43XX_DEBUG=y
CONFIG_BCM43XX_DMA=y
# CONFIG_BCM43XX_DMA_AND_PIO_MODE is not set
CONFIG_BCM43XX_DMA_MODE=y
# CONFIG_BCM43XX_PIO_MODE is not set
# CONFIG_ZD1211RW is not set
[/PHP] 
Hope that helps someone.
BTW-I use wpa_supplicant to handle all my wireless network configurations

---

### Post by TalioGladius on 2008-05-29
> **TalioGladius said:**
> I need help, fresh image today on 8.04 and I can't get this working.  Honestly I think it's a little retarded that wifi doesn't work out of the box with heron when it did with the last 3 versions without a single issue.  But that's another story.


Dell XPS M1710 laptop.  Intel PRO/Wireless 3945ABG.  That's R171131 from dell.

uname -a
Linux Fyodor 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

This is what I did:

wget [http://ftp.us.dell.com/network/R171131.exe](http://ftp.us.dell.com/network/R171131.exe)
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist
gksudo gedit /etc/rc.local  -added the lines specified
unzip -a R171131.exe -d R171131/
changed directories
sudo ndiswrapper -i NETw4k32.INF

I then did
sudo rmmod b43 b44 ssb    which returned this:  ERROR: Module b43 does not exist in /proc/modules
 sudo modprobe ndiswrapper
 sudo modprobe b44


I then rebooted.  No wifi light.  When I go to the tray and network to choose the wireless network, only wired network and my vpnc is available.

ifconfig only displays eth0 and lo, and iwconfig does nothing either, obviously.

Please help, this is a heron deal breaker for me.Well I inadvertantly installed a kernel update before rebooting.  Would that have screwed this up for me?

---

### Post by gimmerealroot on 2008-05-29
> **TalioGladius said:**
> Well I inadvertantly installed a kernel update before rebooting.  Would that have screwed this up for me?

Have you tried an earlier kernel?  Anything under 2.6.24?

---

### Post by jw5801 on 2008-05-30
> **TalioGladius said:**
> I need help, fresh image today on 8.04 and I can't get this working.  Honestly I think it's a little retarded that wifi doesn't work out of the box with heron when it did with the last 3 versions without a single issue.  But that's another story.


Dell XPS M1710 laptop.  Intel PRO/Wireless 3945ABG.  That's R171131 from dell.

uname -a
Linux Fyodor 2.6.24-17-generic #1 SMP Thu May 1 14:31:33 UTC 2008 i686 GNU/Linux

This is what I did:

wget [http://ftp.us.dell.com/network/R171131.exe](http://ftp.us.dell.com/network/R171131.exe)
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist
gksudo gedit /etc/rc.local  -added the lines specified
unzip -a R171131.exe -d R171131/
changed directories
sudo ndiswrapper -i NETw4k32.INF

I then did
sudo rmmod b43 b44 ssb    which returned this:  ERROR: Module b43 does not exist in /proc/modules
 sudo modprobe ndiswrapper
 sudo modprobe b44


I then rebooted.  No wifi light.  When I go to the tray and network to choose the wireless network, only wired network and my vpnc is available.

ifconfig only displays eth0 and lo, and iwconfig does nothing either, obviously.

Please help, this is a heron deal breaker for me.

This guide isn't really suitable for your card. As far as I'm aware ssb shouldn't affect Intel cards, only broadcom cards, and the Intel ones should be supported out of the box using the kernel modules. If it's not you probably want to investigate why, rather than try ndiswrapper.

EDIT: This guide is designed to get around a bunch of annoyances for Broadcom cards in the 2.6.24 series kernels, rather than to be a generic ndiswrapper install guide. For that sort of thread, take a look [here](http://ubuntuforums.org/showthread.php?t=574501). I'll stress again though, your card should be working using an open kernel module, if it's not I'd be looking to file a bug report and try to work out why.

---

### Post by jw5801 on 2008-05-30
> **gimmerealroot said:**
> I see everybody here is using ndiswrapper for for the 4311.  

Is anybody using the in kernel modules successfully with bcm43xx firmwarecutter on a 2.6.24 kernel?  I know I had problems on another OS using the b43 drivers in this manner(didn't want to bother with ndiswrapper so haven't tried it).

It's b43 and b43fwcutter now. I believe it should work, but it has the same old stability issues and still lacks 802.11g support, which are the reasons I still haven't switched over to it. As far as I'm aware it should still work with the 2.6.24 series though.

---

### Post by hellarough on 2008-05-30
Thank You so much!!! This worked perfect the second try for me...(the first time i accidentally typed backlist instead of blacklist). I love linux!!!!!

---

### Post by vexingmodstwo on 2008-05-31
I went through the How To and read every comment in this thread.

My wired connection works but my wireless doesn't.  I was able to get the light to turn a few times but the wireless card never connected.  Now the light won't come on at all.

I have the exact same wifi card that's in the how to.

Needless to say I'm ready to throw this laptop out of a window.  BTW... I'm a total Linux noob so be gentle.

---

### Post by jw5801 on 2008-05-31
> **vexingmodstwo said:**
> I went through the How To and read every comment in this thread.

My wired connection works but my wireless doesn't.  I was able to get the light to turn a few times but the wireless card never connected.  Now the light won't come on at all.

I have the exact same wifi card that's in the how to.

Needless to say I'm ready to throw this laptop out of a window.  BTW... I'm a total Linux noob so be gentle.

Has anything unexpected happened? Can't really help off 'it's not working'.

What happens when you add the ndiswrapper module:
```
sudo rmmod b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n5
```
Post your outputs! (Use "sudo modprobe b44" to bring your wired card back up).

---

### Post by vexingmodstwo on 2008-05-31
> **jw5801 said:**
> Has anything unexpected happened? Can't really help off 'it's not working'.

What happens when you add the ndiswrapper module:
```
sudo rmmod b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n5
```
Post your outputs! (Use "sudo modprobe b44" to bring your wired card back up).

Define "unexpected"... :)

Here's the output:

sudo rmmod b43 b44 ssb ndiswrapper

```
ERROR: Module b43 does not exist in /proc/modules
```

No output from sude modprobe ndiswrapper.  It just gave me the next prompt.  I'm assuming that means it did what it was supposed to do.

dmesg | tail -n5

```

[ 2326.721820] ndiswrapper: using IRQ 16
[ 2326.920212] wlan0: ethernet device 00:1b:fc:de:c6:9e using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 2326.920311] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 2326.966847] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2326.979235] usbcore: registered new interface driver ndiswrapper

```

and then I brought the ethernet card back up with sudo modprobe b44.

---

### Post by jw5801 on 2008-05-31
> **vexingmodstwo said:**
> Define "unexpected"... :)

Here's the output:

sudo rmmod b43 b44 ssb ndiswrapper

```
ERROR: Module b43 does not exist in /proc/modules
```

No output from sude modprobe ndiswrapper.  It just gave me the next prompt.  I'm assuming that means it did what it was supposed to do.

dmesg | tail -n5

```

[ 2326.721820] ndiswrapper: using IRQ 16
[ 2326.920212] wlan0: ethernet device 00:1b:fc:de:c6:9e using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 2326.920311] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 2326.966847] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2326.979235] usbcore: registered new interface driver ndiswrapper

```

and then I brought the ethernet card back up with sudo modprobe b44.

Well the install all appears to be working. What have you done in between now and when the wifi light was coming on? I'm thinking that's probably an issue at bios level or with the hotkey.

---

### Post by vexingmodstwo on 2008-06-01
> **jw5801 said:**
> Well the install all appears to be working. What have you done in between now and when the wifi light was coming on? I'm thinking that's probably an issue at bios level or with the hotkey.

well, the wifi light comes on a startup now and I can see the wireless networks around me but I can't connect to them.  I've installed WICD and it keeps locking up when I try to use it to connect to the wireless networks.

How can I check to see if the problem is at the BIOS level?  What do I look for?

---

### Post by jw5801 on 2008-06-01
> **vexingmodstwo said:**
> well, the wifi light comes on a startup now and I can see the wireless networks around me but I can't connect to them.  I've installed WICD and it keeps locking up when I try to use it to connect to the wireless networks.

How can I check to see if the problem is at the BIOS level?  What do I look for?

If the card is being recognised then you should be fine there. I thought maybe the wireless card had been disabled in the bios or some such, since it's working and seeing networks I would assume not. Have you tried connecting via the commandline?

```
sudo -s
dhclient -r wlan0
ifconfig wlan0 down
iwconfig wlan0 essid "Your-ESSID"
ifconfig wlan0 up
dhclient wlan0
exit
```

You'll need to replace "Your-ESSID" with whatever the ESSID (name) of your network is. That also assumes that your network is open and unencrypted. If it's not I'd be inclined to make it this way and then try connecting.

---

### Post by vexingmodstwo on 2008-06-01
> **jw5801 said:**
> If the card is being recognised then you should be fine there. I thought maybe the wireless card had been disabled in the bios or some such, since it's working and seeing networks I would assume not. Have you tried connecting via the commandline?

```
sudo -s
dhclient -r wlan0
ifconfig wlan0 down
iwconfig wlan0 essid "Your-ESSID"
ifconfig wlan0 up
dhclient wlan0
exit
```

You'll need to replace "Your-ESSID" with whatever the ESSID (name) of your network is. That also assumes that your network is open and unencrypted. If it's not I'd be inclined to make it this way and then try connecting.

Ok.  Disable encryption on the router, did everything up there and got this at the dhclient wlan0 command:

```
There is already a pid file /var/run/dhclient.pid with pid 23685
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1b:fc:de:c6:9e
Sending on   LPF/wlan0/00:1b:fc:de:c6:9e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by jw5801 on 2008-06-01
> **vexingmodstwo said:**
> Ok.  Disable encryption on the router, did everything up there and got this at the dhclient wlan0 command:

```
There is already a pid file /var/run/dhclient.pid with pid 23685
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:1b:fc:de:c6:9e
Sending on   LPF/wlan0/00:1b:fc:de:c6:9e
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

What do ```
iwconfig
ifconfig
dmesg | tail -n10
```
have to say?

---

### Post by vexingmodstwo on 2008-06-01
> **jw5801 said:**
> What do ```
iwconfig
ifconfig
dmesg | tail -n10
```
have to say?

iwconfig:

```

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:1c:23:8e:62:77  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe8e:6277/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6232757 (5.9 MB)  TX bytes:865411 (845.1 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:255328 (249.3 KB)  TX bytes:255328 (249.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:de:c6:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:c0200000-c0204000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:fc:de:c6:9e  
          inet addr:169.254.10.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:c0200000-c0204000

```

dmesg | tail -n10

```

[  935.030741] b44: eth0: Flow control is off for TX and off for RX.
[  935.032987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  421.835010] eth0: no IPv6 routers present
[  988.832391] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  992.537061] b44: eth0: Link is up at 100 Mbps, full duplex.
[  992.537076] b44: eth0: Flow control is off for TX and off for RX.
[  992.539581] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  502.672421] eth0: no IPv6 routers present
[ 1628.108485] APIC error on CPU0: 00(40)
[ 2879.095005] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

### Post by jw5801 on 2008-06-01
> **vexingmodstwo said:**
> iwconfig:

```

lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```

ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:1c:23:8e:62:77  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe8e:6277/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6232757 (5.9 MB)  TX bytes:865411 (845.1 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:255328 (249.3 KB)  TX bytes:255328 (249.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:de:c6:9e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:c0200000-c0204000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:fc:de:c6:9e  
          inet addr:169.254.10.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Memory:c0200000-c0204000

```

dmesg | tail -n10

```

[  935.030741] b44: eth0: Flow control is off for TX and off for RX.
[  935.032987] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  421.835010] eth0: no IPv6 routers present
[  988.832391] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  992.537061] b44: eth0: Link is up at 100 Mbps, full duplex.
[  992.537076] b44: eth0: Flow control is off for TX and off for RX.
[  992.539581] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  502.672421] eth0: no IPv6 routers present
[ 1628.108485] APIC error on CPU0: 00(40)
[ 2879.095005] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

What did you run for the "iwconfig wlan0 essid " command? Did you put your ESSID in? Because iwconfig is still reporting that the interface is not associated with an access point. That command should tell it what AP to try connecting to.

---

### Post by mpgarate on 2008-06-01
after using this tutorial I can use wifi, but after many many many retries to connect with nm-applet. I have noticed it is around 1-3 retries after a system restart, but after a previous connection and disconnection it could take 20+ times of retyping in the password. Is there any way I could restart just the network daemon? I'm guessing that is whats corrected by a reboot?

---

### Post by jw5801 on 2008-06-01
> **mpgarate said:**
> after using this tutorial I can use wifi, but after many many many retries to connect with nm-applet. I have noticed it is around 1-3 retries after a system restart, but after a previous connection and disconnection it could take 20+ times of retyping in the password. Is there any way I could restart just the network daemon? I'm guessing that is whats corrected by a reboot?

My first suggestion would be to try an alternate network manager like wicd or wifi-radar. Otherwise you could try something like "sudo /etc/init.d/networking restart" But I'm reasonably sure all that does is take down your interfaces and bring them back up again. You could also try killing nm-applet and starting it again.

---

### Post by vexingmodstwo on 2008-06-01
> **jw5801 said:**
> What did you run for the "iwconfig wlan0 essid " command? Did you put your ESSID in? Because iwconfig is still reporting that the interface is not associated with an access point. That command should tell it what AP to try connecting to.

I put the name of my AP in there in quotes:

sudo iwconfig wlan0 essid "pumpkin"

EDIT:  I was waiting for your suggestions and I decided to scrap WICD and installed wifiradar.  Somehow that worked. I'm wireless!  (now I just hope it sticks on a reboot)

---

### Post by fishfillet on 2008-06-02
There could be a thousand ways on how to skin a cat.

Mine works with this how-to: [http://tek4dpipol.blogspot.com/2008/04/ubuntu-hardy-on-lenovo-g400.html](http://tek4dpipol.blogspot.com/2008/04/ubuntu-hardy-on-lenovo-g400.html)

Only that I used the .inf supplied with the driver CD given to me and I only rebooted after the last step.

And oh, I am using a Lenovo 3000 g400.

---

### Post by cta16 on 2008-06-03
EDIT: Everything works. I just forgot to turn on my wireless xD Thanks jw5801!

---

### Post by jw5801 on 2008-06-03
> **fishfillet said:**
> There could be a thousand ways on how to skin a cat.

Mine works with this how-to: [http://tek4dpipol.blogspot.com/2008/04/ubuntu-hardy-on-lenovo-g400.html](http://tek4dpipol.blogspot.com/2008/04/ubuntu-hardy-on-lenovo-g400.html)

Only that I used the .inf supplied with the driver CD given to me and I only rebooted after the last step.

And oh, I am using a Lenovo 3000 g400.

Not really, that's exactly the same thing as this How-To :P

The only differences are:
They created a new file to run the commands at startup (adds another step required to cause this file to be run) and they included "modprobe -r ndiswrapper" in the start-up script, which is completely unnecessary as ndiswrapper should not be loaded prior to then anyway. And,
They unload b43 in their start-up script instead of preventing it from loading at all (the more efficient and graceful option).

---

### Post by mpgarate on 2008-06-03
> **jw5801 said:**
> My first suggestion would be to try an alternate network manager like wicd or wifi-radar. Otherwise you could try something like "sudo /etc/init.d/networking restart" But I'm reasonably sure all that does is take down your interfaces and bring them back up again. You could also try killing nm-applet and starting it again.

wifi-rader performs the same way, and restarting nm-applet doesnt do it either. It acts really strange. I will try the network restart next time I need wifi. Any thoughts on what could be causing this?

---

### Post by jw5801 on 2008-06-03
> **mpgarate said:**
> wifi-rader performs the same way, and restarting nm-applet doesnt do it either. It acts really strange. I will try the network restart next time I need wifi. Any thoughts on what could be causing this?

How strong is the signal at your laptop? The problems you're seeing are fairly symptomatic of a weak signal.

---

### Post by mpgarate on 2008-06-03
very strong. its my router, and this happens whether im sitting directly next to it or just upstairs.

---

### Post by jw5801 on 2008-06-04
For anyone else who installs the most recent kernel update through the repositories, if you reboot and find yourself without wireless you may need to manually install the package containing the ndiswrapper module, to do that run:
```
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

$(uname -r) will expand out into the name of your kernel, for example 2.6.24-18-generic.

---

### Post by dilipmannil on 2008-06-07
I followed the steps of the howto to get the wireless card of my Dell laptop working.

Model: Dell inspiron e1405
OS: Ubuntu 8.04

After executing "sudo modprobe ndiswrapper" it gave the following error

FATAL: Could not open '/lib/modules/2.6.24-18-generic/misc/ndiswrapper.ko': No such file or directory

Also my wired internet stopped working. The output of "lspci -nn | grep 14e4" is

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

So i uninstalled ndiswrapper and others following the steps in howto. After reboot the wired internet is working. Can anyone please help how to proceed?

---

### Post by jw5801 on 2008-06-08
> **dilipmannil said:**
> I followed the steps of the howto to get the wireless card of my Dell laptop working.

Model: Dell inspiron e1405
OS: Ubuntu 8.04

After executing "sudo modprobe ndiswrapper" it gave the following error

FATAL: Could not open '/lib/modules/2.6.24-18-generic/misc/ndiswrapper.ko': No such file or directory

Also my wired internet stopped working. The output of "lspci -nn | grep 14e4" is

02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

So i uninstalled ndiswrapper and others following the steps in howto. After reboot the wired internet is working. Can anyone please help how to proceed?

```
sudo apt-get install linux-ubuntu-modules-2.6.24-18-generic
``` For some reason not listed as a dependency for the new kernel when it really should be.

---

### Post by dilipmannil on 2008-06-08
Running "sudo apt-get install linux-ubuntu-modules-2.6.24-18-generic" instead of "sudo apt-get install linux-ubuntu-modules-$(uname -r)" didn't work. After reboot wired broadcomm card stopped working.  

Also,
After executing "sudo modprobe ndiswrapper" it gave the same error

FATAL: Could not open '/lib/modules/2.6.24-18-generic/misc/ndiswrapper.ko': No such file or directory

Following are the command outputs,
#lspci -nn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

#ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)



#lsmod | grep b43 (This command didn't give any output!!!!!)

#lsmod | grep ndiswrapper (This command also didn't give any output!!!!)

# ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2008-06-08 20:23 /etc/rc.local

The strange thing is that the wired card stops working after reboot(sudo shutdown -r now). Then I followed the  uninstalling steps in howto to get the wired internet working.

---

### Post by jw5801 on 2008-06-08
> **dilipmannil said:**
> Running "sudo apt-get install linux-ubuntu-modules-2.6.24-18-generic" instead of "sudo apt-get install linux-ubuntu-modules-$(uname -r)" didn't work. After reboot wired broadcomm card stopped working.  

Also,
After executing "sudo modprobe ndiswrapper" it gave the same error

FATAL: Could not open '/lib/modules/2.6.24-18-generic/misc/ndiswrapper.ko': No such file or directory

Following are the command outputs,
#lspci -nn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

#ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)



#lsmod | grep b43 (This command didn't give any output!!!!!)

#lsmod | grep ndiswrapper (This command also didn't give any output!!!!)

# ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2008-06-08 20:23 /etc/rc.local

The strange thing is that the wired card stops working after reboot(sudo shutdown -r now). Then I followed the  uninstalling steps in howto to get the wired internet working.

```
sudo modprobe b44
``` is all that's required to bring you wired interface back up. If it doesn't then something has gone seriously wrong somewhere before this how-to.

The issue with your Wireless driver is that the module should be located at /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko, rather than the location your install is searching. Try running ```
sudo depmod
```Then trying again.

---

### Post by dilipmannil on 2008-06-08
After running sudo depmod a new error is comming up while running following command

#~/wireless-install/R151519/DRIVER$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

Also, I am able to bring the wired interface up by "sudo modprobe b44" command once it is down. Mine is the fresh installation of ubuntu. Only document I used to bring up  wifi is paperdiesel's howto which included building ndiswrapper.

---

### Post by ucsdrake on 2008-06-08
hey, thanks for the tutorial, I've been following it for as much as I can, and searched the thread to see if this question had already been answered, but I didn't find anything but here's my problem

It seems that I can't blacklist b43 and it's still running, which means I cannot laod b44 and the ssb is running b43, any help on this? I think it's one of the last steps for me to get my wireless working

here are several outputs
```
lukas@Molokai:~/wireless-install$ modprobe -r b43
WARNING: Error removing mac80211 (/lib/modules/2.6.24-16-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error removing led_class (/lib/modules/2.6.24-16-generic/kernel/drivers/leds/led-class.ko): Operation not permitted
WARNING: Error removing input_polldev (/lib/modules/2.6.24-16-generic/kernel/drivers/input/input-polldev.ko): Operation not permitted
lukas@Molokai:~/wireless-install$ modprobe b44
WARNING: Error inserting ssb (/lib/modules/2.6.24-16-generic/kernel/drivers/ssb/ssb.ko): Operation not permitted
FATAL: Error inserting b44 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/b44.ko): Operation not permitted

```

---

### Post by jw5801 on 2008-06-08
> **ucsdrake said:**
> hey, thanks for the tutorial, I've been following it for as much as I can, and searched the thread to see if this question had already been answered, but I didn't find anything but here's my problem

It seems that I can't blacklist b43 and it's still running, which means I cannot laod b44 and the ssb is running b43, any help on this? I think it's one of the last steps for me to get my wireless working

here are several outputs
```
lukas@Molokai:~/wireless-install$ modprobe -r b43
WARNING: Error removing mac80211 (/lib/modules/2.6.24-16-generic/kernel/net/mac80211/mac80211.ko): Operation not permitted
WARNING: Error removing led_class (/lib/modules/2.6.24-16-generic/kernel/drivers/leds/led-class.ko): Operation not permitted
WARNING: Error removing input_polldev (/lib/modules/2.6.24-16-generic/kernel/drivers/input/input-polldev.ko): Operation not permitted
lukas@Molokai:~/wireless-install$ modprobe b44
WARNING: Error inserting ssb (/lib/modules/2.6.24-16-generic/kernel/drivers/ssb/ssb.ko): Operation not permitted
FATAL: Error inserting b44 (/lib/modules/2.6.24-16-generic/kernel/drivers/net/b44.ko): Operation not permitted

```

You need to be root! Try appending 'sudo'.

---

### Post by jw5801 on 2008-06-08
> **dilipmannil said:**
> After running sudo depmod a new error is comming up while running following command

#~/wireless-install/R151519/DRIVER$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

Also, I am able to bring the wired interface up by "sudo modprobe b44" command once it is down. Mine is the fresh installation of ubuntu. Only document I used to bring up  wifi is paperdiesel's howto which included building ndiswrapper.

Hmm, compiling ndiswrapper from source isn't really necessary anymore, but it won't make much difference. You'll need to recompile it for any new kernel however. Where has the ndiswrapper module gone? Try:
```
find /lib/modules -iname 'ndiswrapper.ko'
```

---

### Post by ph0neman on 2008-06-08
great job and thanks for the tutorial worked like a charm.  the only thing i would suggest and i didnt read through the entire thread but i got my wireless to work to connect when i enabled roaming instead of specifying a network 

I am using a Dell E1505 and am typing this on my wireless connection. 

again thanks for the easy tutorial  :)

---

### Post by ucsdrake on 2008-06-09
Hey, I'm still having trouble trying to get this method to work, many of the inputs on the terminal aren't even giving outputs, am I doing something wrong?

```
lukas@Molokai:~$ sudo modprobe -r b43
lukas@Molokai:~$ sudo modprobe b44
lukas@Molokai:~$ sudo echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
lukas@Molokai:~$ sudo echo b43legacy | sudo tee -a /etc/modprobe.d/blacklist
b43legacy
lukas@Molokai:~$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
lukas@Molokai:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'b43legacy'
lukas@Molokai:~$ sudo modprobe b44
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'b43legacy'
lukas@Molokai:~$ gksudo gedit /etc/modprobe.d/blacklist
lukas@Molokai:~$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
lukas@Molokai:~$ lspci -nn | grep 14e4
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
lukas@Molokai:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
lukas@Molokai:~$ lsmod | grep b43
lukas@Molokai:~$ lsmod | grep ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
lukas@Molokai:~$ ls -l /ect/rc.local
ls: cannot access /ect/rc.local: No such file or directory
lukas@Molokai:~$ cd /etc
lukas@Molokai:/etc$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 425 2008-06-08 14:31 /etc/rc.local
lukas@Molokai:/etc$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:fe:1c:c3  
          inet6 addr: fe80::20f:b0ff:fefe:1cc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:449478 (438.9 KB)  TX bytes:40148 (39.2 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67800 (66.2 KB)  TX bytes:67800 (66.2 KB)

lukas@Molokai:/etc$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions
```

---

### Post by dilipmannil on 2008-06-09
This is the output of the following command,

#$ find /lib/modules -iname 'ndiswrapper.ko'
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

How to make "sudo modprobe ndiswrapper" command to detect this path?

---

### Post by jw5801 on 2008-06-09
> **dilipmannil said:**
> This is the output of the following command,

#$ find /lib/modules -iname 'ndiswrapper.ko'
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

How to make "sudo modprobe ndiswrapper" command to detect this path?

Are you sure you have linux-restricted-modules-2.6.24-17 and -18 as well as linux-ubuntu-modules-2.6.24-17 and -18? Try installing:
```
sudo apt-get install ndiswrapper-modules-1.9
```
It's a virtual package which should install linux-ubuntu-modules but we'll see what happens.

If you take a look at the path above, you'll notice that that module is for the older iteration of the kernel (-16 rather than -17 or -18). The module should be the same, but apt should have put it in the other two places as well when you installed the newer kernel (which it hasn't done). If none of the above commands get you the module at /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko, then we can try symlinking the older one:
```
sudo mkdir /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper
sudo ln -s /lib/modules/2.6.24-1{6,8}-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
```

---

### Post by jw5801 on 2008-06-09
> **ucsdrake said:**
> Hey, I'm still having trouble trying to get this method to work, many of the inputs on the terminal aren't even giving outputs, am I doing something wrong?

```
lukas@Molokai:~$ sudo modprobe -r b43
lukas@Molokai:~$ sudo modprobe b44
lukas@Molokai:~$ sudo echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist
blacklist b43
lukas@Molokai:~$ sudo echo b43legacy | sudo tee -a /etc/modprobe.d/blacklist
b43legacy
lukas@Molokai:~$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
lukas@Molokai:~$ sudo modprobe ndiswrapper
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'b43legacy'
lukas@Molokai:~$ sudo modprobe b44
WARNING: /etc/modprobe.d/blacklist line 44: ignoring bad line starting with 'b43legacy'
lukas@Molokai:~$ gksudo gedit /etc/modprobe.d/blacklist
lukas@Molokai:~$ sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
lukas@Molokai:~$ lspci -nn | grep 14e4
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
lukas@Molokai:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4318) present (alternate driver: ssb)
lukas@Molokai:~$ lsmod | grep b43
lukas@Molokai:~$ lsmod | grep ndiswrapper
ndiswrapper           243872  0 
usbcore               169904  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd
lukas@Molokai:~$ ls -l /ect/rc.local
ls: cannot access /ect/rc.local: No such file or directory
lukas@Molokai:~$ cd /etc
lukas@Molokai:/etc$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 425 2008-06-08 14:31 /etc/rc.local
lukas@Molokai:/etc$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:fe:1c:c3  
          inet6 addr: fe80::20f:b0ff:fefe:1cc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:438 errors:0 dropped:0 overruns:0 frame:0
          TX packets:365 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:449478 (438.9 KB)  TX bytes:40148 (39.2 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1356 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67800 (66.2 KB)  TX bytes:67800 (66.2 KB)

lukas@Molokai:/etc$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions
```

Everything looks fine, you've just loaded ndiswrapper in the wrong place in your output above. What happens when you:
```
sudo rmmod ndiswrapper b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```

Alot of the things shouldn't output anything. Only the information producing commands (lsmod iwconfig ifconfig ls) should really output anything, things like modprobe will only output if there are errors (most of the errors you'll see will be when you attempt to remove b43, b44 or ssb when they haven't been added to the kernel, so that's a good error! Means we did something extra that wasn't necessary).

---

### Post by dilipmannil on 2008-06-10
When I tried installing virtual package of ndiswrapper it gave following log,

# sudo apt-get install ndiswrapper-modules-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-modules-1.9 is a virtual package provided by:
  linux-ubuntu-modules-2.6.24-18-rt 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-openvz 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-server 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-generic 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-386 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-16-rt 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-openvz 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-server 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-386 2.6.24-16.23
You should explicitly select one to install.
E: Package ndiswrapper-modules-1.9 has no installation candidate

Then I made symbolic links as  suggested. Did "sudo depmod" and tried running following commands


#sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Invalid module format

The relevent line of dmesg is,
ndiswrapper: disagrees about version of symbol struct_module

---

### Post by imapostdoc on 2008-06-10
wow, what a major achievement!!! after hundreds of repetitions of sudo modprobe ndiswrapper, rmmod b43 b44 ssb in one order or another it finally worked! It's the third time that I get it working again. Now I've saved the
"WALKTHROUGH: Compaq C727 - Broadcom 4311 Setup (HP/Compaq)" by ibun2 on my desktop. Hopefully I won't need it each time I start the beast again.
A great "Thank you" to jw5801 and ibun2!

Peter:lolflag:

---

### Post by jw5801 on 2008-06-10
> **dilipmannil said:**
> When I tried installing virtual package of ndiswrapper it gave following log,

# sudo apt-get install ndiswrapper-modules-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-modules-1.9 is a virtual package provided by:
  linux-ubuntu-modules-2.6.24-18-rt 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-openvz 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-server 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-generic 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-18-386 2.6.24-18.26
  linux-ubuntu-modules-2.6.24-16-rt 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-openvz 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-server 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-generic 2.6.24-16.23
  linux-ubuntu-modules-2.6.24-16-386 2.6.24-16.23
You should explicitly select one to install.
E: Package ndiswrapper-modules-1.9 has no installation candidate

Then I made symbolic links as  suggested. Did "sudo depmod" and tried running following commands


#sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko): Invalid module format

The relevent line of dmesg is,
ndiswrapper: disagrees about version of symbol struct_module

Worth a shot, delete the symlink:
```
sudo rm /lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
```

What output do you get when you install ```
sudo apt-get update 
sudo apt-get install linux-ubuntu-modules-2.6.24-18-generic
```
Because the module is in that package, and really should be there if the package is installed.

---

### Post by dilipmannil on 2008-06-11
Removed symbolic links and tried following commands

#sudo apt-get update
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages                                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources                                                                                                   
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages [206kB]                                                                                      
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages [6156B]                                                                                
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources [68.8kB]                                                                                      
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources [906B]                                                                                  
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages [41.9kB]                                                                                 
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources [7036B]                                                                                   
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages [7687B]                                                                                
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources [1433B]                                                                                
Fetched 399kB in 30s (13.0kB/s)                                                                                                                             
Reading package lists... Done

#sudo apt-get install linux-ubuntu-modules-2.6.24-18-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-ubuntu-modules-2.6.24-18-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.

---

### Post by Steve90210 on 2008-06-11
Edit:

I was having problems with the install before, so I just reinstalled Ubuntu 8.04 LTS and tried this how to again. It appears to have worked first try. I haven't tried turning my wireless switch on and off then on again to see if that works yet though.

So far this is great. Thank you so much! :)

---

### Post by Steve90210 on 2008-06-11
Okay, the on-off switch for the wireless does indeed work.

I'm speechless right now.

The laptop is a HP dv9000 aka dv9420ca and the [hardware specs](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c01063588&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN) are: 


>  Product Name    	 dv9420ca
Product Number 	GL885UA#ABC (French)

GL885UA#ABL (English)
Microprocessor 	1.9 GHz AMD Turion ™ 64 X2 Dual-Core Mobile Technology TL-58
Microprocessor Cache 	512KB+512KB L2 Cache
Memory 	2048 MB DDR2 System Memory (2 Dimm)
Memory Max 	2048 MB max supported
Video Graphics 	NVIDIA GeForce Go 6150 (UMA)
Video Memory 	Up to 559 MB
Hard Drive 	240 GB (5400 RPM) Dual HDD - 120 GB x 2 (SATA)
Multimedia Drive 	LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
Display 	17.0" WXGA+ High-Definition BrightView Widescreen (1440 x 900)
Fax/Modem 	High speed 56k modem
Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
Wireless Connectivity 	802.11b/g WLAN
Multimedia Features 	HP Imprint Finish & HP Pavilion WebCam with Integrated Microphone
Sound 	Altec Lansing
Keyboard 	101-key compatible

Notebook keyboard with scroll bar and integrated numeric keypad

2 Quick Launch Buttons-HP Quick Play Menu and DVD
Pointing Device 	Touch Pad with On/Off button and dedicated vertical scroll Up/Down pad
PC Card Slots 	

    * 1 ExpressCard/54 Slot (also supports ExpressCard/34)

External Ports 	

    * 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards
    * 4 Universal Serial Bus (USB) 2.0
    * 1 Headphone out w/SPDIF Digital Audio
    * 1 microphone-in
    * 1 VGA (15-pin)
    * 1 TV-Out (S-video)
    * 1 RJ-11 (modem)
    * 1 RJ-45 (LAN)
    * 1 Expansion Port 3, 1 IEEE 1394 Firewire (4-pin)
    * 1 Consumer IR (Remote Receiver)

Dimensions 	15.16 (L) x 11.65" (W) x 1.57" (H)
Weight 	7.8 lbs
Security 	

    * Kensington® MicroSaver lock slot
    * Power-on password
    * Accepts 3rd party security lock devices

Power 	

    * 90W AC Adapter
    * 8-Cell Lithium-Ion

What's In The Box 	Mobile Stereo Earbud Headphones (1 pair)

HP Mobile Remote Control

---

### Post by jw5801 on 2008-06-11
> **dilipmannil said:**
> Removed symbolic links and tried following commands
```

#sudo apt-get update
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Translation-en_IN
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates Release [58.5kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Packages                                                                                                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Packages                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/main Sources                                                                                                         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/restricted Sources                                                                                                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Packages                                                                                                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/universe Sources                                                                                                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Packages                                                                                                  
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy/multiverse Sources                                                                                                   
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Packages [206kB]                                                                                      
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Packages [6156B]                                                                                
Get:5 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/main Sources [68.8kB]                                                                                      
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/restricted Sources [906B]                                                                                  
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Packages [41.9kB]                                                                                 
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/universe Sources [7036B]                                                                                   
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Packages [7687B]                                                                                
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) hardy-updates/multiverse Sources [1433B]                                                                                
Fetched 399kB in 30s (13.0kB/s)                                                                                                                             
Reading package lists... Done

#sudo apt-get install linux-ubuntu-modules-2.6.24-18-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-ubuntu-modules-2.6.24-18-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.
```

You might want to run a ```
sudo apt-get dist-upgrade
```since you have 38 packages that haven't been upgraded and see what happens. Otherwise try installing 'linux-ubuntu-modules-2.6.24-17-generic,' I know the module from there will work with the -18 kernel.

---

### Post by jw5801 on 2008-06-11
> **Steve90210 said:**
> Okay, the on-off switch for the wireless does indeed work.

I'm speechless right now.

...

Haha, yeah it's pretty neat. Just a word of caution, if you reboot with the wireless switched off, sometimes it doesn't switch back on again when you come back. I've had it happen a couple of times, resetting the switch in the bios fixes it again.

---

### Post by CaseWestern on 2008-06-11
//sudo rmmod b43 b44 ssb//
sudo modprobe ndiswrapper
sudo modprobe b44

when I issued the first command it says " ERROR: Module b43 does not exist in /proc/modules"

Please resolve my problem.

---

### Post by CaseWestern on 2008-06-12
Awesome.....I am shell shocked after seeing light on wifi indicator....Great going and 1000 thanks to the thread initiator.

I am newbie to ubuntu and also to linux.  I am in the process of getting acquainted to the OS.  Yesterday I installed vpn client and today I configured my wireless card.  Thanks for your help.

Cheers.

---

### Post by jw5801 on 2008-06-12
> **CaseWestern said:**
> //sudo rmmod b43 b44 ssb//
sudo modprobe ndiswrapper
sudo modprobe b44

when I issued the first command it says " ERROR: Module b43 does not exist in /proc/modules"

Please resolve my problem.

That one just means that 'b43' isn't loaded, which doesn't matter at all, since we're trying to unload it.

---

### Post by dilipmannil on 2008-06-12
I tried running "sudo apt-get dist-upgrade" which upgraded some packages like g++, firefox etc but not ndiswrapper.

Also running these commands gave following output

#sudo apt-get install linux-ubuntu-modules-2.6.24-17-generic
[sudo] password for dilip: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.24-17-generic

# sudo modprobe ndiswrapper
FATAL: Could not open '/lib/modules/2.6.24-18-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko': No such file or directory

#uname -r
2.6.24-18-generic

can I use the method decribed in paperdiesel's howto to compile and install only ndiswrapper and follow the rest of the steps in this howto? Will this solve the problem with ndiswrapper incompatability with my version of ubuntu?

---

### Post by dilipmannil on 2008-06-12
Atlast wireless card is up. I followed the step in paperdiesel's howto to download and install ndiswrapper and rest of the steps of your howto to install driver. Now Fn+F2 key switches on the wifi light on my laptop. Thanks a lot for your help by posts and this nice HOWTO. 

Executing the following command gave this output

Code:
```
sudo iwlist scanning
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:FE:48:A8
                    ESSID:"CESC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-23 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
eth0      Interface doesn't support scanning[CODE]
```[/CODE]

Its able to find  my router. I tried configuring the network using wifi-radar. But after selecting my router and clicked "connect", it tried acquiring IP for some time and exited without success. Why is this happening?

---

### Post by emicsun on 2008-06-12
Thank you for this help, however I think my problem all the way was that I did not update my solaris grub loader with the new kernel file names which could possible happen to others, eh?

---

### Post by jw5801 on 2008-06-12
> **dilipmannil said:**
> Atlast wireless card is up. I followed the step in paperdiesel's howto to download and install ndiswrapper and rest of the steps of your howto to install driver. Now Fn+F2 key switches on the wifi light on my laptop. Thanks a lot for your help by posts and this nice HOWTO. 

Executing the following command gave this output

Code:
```
sudo iwlist scanning
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1B:2F:FE:48:A8
                    ESSID:"CESC"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-23 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
eth0      Interface doesn't support scanning
```

Its able to find  my router. I tried configuring the network using wifi-radar. But after selecting my router and clicked "connect", it tried acquiring IP for some time and exited without success. Why is this happening?

Yep, compiling was to be the next resort. You should definitely file a bug against linux-ubuntu-modules though.

Quality 100? Are you sitting on the router?! The first thing to try is disabling WPA and WEP and seeing if you can connect to a completely open network, then once you can, step the security back up incrementally, connecting as you go to identify where the issue is.

---

### Post by dilipmannil on 2008-06-13
Yeah :) Am sitting near to router. When I switched on the laptop today and tried to switch on wifi(fn+f2) it is not working. Wifi LED is also not glowing. Executed the commands in /etc/rc.local script manually with only one change. Executed "modprobe -r ndiswrapper" extra and it started working.

```
modprobe -r b44
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

```

I don't have any ndiswrapper entry in /etc/modules. It was working fine yesterday without this line. Why is this happening?

---

### Post by dilipmannil on 2008-06-13
Still the problem is not solved. I need to manually run the following commands after each reboot for wifi to work,

```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

```

I have added this to /etc/rc. local script. But I think it is not getting executed at startup.

```
$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

exit 0

```

 ```
#ls -al /etc/rc.local
-rwxr-xr-x 1 root root 445 2008-06-13 23:53 /etc/rc.local
```

---

### Post by Grendel336 on 2008-06-13
OK, I'm brand spanky new to linux and ubuntu. Like maybe an hour of experience total.

I have a Dell Inspiron E1505 32 bit laptop with Vista and the wireless Mini-Card being discussed here. Same problems connecting to my wireless Linksys system that Vista finds without problem. 


The question I have is:

My wifi light is **on** and I still can't connect. 
Do I still have to try to run through the exercise in the first post?

Thanks for any help.

---

### Post by jw5801 on 2008-06-13
> **Grendel336 said:**
> OK, I'm brand spanky new to linux and ubuntu. Like maybe an hour of experience total.

I have a Dell Inspiron E1505 32 bit laptop with Vista and the wireless Mini-Card being discussed here. Same problems connecting to my wireless Linksys system that Vista finds without problem. 


The question I have is:

My wifi light is **on** and I still can't connect. 
Do I still have to try to run through the exercise in the first post?

Thanks for any help.

Have you run through the How-To? If not then you'll be using b43, the open source driver for these chipsets that I'm not particularly fond of, in which case you'll need to enable some firmware in the 'Restricted Drivers Manager' (probably under System > Hardware Drivers). Otherwise give this how-to a try, which uses a different method.

---

### Post by jw5801 on 2008-06-13
> **dilipmannil said:**
> Still the problem is not solved. I need to manually run the following commands after each reboot for wifi to work,

```
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

```

I have added this to /etc/rc. local script. But I think it is not getting executed at startup.

```
$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper
modprobe b44

exit 0

```

 ```
#ls -al /etc/rc.local
-rwxr-xr-x 1 root root 445 2008-06-13 23:53 /etc/rc.local
```

You're not having much luck with anything are you? 

Do you have a /etc/init.d/rc.local? And is it linked in the runlevels?
```
cat /etc/init.d/rc.local
update-rc.d -n -f rc.local remove
```
The '-n' there tells it not to actually do anything, just to show what would happen.

---

### Post by Grendel336 on 2008-06-13
> **jw5801 said:**
> Have you run through the How-To? If not then you'll be using b43, the open source driver for these chipsets that I'm not particularly fond of, in which case you'll need to enable some firmware in the 'Restricted Drivers Manager' (probably under System > Hardware Drivers). Otherwise give this how-to a try, which uses a different method.

I'm sorry for my ignorance. 

By running the "How to" are you talking about the things in the first post of this thread? 

I don't know what b43 is. 

I'll have to see if I can find the "hardware drivers". The last time I looked around in ubuntu I could not find anything like that. I'll try again. I'm excited about learning this system. I just wish I didn't have to keep going back to Vista to communicate with you wonderful people.

Thanks again.

---

### Post by dilipmannil on 2008-06-14
Today when I booted-up the laptop wifi card is getting detected. It is pretty strange that occurance of this problem is random. Anyway, I tried the following commands,

#cat /etc/init.d/rc.local 
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
        if [ -x /etc/rc.local ]; then
                log_begin_msg "Running local boot scripts (/etc/rc.local)"
                /etc/rc.local
                log_end_msg $?
        fi
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
# update-rc.d -n -f rc.local remove
 Removing any system startup links for /etc/init.d/rc.local ...
   /etc/rc2.d/S99rc.local
   /etc/rc3.d/S99rc.local
   /etc/rc4.d/S99rc.local
   /etc/rc5.d/S99rc.local

Are you able to figure out something wrong in the above command outputs?

---

### Post by jw5801 on 2008-06-14
> **dilipmannil said:**
> Today when I booted-up the laptop wifi card is getting detected. It is pretty strange that occurance of this problem is random. Anyway, I tried the following commands,

#cat /etc/init.d/rc.local 
#! /bin/sh

PATH=/sbin:/bin:/usr/sbin:/usr/bin
[ -f /etc/default/rcS ] && . /etc/default/rcS
. /lib/lsb/init-functions

do_start() {
        if [ -x /etc/rc.local ]; then
                log_begin_msg "Running local boot scripts (/etc/rc.local)"
                /etc/rc.local
                log_end_msg $?
        fi
}

case "$1" in
    start)
        do_start
        ;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
# update-rc.d -n -f rc.local remove
 Removing any system startup links for /etc/init.d/rc.local ...
   /etc/rc2.d/S99rc.local
   /etc/rc3.d/S99rc.local
   /etc/rc4.d/S99rc.local
   /etc/rc5.d/S99rc.local

Are you able to figure out something wrong in the above command outputs?

That all looks as it should, so the module should be getting loaded as required. Are you connecting to networks now?

---

### Post by Grendel336 on 2008-06-14
> **Grendel336 said:**
> I'm sorry for my ignorance. 

By running the "How to" are you talking about the things in the first post of this thread? 

I don't know what b43 is. 

I'll have to see if I can find the "hardware drivers". The last time I looked around in ubuntu I could not find anything like that. I'll try again. I'm excited about learning this system. I just wish I didn't have to keep going back to Vista to communicate with you wonderful people.

Thanks again.

Just hoping this post doesn't get lost on an old page. 

I did a quick look for the hardware/driver list through the Admin  menu and I found nothing that I could enable or disable that might resemble a wireless card.

---

### Post by jw5801 on 2008-06-14
> **Grendel336 said:**
> Just hoping this post doesn't get lost on an old page. 

I did a quick look for the hardware/driver list through the Admin  menu and I found nothing that I could enable or disable that might resemble a wireless card.

b43 is a kernel module (a 'driver' for your card), I tend to prefer ndiswrapper (another module, which takes a Windows driver file and uses it with the linux kernel) over b43 for stability and performance reasons. So, if you follow the How-To (the first post) then you will remove b43 (the light will go off which is ok, since at the moment it's not working properly anyway) and configure ndiswrapper to work for your card.

---

### Post by Grendel336 on 2008-06-14
> **jw5801 said:**
> b43 is a kernel module (a 'driver' for your card), I tend to prefer ndiswrapper (another module, which takes a Windows driver file and uses it with the linux kernel) over b43 for stability and performance reasons. So, if you follow the How-To (the first post) then you will remove b43 (the light will go off which is ok, since at the moment it's not working properly anyway) and configure ndiswrapper to work for your card.

Thank you very much. That explained some things for me in a way I can understand. I'm sure the process in the first post will be a fun exercise and get my feet wet just a bit in ubuntu/linux. 

Hopefully my next post will be from a linux os. :)

---

### Post by dilipmannil on 2008-06-14
Now the wifi card is getting detected almost consistently after startup. I have not got network up yet. As suggested turned off encryption of my router and used wifi-radar to connect to the network. It got connected successfully and got an ip address via dhcp(10.0.0.3). But I am not able to connect to internet or ping any websites. I am able to successfully ping 10.0.0.1(which is router). I am using same router for wired card and it works perfectly fine for internet. Since I am able to ping the router over wifi, I hope wifi driver is working perfectly fine and there is some problem with some other configurations. Can anyone give some pointer regarding how to tackle this problem ?

---

### Post by jw5801 on 2008-06-14
> **dilipmannil said:**
> Now the wifi card is getting detected almost consistently after startup. I have not got network up yet. As suggested turned off encryption of my router and used wifi-radar to connect to the network. It got connected successfully and got an ip address via dhcp(10.0.0.3). But I am not able to connect to internet or ping any websites. I am able to successfully ping 10.0.0.1(which is router). I am using same router for wired card and it works perfectly fine for internet. Since I am able to ping the router over wifi, I hope wifi driver is working perfectly fine and there is some problem with some other configurations. Can anyone give some pointer regarding how to tackle this problem ?

If you can ping the router then the driver and card are working fine. Probably a DNS issue, have you connected wirelessly through the router before? If you haven't it might be a router setting for Wireless that's playing up, otherwise your install is being odd again, so have a look at /etc/resolv.conf ```
cat /etc/resolv.conf
```

---

### Post by dilipmannil on 2008-06-15
These are the command outputs,
```
# cat /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4921
#
### END INFO

nameserver 10.0.0.1

```
Now I am able to ping google.com once connection is made over wifi to my router. But I am not able to open that webpage on the firefox browser. Firefox internet options seems to be okay with "Use System Proxy Settings" highlighted.

After this I switched off wifi(fn+f2) and reverted back to wired internet. But now I am not able to ping google.com (or) open it in firefox. Tried pinging router
```
#ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 10.0.0.3 icmp_seq=2 Destination Host Unreachable
From 10.0.0.3 icmp_seq=3 Destination Host Unreachable

```

Below is the output of ifconfig,

#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6b:59:dd  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6b:59dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:348733 (340.5 KB)  TX bytes:54291 (53.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77716 (75.8 KB)  TX bytes:77716 (75.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:71:b4:5e  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe71:b45e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17174 (16.7 KB)  TX bytes:19388 (18.9 KB)
          Interrupt:17 Memory:dfdfc000-dfe00000 


Eventhough the IP address acquired for wired connection was 10.0.0.2 ping was done from 10.0.0.3 which was the IP for wifi connection. Why is this happening? After reboot again the wired connection works fine.

---

### Post by jw5801 on 2008-06-15
> **dilipmannil said:**
> These are the command outputs,
```
# cat /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4921
#
### END INFO

nameserver 10.0.0.1

```
Now I am able to ping google.com once connection is made over wifi to my router. But I am not able to open that webpage on the firefox browser. Firefox internet options seems to be okay with "Use System Proxy Settings" highlighted.

After this I switched off wifi(fn+f2) and reverted back to wired internet. But now I am not able to ping google.com (or) open it in firefox. Tried pinging router
```
#ping 10.0.0.1
PING 10.0.0.1 (10.0.0.1) 56(84) bytes of data.
From 10.0.0.3 icmp_seq=2 Destination Host Unreachable
From 10.0.0.3 icmp_seq=3 Destination Host Unreachable

```

Below is the output of ifconfig,

```
#ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:6b:59:dd  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe6b:59dd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:425 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:348733 (340.5 KB)  TX bytes:54291 (53.0 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1520 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1520 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:77716 (75.8 KB)  TX bytes:77716 (75.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:71:b4:5e  
          inet addr:10.0.0.3  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe71:b45e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:187 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17174 (16.7 KB)  TX bytes:19388 (18.9 KB)
          Interrupt:17 Memory:dfdfc000-dfe00000 
```


Eventhough the IP address acquired for wired connection was 10.0.0.2 ping was done from 10.0.0.3 which was the IP for wifi connection. Why is this happening? After reboot again the wired connection works fine.

See how wlan0 (your wireless interface) is still present? That means network-manager expects to still be able to use that interface, even though you've cut the power to the device. A "sudo ifconfig wlan0 down" should fix that.

Just switching off the device is not the best way to do this. As far as network manager is concerned it still has the wireless IP until the lease expires. You shouldn't need to switch the wireless card off in order to tell it to use the wired connection, if you don't switch it off then it can gracefully close the connection and release the IP back to the dhcp pool. That being said, if you turn it off and then tell network manager to connect using the wired connection, all should be fine, there's no need to turn it off though. (This is possibly one of the many reasons I'm not fond of network-manager and instead use Wicd).

You don't have a proxy or anything set up for the wired connection? When you're connected using the wired connection what is present in /etc/resolv.conf? At the moment it's set up to use your router as the default gateway when connected over wireless, I'm just wondering if the router is set up to ignore DNS (Domain Name Service, the method used to establish an IP from a domain name) requests for wireless connections?

---

### Post by dilipmannil on 2008-06-15
Now I am able to connect and browse internet using firefox. The "work offline" option of firefox was checked before due to which I was able to ping but not able to connect to internet over wifi. But I still wonder how was it working for wired one.
I don't have a  proxy for network connection.

 When using wired connection,

```
$ cat /etc/resolv.conf 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   4929
#
### END INFO



nameserver 10.0.0.1

```

But when using wifi connection,

```
$ cat /etc/resolv.conf
nameserver 10.0.0.1

```

I am using wifi-radar for managing wifi connection. Only difference is the header part which contains the comments by NetworkManager. After switching back to wired connection from wifi I need to execute "sudo ifconfig wlan0 down" to get wired working, without which it still tries pinging from the IP acquired duing wifi session. I think network manager comes default with Ubuntu. Is it a good idea to remove both network-manager and wifi-radar and install wicd to manage both wired and wireless connections? If so, how can I remove network manager?

---

### Post by dilipmannil on 2008-06-15
After enabling WPA encryption on my router I am not able to connect to router over wifi. It was working fine when encryption was off. I am using wifi-radar to connect. It tries to acquire IP for sometime and fail. Saw on some blog that /etc/wpa_supplicant/wpa_supplicant.conf is needed which is not there in my installation(Ubuntu 8.04). I has some other files in that directoy.

```
# ls -l  /etc/wpa_supplicant/
total 28
-rwxr-xr-x 1 root root 22485 2008-03-13 02:58 functions.sh
-rwxr-xr-x 1 root root  3133 2008-03-13 02:58 ifupdown.sh

```
Also on wifi-radar gui there is one "Use WPA " option uder which we have to configure driver. Something like "wext" etc. How can I check whether this driver is on my installation?

---

### Post by jw5801 on 2008-06-15
> **dilipmannil said:**
> After enabling WPA encryption on my router I am not able to connect to router over wifi. It was working fine when encryption was off. I am using wifi-radar to connect. It tries to acquire IP for sometime and fail. Saw on some blog that /etc/wpa_supplicant/wpa_supplicant.conf is needed which is not there in my installation(Ubuntu 8.04). I has some other files in that directoy.

```
# ls -l  /etc/wpa_supplicant/
total 28
-rwxr-xr-x 1 root root 22485 2008-03-13 02:58 functions.sh
-rwxr-xr-x 1 root root  3133 2008-03-13 02:58 ifupdown.sh

```
Also on wifi-radar gui there is one "Use WPA " option uder which we have to configure driver. Something like "wext" etc. How can I check whether this driver is on my installation?

I honestly don't know much about WPA connections, for that I refer you to kevdog's [thread](http://ubuntuforums.org/showthread.php?t=571188) for some connection troubleshooting. You shouldn't need the first section about commandline connecting. But the later section on configuring WPA could come in handy. To answer your question the wpa_supplicant driver that you're after is simply the driver powering your card, so in this case 'ndiswrapper' (**EDIT**: I stand corrected, apparently for ndiswrapper we should use wext in spite of the documentation. Hopefully following that part of kevdog's tutorial should help you learn enough to fill in the boxes in the WifiRadar (or wicd) WPA setup).

As far as completely removing network-manager goes, a "sudo apt-get remove network-manager" should do it. I personally prefer wicd, but it's basically a matter of preference. As a word of warning, I don't think WifiRadar can handle wired connections, so if you remove it, you'll have to command line for those. "sudo ifconfig eth0 up" then "sudo dhclient eth0" should be all you need to get an IP though. I think Wicd can do wired connections for you, but I'm not certain.

---

### Post by jhallward on 2008-06-16
I'm getting the 'no wireless interfaces' problem, in other words, after loading ndiswrapper, neither iwconfig nor ifconfig show any wireless extensions such as eth1 or wlan0.  I've searched around and clearly a number of people are having or have had this problem.  For some reason though the only solution anybody has posted is something to the tune of "I reinstalled and it just worked this time around" or "I screwed around with things until it worked, but I'm not sure what did it".  I fall in the latter group, this is the third time I've run into this problem (first two times on Ubuntu and now on Gentoo), only this time I've been stuck at this point for a few months (since upgrading to the new 2.6.24 kernel).

Can we figure out what's causing this once and for all?  This is such a common problem that I feel it's caused by the same 'bug' (for lack of a better word, because it's probably a configuration issue) and is something the ndiswrapper developers should address, but since they're not, can we get down to it at least?

Here's my output to the generic stuff:

```
lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
```

```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

Notice how bcm43xx is listed as the 'alternate driver'?  Well, the ndiswrapper documentation claims that if an 'alternate driver' is listed that driver may be used by ndiswrapper to "initialize" the hardware.  Coincidentally bcm43xx doesn't initialize any interfaces either.  So maybe the problem lies with bcm43xx and not ndiswrapper, but who knows at this point, because I've not been able to make any headway with bcm43xx either.  It's possible that a single problem is resulting in the same bug indepdendently in both cases, so we can't assume it's a casual relationship until I make some progress with bcm43xx and see that the changes carry over to ndiswrapper.

the lsmod output also is good.  Gentoo doesn't have an rc.local file, and I don't want to get into details about it here, so just assume the startup order is fine (because I can simulate setting the order to whatever I want by just unloading and reloading the appropriate modules in the correct order, and switching things around like this hasn't helped me at all).

So far the only ideas I have are that it could be a networking stack issue (since it was changed in 2.6.24 and I haven't been able to get ndiswrapper or bcm43xx to work since 2.6.23), it could be a udev issue (but I've tinkered around with /etc/udev/rules.d/70-persistent-net.rules -or whatever it is- a bit and it hasn't solved anything), an issue with bcm43xx, or an issue with ndiswrapper itself, beyond that I've hit a dead end.

Oh also, dmesg gives a single line of output on 'modprobe ndiswrapper':
```

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

```
(I get something equivalent with bcm43xx).
I'm thinking more should be shown...

Any help that any of you can give me with this would be hugely appreciated.

---

### Post by jw5801 on 2008-06-16
> **jhallward said:**
> I'm getting the 'no wireless interfaces' problem, in other words, after loading ndiswrapper, neither iwconfig nor ifconfig show any wireless extensions such as eth1 or wlan0.  I've searched around and clearly a number of people are having or have had this problem.  For some reason though the only solution anybody has posted is something to the tune of "I reinstalled and it just worked this time around" or "I screwed around with things until it worked, but I'm not sure what did it".  I fall in the latter group, this is the third time I've run into this problem (first two times on Ubuntu and now on Gentoo), only this time I've been stuck at this point for a few months (since upgrading to the new 2.6.24 kernel).

Can we figure out what's causing this once and for all?  This is such a common problem that I feel it's caused by the same 'bug' (for lack of a better word, because it's probably a configuration issue) and is something the ndiswrapper developers should address, but since they're not, can we get down to it at least?

Here's my output to the generic stuff:

```
lspci -nn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
```

```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: bcm43xx)

```

Notice how bcm43xx is listed as the 'alternate driver'?  Well, the ndiswrapper documentation claims that if an 'alternate driver' is listed that driver may be used by ndiswrapper to "initialize" the hardware.  Coincidentally bcm43xx doesn't initialize any interfaces either.  So maybe the problem lies with bcm43xx and not ndiswrapper, but who knows at this point, because I've not been able to make any headway with bcm43xx either.  It's possible that a single problem is resulting in the same bug indepdendently in both cases, so we can't assume it's a casual relationship until I make some progress with bcm43xx and see that the changes carry over to ndiswrapper.

the lsmod output also is good.  Gentoo doesn't have an rc.local file, and I don't want to get into details about it here, so just assume the startup order is fine (because I can simulate setting the order to whatever I want by just unloading and reloading the appropriate modules in the correct order, and switching things around like this hasn't helped me at all).

So far the only ideas I have are that it could be a networking stack issue (since it was changed in 2.6.24 and I haven't been able to get ndiswrapper or bcm43xx to work since 2.6.23), it could be a udev issue (but I've tinkered around with /etc/udev/rules.d/70-persistent-net.rules -or whatever it is- a bit and it hasn't solved anything), an issue with bcm43xx, or an issue with ndiswrapper itself, beyond that I've hit a dead end.

Oh also, dmesg gives a single line of output on 'modprobe ndiswrapper':
```

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

```
(I get something equivalent with bcm43xx).
I'm thinking more should be shown...

Any help that any of you can give me with this would be hugely appreciated.

Gentoo :). I'm playing with it on another partition at the moment, enjoying it so far! I do have ndiswrapper working for this card using a similar method to the one I use in Ubuntu (which is a little different to this How-To). I have removed /etc/init.d/net.eth0, so that b44 isn't added so I don't have to deal with the ssb issue either, it's just a matter of adding net.wlan0 and adding ndiswrapper to /etc/modules.autoload.d/kernel-2.6.

Have you reemerged ndiswrapper since changing to the newer kernel? It sounds like you haven't since bcm43xx isn't present in the 2.6.24 series kernels, b43 has replaced it. I'd just leave out b43 from your kernel when you compile it anyway, then you only have to deal with the ssb issue.

As far as this being a 'bug' I'm much more inclined to put it down to something not being completed correctly during the first installation, hence the reinstall 'fixes' the 'bug'. Which is almost certainly what the ndiswrapper devs will put it down to if you report it as such.

Something to try is 'ndiswrapper -m' which writes an alias to wlan0, so that when you bring up wlan0, the ndiswrapper module is autoloaded. But I can't see how that would make a difference in your case, since loading ndiswrapper should bring up wlan0 anyway.

Do you get anything interesting when you:
```
sudo rmmod bcm43xx b43 b43legacy b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n15
```The kernel should complain that bcm43xx, b43, b43legacy and ndiswrapper aren't present in /proc/modules, if it doesn't then something interesting is happening somewhere.

---

### Post by dilipmannil on 2008-06-16
Thanks a lot for your help jw5801. Got wifi working with WPA turned on.......

---

### Post by Grendel336 on 2008-06-16
To explain my newbness:

> lspci -nn | grep 14e4

How do I type this? Are there spaces where it looks like spaces?
What is the straight line between the -nn and the grep? Do I type that straight line somehow, or does that represent something else? 

Thanks for your help and sorry for the beyond-easy questions.

---

### Post by schlort on 2008-06-16
yes, there are spaces (as such)
lspci [sp] -nn [sp] | [sp] grep [sp] 14e4
the '|' is a pipe, which on a typical keyboard is found on the backslash key.

---

### Post by Grendel336 on 2008-06-16
> **schlort said:**
> yes, there are spaces (as such)
lspci [sp] -nn [sp] | [sp] grep [sp] 14e4
the '|' is a pipe, which on a typical keyboard is found on the backslash key.

Thank you. 

|  <-- :)

A "pipe" huh? Looks different on keybord than it looks on screen.

---

### Post by jw5801 on 2008-06-16
When everyone completes the new kernel upgrade, make sure to also install ```
sudo apt-get install linux-ubuntu-modules-2.6.24-19-generic
```

---

### Post by jhallward on 2008-06-17
> **jw5801 said:**
> Gentoo :). I'm playing with it on another partition at the moment, enjoying it so far! I do have ndiswrapper working for this card using a similar method to the one I use in Ubuntu (which is a little different to this How-To). I have removed /etc/init.d/net.eth0, so that b44 isn't added so I don't have to deal with the ssb issue either, it's just a matter of adding net.wlan0 and adding ndiswrapper to /etc/modules.autoload.d/kernel-2.6.

Have you reemerged ndiswrapper since changing to the newer kernel? It sounds like you haven't since bcm43xx isn't present in the 2.6.24 series kernels, b43 has replaced it. I'd just leave out b43 from your kernel when you compile it anyway, then you only have to deal with the ssb issue.


I have reemerged ndiswrapper since changing kernels, bcm43xx is still supported in the newer kernels, it's just listed as "depricated" in the kernel config.  In fact I emerged the newest (masked) version of ndiswrapper yesterday, so I know it's not a kernel compatibility issue.  I'm going to try eliminating bcm43xx from the kernel config to force ndiswrapper to use something else for initialization and see what happens.

> 
As far as this being a 'bug' I'm much more inclined to put it down to something not being completed correctly during the first installation, hence the reinstall 'fixes' the 'bug'. Which is almost certainly what the ndiswrapper devs will put it down to if you report it as such.


Right, what would have liked would be for this to be listed on the official ndiswrapper troubleshooting page saying something like "if you do A, B or C you won't see any wireless interfaces, to fix this do X, Y and then Z".

> 
Something to try is 'ndiswrapper -m' which writes an alias to wlan0, so that when you bring up wlan0, the ndiswrapper module is autoloaded. But I can't see how that would make a difference in your case, since loading ndiswrapper should bring up wlan0 anyway.

Right, didn't do anything.

> 
Do you get anything interesting when you:
```
sudo rmmod bcm43xx b43 b43legacy b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n15
```The kernel should complain that bcm43xx, b43, b43legacy and ndiswrapper aren't present in /proc/modules, if it doesn't then something interesting is happening somewhere.

I got all the relevant complaints, and then all I get from the dmesg is:
```

TKIP decrypt: ************
TKIP decrypt: ************
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
phy0: Removed STA 00:1d:5a:06:04:a1
ndiswrapper version 1.53 loaded (smp=yes, preempt=no)

```

Most of that is just junk from NetworkManager (normally TKIP decrypt: would list some hex data after it, but I got rid of it for security reasons, replaced first by *****'s and then by empty space), the only line that results from the commands you gave me is the last one.

---

### Post by jw5801 on 2008-06-17
> **jhallward said:**
> I have reemerged ndiswrapper since changing kernels, bcm43xx is still supported in the newer kernels, it's just listed as "depricated" in the kernel config.  In fact I emerged the newest (masked) version of ndiswrapper yesterday, so I know it's not a kernel compatibility issue.  I'm going to try eliminating bcm43xx from the kernel config to **force ndiswrapper to use something else for initialization** and see what happens.

The highlighted statement above shows a bit of misunderstanding. bcm43xx is *not* used by ndiswrapper at all! It's an alternative to ndiswrapper, loading it at all will cause ndiswrapper to fail (pretty much as you describe it doing). If it's compiled into your kernel, recompile without it, if it's there as a module, blacklist it, the same applies for b43 (the replacement of bcm43xx):
```
echo -e "blacklist bcm43xx\nblacklist b43" >> /etc/modprobe.d/blacklist
update-modules
```

> Right, what would have liked would be for this to be listed on the official ndiswrapper troubleshooting page saying something like "if you do A, B or C you won't see any wireless interfaces, to fix this do X, Y and then Z".
Fair call. If we discover a common configuration issue that people often make, then it would probably be worth suggesting to their documentation maintainers.

> I got all the relevant complaints, and then all I get from the dmesg is:
```
TKIP decrypt: ************
TKIP decrypt: ************
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
TKIP decrypt:
phy0: Removed STA 00:1d:5a:06:04:a1
ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
```

Most of that is just junk from NetworkManager (normally TKIP decrypt: would list some hex data after it, but I got rid of it for security reasons, replaced first by *****'s and then by empty space), the only line that results from the commands you gave me is the last one.

It appears as though ndiswrapper is not finding the card at all. What does lshw report about the device? You may need to "emerge lshw" then run:
```
lshw -C network
```
You want to make sure that the device isn't listed as 'UNCLAIMED' and that in the 'configuration' section you see 'driver=ndiswrapper+bcmwl5'.

---

### Post by jhallward on 2008-06-17
I've got some more useful output from various commands.

"lshw -C network" gvae me some interesting results:
```

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
 *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       <edited this section down since it's not relevant>
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: dummy0
       serial: 16:1d:6e:30:4d:1d
       capabilities: ethernet physical
       configuration: broadcast=yes

```

As expected ndiswrapper doesn't show up in the configuration line, but interestingly the device is still 'claimed'.  Any idea if I should worry about who's claimed what here?  And if so, how do I tell ndiswrapper to claim the hardware?

> 
The highlighted statement above shows a bit of misunderstanding. bcm43xx is not used by ndiswrapper at all! It's an alternative to ndiswrapper, loading it at all will cause ndiswrapper to fail (pretty much as you describe it doing). If it's compiled into your kernel, recompile without it, if it's there as a module, blacklist it, the same applies for b43 (the replacement of bcm43xx):

Ah, I guess I was reading too far into the ndiswrapper documentation.  I was just being stupid, thanks.  bcm43xx had been compiled as a module and blacklisted this entire time though, and it doesn't work either (same problem as what I'm getting with ndiswrapper) so I don't know if it would even have mattered.  I'm now running a kernel without bcm43xx at all, and still no improvement, though now the output of ndiswrapper -l has changed to reflect the lack of bcm43xx of course.

I stumbled across some useful debugging output though, it seems the ndiswrapper driver is just never loaded.  I recompiled the ndiswrapper module with debugging options and then loaded it up as so,
```

make DEBUG=6 IO_DEBUG=1 EVENT_DEBUG=1
insmod ./ndiswrapper.ko debug=3

```
and then loaded it into the kernel, here's a sample of what I got (bolding is my own):
```

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (ntoskernel_init:2514): 128581578310362050
ndiswrapper (wrap_worker_init:2473): d98c1e54
ndiswrapper (wrap_worker_init_func:2462): d98c1e54
ndiswrapper (allocate_object:142): allocated hdr: e125ea80, body: e125eaa0
ndiswrapper (wrap_worker_init:2483): e125eaa0
ndiswrapper (ntoskernel_init:2535): e125eaa0
ndiswrapper (add_bus_driver:174): bus driver PCI is at d98bc028
ndiswrapper (add_bus_driver:174): bus driver USB is at d98bc128
ndiswrapper (ntoskernel_init:2549): f7c03600
ndiswrapper (wrap_worker_init:2473): d98c1e68
ndiswrapper (wrap_worker_init_func:2462): d98c1e68
ndiswrapper (allocate_object:142): allocated hdr: e125e9c0, body: e125e9e0
ndiswrapper (wrap_worker_init:2483): e125e9e0
ndiswrapper (ndis_init:2974): e125e9e0
ndiswrapper (wrap_worker_init:2473): d98c1e68
ndiswrapper (wrap_worker_init_func:2462): d98c1e68
ndiswrapper (allocate_object:142): allocated hdr: e125e660, body: e125e680
ndiswrapper (wrap_worker_init:2483): e125e680
ndiswrapper (wrapndis_init:2072): e125e680
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (notifier_event:1692): Enter 0x1
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (notifier_event:1692): Enter 0x1
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27a0:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27a0, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27a0, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter 
[b]ndiswrapper (load_wrap_device:706): couldn't load device 8086:27a0; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27d8:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27d8, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27d8, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter 
**ndiswrapper (load_wrap_device:706): couldn't load device 8086:27d8; check system log for messages from 'loadndisdriver'**
ndiswrapper (load_wrap_device:707): Exit
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:2448:0000:0000
ndiswrapper (load_wrap_device:679): Enter 8086, 2448, 0000, 0000
ndiswrapper (load_wrap_device:695): 8086, 2448, 0000, 0000, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 8086:2448; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27b9:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27b9, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27b9, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 8086:27b9; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27da:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27da, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27da, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 8086:27da; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_usb_device:661): Enter 0b97, 7762, 0000
ndiswrapper (load_wrap_device:679): Enter 0b97, 7762, 0000, 0000
ndiswrapper (load_wrap_device:695): 0b97, 7762, 0000, 0000, 000f
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 0b97:7762; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_usb_device:680): 00000000
ndiswrapper (wrap_pnp_start_usb_device:695): ret: -19
ndiswrapper (wrap_pnp_start_usb_device:697): Exit
usbcore: registered new interface driver ndiswrapper
ndiswrapper (register_devices:646): Exit
ndiswrapper (loader_init:858): Exit
ndiswrapper (wrapper_init:111): Exit

```

It looks like ndiswrapper (probably via loadndisdriver) is trying to load the driver and failing for whatever reason.  I don't see any of the supposed debugging (dmesg) output from loadndisdriver that should be picked up by syslog though.  Anyone know what I need to do to start seeing loadndisdriver's output?

---

### Post by jhallward on 2008-06-17
Also, here are the names of the packages I've used for drivers i've tried with ndiswrapper (the bcmwl5.inf file)
HP: SP23107A SP34152 SP37950 
Dell: R174281 R151519

The number indicates version, but based on the variety I've used I'm thinking it's not a driver problem.  Note that the dell drivers are made specifically for Dell's version of the BCM4311 (or BCM94311, not sure what the difference is), while HP's are more generic, yet neither work here.  I can't guarantee this, but I'm pretty sure one of these five worked in the past, since I don't remember ever getting drivers from anywhere besides HP or Dell.

---

### Post by jw5801 on 2008-06-17
> **jhallward said:**
> I've got some more useful output from various commands.

"lshw -C network" gvae me some interesting results:
```

 *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
 *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       <edited this section down since it's not relevant>
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: dummy0
       serial: 16:1d:6e:30:4d:1d
       capabilities: ethernet physical
       configuration: broadcast=yes

```

As expected ndiswrapper doesn't show up in the configuration line, but interestingly the device is still 'claimed'.  Any idea if I should worry about who's claimed what here?  And if so, how do I tell ndiswrapper to claim the hardware?


Ah, I guess I was reading too far into the ndiswrapper documentation.  I was just being stupid, thanks.  bcm43xx had been compiled as a module and blacklisted this entire time though, and it doesn't work either (same problem as what I'm getting with ndiswrapper) so I don't know if it would even have mattered.  I'm now running a kernel without bcm43xx at all, and still no improvement, though now the output of ndiswrapper -l has changed to reflect the lack of bcm43xx of course.

I stumbled across some useful debugging output though, it seems the ndiswrapper driver is just never loaded.  I recompiled the ndiswrapper module with debugging options and then loaded it up as so,
```

make DEBUG=6 IO_DEBUG=1 EVENT_DEBUG=1
insmod ./ndiswrapper.ko debug=3

```
and then loaded it into the kernel, here's a sample of what I got (bolding is my own):
```

ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
ndiswrapper (ntoskernel_init:2514): 128581578310362050
ndiswrapper (wrap_worker_init:2473): d98c1e54
ndiswrapper (wrap_worker_init_func:2462): d98c1e54
ndiswrapper (allocate_object:142): allocated hdr: e125ea80, body: e125eaa0
ndiswrapper (wrap_worker_init:2483): e125eaa0
ndiswrapper (ntoskernel_init:2535): e125eaa0
ndiswrapper (add_bus_driver:174): bus driver PCI is at d98bc028
ndiswrapper (add_bus_driver:174): bus driver USB is at d98bc128
ndiswrapper (ntoskernel_init:2549): f7c03600
ndiswrapper (wrap_worker_init:2473): d98c1e68
ndiswrapper (wrap_worker_init_func:2462): d98c1e68
ndiswrapper (allocate_object:142): allocated hdr: e125e9c0, body: e125e9e0
ndiswrapper (wrap_worker_init:2483): e125e9e0
ndiswrapper (ndis_init:2974): e125e9e0
ndiswrapper (wrap_worker_init:2473): d98c1e68
ndiswrapper (wrap_worker_init_func:2462): d98c1e68
ndiswrapper (allocate_object:142): allocated hdr: e125e660, body: e125e680
ndiswrapper (wrap_worker_init:2483): e125e680
ndiswrapper (wrapndis_init:2072): e125e680
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (notifier_event:1692): Enter 0x1
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (notifier_event:1692): Enter 0x1
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (notifier_event:1692): Enter 0x5
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27a0:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27a0, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27a0, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter 
[b]ndiswrapper (load_wrap_device:706): couldn't load device 8086:27a0; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27d8:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27d8, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27d8, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter 
**ndiswrapper (load_wrap_device:706): couldn't load device 8086:27d8; check system log for messages from 'loadndisdriver'**
ndiswrapper (load_wrap_device:707): Exit
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:2448:0000:0000
ndiswrapper (load_wrap_device:679): Enter 8086, 2448, 0000, 0000
ndiswrapper (load_wrap_device:695): 8086, 2448, 0000, 0000, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 8086:2448; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27b9:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27b9, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27b9, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 8086:27b9; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_pci_device:612): Enter called for 8086:27da:1028:01c2
ndiswrapper (load_wrap_device:679): Enter 8086, 27da, 1028, 01c2
ndiswrapper (load_wrap_device:695): 8086, 27da, 1028, 01c2, 0005
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 8086:27da; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_pci_device:621): Exit
ndiswrapper (wrap_pnp_start_usb_device:661): Enter 0b97, 7762, 0000
ndiswrapper (load_wrap_device:679): Enter 0b97, 7762, 0000, 0000
ndiswrapper (load_wrap_device:695): 0b97, 7762, 0000, 0000, 000f
ndiswrapper (wrapper_ioctl:762): Enter cmd: 1074097664
ndiswrapper (wrapper_ioctl:773): 0000, 0000, 0000, 0000
ndiswrapper (wrapper_ioctl:823): Exit
ndiswrapper (wrapper_ioctl_release:828): Enter [b]
ndiswrapper (load_wrap_device:706): couldn't load device 0b97:7762; check system log for messages from 'loadndisdriver'
ndiswrapper (load_wrap_device:707): Exit[/b]
ndiswrapper (wrap_pnp_start_usb_device:680): 00000000
ndiswrapper (wrap_pnp_start_usb_device:695): ret: -19
ndiswrapper (wrap_pnp_start_usb_device:697): Exit
usbcore: registered new interface driver ndiswrapper
ndiswrapper (register_devices:646): Exit
ndiswrapper (loader_init:858): Exit
ndiswrapper (wrapper_init:111): Exit

```

It looks like ndiswrapper (probably via loadndisdriver) is trying to load the driver and failing for whatever reason.  I don't see any of the supposed debugging (dmesg) output from loadndisdriver that should be picked up by syslog though.  Anyone know what I need to do to start seeing loadndisdriver's output?

ndiswrapper is being loaded and loading the driver file, but is failing to initialise the device. If you take a look at the lshw driver this is because the device is being claimed by b43-pci-bridge, which is a module I haven't encountered before. So try removing the module (you'll probably have to get rid of ssb while you're at it) and readd ndiswrapper:
```
rmmod b43-pci-bridge ssb ndiswrapper
modprobe ndiswrapper
```

As far as deleting a post goes, you need to get a mod to do it, use the 'report' button to do that (which I did for you).

EDIT: Although now I notice you changed the post to include some other info, whoops!

---

### Post by jhallward on 2008-06-17
haha, the post got deleted with the driver info too.  No problem.  Here's the same data again:
Driver packages I've tried (with no success):
HP: SP23107A SP34152 SP37950
Dell: R151519 R174291

as for b43-pci-bridge that's the new b43 module that replaces bcm43xx in the 2.6.24 kernels.  I've compiled it out of the kernel and ran update-modules and depmod -a (I'm not sure what exactly these do beyond modifying /etc/modules.conf, and I'm pretty sure executing depmod -a was redundant, but thought it couldn't hurt).  'lshw -C network' returns the same results.

Could this be a firmware issue?  I know that normally the broadcom's need firmware to be loaded to run, I'm thinking that maybe the firmware just hasn't been loaded.  Normally firmware should be installed when the inf file is given, but if the relevant firmware files aren't present in right location (e.g. firmware files are in a directory above where bcmwl5.inf/sys are) they wouldn't be integrated into the system correctly.

---

### Post by jw5801 on 2008-06-17
They only need extra firmware loaded if you want to use the open source module, for ndiswrapper they should be fine. The driver I use is R151519, but lots of them should be ok.

b43 is the module that replaces bcm43xx, I think b43-pci-bridge could be something along the lines of b43legacy, but I've honestly never encountered it before. Can you remove the module with 'rmmod b43-pci-bridge'?

EDIT: Hey, my 1000 posts went by, and I didn't even notice! :(

---

### Post by jhallward on 2008-06-17
There is no actual b43-pci-bridge module.  I think it's just a name that designates the b43 module or maybe it's more broadly defined and includes b43 and b43legacy, I'm not sure, but I know that in my case it's a label meant to point to the b43 module.

---

### Post by dilipmannil on 2008-06-17
I have compiled and installed ndiswrapper for 2.6.24-18-generic. Now 2.6.24-19-generic is out and it it prompts to upgrade to the new package while connected to internet. Whether this upgrade will stop my wireless card because of differnet version of kernel and I may have to compile ndiswrapper for new kernel?

---

### Post by jw5801 on 2008-06-17
> **dilipmannil said:**
> I have compiled and installed ndiswrapper for 2.6.24-18-generic. Now 2.6.24-19-generic is out and it it prompts to upgrade to the new package while connected to internet. Whether this upgrade will stop my wireless card because of differnet version of kernel and I may have to compile ndiswrapper for new kernel?

Yeah, you'll probably need to recompile. Try installing it and 'linux-ubuntu-modules-2.6.24-19-generic' though, and see what happens. I've reported the bug about it not auto-updating, although haven't heard anything back about it from anyone empowered to do anything.

---

### Post by jw5801 on 2008-06-17
> **jhallward said:**
> There is no actual b43-pci-bridge module.  I think it's just a name that designates the b43 module or maybe it's more broadly defined and includes b43 and b43legacy, I'm not sure, but I know that in my case it's a label meant to point to the b43 module.

Hmm... a bit of googling shows that it could be related to the ohci-hcd module, so try:
```
rmmod ohci-hcd b44 ssb ndiswrapper
modprobe ndiswrapper
modprobe ohci-hcd
modprobe b44
```

---

### Post by Grendel336 on 2008-06-20
Freakin fabulous. It worked. I am posting my first post from a Linux platform. Thank you so much. The "How to.." is pretty user friendly even for a complete newb.

---

### Post by Papenco on 2008-06-20
I will try this in my Dell E1505 and tell you.

---

### Post by Grendel336 on 2008-06-20
So, I had to shut down the laptop and take care of some stuff. 

Upon returning to Ubuntu and re-starting I found I could not connect to internet. 

What am I missing?

---

### Post by jw5801 on 2008-06-21
> **Grendel336 said:**
> So, I had to shut down the laptop and take care of some stuff. 

Upon returning to Ubuntu and re-starting I found I could not connect to internet. 

What am I missing?

Were you connected before you shut down? Run:
```
sudo rmmod b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe b44
```

To bring it back up. Then post the output from the following:
```
cat /etc/rc.local
cat /etc/modules
cat /etc/modprobe.d/blacklist
```

---

### Post by Grendel336 on 2008-06-21
Yes, I had been connected before I shut down. 

Here's the output from the "cat" codes:

> link@link-laptop:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
link@link-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
link@link-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43
blacklist b43legacy
link@link-laptop:~$ 


---

### Post by jw5801 on 2008-06-21
Why don't you follow the rest of the instructions and add the script to /etc/rc.local. Then it'll stick on a reboot.

---

### Post by Grendel336 on 2008-06-21
rest of instructions?

I followed everything all the way through to "cleaning up", "trouble shooting", and "uninstalling". 

Funny thing is...now it's working. So messing around with something worked. 

I'm sorry for not understanding what you mean by "rest of instructions".

What have I missed?

---

### Post by Grendel336 on 2008-06-21
Here's what I got from the modprobe code:

> link@link-laptop:~$ sudo rmmod b43 b44 ssb 
[sudo] password for link: 
ERROR: Module b43 does not exist in /proc/modules 
link@link-laptop:~$ sudo modprobe ndiswrapper 
link@link-laptop:~$ sudo modprobe b44 
link@link-laptop:~$ 

---

### Post by Grendel336 on 2008-06-21
Here is the output I get from the trouble shooting code:

> link@link-laptop:~$ lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
link@link-laptop:~$ ndiswrapper -1
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
link@link-laptop:~$ lsmod | grep b43
link@link-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,uhci_hcd,ehci_hcd
link@link-laptop:~$ ls -1 /etc/rc.local
/etc/rc.local
link@link-laptop:~$ 

---

### Post by Grendel336 on 2008-06-21
> **jw5801 said:**
> Why don't you follow the rest of the instructions and add the script to /etc/rc.local. Then it'll stick on a reboot.


Are you talking about adding this part:

> modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

as you describe right at the end of Step 2?

I thought I did that...but I'll go check.

---

### Post by jw5801 on 2008-06-21
> **Grendel336 said:**
> Are you talking about adding this part:



as you describe right at the end of Step 2?

I thought I did that...but I'll go check.

Sure am. That's the bit that executes the commands you need to get your WiFi running during the boot process. So if it's not present after a reboot then that's the bit you missed. If you look at your 'cat /etc/rc.local' from earlier, thats the contents of you /etc/rc.local, which didn't have any of those commands.

---

### Post by Grendel336 on 2008-06-21
You rock. 

So it should look like this:

> link@link-laptop:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

link@link-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
link@link-laptop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43
blacklist b43legacy
link@link-laptop:~$ 


I must have not "saved" that part properly the first time.

---

### Post by jw5801 on 2008-06-21
Yup, that all looks good! Try it out.

---

### Post by Grendel336 on 2008-06-21
> **jw5801 said:**
> Yup, that all looks good! Try it out.
 Dude, you are awesome. Thank you so much. 

It worked like a charm at next reboot. 

You are my hero for the day.

---

### Post by SimonTheMime on 2008-06-23
thanks, this worked!

---

### Post by Zielvos on 2008-06-25
I don't know what I'm doing wrong, I got the light on but it still won't connect to the internet. Could it be that I did all this while being connected to the internet threw a wired connection or should that not matter. This is what it looks like right now.

> zielvos@zielvosport:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

zielvos@zielvosport:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
lp
sbp2
fuse

zielvos@zielvosport:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist b43
blacklist b43legacy
zielvos@zielvosport:~$ 


---

### Post by jw5801 on 2008-06-25
> **Zielvos said:**
> I don't know what I'm doing wrong, I got the light on but it still won't connect to the internet. Could it be that I did all this while being connected to the internet threw a wired connection or should that not matter. This is what it looks like right now.

That all looks fine, what out put do you get with:
```
ndiswrapper -l
lshw -C network
sudo rmmod ndiswrapper b43 b44 ssb
sudo modprobe ndiswrapper
dmesg | tail
```

---

### Post by Zielvos on 2008-06-26
Well this is what I got, don't understand anything about it but a few errors did show up. under code _sudo rmmod ndiswrapper b43 b44 ssb_

> 
zielvos@zielvosport:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)

zielvos@zielvosport:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:87:69:1c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5752-v3.19 ip=192.168.1.101 latency=0 module=tg3 multicast=yes

zielvos@zielvosport:~$ sudo rmmod ndiswrapper b43 b44 ssb
[sudo] password for zielvos: 
ERROR: Module ndiswrapper does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules

zielvos@zielvosport:~$ sudo modprobe ndiswrapper

zielvos@zielvosport:~$ dmesg | tail
[65924.000497] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
[65924.000673] usbcore: deregistering interface driver ndiswrapper
[66254.972801] ndiswrapper version 1.52 loaded (smp=yes, preempt=rt)
[66253.355359] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[66253.355783] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[66253.355867] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[66253.361512] ndiswrapper: using IRQ 17
[66255.548351] wlan0: ethernet device 00:1b:fc:be:f6:09 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[66255.549098] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[66255.551943] usbcore: registered new interface driver ndiswrapper



---

### Post by jw5801 on 2008-06-26
Well, after running those commands it should be working fine. You appear to not be running Hardy however? If you're running anything pre-Hardy, look at paperdiesel's how-to [here](http://ubuntuforums.org/showthread.php?t=297092).

---

### Post by Zielvos on 2008-06-26
I think it still is Hardy. I have Ubuntu Studio 8.04 and i don't know what they did or what could have been changed. Oh well, if all else fails I will just get the non-studio version of it and try again.

---

### Post by jw5801 on 2008-06-26
> **Zielvos said:**
> I think it still is Hardy. I have Ubuntu Studio 8.04 and i don't know what they did or what could have been changed. Oh well, if all else fails I will just get the non-studio version of it and try again.

Well, they're not using the same kernel as Hardy, that's for sure. What does ```
uname -a
``` report? Just to satisfy my curiosity!

To get yourself working:
```
sudo rmmod bcm43xx ndiswrapper
sudo modprobe ndiswrapper
```

If that works, then remove the lines we put in /etc/rc.local, and run the following commands:
```
echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist
echo ndiswrapper | sudo tee -a /etc/modules
```

Which will make what you just did stick on a reboot.

---

### Post by zx5itouch on 2008-06-28
I ran through this tutuorial as I am a Noob. However, I cannot get this card working. I also do not see the ndiswrapper application through the system pull-down menu.

The code for sudo apt-get install linux-ubuntu-modules-$ (uname -r) does not accept the parenthesis symbols. 
What did I do wrong?

I uninstalled like in this tutorial just to get my ethernet back up & running. 

Here is my troubleshooting code:

lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

lsmod | grep b43

lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  7 ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2008-06-28 00:13 /etc/rc.local

Please help if you can.

---

### Post by Zielvos on 2008-06-28
Here is that input that you wanted to see.

```

zielvos@zielvosport:~$ uname -a
Linux zielvosport 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

```

I'm going to just install 8.04 and try this over again, if that works then it was a problem with Studio.

---

### Post by jw5801 on 2008-06-28
> **Zielvos said:**
> Here is that input that you wanted to see.

```

zielvos@zielvosport:~$ uname -a
Linux zielvosport 2.6.24-19-rt #1 SMP PREEMPT RT Wed Jun 18 16:35:41 UTC 2008 i686 GNU/Linux

```

I'm going to just install 8.04 and try this over again, if that works then it was a problem with Studio.

Use paperdiesel's how-to. It should work. You'll need to compile ndiswrapper from source for that kernel, but otherwise things should be dandy.

---

### Post by jw5801 on 2008-06-28
> **zx5itouch said:**
> I ran through this tutuorial as I am a Noob. However, I cannot get this card working. I also do not see the ndiswrapper application through the system pull-down menu.
ndiswrapper has no GUI thus it has no menu entry. It's not really an application per se, closer to a driver (although you could call them all applications)

> The code for sudo apt-get install linux-ubuntu-modules-$ (uname -r) does not accept the parenthesis symbols. 
What did I do wrong?
There shouldn't be a space between the $ and the (. Copy and paste is your friend!

> I uninstalled like in this tutorial just to get my ethernet back up & running.

Shouldn't need to:
```
sudo modprobe b44
```
Is all you need to bring wired back up again.

> Here is my troubleshooting code:

```
lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

lsmod | grep b43

lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  7 ndiswrapper,usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd

ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2008-06-28 00:13 /etc/rc.local
```

Please help if you can.

Run the how-to and then let me know what happens when you add the driver:
```
sudo rmmod b44 ssb ndiswrapper
sudo modprobe ndiswrapper
dmesg | tail -n10
iwlist scan
```

Copy the outputs to here. Remember that ```
sudo modprobe b44
``` will bring your wired interface back up.

---

### Post by Zielvos on 2008-06-28
I got everything working on just 8.04. Thanks for your help and I will check out paperdiesel's how-to for my friends computer.

---

### Post by zx5itouch on 2008-06-29
It still doesn't work for me. Am I supposed to use the Network Manager to set the password and IP info? I have a WEP open, but it seems that the Network Manager doesn't like to work very well. FYI, the code: sudo modprobe b44 does NOT bring my wired ethernet back. I have to run through the uninstall first. I am writing this reply on my XP boot. I will try to post my code tomorrow from start of tutorial to the code in jw5801's last reply to my post from earlier this morning. Had one hell of a day with Windows and partitioning to dual boot for XP and Ubuntu Linux. Thanks for your fast help.

---

### Post by zx5itouch on 2008-06-29
Sorry for the long code, but here it is to see why its not working.

code: mlastudios@mlastudios-laptop:~$ sudo apt-get install linux-ubuntu-modules-2.6.24-19-generic 
[sudo] password for mlastudios: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  linux-image-2.6.24-19-generic 
Suggested packages: 
  linux-doc-2.6.24 linux-source-2.6.24 
The following NEW packages will be installed: 
  linux-image-2.6.24-19-generic linux-ubuntu-modules-2.6.24-19-generic 
0 upgraded, 2 newly installed, 0 to remove and 198 not upgraded. 
Need to get 23.0MB of archives. 
After this operation, 77.5MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-19-generic 2.6.24-19.34 [18.4MB] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-ubuntu-modules-2.6.24-19-generic 2.6.24-19.28 [4605kB] 
Fetched 23.0MB in 1min24s (271kB/s)                                            
Selecting previously deselected package linux-image-2.6.24-19-generic. 
(Reading database ... 95678 files and directories currently installed.) 
Unpacking linux-image-2.6.24-19-generic (from .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ... 
Done. 
Selecting previously deselected package linux-ubuntu-modules-2.6.24-19-generic. 
Unpacking linux-ubuntu-modules-2.6.24-19-generic (from .../linux-ubuntu-modules-2.6.24-19-generic_2.6.24-19.28_i386.deb) ... 
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic 
Running postinst hook script /sbin/update-grub. 
Searching for GRUB installation directory ... found: /boot/grub 
Searching for default file ... found: /boot/grub/default 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.24-19-generic 
Found kernel: /boot/vmlinuz-2.6.24-16-generic 
Found kernel: /boot/memtest86+.bin 
Replacing config file /var/run/grub/menu.lst with new version 
Updating /boot/grub/menu.lst ... done 


Setting up linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.28) ... 
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic 

mlastudios@mlastudios-laptop:~$ lspci -nn | grep 14e4 
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01) 
mlastudios@mlastudios-laptop:~$ mkdir wireless-install 
mlastudios@mlastudios-laptop:~$ cd wireless-install 
mlastudios@mlastudios-laptop:~/wireless-install$ wget [http://ftp.us.dell.com/network/R151519.EXE](http://ftp.us.dell.com/network/R151519.EXE) 
--20:03:03--  [http://ftp.us.dell.com/network/R151519.EXE](http://ftp.us.dell.com/network/R151519.EXE) 
           => `R151519.EXE' 
Resolving ftp.us.dell.com... 143.166.170.10 
Connecting to ftp.us.dell.com|143.166.170.10|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 54,735,960 (52M) [application/octet-stream] 

100%[====================================>] 54,735,960   261.08K/s    ETA 00:00 

20:07:55 (183.03 KB/s) - `R151519.EXE' saved [54735960/54735960] 

mlastudios@mlastudios-laptop:~/wireless-install$ sudo apt-get update 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources 
Reading package lists... Done 
mlastudios@mlastudios-laptop:~/wireless-install$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Suggested packages: 
  ndiswrapper-source 
The following NEW packages will be installed: 
  ndiswrapper-common ndiswrapper-utils-1.9 
0 upgraded, 2 newly installed, 0 to remove and 198 not upgraded. 
Need to get 30.4kB of archives. 
After this operation, 213kB of additional disk space will be used. 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11.4kB] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19.0kB] 
Fetched 30.4kB in 1s (29.9kB/s)            
Selecting previously deselected package ndiswrapper-common. 
(Reading database ... 98374 files and directories currently installed.) 
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ... 
Selecting previously deselected package ndiswrapper-utils-1.9. 
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ... 
Setting up ndiswrapper-common (1.50-1ubuntu1) ... 
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ... 
mlastudios@mlastudios-laptop:~/wireless-install$ sudo apt-get install linux-ubuntu-modules-$(uname -r) 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
linux-ubuntu-modules-2.6.24-16-generic is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 198 not upgraded. 
mlastudios@mlastudios-laptop:~/wireless-install$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist 
blacklist b43 
mlastudios@mlastudios-laptop:~/wireless-install$ echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist 
blacklist b43legacy 
mlastudios@mlastudios-laptop:~/wireless-install$ gksudo gedit /etc/rc.local 
mlastudios@mlastudios-laptop:~/wireless-install$ cd ~/wireless-install/ 
mlastudios@mlastudios-laptop:~/wireless-install$ unzip -a R151519.EXE -d R151519/ 
Archive:  R151519.EXE 
  inflating: R151519/DellInfo.exe    [binary] 
  inflating: R151519/dellinst.exe    [binary] 
  inflating: R151519/ikernel.ex_     [binary] 
  inflating: R151519/is.exe          [binary] 
 extracting: R151519/launcher.ini    [text]  
  inflating: R151519/layout.bin      [binary] 
  inflating: R151519/MFC71.DLL       [binary] 
  inflating: R151519/msvcp71.DLL     [binary] 
  inflating: R151519/msvcr71.DLL     [binary] 
  inflating: R151519/preflib.dll     [binary] 
  inflating: R151519/README.rtf      [text]  
  inflating: R151519/setup.exe       [binary] 
  inflating: R151519/Setup.ini       [text]  
  inflating: R151519/setup.inx       [binary] 
  inflating: R151519/setup.iss       [text]  
  inflating: R151519/WLBCGCBPRO731.DLL  [binary] 
  inflating: R151519/wltray.exe      [binary] 
  inflating: R151519/wltrynt.dll     [binary] 
  inflating: R151519/wltrysvc.exe    [binary] 
  inflating: R151519/AMD64/atl71.dll  [binary] 
  inflating: R151519/AMD64/BCMLogon64.dll  [binary] 
  inflating: R151519/AMD64/bcmwlcpl64.cpl  [binary] 
  inflating: R151519/AMD64/MFC71.DLL  [binary] 
  inflating: R151519/AMD64/msvcp71.DLL  [binary] 
  inflating: R151519/AMD64/msvcr71.DLL  [binary] 
  inflating: R151519/DRIVER/bcm43xx.cat  [binary] 
  inflating: R151519/DRIVER/bcm43xx64.cat  [binary] 
  inflating: R151519/DRIVER/bcmwl5.inf  [binary] 
  inflating: R151519/DRIVER/bcmwl5.sys  [binary] 
  inflating: R151519/DRIVER/bcmwl564.sys  [binary] 
  inflating: R151519/ATL71.DLL       [binary] 
  inflating: R151519/bcm1xsup.dll    [binary] 
  inflating: R151519/BCMLogon.dll    [binary] 
  inflating: R151519/Bcmnpf64.sys    [binary] 
  inflating: R151519/bcmwlcpl.cpl    [binary] 
  inflating: R151519/bcmwlhlp.cab    [binary] 
  inflating: R151519/bcmwlhlp.chm    [binary] 
  inflating: R151519/bcmwliss.dll    [binary] 
  inflating: R151519/bcmwlnpf.sys    [binary] 
  inflating: R151519/bcmwlpkt.dll    [binary] 
  inflating: R151519/bcmwls32.exe    [binary] 
  inflating: R151519/bcmwls64.exe    [binary] 
  inflating: R151519/bcmwls.ini      [binary] 
  inflating: R151519/bcmwltry.exe    [binary] 
  inflating: R151519/bcmwlu00.exe    [binary] 
  inflating: R151519/data1.cab       [binary] 
  inflating: R151519/data1.hdr       [binary] 
  inflating: R151519/data2.cab       [binary] 
  inflating: R151519/DellInfo64.exe  [binary] 
  inflating: R151519/Version.txt     [binary] 
mlastudios@mlastudios-laptop:~/wireless-install$ cd R151519/DRIVER/ 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo ndiswrapper -i bcmwl5.inf 
installing bcmwl5 ... 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo rmmod b43 b44 ssb 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo modprobe ndiswrapper 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo modprobe b44 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ 

mlastudios@mlastudios-laptop:~$ sudo rmmod b44 ssb ndiswrapper 
mlastudios@mlastudios-laptop:~$ sudo modprobe ndiswrapper 
mlastudios@mlastudios-laptop:~$ dmesg | tail -n10 
[  439.362043] usbcore: deregistering interface driver ndiswrapper 
[  474.332160] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[  476.348676] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[  476.349264] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[  476.349329] PCI: Setting latency timer of device 0000:0b:00.0 to 64 
[  476.353987] ndiswrapper: using IRQ 16 
[  476.716289] wlan0: ethernet device 00:16:ce:72:2f:00 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf 
[  476.716371] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[  476.719869] usbcore: registered new interface driver ndiswrapper 
[  474.736400] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
mlastudios@mlastudios-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:1A:C4:BF:CF:49 
                    ESSID:"2WIRE271" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 02 - Address: 00:90:4C:7E:00:6E 
                    ESSID:"NETGEAR" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
          Cell 03 - Address: 00:14:6C:01:B7:1A 
                    ESSID:"Tek" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 04 - Address: 00:19:E4:20:42:B9 
                    ESSID:"2WIRE754" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 05 - Address: 00:1D:5A:E0:4E:39 
                    ESSID:"2WIRE679" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.442 GHz (Channel 7) 
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 

mlastudios@mlastudios-laptop:~$ 


My network is the 2WIRE271

---

### Post by jw5801 on 2008-06-29
> **zx5itouch said:**
> Sorry for the long code, but here it is to see why its not working.

```
mlastudios@mlastudios-laptop:~$ sudo apt-get install linux-ubuntu-modules-2.6.24-19-generic 
[sudo] password for mlastudios: 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  linux-image-2.6.24-19-generic 
Suggested packages: 
  linux-doc-2.6.24 linux-source-2.6.24 
The following NEW packages will be installed: 
  linux-image-2.6.24-19-generic linux-ubuntu-modules-2.6.24-19-generic 
0 upgraded, 2 newly installed, 0 to remove and 198 not upgraded. 
Need to get 23.0MB of archives. 
After this operation, 77.5MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-image-2.6.24-19-generic 2.6.24-19.34 [18.4MB] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-ubuntu-modules-2.6.24-19-generic 2.6.24-19.28 [4605kB] 
Fetched 23.0MB in 1min24s (271kB/s)                                            
Selecting previously deselected package linux-image-2.6.24-19-generic. 
(Reading database ... 95678 files and directories currently installed.) 
Unpacking linux-image-2.6.24-19-generic (from .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ... 
Done. 
Selecting previously deselected package linux-ubuntu-modules-2.6.24-19-generic. 
Unpacking linux-ubuntu-modules-2.6.24-19-generic (from .../linux-ubuntu-modules-2.6.24-19-generic_2.6.24-19.28_i386.deb) ... 
Setting up linux-image-2.6.24-19-generic (2.6.24-19.34) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic 
Running postinst hook script /sbin/update-grub. 
Searching for GRUB installation directory ... found: /boot/grub 
Searching for default file ... found: /boot/grub/default 
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst 
Searching for splash image ... none found, skipping ... 
Found kernel: /boot/vmlinuz-2.6.24-19-generic 
Found kernel: /boot/vmlinuz-2.6.24-16-generic 
Found kernel: /boot/memtest86+.bin 
Replacing config file /var/run/grub/menu.lst with new version 
Updating /boot/grub/menu.lst ... done 


Setting up linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.28) ... 
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic 

mlastudios@mlastudios-laptop:~$ lspci -nn | grep 14e4 
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01) 
mlastudios@mlastudios-laptop:~$ mkdir wireless-install 
mlastudios@mlastudios-laptop:~$ cd wireless-install 
mlastudios@mlastudios-laptop:~/wireless-install$ wget [http://ftp.us.dell.com/network/R151519.EXE](http://ftp.us.dell.com/network/R151519.EXE) 
--20:03:03--  [http://ftp.us.dell.com/network/R151519.EXE](http://ftp.us.dell.com/network/R151519.EXE) 
           => `R151519.EXE' 
Resolving ftp.us.dell.com... 143.166.170.10 
Connecting to ftp.us.dell.com|143.166.170.10|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 54,735,960 (52M) [application/octet-stream] 

100%[====================================>] 54,735,960   261.08K/s    ETA 00:00 

20:07:55 (183.03 KB/s) - `R151519.EXE' saved [54735960/54735960] 

mlastudios@mlastudios-laptop:~/wireless-install$ sudo apt-get update 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US 

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources 
Reading package lists... Done 
mlastudios@mlastudios-laptop:~/wireless-install$ sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Suggested packages: 
  ndiswrapper-source 
The following NEW packages will be installed: 
  ndiswrapper-common ndiswrapper-utils-1.9 
0 upgraded, 2 newly installed, 0 to remove and 198 not upgraded. 
Need to get 30.4kB of archives. 
After this operation, 213kB of additional disk space will be used. 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-common 1.50-1ubuntu1 [11.4kB] 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main ndiswrapper-utils-1.9 1.50-1ubuntu1 [19.0kB] 
Fetched 30.4kB in 1s (29.9kB/s)            
Selecting previously deselected package ndiswrapper-common. 
(Reading database ... 98374 files and directories currently installed.) 
Unpacking ndiswrapper-common (from .../ndiswrapper-common_1.50-1ubuntu1_all.deb) ... 
Selecting previously deselected package ndiswrapper-utils-1.9. 
Unpacking ndiswrapper-utils-1.9 (from .../ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb) ... 
Setting up ndiswrapper-common (1.50-1ubuntu1) ... 
Setting up ndiswrapper-utils-1.9 (1.50-1ubuntu1) ... 
mlastudios@mlastudios-laptop:~/wireless-install$ sudo apt-get install linux-ubuntu-modules-$(uname -r) 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
linux-ubuntu-modules-2.6.24-16-generic is already the newest version. 
0 upgraded, 0 newly installed, 0 to remove and 198 not upgraded. 
mlastudios@mlastudios-laptop:~/wireless-install$ echo blacklist b43 | sudo tee -a /etc/modprobe.d/blacklist 
blacklist b43 
mlastudios@mlastudios-laptop:~/wireless-install$ echo blacklist b43legacy | sudo tee -a /etc/modprobe.d/blacklist 
blacklist b43legacy 
mlastudios@mlastudios-laptop:~/wireless-install$ gksudo gedit /etc/rc.local 
mlastudios@mlastudios-laptop:~/wireless-install$ cd ~/wireless-install/ 
mlastudios@mlastudios-laptop:~/wireless-install$ unzip -a R151519.EXE -d R151519/ 
Archive:  R151519.EXE 
  inflating: R151519/DellInfo.exe    [binary] 
  inflating: R151519/dellinst.exe    [binary] 
  inflating: R151519/ikernel.ex_     [binary] 
  inflating: R151519/is.exe          [binary] 
 extracting: R151519/launcher.ini    [text]  
  inflating: R151519/layout.bin      [binary] 
  inflating: R151519/MFC71.DLL       [binary] 
  inflating: R151519/msvcp71.DLL     [binary] 
  inflating: R151519/msvcr71.DLL     [binary] 
  inflating: R151519/preflib.dll     [binary] 
  inflating: R151519/README.rtf      [text]  
  inflating: R151519/setup.exe       [binary] 
  inflating: R151519/Setup.ini       [text]  
  inflating: R151519/setup.inx       [binary] 
  inflating: R151519/setup.iss       [text]  
  inflating: R151519/WLBCGCBPRO731.DLL  [binary] 
  inflating: R151519/wltray.exe      [binary] 
  inflating: R151519/wltrynt.dll     [binary] 
  inflating: R151519/wltrysvc.exe    [binary] 
  inflating: R151519/AMD64/atl71.dll  [binary] 
  inflating: R151519/AMD64/BCMLogon64.dll  [binary] 
  inflating: R151519/AMD64/bcmwlcpl64.cpl  [binary] 
  inflating: R151519/AMD64/MFC71.DLL  [binary] 
  inflating: R151519/AMD64/msvcp71.DLL  [binary] 
  inflating: R151519/AMD64/msvcr71.DLL  [binary] 
  inflating: R151519/DRIVER/bcm43xx.cat  [binary] 
  inflating: R151519/DRIVER/bcm43xx64.cat  [binary] 
  inflating: R151519/DRIVER/bcmwl5.inf  [binary] 
  inflating: R151519/DRIVER/bcmwl5.sys  [binary] 
  inflating: R151519/DRIVER/bcmwl564.sys  [binary] 
  inflating: R151519/ATL71.DLL       [binary] 
  inflating: R151519/bcm1xsup.dll    [binary] 
  inflating: R151519/BCMLogon.dll    [binary] 
  inflating: R151519/Bcmnpf64.sys    [binary] 
  inflating: R151519/bcmwlcpl.cpl    [binary] 
  inflating: R151519/bcmwlhlp.cab    [binary] 
  inflating: R151519/bcmwlhlp.chm    [binary] 
  inflating: R151519/bcmwliss.dll    [binary] 
  inflating: R151519/bcmwlnpf.sys    [binary] 
  inflating: R151519/bcmwlpkt.dll    [binary] 
  inflating: R151519/bcmwls32.exe    [binary] 
  inflating: R151519/bcmwls64.exe    [binary] 
  inflating: R151519/bcmwls.ini      [binary] 
  inflating: R151519/bcmwltry.exe    [binary] 
  inflating: R151519/bcmwlu00.exe    [binary] 
  inflating: R151519/data1.cab       [binary] 
  inflating: R151519/data1.hdr       [binary] 
  inflating: R151519/data2.cab       [binary] 
  inflating: R151519/DellInfo64.exe  [binary] 
  inflating: R151519/Version.txt     [binary] 
mlastudios@mlastudios-laptop:~/wireless-install$ cd R151519/DRIVER/ 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo ndiswrapper -i bcmwl5.inf 
installing bcmwl5 ... 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo rmmod b43 b44 ssb 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo modprobe ndiswrapper 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ sudo modprobe b44 
mlastudios@mlastudios-laptop:~/wireless-install/R151519/DRIVER$ 

mlastudios@mlastudios-laptop:~$ sudo rmmod b44 ssb ndiswrapper 
mlastudios@mlastudios-laptop:~$ sudo modprobe ndiswrapper 
mlastudios@mlastudios-laptop:~$ dmesg | tail -n10 
[  439.362043] usbcore: deregistering interface driver ndiswrapper 
[  474.332160] ndiswrapper version 1.52 loaded (smp=yes, preempt=no) 
[  476.348676] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded 
[  476.349264] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16 
[  476.349329] PCI: Setting latency timer of device 0000:0b:00.0 to 64 
[  476.353987] ndiswrapper: using IRQ 16 
[  476.716289] wlan0: ethernet device 00:16:ce:72:2f:00 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf 
[  476.716371] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK 
[  476.719869] usbcore: registered new interface driver ndiswrapper 
[  474.736400] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
mlastudios@mlastudios-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

wlan0     Scan completed : 
          Cell 01 - Address: 00:1A:C4:BF:CF:49 
                    ESSID:"2WIRE271" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 02 - Address: 00:90:4C:7E:00:6E 
                    ESSID:"NETGEAR" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
          Cell 03 - Address: 00:14:6C:01:B7:1A 
                    ESSID:"Tek" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm 
                    Encryption key:off 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 04 - Address: 00:19:E4:20:42:B9 
                    ESSID:"2WIRE754" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality:46/100  Signal level:-66 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
          Cell 05 - Address: 00:1D:5A:E0:4E:39 
                    ESSID:"2WIRE679" 
                    Protocol:IEEE 802.11g 
                    Mode:Managed 
                    Frequency:2.442 GHz (Channel 7) 
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm 
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:bcn_int=100 
                    Extra:atim=0 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 

mlastudios@mlastudios-laptop:~$ 
```


My network is the 2WIRE271

[code] tags are useful! :P

That all looks fine, if you can see other wireless networks then your card and driver should be working ok. 'modprobe b44' reloads the module that is responsible for broadcom wired cards. So running that command gives you access to the device again, you may need to tell network manager to reconnect to your wired network however.

As far as getting connected to your router, try disabling WEP (just for the attempt) and see if you can connect then. If you can, reenable WEP and see what happens. If not, try taking a look at kevdog's tutorial over [here](http://ubuntuforums.org/showthread.php?t=571188) or try a different network manager, like wifi-radar or wicd (search this thread for those names if you're unsure).

---

### Post by jpyanowski on 2008-06-29
I did it...it works...'nuf said...THANKS  \\:D/

---

### Post by l068904 on 2008-07-01
Worked like a charm...I copied and paste from the instruction to the command screen. Everything working just fine now. Thanks.

Inspiron E1505 
Vista and Ubuntu 8.04
Intel core duo

---

### Post by Freakeomi on 2008-07-03
I was having problems with this when HH first came out, and I have not had a chance to get back on the forum (work etc).  I actually followed instructions from the beginning and got it working, but unfortunately had to get a new HDD for my laptop.  (e1505 dell w/ 1390 wlan etc).  

I reinstalled Ubuntu 8.04 and follow the instructions and they work great, except I can't seem to get network manager to work properly (keeps asking me for my network password after I try connect w/ password for my network). 

I tested out programs like wifi radar or wicd and they connect but programs like wine-doors, firefox will always detect offline mode.

Does this have anything to do w/ this set up? or network manager?

---

### Post by jw5801 on 2008-07-03
> **Freakeomi said:**
> I was having problems with this when HH first came out, and I have not had a chance to get back on the forum (work etc).  I actually followed instructions from the beginning and got it working, but unfortunately had to get a new HDD for my laptop.  (e1505 dell w/ 1390 wlan etc).  

I reinstalled Ubuntu 8.04 and follow the instructions and they work great, except I can't seem to get network manager to work properly (keeps asking me for my network password after I try connect w/ password for my network). 

I tested out programs like wifi radar or wicd and they connect but programs like wine-doors, firefox will always detect offline mode.

Does this have anything to do w/ this set up? or network manager?

It's a network-manager issue that's not unique to this set-up. I don't know what wine-doors is, but Firefox definitely shouldn't put you in offline mode, there would be something else causing that issue other than a lack of network-manager. This probably isn't the thread to debug that though, might want to create a new one. Feel free to link to it here though :)

---

### Post by poissonsl on 2008-07-04
Thank you for this guide!  It worked perfectly.  I thought it didn't for a few minutes, even though the install went smoothly.  I had to do two extra little things (please excuse me if I'm repeating anything, as I did not read through all of the comments here): 1-I have my wireless router set up to not broadcast the SSID and I had to broadcast the SSID so I could see it when I scanned.  2-I had to disable and reinable networking (even after a restart) in order to get it to work.  So, I guess if everything seems OK, but you still don't seem to have a connection you can try these things.  

Thank you for a great guide!!

---

### Post by Asgautr on 2008-07-08
Hello, I've followed the guide  2 times, each with a fresh install of Ubuntu, and I can't seem to get it to work. I don't think there's any specific error, it just doesn't find any network when it scans.

```
jessica@jessica-laptop:~$ lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
jessica@jessica-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: bcm43xx)
jessica@jessica-laptop:~$ lsmod | grep b43
jessica@jessica-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,uhci_hcd
jessica@jessica-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 372 2008-07-08 08:36 /etc/rc.local
jessica@jessica-laptop:~$ sudo modprobe -r b44
jessica@jessica-laptop:~$ sudo modprobe -r ssb
jessica@jessica-laptop:~$ sudo modprobe ndiswrapper
jessica@jessica-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

jessica@jessica-laptop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1644 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82200 (80.2 KB)  TX bytes:82200 (80.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:a6:f4:69:b5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:efcfc000-efd00000 


```

I appreciate it.

---

### Post by jw5801 on 2008-07-08
Asgautr, a few more outputs for me please:
```
uname -a
lshw -C network
sudo rmmod ndiswrapper b43 b44 b43legacy bcm43xx ssb
sudo modprobe ndiswrapper
dmesg | tail -n15
```

---

### Post by Asgautr on 2008-07-08
Thanks for the quick response! Here it is:
```
jessica@jessica-laptop:~$ uname -a
Linux jessica-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
jessica@jessica-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:0e:a6:f4:69:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:cc:b8:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.105 latency=64 module=ssb multicast=yes
jessica@jessica-laptop:~$ sudo rmmod ndiswrapper b43 b44 b43legacy bcm43xx ssb
[sudo] password for jessica: 
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
jessica@jessica-laptop:~$ sudo modprobe ndiswrapper
jessica@jessica-laptop:~$ dmesg | tail -n15
[  928.578305] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  942.498650] eth0: no IPv6 routers present
[ 3380.350639] ndiswrapper: device wlan0 removed
[ 3380.350671] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 3380.350805] usbcore: deregistering interface driver ndiswrapper
[ 3380.675373] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 3393.045403] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3393.060953] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 3393.061530] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 3393.061597] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[ 3393.067417] ndiswrapper: using IRQ 16
[ 3393.268540] wlan0: ethernet device 00:0e:a6:f4:69:b5 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 3393.268773] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 3393.279716] usbcore: registered new interface driver ndiswrapper
[ 3393.291615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jessica@jessica-laptop:~$ 


```

---

### Post by jw5801 on 2008-07-08
> **Asgautr said:**
> Thanks for the quick response! Here it is:
```
jessica@jessica-laptop:~$ uname -a
Linux jessica-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
jessica@jessica-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 01
       serial: 00:0e:a6:f4:69:b5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:cc:b8:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.105 latency=64 module=ssb multicast=yes
jessica@jessica-laptop:~$ sudo rmmod ndiswrapper b43 b44 b43legacy bcm43xx ssb
[sudo] password for jessica: 
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
jessica@jessica-laptop:~$ sudo modprobe ndiswrapper
jessica@jessica-laptop:~$ dmesg | tail -n15
[  928.578305] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  942.498650] eth0: no IPv6 routers present
[ 3380.350639] ndiswrapper: device wlan0 removed
[ 3380.350671] ACPI: PCI interrupt for device 0000:0b:00.0 disabled
[ 3380.350805] usbcore: deregistering interface driver ndiswrapper
[ 3380.675373] ACPI: PCI interrupt for device 0000:03:00.0 disabled
[ 3393.045403] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[ 3393.060953] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[ 3393.061530] ACPI: PCI Interrupt 0000:0b:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 3393.061597] PCI: Setting latency timer of device 0000:0b:00.0 to 64
[ 3393.067417] ndiswrapper: using IRQ 16
[ 3393.268540] wlan0: ethernet device 00:0e:a6:f4:69:b5 using NDIS driver: bcmwl5, version: 0x4640f05, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4311.5.conf
[ 3393.268773] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[ 3393.279716] usbcore: registered new interface driver ndiswrapper
[ 3393.291615] ADDRCONF(NETDEV_UP): wlan0: link is not ready
jessica@jessica-laptop:~$ 


```

Looks like it's all working reasonably fine from a driver standpoint. The WiFi light is on? What networks should it be seeing?

---

### Post by Asgautr on 2008-07-08
> **jw5801 said:**
> Looks like it's all working reasonably fine from a driver standpoint. The WiFi light is on? What networks should it be seeing?

The WiFi light is not on. It should be seeing my Linksys router which is in the same room and worked perfectly last night on WinXP before I converted my girlfriend to Ubuntu. :)

Manually entering the SSID doesn't work either. My friend's PS3 picks up the signal just fine (and it's not a conflict problem with the PS3 because he brought it over after I was having problems with the laptop's WiFi).

EDIT

Wow, as I was sitting here searching for other people that had no WiFi light, it came on out of nowhere. I've been tinkering with it all day and it just comes on for no reason. Connected to my router and everything, works great! Thanks for the guide.

---

### Post by iwc5893 on 2008-07-14
Finally, I found the answer I was looking for.  Worked like a charm!!!!  Thanks.

---

### Post by eeyy on 2008-07-17
It really works. Great!

Thank you so much.

---

### Post by mpgarate on 2008-07-17
Does anyone else have the problem that it will not connect and repeatedly asks for my wifi password? after 10 tries or so it will connect, but it takes ages and is extremely annoying. Could it be the kind of security used by my router? i believe it is wpa personal

---

### Post by queonda on 2008-07-23
jw5801,

Thank you very much for you help.  it took me several tries and reading though the post to come to the solution.  Can you change your 1st post, if you have KDE to use KDEsudo instead of just sudo?

I may be wrong but it seem when I just use sudo I couldn't get to work.  After I used KDEsudo then the wifi light came on when it should.  I still need to try the wifi at home with encryption but I'm happy the light is on now.
:guitar:

BTW, I have a D620 which I've been trying to get to work, off and on for about a month when I came across this thread.  Then again I probably could of gotten it work before if I new about the kdesudo.  I guess being a Noob is why I have a big Costco asprin for my headaches.  LOL

---

### Post by jw5801 on 2008-07-23
> **queonda said:**
> jw5801,

Thank you very much for you help.  it took me several tries and reading though the post to come to the solution.  Can you change your 1st post, if you have KDE to use KDEsudo instead of just sudo?

I may be wrong but it seem when I just use sudo I couldn't get to work.  After I used KDEsudo then the wifi light came on when it should.  I still need to try the wifi at home with encryption but I'm happy the light is on now.
:guitar:

BTW, I have a D620 which I've been trying to get to work, off and on for about a month when I came across this thread.  Then again I probably could of gotten it work before if I new about the kdesudo.  I guess being a Noob is why I have a big Costco asprin for my headaches.  LOL

:) Glad it worked for you.

You shouldn't use kdesudo everywhere, only when you're opening a graphical application, have a look [here](http://www.psychocats.net/ubuntu/graphicalsudo) for an explanation of why. This is why I've used gksudo (the gtk equivalent) whenever we need to open a graphical text editor with root permissions. If you try and use gksudo under KDE, however, it'll complain that the command doesn't exist.

'sudo' however, is consistent across any desktop environment as it is a purely command line tool.

---

### Post by cmmcnamara on 2008-07-25
I can't get my darn WiFi to work. I can get it to turn the light on and at one point I could get it to scan and find Networks using terminal commands but not connect. Here is all what the Terminal spit out (I am on Kubuntu Hardy Heron BTW):

lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)

ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload

lsmod | grep b43

lsmod | grep ndiswrapper
ndiswrapper           243872  0
usbcore               169904  4 ndiswrapper,uhci_hcd,ehci_hcd

ls -l /etc/rc.local
-rwxr-xr-x 1 root root 420 2008-07-24 22:22 /etc/rc.local

cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

sudo lshw -C network
[sudo] password for chris:
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:1e:8a:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b6:2d:b2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.106 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:11:06:10
                    ESSID:"McNamara"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1F:C6:21:22:1C
                    ESSID:"evan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:F8:4D:78:87
                    ESSID:"sweetdaddy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:01:A2:1B:13
                    ESSID:"dominicvaca"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

eth0      Interface doesn't support scanning.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b6:2d:b2
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feb6:2db2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:780290 (762.0 KB)  TX bytes:89247 (87.1 KB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:1f:3a:1e:8a:e8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f9ffc000-fa000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

That is all the requested information needed for help as per the Original Poster's request as well as some additional info as requested by a few other later posters. Also a note is the WiFi light is on. Also the Wireless ZeroConf module in the system settings menu on KDE when attempted to enable it says a warning box stating command not found...I don't know if this is an issue not getting the wireless card to work. Thanks in advance for any help.

---

### Post by jw5801 on 2008-07-25
> **cmmcnamara said:**
> I can't get my darn WiFi to work. I can get it to turn the light on and at one point I could get it to scan and find Networks using terminal commands but not connect. Here is all what the Terminal spit out (I am on Kubuntu Hardy Heron BTW):
```

lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)

ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload

lsmod | grep b43

lsmod | grep ndiswrapper
ndiswrapper           243872  0
usbcore               169904  4 ndiswrapper,uhci_hcd,ehci_hcd

ls -l /etc/rc.local
-rwxr-xr-x 1 root root 420 2008-07-24 22:22 /etc/rc.local

cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

sudo lshw -C network
[sudo] password for chris:
  *-network
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:1e:8a:e8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:b6:2d:b2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.106 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

iwlist scan
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:46:11:06:10
                    ESSID:"McNamara"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:90/100  Signal level:-38 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1F:C6:21:22:1C
                    ESSID:"evan"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 00:18:F8:4D:78:87
                    ESSID:"sweetdaddy"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:17/100  Signal level:-85 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 04 - Address: 00:18:01:A2:1B:13
                    ESSID:"dominicvaca"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.452 GHz (Channel 9)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    Extra:atim=0

eth0      Interface doesn't support scanning.

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:b6:2d:b2
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feb6:2db2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:780290 (762.0 KB)  TX bytes:89247 (87.1 KB)
          Interrupt:17

eth1      Link encap:Ethernet  HWaddr 00:1f:3a:1e:8a:e8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f9ffc000-fa000000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

That is all the requested information needed for help as per the Original Poster's request as well as some additional info as requested by a few other later posters. Also a note is the WiFi light is on. Also the Wireless ZeroConf module in the system settings menu on KDE when attempted to enable it says a warning box stating command not found...I don't know if this is an issue not getting the wireless card to work. Thanks in advance for any help.

Well from that you can see that the card is working fine. You can see networks and lshw -C network reports the driver as 'ndiswrapper+bcmwl5' which is what we want.

I assume the network with essid 'evan' is yours? Try turning the encryption off (just for a little bit) and seeing if you can connect that way. Otherwise try the manual connection method and see if we can come across anything interesting.

---

### Post by cmmcnamara on 2008-07-25
Actually my network is the one which showed up as McNamara. The trouble is I can't get KNetworkManager to even search for available networks. So therefore I can't connect. The manager shows there is a wired and a wireless connection and that both are active and functioning properly but the wireless one can't find and wireless networks. All I can really do is enable and disable it. Could it be that its because the Wireless ZeroConf service is having issues?

---

### Post by jw5801 on 2008-07-25
The "Wireless ZeroConf service"? I'm not sure what that is. You can see the network fine, so if KNetworkManager is refusing to notice, don't use KNetworkManager! Try wifi-radar or wicd. Or try [connecting from the commandline](http://ubuntuforums.org/showthread.php?t=571188).

Also, I did mean to type 'McNamara' rather than 'evan', and my suggestion was relating to your network. I had a look at the settings and then matched up the wrong ssid!

---

### Post by d.avid on 2008-07-28
Hi, thanks for the HowTo!

I've got difficulties getting my wlan to work, though. I followed your instructions and get a connection to the wlan (iwconfig and wicd say). But the only thing that works is pinging myself. I cannot ping my router or reach any other ip. Connecting without encryption instead of WPA/WPA2 works "fine". Otherwise the router rejects every attempt due to an "invalid key" (authorization failed) [the key is correct, though].
This kind of proves that the drivers are working, but after hours of research I have absolutely no clue und reached an unhealthy level of annoyance and despair. Maybe anyone has an idea or two? :)
I already tried the HowTos: "Wireless Security" and "Manual Network Configuration without the need for Network Manager".

Output:
**lspci -nn | grep 14e4**
```
05:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
```
*(I use the hp driver "14e4:4312 (rev 02)", linked on the ndiswrapper website)*

**ndiswrapper -l**
```
bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: bcm43xx)
```

**ndiswrapper -v**
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-generic SMP mod_unload 586 
```

**lsmod | grep b43**
no output

**lsmod | grep ndiswrapper**
```
ndiswrapper           192920  0 
usbcore               146028  4 ndiswrapper,ehci_hcd,ohci_hcd
```

**ls -l /etc/rc.local**
```
-rwxr-xr-x 1 root root 458 2008-07-28 02:07 /etc/rc.local
```

**cat /etc/rc.local**
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/etc/init.d/networking restart

## ndiswrapper und b44 in korrekter Reihenfolge laden
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
```

**lshw -C network**
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:14:b9:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,07/11/2007, 4.150. ip=192.168.178.22 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:b3:56:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes

```

Thanks!

---

### Post by jw5801 on 2008-07-28
> **d.avid said:**
> Hi, thanks for the HowTo!

I've got difficulties getting my wlan to work, though. I followed your instructions and get a connection to the wlan (iwconfig and wicd say). But the only thing that works is pinging myself. I cannot ping my router or reach any other ip. Connecting without encryption instead of WPA/WPA2 works "fine". Otherwise the router rejects every attempt due to an "invalid key" (authorization failed) [the key is correct, though].
This kind of proves that the drivers are working, but after hours of research I have absolutely no clue und reached an unhealthy level of annoyance and despair. Maybe anyone has an idea or two? :)
I already tried the HowTos: "Wireless Security" and "Manual Network Configuration without the need for Network Manager".

...

Thanks!

Well, the driver is working fine. You can connect properly without WPA, but you're seeing the issue when you connect with WPA? Or you can't connect at all with WPA, but you can get the odd half-connection without it? I haven't had much experience using WPA, so I probably won't be much help there. Does 'ifconfig' report you as having a valid IP when you're connected?

---

### Post by d.avid on 2008-07-28
Thank you for your prompt reply!

> **jw5801 said:**
> You can connect properly without WPA, but you're seeing the issue when you connect with WPA? 
Yep!

> 
Does 'ifconfig' report you as having a valid IP when you're connected?
ifconfig returns the static ip address I assigned to the notebook.

---

### Post by jw5801 on 2008-07-29
> **d.avid said:**
> ifconfig returns the static ip address I assigned to the notebook.

Ok, that sounds like it's not establishing a connection with WPA. Do you have DHCP set up at the router? You'll probably find that if you try and get an IP through DHCP with WPA enabled it will fail. You had no luck with kevdog's commandline tutorial? Might be an idea to give it a try and post any issues in his thread, as the commandline is the best way to get any debugging output and he is alot more familiar with WPA than I am. You can be assured that your driver is up and the card appears to be working properly however!

---

### Post by d.avid on 2008-07-29
Ok, I'll try. Thanks for your help! I just hope it's not the driver somehow not supporting wpa -- ie. caused by the (rev 02)-driver for my 01-card? Anyway!

---

### Post by jw5801 on 2008-07-30
> **d.avid said:**
> Ok, I'll try. Thanks for your help! I just hope it's not the driver somehow not supporting wpa -- ie. caused by the (rev 02)-driver for my 01-card? Anyway!

You mean the R151519.EXE being for Rev 2? That could present issues, although one would assume that they would be backwards compatible. If you can find a Rev 1 exe you could try it. All you'll need to do is install the new driver using the same method we used to install the one listed in the thread. Just make sure you remove the existing driver first with 'ndiswrapper -e bcmwl5'.

---

### Post by Meghnaad on 2008-07-30
Works like charm !
Thank you  ubuntu :KS

---

### Post by d.avid on 2008-07-30
> **jw5801 said:**
> You mean the R151519.EXE being for Rev 2? That could present issues, although one would assume that they would be backwards compatible. If you can find a Rev 1 exe you could try it. All you'll need to do is install the new driver using the same method we used to install the one listed in the thread. Just make sure you remove the existing driver first with 'ndiswrapper -e bcmwl5'.

Ah no, I should have mentioned: My card is the BCM4312 802.11a/b/g (rev 01). The ndiswrapper website doesn't list this one but the (rev 02)-version (first entry): [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)
"sp38664.exe". Well, I posted in the other thread and hope the WPA expert can help :)

bye

---

### Post by marcopolo1981 on 2008-08-01
Bingo Buddy! This worked perfectly, first time. Much appreciated

Mark

---

### Post by marcopolo1981 on 2008-08-02
Quick question, is there any way to change the speed? Mine says 36Mb/s instead of 54Mb/s. 

Running lspci -nn | grep 14e4 in terminal says :

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

Edit : And also, wireless signal isn't very high even when sitting next to router. It's never more than 35% Can it be fixed?

So I'm pretty certain that I have installed the correct driver. If not, no big deal because at least I'm wireless again. Just wondered. 

Thanks again
Mark

---

### Post by jw5801 on 2008-08-02
> **marcopolo1981 said:**
> Quick question, is there any way to change the speed? Mine says 36Mb/s instead of 54Mb/s. 

Running lspci -nn | grep 14e4 in terminal says :

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)

Edit : And also, wireless signal isn't very high even when sitting next to router. It's never more than 35% Can it be fixed?

So I'm pretty certain that I have installed the correct driver. If not, no big deal because at least I'm wireless again. Just wondered. 

Thanks again
Mark

As far as the 'speed' goes, that's dependent on the signal from the router and the signal to noise ratio. It's a theoretical maximum as well, so normally doesn't mean much. As far as the signal percentage goes, that a signal-to-noise ratio, so if you've got a wireless phone base station or something similar near the router that could be interfering a little bit, otherwise I'm not sure.

---

### Post by mace2 on 2008-08-03
Thank you SO MUCH jw5801! I was about to give up when I found this thread. I can't believe it worked!

I registered just to post this. Again, thanks!!

---

### Post by 0004tom on 2008-08-03
I'm having a problem, making this work with hardy 8.04.1 is this because something changed with 8.04.1 or i've missunderstood something ?

Many thanks

---

### Post by jw5801 on 2008-08-03
> **0004tom said:**
> I'm having a problem, making this work with hardy 8.04.1 is this because something changed with 8.04.1 or i've missunderstood something ?

Many thanks

8.04.1 hasn't changed all that much other than a bunch of bug fixes and security updates, since this issue is with the 2.6.24 kernel which we're still using, the how-to still works perfectly.

Did you encounter any errors while you were following it?

---

### Post by superm1 on 2008-08-07
The cards targeted in this post should also  be supported by this update: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Anyone without things working yet might consider giving this a shot too.  You should have a more functional card this way than with ndiswrapper...

---

### Post by jw5801 on 2008-08-07
> **superm1 said:**
> The cards targeted in this post should also  be supported by this update: [http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Anyone without things working yet might consider giving this a shot too.  You should have a more functional card this way than with ndiswrapper...

Is b43 now supporting 802.11g?

---

### Post by superm1 on 2008-08-07
> **jw5801 said:**
> Is b43 now supporting 802.11g?
That isn't for b43.  Read the post...

---

### Post by jw5801 on 2008-08-08
> **superm1 said:**
> That isn't for b43.  Read the post...

Ah, right, my apologies. Was in a hurry so just had a quick scan through. Will give it a test if I get the chance.

---

### Post by shreko on 2008-08-10
Thanks for the guide,

It worked for me, without it I could not do it. I had a strange situation when I tested live cd 8.04 on my Vostro 1000 laptop wifi worked via fwcutter (or whatever is called). So I run it for an evening and the following day decided to wipe out win xp and install ubuntu. When I installed it, it just did not wanna work the same way as on live cd. This guide saved me

Cheers

---

### Post by jimistephen on 2008-08-10
Help!!!

ok, i've tried this thing a couple of times and still can't get it to work. and i've ran all the troubleshooting codes and this is what i got 
lspci -nn | grep 14e4:
03:00.0 Network cfontroller [0280]: Broadcom Corporation Bcm94311mcg wlan mini-PCI- [14E4:4311] (REV 01)

ndiswrapper -l:
error: no ndiswrapper utils found!

ndiswrapper -v:
Error: no ndiswrapper utils found!

lsmod | grep b43:
b43  144420 0
rfkill  8595 51 rfkill_input,b43
mac80211  165652 1 b43
led_class  6020 2 acer_acpi,b43
input_polldev  5896 1 b43
ssb  34308 1 b43

lsmod | grep ndiswrapper:
(*nothing happened*)

ls -l /etc/rc.local:
/etc/re.local showed up in green

cat /etc/rc.local:
shows what's in the re.local with 

##loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0 at the end

lshw -C network:
WARNING: you should run this program and a super-user
PCI (sysfs)
*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd. 
physical id:0
bus info: pci@0000:02:00.0
logical name: eth0
version 14
serial: 00:1b:24:3a:37:d4
width: 64 bits
clock: 33MHz
capabilites" bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes

*-network
description: Network controller
product: BCM94311MCG wlan mini-PCI
vender: Broadcom Corporation
physical id:0 
bus info: pci@0000:03:00.0
version 01
width 32 bits
clock 33MHz
capabilites: bus_master cap_list
configuration: driver=b43 pci-bridge latency=0 module=ssb

*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:19:7e:5f:d7:b5
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless+IEEE 802.11g


Thanks in advance for any help possible

---

### Post by jw5801 on 2008-08-11
> **jimistephen said:**
> Help!!!

ok, i've tried this thing a couple of times and still can't get it to work. and i've ran all the troubleshooting codes and this is what i got 
```
lspci -nn | grep 14e4:
03:00.0 Network cfontroller [0280]: Broadcom Corporation Bcm94311mcg wlan mini-PCI- [14E4:4311] (REV 01)

[b]ndiswrapper -l:
error: no ndiswrapper utils found!

ndiswrapper -v:
Error: no ndiswrapper utils found![/b]

[b]lsmod | grep b43:
b43  144420 0
rfkill  8595 51 rfkill_input,b43
mac80211  165652 1 b43
led_class  6020 2 acer_acpi,b43
input_polldev  5896 1 b43
ssb  34308 1 b43[/b]

lsmod | grep ndiswrapper:
**(*nothing happened*)**

ls -l /etc/rc.local:
/etc/re.local showed up in green

cat /etc/rc.local:
shows what's in the re.local with 

##loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0 at the end

lshw -C network:
WARNING: you should run this program and a super-user
PCI (sysfs)
*-network
description: Ethernet interface
product: 88E8038 PCI-E Fast Ethernet Controller
vendor: Marvell Technology Group Ltd. 
physical id:0
bus info: pci@0000:02:00.0
logical name: eth0
version 14
serial: 00:1b:24:3a:37:d4
width: 64 bits
clock: 33MHz
capabilites" bus_master cap_list ethernet physical
configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes

[b]*-network
description: Network controller
product: BCM94311MCG wlan mini-PCI
vender: Broadcom Corporation
physical id:0 
bus info: pci@0000:03:00.0
version 01
width 32 bits
clock 33MHz
capabilites: bus_master cap_list
configuration: driver=b43 pci-bridge latency=0 module=ssb[/b]

*-network DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:19:7e:5f:d7:b5
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless+IEEE 802.11g
```


Thanks in advance for any help possible

You haven't installed ndiswrapper.
```
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
sudo apt-get install linux-ubuntu-modules-$(uname -r)
```

---

### Post by jimistephen on 2008-08-11
i feel like a retard, it's still not working :( i'm open to any advise

---

### Post by jw5801 on 2008-08-11
> **jimistephen said:**
> i feel like a retard, it's still not working :( i'm open to any advise

No need to feel like a retard! Are you connected to a network when you're attempting to install ndiswrapper. Can you post the output from the commands you're attempting to run?

---

### Post by jimistephen on 2008-08-12
no, i'm not on a network because i can't get my Ethernet or my wlan to work

my R151519.exe file is on a thumb drive and it's already been unzipped, i need help with that. and i have the file on my ubuntu desktop. everything else i think i have ok... and what is "uname" in "sudo apt-get install linux-ubuntu-modules-$(uname -r)

---

### Post by jw5801 on 2008-08-12
Ok, the 'uname -r' returns the number of your kernel, 2.6.24-XX. If you're not on the internet then you'll need to install the packages you need from your LiveCD as I detailed in the first post, if you just use apt-get without telling it it can use the CD it'll try and fetch the packages it needs over the net, which it can't do. Give it another try on the ndiswrapper and linux-ubuntu-modules packages.

Put the LiveCD in the drive and try:
```
sudo mount /dev/cdrom /cdrom
sudo apt-cdrom add -m
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 linux-ubuntu-modules-$(uname -r)
```

---

### Post by jimistephen on 2008-08-12
ok, i have that, that's not my biggest problem right now, my problem is the r151519 drive on a jump drive that's been unzip before i could put it on there (stupid vista's) how do i load that up? do i need to put it on another cd instead?

---

### Post by jw5801 on 2008-08-13
> **jimistephen said:**
> ok, i have that, that's not my biggest problem right now, my problem is the r151519 drive on a jump drive that's been unzip before i could put it on there (stupid vista's) how do i load that up? do i need to put it on another cd instead?

Well, you can't actually do anything with R151519 until you have ndiswrapper installed, so that's your first port of call. Provided that's done, I'm not sure what you mean about the flash drive. Is it in some way encrypted so you can't access anything on it? If R151519.EXE has already been unzipped then that's no issue, we need to do that anyway.

---

### Post by jimistephen on 2008-08-13
i have ndiswrapper installed now, when i do sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 they both say they're the newest versions of it.

let me put the out put of where i am

---

### Post by jimistephen on 2008-08-13
_mkdir wireless-install_:
mkdir" cannot create directory 'wireless-install': File exists
*it's said that since i first tried this

ok, _gksudo gedit /etc/modules_ brings up another box that says

# /etc/modules: kernel modules to load at boot time.
#
#this files contains the names of kernel modules that should be loaded(on previous) 
# at boot time, one per line. lines beginning with "#" are ignored.

fuse
lp


ok. _unzip -a R151519.exe -dR151519/_
unzip: cannot find or open R151519.exe, R151519.exe.zip or r151519.exe.ZIP

_cd R151519/DRIVER_:
bash: cd:r151519/driver: no such file or directory

_sudo ndiswrapper -i bcmw15.inf_
couldn't open bcmw15.inf: now such file or directory at /usr/sbin/ndiswrapper-1.9 line 219

---

### Post by jw5801 on 2008-08-13
> **jimistephen said:**
> _mkdir wireless-install_:
mkdir" cannot create directory 'wireless-install': File exists
*it's said that since i first tried this
That's because you already created the driectory. It will have said this every time apart from the first time you tried.

> ok, _gksudo gedit /etc/modules_ brings up another box that says

# /etc/modules: kernel modules to load at boot time.
#
#this files contains the names of kernel modules that should be loaded(on previous) 
# at boot time, one per line. lines beginning with "#" are ignored.

fuse
lp
That's what it should look like.


> ok. _unzip -a R151519.exe -dR151519/_
unzip: cannot find or open R151519.exe, R151519.exe.zip or r151519.exe.ZIP

See how it says it can't find it? Where have you put R151519.EXE? The commands after rely on being able to find what was extracted from the .EXE, since nothing has been extracted, don't worry about continuing just yet. Copy R151519.EXE into the ~/wireless-install directory you created, then change into that directory (using 'cd ~/wireless-install') and try again.

---

### Post by jimistephen on 2008-08-13
r151519.exe is on a usb flash drive

---

### Post by jw5801 on 2008-08-14
> **jimistephen said:**
> r151519.exe is on a usb flash drive

Then copy it from there to our working directory, which is called wireless-install and is in your home directory. Then try it again. Don't forget that R151519.EXE, r151519.EXE, R151519.exe and r151519.exe are all completely different things as far as Linux is concerned, so make sure you've got the right one.

---

### Post by jimistephen on 2008-08-14
that, my good sir, is what i was asking how to do a few post back when i started talking about the usb drive

---

### Post by jw5801 on 2008-08-14
> **jimistephen said:**
> that, my good sir, is what i was asking how to do a few post back when i started talking about the usb drive

Ah, righto. Well if you're running a base Ubuntu install you'll have Gnome, which means when you plug the flash drive in, it should appear on the desktop, so you can click on it and browse away, then drag and drop the file you want to move (or ctrl+c, ctrl+v, whatever takes your fancy).

If it doesn't appear on the desktop, then we'll need to work out why, but that's probably best suited for a new thread, rather than cluttering up this one.

---

### Post by jimistephen on 2008-08-14
ok, got that done. now i just need to know how to make it connect with my linksys wrt54g router...thank you so much for all your help

---

### Post by VerballyCopulating on 2008-08-16
I followed this post to get my WiFi working and it worked, but now I have a different problem. My wireless connection keeps disappearing from "Network Settings" after a reboot, with the exact same dell model (E1505)  and wireless card (14e4:4311) referred to in this post.

Whenever I boot Linux it's become a little suspenseful because I don't know if my wireless will be working this time or not.  I know it's not due to the fact that the card is disabled, its just gone.  No WiFi light, and no entry in Network settings.  Help!

---

### Post by jw5801 on 2008-08-16
> **VerballyCopulating said:**
> I followed this post to get my WiFi working and it worked, but now I have a different problem. My wireless connection keeps disappearing from "Network Settings" after a reboot, with the exact same dell model (E1505)  and wireless card (14e4:4311) referred to in this post.

Whenever I boot Linux it's become a little suspenseful because I don't know if my wireless will be working this time or not.  I know it's not due to the fact that the card is disabled, its just gone.  No WiFi light, and no entry in Network settings.  Help!

Those things don't mean that it's 'gone' just that it doesn't have anything controlling it. Meaning that ndiswrapper has not been loaded to interface with the card, therefore nothing else knows it exists. Running:
```
sudo rmmod ndiswrapper b44 b43 ssb
sudo modprobe ndiswrapper b44
```
should get it running. The output to the first command will give us an idea as to what's happening. Also if you could post:
```
ls -la /etc/rc.local
cat /etc/rc.local
cat /etc/modules
```

---

### Post by VerballyCopulating on 2008-08-16
Cheers for getting back so quickly.  I noticed booting into my wireless light was on, but still same problem.

> e@Blaster:~$ sudo rmmod ndiswrapper b44 b43 ssb
[sudo] password for e: 
ERROR: Module b43 does not exist in /proc/modules


and if I run it again... 

> e@Blaster:~$ sudo rmmod ndiswrapper b44 b43 ssb
ERROR: Module ndiswrapper does not exist in /proc/modules
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules


> e@Blaster:~$ sudo modprobe ndiswrapper b44
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.24-19-generic/misc/ndiswrapper.ko): Unknown symbol in module, or unknown parameter (see dmesg)


> e@Blaster:~$ ls -la /etc/rc.local
-rwxr-xr-x 1 root root 421 2008-08-04 21:54 /etc/rc.local


> e@Blaster:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0


> e@Blaster:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0


> e@Blaster:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2


---

### Post by jw5801 on 2008-08-16
> **VerballyCopulating said:**
> Cheers for getting back so quickly.  I noticed booting into my wireless light was on, but still same problem.



and if I run it again...

I think that time it read 'b44' as a parameter of 'ndiswrapper' in the modprobe statement, try:
```
sudo rmmod ndiswrapper b44 ssb
sudo modprobe ndiswrapper
sudo modprobe b44
```

---

### Post by VerballyCopulating on 2008-08-17
```
e@Blaster:~$ sudo rmmod ndiswrapper b44 ssb 
e@Blaster:~$ sudo modprobe ndiswrapper
e@Blaster:~$ sudo modprobe b44
```

as soon as I hit enter on the last modprobe I noticed the nm-applet start connecting.  Thanks!  

What exactly did that do?  Is this a permanent fix, or should I keep these lines in mind for the next reboot?

Grüße aus dem Schwartzwald

---

### Post by jw5801 on 2008-08-17
> **VerballyCopulating said:**
> ```
e@Blaster:~$ sudo rmmod ndiswrapper b44 ssb 
e@Blaster:~$ sudo modprobe ndiswrapper
e@Blaster:~$ sudo modprobe b44
```

as soon as I hit enter on the last modprobe I noticed the nm-applet start connecting.  Thanks!  

What exactly did that do?  Is this a permanent fix, or should I keep these lines in mind for the next reboot?

Grüße aus dem Schwartzwald

Not a permanent fix, it's effectively what the script we added to /etc/rc.local does, except also removing and readding ndiswrapper. This strictly shouldn't be necessary unless you've told ndiswrapper to be loaded elsewhere, you haven't added it to /etc/modules (if you have, remove it from there)? To fix the issue you can take the untidy brute force method and ndiswrapper to the list of modules you're removing in /etc/rc.local, or you can attempt to debug why ndiswrapper is being loaded when it shouldn't be.

---

### Post by VerballyCopulating on 2008-08-17
> To fix the issue you can take the untidy brute force method and ndiswrapper to the list of modules you're removing in /etc/rc.local, or you can attempt to debug why ndiswrapper is being loaded when it shouldn't be.
Yeah, I noticed a reboot effectively left me at the same place as before.

No, I havent added ndiswrapper to /etc/modules and I'm assuming a "cat /etc/modules" would report the same as above.

Just to clarify the brut force method... I should *add* ndiswrapper in /etc/rc.local ?  But it appears to be already there, the third entry?  Or are you saying there should be an -r tag in front of it?  I'm a little stuck there...

As far as debugging, I'm affraid it's not going to get me far, as I am a relatively inexperienced linux user :( but the will is there and I want to learn more!  Cheers!

---

### Post by legofsalmon on 2008-08-25
Hey there...

I'm completely new to all this but as far as I know I followed the tutorial to the letter and everything seemed fine. I've probably made a simple mistake or something. Here's the output from those commands...

```

lspci -nn | grep 14e4

[INDENT]03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/INDENT]

ndiswrapper -l

[INDENT]
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
[/INDENT]

ndiswrapper -v

[INDENT]
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-rt/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-rt SMP preempt mod_unload 586
[/INDENT]

lsmod | grep b43

[INDENT]
*Nothing returned for this command*
[/INDENT]

lsmod | grep ndiswrapper

[INDENT]
ndiswrapper           197544  0 
usbcore               146924  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,uhci_hcd
[/INDENT]

ls -l /etc/rc.local

[INDENT]
-rwxr-xr-x 1 root root 373 2008-08-25 08:31 /etc/rc.local
[/INDENT]

cat /etc/rc.local

[INDENT]
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

[/INDENT]

lshw -C network

[INDENT]
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:82:2b:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a4:66:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.140 latency=64 module=ssb multicast=yes

[/INDENT]

Does anyone have any ideas?

```

---

### Post by jw5801 on 2008-08-25
> **legofsalmon said:**
> Hey there...

I'm completely new to all this but as far as I know I followed the tutorial to the letter and everything seemed fine. I've probably made a simple mistake or something. Here's the output from those commands...

```

lspci -nn | grep 14e4

[INDENT]03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
[/INDENT]

ndiswrapper -l

[INDENT]
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
[/INDENT]

ndiswrapper -v

[INDENT]
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-19-rt/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-19-rt SMP preempt mod_unload 586
[/INDENT]

lsmod | grep b43

[INDENT]
*Nothing returned for this command*
[/INDENT]

lsmod | grep ndiswrapper

[INDENT]
ndiswrapper           197544  0 
usbcore               146924  6 ndiswrapper,hci_usb,usbhid,ehci_hcd,uhci_hcd
[/INDENT]

ls -l /etc/rc.local

[INDENT]
-rwxr-xr-x 1 root root 373 2008-08-25 08:31 /etc/rc.local
[/INDENT]

cat /etc/rc.local

[INDENT]
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

[/INDENT]

lshw -C network

[INDENT]
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1e:4c:82:2b:6a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:a4:66:cb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.140 latency=64 module=ssb multicast=yes

[/INDENT]
```

Does anyone have any ideas?


Well, it looks like the driver is working fine. Did the light come on? Can you see any networks?
```
iwlist scan
```

---

### Post by legofsalmon on 2008-08-25
The light on it only worked when I bought it. After a re installation it wouldn't even work under windows xp.

that command brought out

```

lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.


```

I know my wireless is working as I have windows xp on the same system and it works fine on that. I even have two wireless in my house and I can't connect to either.

Wired over ethernet works fine though, speedy as anything.

---

### Post by iwc5893 on 2008-09-20
I was able to get the wifi adapter on my Dell Vostro 1510 working using this procedure, but I had to use the drivers that were in my C:/drivers/network/R189335 directory.

---

### Post by jw5801 on 2008-09-20
> **iwc5893 said:**
> I was able to get the wifi adapter on my Dell Vostro 1510 working using this procedure, but I had to use the drivers that were in my C:/drivers/network/R189335 directory.

For the reference of others, what card does your laptop have? I'm assuming it's a broadcom, so what does ```
lspci|grep 14e4
``` return?

---

### Post by iwc5893 on 2008-09-21
> **jw5801 said:**
> For the reference of others, what card does your laptop have? I'm assuming it's a broadcom, so what does ```
lspci|grep 14e4
``` return?

The 14e4 didn't return anything, but here is the networking portion of the lspci command

> 06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)


---

### Post by jw5801 on 2008-09-21
> **iwc5893 said:**
> The 14e4 didn't return anything, but here is the networking portion of the lspci command

Whoops! Try putting a -nn in there (lspci -nn | grep 14e4). Never mind though:
```
**06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)**
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
```

The bolded line is your wireless card, so it's a 4312 rather than a 4311. So it would appear R189335 works for this card.

---

### Post by iwc5893 on 2008-09-21
> **jw5801 said:**
> Whoops! Try putting a -nn in there (lspci -nn | grep 14e4). Never mind though:
```
**06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)**
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev ff)
```

The bolded line is your wireless card, so it's a 4312 rather than a 4311. So it would appear R189335 works for this card.

Yeah, I figured that one out after about 15 minutes during my initial config.  That's why I posted which driver I had to use to get it working.

---

### Post by Light Engine on 2008-09-21
Thanks for the help. This helped me get my wireless card working when the first time I used Hardy and the second time when I had to re-install it later for different problems.

Rock on,

-David

---

### Post by ep3w on 2008-09-26
Will this work for 8.10/ Intrepid?

---

### Post by jw5801 on 2008-09-27
> **ep3w said:**
> Will this work for 8.10/ Intrepid?

Last I checked it was still necessary to use the workaround with kernel 2.6.27 (the one Intrepid was using, last I checked). As for a full install of Intrepid, I'm unsure. Boot up, see if it works using b43 (the default), failing that install ndiswrapper and a driver (as detailed in this How-To) and 'modprobe ndiswrapper', if nothing happens try 'rmmod ndiswrapper b43 b44 ssb && modprobe ndiswrapper' and see what happens then. If only the last works, then this workaround is still necessary. If the first works you don't need to do anything, and if the second works, just add ndiswrapper to /etc/modules and you'll be set.

---

### Post by ep3w on 2008-09-27
> **jw5801 said:**
> Last I checked it was still necessary to use the workaround with kernel 2.6.27 (the one Intrepid was using, last I checked). As for a full install of Intrepid, I'm unsure. Boot up, see if it works using b43 (the default), failing that install ndiswrapper and a driver (as detailed in this How-To) and 'modprobe ndiswrapper', if nothing happens try 'rmmod ndiswrapper b43 b44 ssb && modprobe ndiswrapper' and see what happens then. If only the last works, then this workaround is still necessary. If the first works you don't need to do anything, and if the second works, just add ndiswrapper to /etc/modules and you'll be set.

Thanks, I will have to give it a shot next time I get a chance.  I am always hesitant to update my notebook when I am not sure about getting the wireless to work but I was tempted to update early this time and see how it progresses.

---

### Post by jw5801 on 2008-09-27
> **ep3w said:**
> Thanks, I will have to give it a shot next time I get a chance.  I am always hesitant to update my notebook when I am not sure about getting the wireless to work but I was tempted to update early this time and see how it progresses.

You could always create another partition to test it in. I have a spare partition on my external drive I use for testing different distros and different versions of distros before I install them, just to make sure I can get everything working with relative ease.

---

### Post by Fuffed on 2008-10-30
I did exactly what you told me to do.
And its up and running.
But I can connect to a wireless network (tried more than 1 so thats not the problem)

I can see a list of all networks avalaible and I can type the WEP key (it's the correct one) but then it doesn't connect to it.

A clear newb @ linux, but still love it though.

Hope someone can help me out :)

---

### Post by mpgarate on 2008-10-30
try the latest version of ubuntu, 8.10 intrepid, which solved this issue for me. Wifi drivers were added and I could install them via System > administration > hardware drivers

---

### Post by jw5801 on 2008-10-30
> **Fuffed said:**
> I did exactly what you told me to do.
And its up and running.
But I can connect to a wireless network (tried more than 1 so thats not the problem)

I can see a list of all networks avalaible and I can type the WEP key (it's the correct one) but then it doesn't connect to it.

A clear newb @ linux, but still love it though.

Hope someone can help me out :)

Can you post the list of debug info at the end of the how-to for me? That'll give me more of an idea what's going on.

---

### Post by Fuffed on 2008-10-31
It's workin!

Finally got it right, I did everything correct on your how-to. And it did a great job now.
THe only thing I had to do was to configure manually to my wireless network. 

So for the people who have the same problem.
Left-mouse on your network icon, activate your wireless connection and configure it. Then the network is setting up the new configures and hopefully it will work :)

Many thanks :)

I love Ubuntu!

---

### Post by Repubhippy on 2008-10-31
I installed Intrepid on my Inspiron 6400 and my Dell 1390 is Showing up when I run LPSCI, but I can't connect to my Wireless network.  Also when I try to enable the restricted drivers For my ATI 1300 It does not go to enabled, it simply asks for my password and then stops.

---

### Post by jw5801 on 2008-11-01
> **Repubhippy said:**
> I installed Intrepid on my Inspiron 6400 and my Dell 1390 is Showing up when I run LPSCI, but I can't connect to my Wireless network.

Have you run the How-To? If so, please post the output from the debug commands at the end.

> Also when I try to enable the restricted drivers For my ATI 1300 It does not go to enabled, it simply asks for my password and then stops.

You'll have to start a new thread for this one.

---

### Post by jwatts on 2008-11-12
I don't know what other variables might be involved, but I have the exact chipset mentioned in the title of this thread, and it works like a charm with fwcutter and b43. My laptop is a Dell Inspiron E1405. The fwcutter instructions I used came from [here]("http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation"). I've reprocessed them to make them specifically relevant to users like me (Ubuntu 8.10 and Broadcom 4311). These instructions also assume wired connectivity for the necessary download.

To see if these instructions are relevant to you, run:

```
lspci  | grep Broadcom\ Corporation
```

If the result contains a line like:

```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

You're in business. Note that the initial "0c:00.0" may differ for you. If anything else on the line is different, your chances of these instructions working just went down. If you'd like to try anyway, read on.

In a terminal window, execute:

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

A colorful text screen will ask if you want it to do stuff automatically. You do. Say yes. You may also need to execute to blacklist the older module:

```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

That's it. You may need to throw in a reboot and I had to hit the key combination to enable the wireless card (Fn+F2 for me).

---

### Post by jw5801 on 2008-11-13
> **jwatts said:**
> I don't know what other variables might be involved, but I have the exact chipset mentioned in the title of this thread, and it works like a charm with fwcutter and b43. My laptop is a Dell Inspiron E1405. The fwcutter instructions I used came from [here]("http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation"). I've reprocessed them to make them specifically relevant to users like me (Ubuntu 8.10 and Broadcom 4311). These instructions also assume wired connectivity for the necessary download.

Might be an idea to start a new thread for this.

> To see if these instructions are relevant to you, run:

```
lspci  | grep Broadcom\ Corporation
```

If the result contains a line like:

```
0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```

You're in business. Note that the initial "0c:00.0" may differ for you. If anything else on the line is different, your chances of these instructions working just went down. If you'd like to try anyway, read on.

The 0c:00.0 is "The name of the slot where the device resides ([domain:]bus:device.function)." to quote the lspci man page. So it doesn't actually mean anything about the device, other than where it's installed. For some more information, look at `lspci -nn' which will output the chipset id [14e4:4311] which is all that should matter from a firmware perspective.

> In a terminal window, execute:

```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

A colorful text screen will ask if you want it to do stuff automatically. You do. Say yes. You may also need to execute to blacklist the older module:

```
sudo echo blacklist bcm43xx >> /etc/modprobe.d/blacklist
```

That's it. You may need to throw in a reboot and I had to hit the key combination to enable the wireless card (Fn+F2 for me).

You shouldn't need a complete reboot, just removing and reloading the b43 module should do it `modprobe -r b43 && modprobe b43'. And bcm43xx shouldn't exist at all in the newer kernel, so you'd only need to blacklist it if you've still got it left over from a much older kernel on your system, and even then it should be somewhere modprobe won't look for the newer kernel.

---

### Post by hmaccorkle on 2008-11-13
This worked for me! Thank you so very much!!:popcorn:

---

### Post by mg620 on 2008-11-15
Thank you!  This worked perfectly the first time I tried it.  I've even restarted twice just to make sure!  (Running Dell Vostro, AMD Athlon x2, bcm4311 wifi card, ubuntu 8.10.)

---

### Post by Dutchmidget on 2008-12-16
Dell Vostro 1500 running 8.10 and working like a charm, followed instructions and everything runs perfectly. Thank you!:p

---

### Post by bcravvar on 2009-01-13
Can you please help me I am still not able to use my wireless network card. The WIFI light is on.

bongu@bongu-laptop:~$ lspci -nn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
bongu@bongu-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
bcmwl6 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
bongu@bongu-laptop:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
version:        1.51
vermagic:       2.6.24-16-generic SMP mod_unload 586 
bongu@bongu-laptop:~$ lsmod | grep b43
bongu@bongu-laptop:~$ lsmod | grep ndiswrapper
ndiswrapper           193500  0 
usbcore               146028  6 hci_usb,ndiswrapper,usbhid,ehci_hcd,uhci_hcd
bongu@bongu-laptop:~$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2009-01-13 22:10 /etc/rc.local
bongu@bongu-laptop:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0
bongu@bongu-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:79:98:7a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.106 latency=64 module=ssb multicast=yes

bongu@bongu-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

bongu@bongu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:79:98:7a  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe79:987a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:835867 (816.2 KB)  TX bytes:103977 (101.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84200 (82.2 KB)  TX bytes:84200 (82.2 KB)

---

### Post by jw5801 on 2009-01-14
> **bcravvar said:**
> Can you please help me I am still not able to use my wireless network card. The WIFI light is on.

...
```
bongu@bongu-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
bcmwl6 : driver installed
	device (14E4:4311) present (alternate driver: ssb)
```
...


You don't want the bcmwl6 driver installed. That's for Vista and won't work with ndiswrapper, it'll interfere, which is why ndiswrapper isn't working. We'll remove it and then try loading the module again.

```
sudo -i
ndiswrapper -e bcmwl6
rmmod ndiswrapper b44 ssb
modprobe -v ndiswrapper
lshw -C network
logout
```

That should get it working, if not post all the outputs and we'll see what's happening.

---

### Post by bcravvar on 2009-01-14
> **jw5801 said:**
> You don't want the bcmwl6 driver installed. That's for Vista and won't work with ndiswrapper, it'll interfere, which is why ndiswrapper isn't working. We'll remove it and then try loading the module again.

```
sudo -i
ndiswrapper -e bcmwl6
rmmod ndiswrapper b44 ssb
modprobe -v ndiswrapper
lshw -C network
logout
```

That should get it working, if not post all the outputs and we'll see what's happening.




Thanks you!!!!!!!!! Hurray its working now,

---

### Post by Bucky Ball on 2009-01-14
What is wrong with b43 for this broadcom card? Easier, quicker. I tried ndiswrapper for months with no success. Installed 8.0.4 and was up in about 5 minutes.

---

### Post by jw5801 on 2009-01-15
> **Bucky Ball said:**
> What is wrong with b43 for this broadcom card? Easier, quicker. I tried ndiswrapper for months with no success. Installed 8.0.4 and was up in about 5 minutes.

Nothing. I've found ndiswrapper to be more stable that b43, and it doesn't require installing any firmware, but they're both valid methods of getting the card running. One works for some, the other for others.

---

### Post by Invincible13 on 2009-01-15
Okay, I don't know if something happened or what, but I cannot download the modules package to add ndiswrapper as a modprobe module.  Can anyone explain how to fix this ?

---

### Post by jw5801 on 2009-01-16
> **Invincible13 said:**
> Okay, I don't know if something happened or what, but I cannot download the modules package to add ndiswrapper as a modprobe module.  Can anyone explain how to fix this ?

You can't install linux-ubuntu-modules? Can you install any repository packages? You can find the deb through your browser at packages.ubuntu.com.

---

### Post by bloob on 2009-02-07
JW,

First, I'd like to thank you for the tremendous amount of time and energy you've put into developing this Howto and into your responses to queries.  You're great!!

I'm running a fresh install of Hardy 8.04 on my friend's laptop, a hp pavillion dv2000, that has a Broadcom 4311 wireless card, {14e4:4311}.  I would post all of the outputs you requested in the troubleshooting, but I don't have a wired connection on the laptop (i'm accessing the internet from my own box, which also has Hardy) and it would take a lot of time to transcribe the output in the terminal.  

In followed your directions, but then, like a lot of others, couldn't get the wireless light to turn on, nor would the wireless icon register in the network manager.  I found that typing these commands


sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up


suddenly got the network manager showing the wireless network, and I connected, no problem.  After a restart, though, I got the wireless light on, but again no wireless recognition in the network manager.  Typing the same set of commands brought up the wireless networks in manager and I was again able to connect.  

My friend, who owns the laptop, is brandspankin' new to Ubuntu, so I didn't want to leave it here.  Following your advice to another user, I added 

ndiswrapper

to the end of the /etc/modules file and rebooted.  Couldn't get a connection.  Then I removed ndiswrapper from the end of /etc/modules and rebooted, but still couldn't get a connection.  

Now, when I try the commands that worked before, I get:

~$ sudo modprobe -r b43 b44 ssb ndiswrapper
FATAL: Module sbb not found
~$sudo modprobe ndiswrapper
~$sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device[/INDENT]


Here is the contents of /etc/modules:

fuse
lp
sbp2


And here is the contents of /etc/rc.local:

modprobe -r b44
modprobe -r sbb
modprobe ndiswrapper
modprobe b44


That's where I am right now.  As you've already guessed, I'm an utter newb; this is my first project on the command-line and my first post to the forums.  Sorry about the poor formatting for the post; still tryin' to figure it all out.  

Again, JW, really appreciate your diligence and help.

PJB

---

### Post by jw5801 on 2009-02-07
> **bloob said:**
> JW,

First, I'd like to thank you for the tremendous amount of time and energy you've put into developing this Howto and into your responses to queries.  You're great!!

I'm running a fresh install of Hardy 8.04 on my friend's laptop, a hp pavillion dv2000, that has a Broadcom 4311 wireless card, {14e4:4311}.  I would post all of the outputs you requested in the troubleshooting, but I don't have a wired connection on the laptop (i'm accessing the internet from my own box, which also has Hardy) and it would take a lot of time to transcribe the output in the terminal.  

In followed your directions, but then, like a lot of others, couldn't get the wireless light to turn on, nor would the wireless icon register in the network manager.  I found that typing these commands


sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up


suddenly got the network manager showing the wireless network, and I connected, no problem.  After a restart, though, I got the wireless light on, but again no wireless recognition in the network manager.  Typing the same set of commands brought up the wireless networks in manager and I was again able to connect.  

My friend, who owns the laptop, is brandspankin' new to Ubuntu, so I didn't want to leave it here.  Following your advice to another user, I added 

ndiswrapper

to the end of the /etc/modules file and rebooted.  Couldn't get a connection.  Then I removed ndiswrapper from the end of /etc/modules and rebooted, but still couldn't get a connection.  

Now, when I try the commands that worked before, I get:

~$ sudo modprobe -r b43 b44 ssb ndiswrapper
FATAL: Module sbb not found
~$sudo modprobe ndiswrapper
~$sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device[/INDENT]


Here is the contents of /etc/modules:

fuse
lp
sbp2


And here is the contents of /etc/rc.local:

modprobe -r b44
modprobe -r sbb
modprobe ndiswrapper
modprobe b44


That's where I am right now.  As you've already guessed, I'm an utter newb; this is my first project on the command-line and my first post to the forums.  Sorry about the poor formatting for the post; still tryin' to figure it all out.  

Again, JW, really appreciate your diligence and help.

PJB

From what I can see, it looks as though you haven't blacklisted b43, since you're needing to rmmod it before being able to get started. Is there a "blacklist b43" line in /etc/modprobe.d/blacklist? At least for the original issue, that would work. Don't put the line into /etc/modules, that just means you'll need to remove ndiswrapper and readd it (as you've seen), which adds complexity.

If you can copy the terminal outputs into a text file and copy that across to a networked machine using a USB drive, that could provide some insight?

For anyone following this thread who's a bit more adventurous, the best method by far to get around this problem, is to build your own kernel and just not build the b43 module at all. Then you can also avoid needing an initrd. There's a bit more of an investment of time learning how to configure the kernel, however.

---

### Post by bloob on 2009-02-07
> **jw5801 said:**
> From what I can see, it looks as though you haven't blacklisted b43, since you're needing to rmmod it before being able to get started. Is there a "blacklist b43" line in /etc/modprobe.d/blacklist? At least for the original issue, that would work. Don't put the line into /etc/modules, that just means you'll need to remove ndiswrapper and readd it (as you've seen), which adds complexity.

If you can copy the terminal outputs into a text file and copy that across to a networked machine using a USB drive, that could provide some insight?

For anyone following this thread who's a bit more adventurous, the best method by far to get around this problem, is to build your own kernel and just not build the b43 module at all. Then you can also avoid needing an initrd. There's a bit more of an investment of time learning how to configure the kernel, however.

Jw,

Thanks for getting back so quickly.  After a reboot, the command string

sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up

gets me connected.  I don't even need to mess around with network manager or select a wireless network or give the password.  

There is both a "blacklist b43" and a "blacklist b43legacy" line in the blacklist file, so I don't think that's the problem.  I saw someone elsewhere recommend adding "blacklist b43xxx" to the list.  Should I do that?

---

### Post by jw5801 on 2009-02-08
> **bloob said:**
> Jw,

Thanks for getting back so quickly.  After a reboot, the command string

sudo modprobe -r b43 b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo ifconfig wlan0 up

gets me connected.  I don't even need to mess around with network manager or select a wireless network or give the password.  

There is both a "blacklist b43" and a "blacklist b43legacy" line in the blacklist file, so I don't think that's the problem.  I saw someone elsewhere recommend adding "blacklist b43xxx" to the list.  Should I do that?

Probably not. bcm43xx is the old version of b43, so unless you're running an old kernel, it shouldn't exist. Boot up, and while it's not working check `lshw -C network' to see which module has control of the wireless card. Also try running those commands without rmmodding b43. ie.
```
sudo rmmod b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```

If that works, then your issue is in your /etc/rc.local script, so check that.

Can you get the debug output while it's not working, then run the commands to fix it so you can connect and post the debug output?

---

### Post by bloob on 2009-02-08
> **jw5801 said:**
> Probably not. bcm43xx is the old version of b43, so unless you're running an old kernel, it shouldn't exist. Boot up, and while it's not working check `lshw -C network' to see which module has control of the wireless card. Also try running those commands without rmmodding b43. ie.
```
sudo rmmod b44 ssb ndiswrapper
sudo modprobe ndiswrapper
```

If that works, then your issue is in your /etc/rc.local script, so check that.

Can you get the debug output while it's not working, then run the commands to fix it so you can connect and post the debug output?

JW, 

Here is the result of lshw -C network *before* it starts working:

[FONT="Courier New"]tuan@tuan-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
tuan@tuan-laptop:~$[/FONT]

I tried running the command string without rmmoding b43 and it didn't get the network up:

[FONT="Courier New"]tuan@tuan-laptop:~$ sudo rmmod b44 sbb ndiswrapper
[sudo] password for tuan: 
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module sbb does not exist in /proc/modules
ERROR: Module ndiswrapper does not exist in /proc/modules
tuan@tuan-laptop:~$ sudo modprobe ndiswrapper
tuan@tuan-laptop:~$ sudo ifconfig wlan0up
wlan0up: error fetching interface information: Device not found
tuan@tuan-laptop:~$ [/FONT]

Neither did this get it up and running: 

[FONT="Courier New"]
tuan@tuan-laptop:~$ sudo rmmod b44 sbb ndiswrapper b43
ERROR: Module b44 does not exist in /proc/modules
ERROR: Module sbb does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules
tuan@tuan-laptop:~$ sudo modprobe ndiswrapper
tuan@tuan-laptop:~$ sudo ifconfig wlan0up
wlan0up: error fetching interface information: Device not found[/FONT]

This still did, though, immediately afterward:

[FONT="Courier New"]tuan@tuan-laptop:~$ sudo modprobe -r b43 b44 sbb ndiswrapper
FATAL: Module sbb not found.
tuan@tuan-laptop:~$ sudo modprobe ndiswrapper
tuan@tuan-laptop:~$ sudo ifconfig wlan0up
wlan0up: error fetching interface information: Device not found
tuan@tuan-laptop:~$ [/FONT]

Funny, since it gives me error messages...

And the result of [FONT="Courier New"]lshw -C network[/FONT] while it's working: 

[FONT="Courier New"]tuan@tuan-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:14:a5:f8:f5:1d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. ip=192.168.0.3 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
tuan@tuan-laptop:~$ [/FONT]


Again, JW, thanks for the help with this.

---

### Post by jw5801 on 2009-02-09
You shouldn't need to run 'sudo ifconfig wlan0 up' and the error that was giving you was because you left out the space between 'wlan0' and 'up' so ifconfig couldn't identify the interface 'wlan0up' because it doesn't exist.

> **bloob said:**
> ```
]tuan@tuan-laptop:~$ sudo rmmod b44 sbb ndiswrapper
[sudo] password for tuan: 
[b]ERROR: Module b44 does not exist in /proc/modules
ERROR: Module sbb does not exist in /proc/modules
ERROR: Module ndiswrapper does not exist in /proc/modules[/b]
tuan@tuan-laptop:~$ sudo modprobe ndiswrapper
tuan@tuan-laptop:~$ sudo ifconfig wlan0up
wlan0up: error fetching interface information: Device not found
tuan@tuan-laptop:~$ 
```

```
tuan@tuan-laptop:~$ sudo rmmod b44 sbb ndiswrapper b43
[b]ERROR: Module b44 does not exist in /proc/modules
ERROR: Module sbb does not exist in /proc/modules
ERROR: Module b43 does not exist in /proc/modules[/b]
tuan@tuan-laptop:~$ sudo modprobe ndiswrapper
tuan@tuan-laptop:~$ sudo ifconfig wlan0up
wlan0up: error fetching interface information: Device not found
```

You mistyped ssb (you have sbb), but it makes no difference, since ssb wasn't modprobed anyway. Note the messages I've highlighted in bold above. These are telling you that none of b43, b44 or ndiswrapper were loaded when you first booted up.

> ```
tuan@tuan-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
tuan@tuan-laptop:~$
```
The message above tells you that your wireless card is 'unclaimed', ie. a module capable of controlling it has not been loaded into the kernel. This means that all you need to do is 'sudo modprobe ndiswrapper' once you've booted up and it should be fine. All you did with the last command was remove ndiswrapper and reload it, which wouldn't actually have made any difference.

This means that the issue is in your /etc/rc.local, so if you can post that?

---

### Post by bloob on 2009-02-10
> **jw5801 said:**
> 
This means that the issue is in your /etc/rc.local, so if you can post that?


Got it.  Typo (of course) in my 
[FONT="Courier New"]
modprobe ndiswrapper[/FONT]

line in [FONT="Courier New"]/etc/rc.local[/FONT] meant that ndiswrapper wasn't modprobed on startup.  Fixed it, and things have gone swimmingly for two reboots.

If you can walk a noob like me through it, I'm sure you could get a chimp up and accessing his wireless network!

I can't recommend this thread, or your advice highly enough.  Thank you.

PJB

---

### Post by jw5801 on 2009-02-10
> **bloob said:**
> Got it.  Typo (of course) in my 
[FONT="Courier New"]
modprobe ndiswrapper[/FONT]

line in [FONT="Courier New"]/etc/rc.local[/FONT] meant that ndiswrapper wasn't modprobed on startup.  Fixed it, and things have gone swimmingly for two reboots.

If you can walk a noob like me through it, I'm sure you could get a chimp up and accessing his wireless network!

I can't recommend this thread, or your advice highly enough.  Thank you.

PJB

No problems! Thanks for appreciating :)

---

### Post by C. M .Hughes on 2009-05-07
This worked great for me on my Dell 1521 with BCM4311 802.11b/g WLAN

Thanks for posting, it was really easy to follow.

---

### Post by bcravvar on 2009-06-06
Hi,

I installed ubuntu 9.04 and I tried this thread for 8.04 and it worked wonders. Can you please help me what's wrong in 9.04

bongu@bongu-laptop:~/DRIVER$ lspci -nn | grep 14e4
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

bongu@bongu-laptop:~/DRIVER$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

bongu@bongu-laptop:~/DRIVER$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.28-11-generic/misc/ndiswrapper.ko
version:        1.54
vermagic:       2.6.28-11-generic SMP mod_unload modversions 586 

bongu@bongu-laptop:~/DRIVER$ lsmod | grep b43

bongu@bongu-laptop:~/DRIVER$ lsmod | grep ndiswrapper
ndiswrapper           193308  0 

bongu@bongu-laptop:~/DRIVER$ ls -l /etc/rc.local
-rwxr-xr-x 1 root root 421 2009-06-06 12:20 /etc/rc.local
bongu@bongu-laptop:~/DRIVER$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

bongu@bongu-laptop:~/DRIVER$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:79:98:7a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.106 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:f6:e1:06:9c:b1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by jw5801 on 2009-06-06
> **bcravvar said:**
> Hi,

I installed ubuntu 9.04 and I tried this thread for 8.04 and it worked wonders. Can you please help me what's wrong in 9.04

Looks as though the ndiswrapper module is being loaded earlier than it should be. As a quick fix you can run:
```
modprobe -r b43 b44 ssb ndiswrapper
modprobe ndiswrapper
modprobe b44
```
That should give you an error about b43 not being loaded into the kernel, but I've added it there just in case.

If that works you can get it to persist on reboot by adding a `modprobe -r ndiswrapper' line at the start of your rc.local, however it's not the nicest solution.

A better solution would be to find where ndiswrapper is being loaded into the kernel, and prevent it from happening until we want it to.

> bongu@bongu-laptop:~/DRIVER$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: ssb)

I'm curious about this `/etc/modprobe.d/ndiswrapper' file that's being complained about. Can you print whatever is in it up here?
```
cat /etc/modprobe.d/ndiswrapper
```

---

### Post by bcravvar on 2009-06-06
No Luck it diasable my wired network and enabled it again.

This is the output of 
bongu@bongu-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

---

### Post by Valk01 on 2009-06-08
Just wanted to report this worked np for me in 8.04 on my HP 2710P tablet with broadcom. 

thank you!

---

### Post by jw5801 on 2009-06-08
> **bcravvar said:**
> No Luck it diasable my wired network and enabled it again.

This is the output of 
bongu@bongu-laptop:~$ cat /etc/modprobe.d/ndiswrapper
alias wlan0 ndiswrapper

Ok, did you get any errors from those commands?

---

### Post by bcravvar on 2009-06-11
> **Valk01 said:**
> Just wanted to report this worked np for me in 8.04 on my HP 2710P tablet with broadcom. 

thank you!
It worked for me on 8.04 thats the reason I am trying it for 9.04

---

### Post by bcravvar on 2009-06-11
> **jw5801 said:**
> Ok, did you get any errors from those commands?
bongu@bongu-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
[sudo] password for bongu: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
Wired network disabled here

bongu@bongu-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

bongu@bongu-laptop:~$ sudo modprobe b44
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

Wired network is back again. Still the wireless network is not working.

Let me know if you need more details

---

### Post by jw5801 on 2009-06-11
> **bcravvar said:**
> ```
bongu@bongu-laptop:~$ sudo modprobe -r b43 b44 ssb ndiswrapper
[sudo] password for bongu: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```
Wired network disabled here

```
bongu@bongu-laptop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

```
bongu@bongu-laptop:~$ sudo modprobe b44
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

Wired network is back again. Still the wireless network is not working.

Let me know if you need more details

Your wired NIC is controlled by the b44 module, which is why it goes down. b44 requires ssb which hijacks the wireless card, that's why we have to remove both of them. It should be yelling at you about rmmoding b43, have you blacklisted it? Regardless that won't help in the short term. What do you see from the following (code tags are nice :))?

```
sudo -s #the -s essentially gives you a root shell for a bit
# Let's see what's controlling the card to start off with
lshw -C network

# When there should be nothing loaded to control it
rmmod b43 b44 ssb ndiswrapper
lshw -C network

# And with ndiswrapper loaded
modprobe ndiswrapper
lshw -C network

# Reload b44 to get your wired back up, and then exit the root shell
modprobe b44
exit
```

---

### Post by bcravvar on 2009-06-21
sudo -s #the -s essentially gives you a root shell for a bit
# Let's see what's controlling the card to start off with
lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:dc:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:79:98:7a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.106 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1e:5d:2a:2f:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@bongu-laptop:~# 


# When there should be nothing loaded to control it
rmmod b43 b44 ssb ndiswrapper

root@bongu-laptop:~# rmmod b43 b44 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules

lshw -C network
root@bongu-laptop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:dc:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1e:5d:2a:2f:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


# And with ndiswrapper loaded
modprobe ndiswrapper

root@bongu-laptop:~# modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

lshw -C network
root@bongu-laptop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:dc:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1e:5d:2a:2f:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


# Reload b44 to get your wired back up, and then exit the root shell
modprobe b44

root@bongu-laptop:~# modprobe b44
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


root@bongu-laptop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:dc:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:79:98:7a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.106 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1e:5d:2a:2f:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


exit

---

### Post by jw5801 on 2009-06-21
> **bcravvar said:**
> ```
sudo -s #the -s essentially gives you a root shell for a bit
# Let's see what's controlling the card to start off with
lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:dc:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:79:98:7a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.106 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1e:5d:2a:2f:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@bongu-laptop:~# 
```

# When there should be nothing loaded to control it
rmmod b43 b44 ssb ndiswrapper

```
root@bongu-laptop:~# rmmod b43 b44 ssb ndiswrapper
ERROR: Module b43 does not exist in /proc/modules

lshw -C network
root@bongu-laptop:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7e:4d:dc:81
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.54+Broadcom,10/12/2006, 4.100. latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:1e:5d:2a:2f:17
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

...

code tags are nice ;)

Ok, your wireless card was working before we started running any of these commands. Something funny is happening here (ndispwrapper was not removed when you rmmodded it), but it won't make any difference. 

Without doing anything after booting, what do you see from the following?

```
ifconfig
```

---

### Post by bcravvar on 2009-06-22
ifconfig
bongu@bongu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:79:98:7a  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe79:987a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1630 (1.6 KB)  TX bytes:4451 (4.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by jw5801 on 2009-06-22
> **bcravvar said:**
> ifconfig
```
bongu@bongu-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:c5:79:98:7a  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe79:987a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1630 (1.6 KB)  TX bytes:4451 (4.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

Please use code tags, it makes outputs so much easier to read.

The above conflicts with your previous outputs. Your previous output has your wireless card working fine using ndiswrapper with a logical interface of wlan0. Maybe try running:
```
ifconfig wlan0 up
```

That shouldn't be necessary though.

---

### Post by soumo on 2009-07-10
Been banging my head around on this for a week now.  No luck.
Wifi was fine, then it wasn't.  I can't remember if it was shortly after I was trying to get a bluetooth headset working or if it was after an update, but here goes...Any help is appreciated:

~/Desktop$ lspci -nn | grep 14e4

[INDENT]03:00.0 Network controller [0280]: Broadcom Corporation BCM4328 802.11a/b/g/n [14e4:4328] (rev 01)
[/INDENT]
~/Desktop$ ndiswrapper -l

[INDENT]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
	device (14E4:4328) present (alternate driver: ssb)
[/INDENT]
~/Desktop$ ndiswrapper -v

[INDENT]utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.28-13-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.28-13-generic SMP mod_unload modversions 586 [/INDENT]

~/Desktop$ lsmod | grep b43

~/Desktop$ lsmod | grep ndiswrapper

[INDENT]ndiswrapper           193436  0 [/INDENT]

~/Desktop$ ls -l /etc/rc.local

[INDENT]-rwxr-xr-x 1 root root 372 2009-07-06 23:13 /etc/rc.local[/INDENT]

~/Desktop$ cat /etc/rc.local

[INDENT]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0[/INDENT]

~/Desktop$ lshw -C network

[INDENT]WARNING: you should run this program as super-user.

       description: Wireless interface
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:19:7d:a6:ed:d3
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,02/20/2008, 4.170. latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth4
       version: 10
       serial: 00:1b:38:0b:8d:bb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.10.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:88:11:37:13:64
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes[/INDENT]

~/Desktop$ ifconfig 

[INDENT]eth4      Link encap:Ethernet  HWaddr 00:1b:38:0b:8d:bb  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe0b:8dbb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8976 errors:5 dropped:5 overruns:5 frame:0
          TX packets:9300 errors:0 dropped:0 overruns:3 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7660994 (7.6 MB)  TX bytes:1267329 (1.2 MB)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81817 (81.8 KB)  TX bytes:81817 (81.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7d:a6:ed:d3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:d0200000-d0204000[/INDENT] 

~/Desktop$ iwconfig

[INDENT]lo        no wireless extensions.

eth4      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:270 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.[/INDENT]

~/Desktop$ cat /etc/NetworkManager/nm-system-settings.conf

[INDENT][main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true[/INDENT]

~/Desktop$ iwlist scan  #

[INDENT]lo        Interface doesn't support scanning.

eth4      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:51:03:AA
                    ESSID:"trendnet"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:93/100  Signal level:-36 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:01:29:C5:D7
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

pan0      Interface doesn't support scanning.[/INDENT]

~/Desktop$ cat /etc/modules

[INDENT]# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
#snd_bt_sco, sco =BT

lp
sbp2
#ndiswrapper
snd_bt_sco
sco
[/INDENT]
~/Desktop$ cat /etc/modprobe.d/blacklist

[INDENT]blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb
[/INDENT]
~/Desktop$ dmesg | grep -e ndis -e wlan

[INDENT][   14.893944] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   16.018469] ndiswrapper: driver bcmwl5 (Broadcom,02/20/2008, 4.170.75.0) loaded
[   16.018709] ndiswrapper 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.018798] ndiswrapper 0000:03:00.0: setting latency timer to 64
[   16.033826] ndiswrapper: using IRQ 17
[   16.252877] wlan0: ethernet device 00:19:7d:a6:ed:d3 using NDIS driver: bcmwl5, version: 0x4aa4b00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4328.5.conf
[   16.252924] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   16.261573] usbcore: registered new interface driver ndiswrapper
[   21.110519] ndiswrapper (add_wep_key:841): adding encryption key 1 failed (C0010015)
[   30.200798] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[/INDENT]
~/Desktop$ cat /etc/udev/rules.d/70-persistent-net.rules

[INDENT]# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0f:b0:d2:64:40", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4328 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:7d:a6:ed:d3", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x1011:0x0019 (tulip)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:a0:0c:90:68:1b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x4328 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:7d:a6:ed:d3", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x8086:0x1092 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:36:9b:43:4b", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"

# PCI device 0x8086:0x4222 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:de:53:97:3a", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:38:0b:8d:bb", ATTR{type}=="1", KERNEL=="eth*", NAME="eth4"[/INDENT]

~/Desktop$ ls /etc/udev/rules.d

[INDENT]45-libmtp7.rules  50-libfprint0.rules  70-persistent-cd.rules  70-persistent-net.rules  85-brltty.rules  README[/INDENT]

~/Desktop$ cat /etc/resolv.conf

[INDENT]domain phub.net.cable.rogers.com
search phub.net.cable.rogers.com
nameserver 192.168.10.1[/INDENT]

~/Desktop$ cat /etc/network/interfaces

[INDENT]auto lo
iface lo inet loopback
iface wlan0 inet dhcp
wireless-key s:********************
wireless-essid Lila

auto wlan0

iface eth4 inet dhcp

auto eth4
[/INDENT]

Sorry looks like i posted in the wrong place, still if anyone has any tips...

:D

---

### Post by jw5801 on 2009-07-11
> **soumo said:**
> Been banging my head around on this for a week now.  No luck.
Wifi was fine, then it wasn't.  I can't remember if it was shortly after I was trying to get a bluetooth headset working or if it was after an update, but here goes...Any help is appreciated:

...

Sorry looks like i posted in the wrong place, still if anyone has any tips...

:D

Haha, well from a driver perspective, everything is fine!

About all I can suggest is to try connecting to your network without any encryption, if that works fine, turn the encryption back on and try again. Otherwise try it with a different network manager (I use wicd, which I've always found to be far more reliable than the standard gnome network manager), or even with [no graphical network manager at all](http://ubuntuforums.org/showthread.php?t=571188).

---

### Post by soumo on 2009-07-12
Thank you!

Actually I was using wicd, but no dice.
I would try the no encryption, but I don't have an interface to connect to any network.

---

### Post by jw5801 on 2009-07-12
> **soumo said:**
> Thank you!

Actually I was using wicd, but no dice.
I would try the no encryption, but I don't have an interface to connect to any network.

What do you mean you don't have an interface? You have wlan0, and you can see a couple of networks through it.

> **soumo said:**
> 
...
```
~/Desktop$ ifconfig

...

    wlan0 Link encap:Ethernet HWaddr 00:19:7d:a6:ed:d3
    UP BROADCAST MULTICAST MTU:1500 Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
    Interrupt:17 Memory:d0200000-d0204000

~/Desktop$ iwconfig

...

    wlan0 IEEE 802.11g ESSIDff/any
    Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
    Bit Rate:270 Mb/s Tx-Power:32 dBm
    RTS thr:2347 B Fragment thr:2346 B
    Power Managementff
    Link Quality:0 Signal level:0 Noise level:0
    Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
    Tx excessive retries:0 Invalid misc:0 Missed beacon:0

...

~/Desktop$ iwlist scan #

...

    wlan0 Scan completed :

    Cell 01 - Address: 00:141:51:03:AA
    ESSID:"trendnet"
    Protocol:IEEE 802.11g
    Mode:Managed
    Frequency:2.427 GHz (Channel 4)
    Quality:93/100 Signal level:-36 dBm Noise level:-96 dBm
    Encryption keyn
    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
    9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
    48 Mb/s; 54 Mb/s
    Extra:bcn_int=100
    Extra:atim=0
    IE: WPA Version 1
    Group Cipher : TKIP
    Pairwise Ciphers (1) : TKIP
    Authentication Suites (1) : PSK

    Cell 02 - Address: 00:24:01:29:C57
    ESSID:"dlink"
    Protocol:IEEE 802.11g
    Mode:Managed
    Frequency:2.412 GHz (Channel 1)
    Quality:15/100 Signal level:-86 dBm Noise level:-96 dBm
    Encryption keyff
    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
    9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
    48 Mb/s; 54 Mb/s
    Extra:bcn_int=100
    Extra:atim=0

...
```

...

The problem at the moment appears to be with wpa_supplicant (the authentication back-end to wicd), as I believe a few of the log messages you're seeing come from it trying to do things.
> **soumo said:**
> ```
[ 21.110519] ndiswrapper (add_wep_key:841): adding encryption key 1 failed (C0010015)
[ 30.200798] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

My recommendation would be to attempt connecting manually using just wpa_supplicant and see if it gives any useful debug messages.

[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by bcravvar on 2009-07-22
Thanks buddy for your help!! I reverted the changes and repeated the steps again and its working this time :)

---

### Post by imapostdoc on 2009-09-02
it used to work and so well... *sigh* about a year ago I followed these instructions to install ndiswrapper and after several attempts got it running. Then it worked for a year and now it fails again. Meanwhile we tried to hook up to our own wireless router.

It seems that module b43 is absent
```
 sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
```
and
```
 lsmod |grep b43
```
has an empty outcome.

How can that be fixed? Is any other diagnostic output needed?

Thank you and best regards,
Peter

---

### Post by jw5801 on 2009-09-04
> **imapostdoc said:**
> it used to work and so well... *sigh* about a year ago I followed these instructions to install ndiswrapper and after several attempts got it running. Then it worked for a year and now it fails again. Meanwhile we tried to hook up to our own wireless router.

It seems that module b43 is absent
```
 sudo rmmod b43 b44 ssb
ERROR: Module b43 does not exist in /proc/modules
```
and
```
 lsmod |grep b43
```
has an empty outcome.

How can that be fixed? Is any other diagnostic output needed?

Thank you and best regards,
Peter

b43 not being loaded is a good thing if you're trying to use ndiswrapper. All you should then have to do is load ndiswrapper and all should be happy. Can you post the rest of the suggested debug output?

---

### Post by imapostdoc on 2009-09-07
hello jw5801,
thank you for you offer to help.
here is the output of the diagnostic commands
```
lspci -nn | grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)

```

```
 ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: wl)
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-24-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-24-generic SMP mod_unload 586 

```

```
lsmod | grep b43
lsmod | grep ndiswrapper
ndiswrapper           192920  0 
usbcore               146412  4 ndiswrapper,ehci_hcd,uhci_hcd

```
(no output after the first command)

```
cat  /etc/rc.local
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44
exit 0

```

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:c4:df:bd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:94:e6:1e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.101 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
```

```

iwconfig
lo        no wireless extensions.
 
eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:162
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

It is not the first time that I have this trouble. Last year I went through the installation procedure at least twice. We recently moved and tried to hook up this laptop to our new wireless internet router. This didn't work (I can describe that in greater detail if you want), but also now the network is not detected.

Thank you and best regards to Australia,
Peter

---

### Post by jw5801 on 2009-09-07
> **imapostdoc said:**
> ...

```
 ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4311) present (alternate driver: wl)
ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-24-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-24-generic SMP mod_unload 586 

```

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:c4:df:bd
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11
```

...

Always happy to help!

If you notice the new alternate driver is listed as `wl', and that this wl0 driver is claiming the card. I haven't encountered this module before, but you should be able to add it to the blacklist and all will be good.

As a test, try removing the offending module and reloading ndiswrapper:
```
sudo rmmod ndiswrapper wl
sudo modprobe ndiswrapper
```

Just out of curiosity, what kernel are you using ('uname -a' will tell you).

---

### Post by imapostdoc on 2009-09-08
> **jw5801 said:**
> Always happy to help!

If you notice the new alternate driver is listed as `wl', and that this wl0 driver is claiming the card. I haven't encountered this module before, but you should be able to add it to the blacklist and all will be good.

As a test, try removing the offending module and reloading ndiswrapper:
```
sudo rmmod ndiswrapper wl
sudo modprobe ndiswrapper
```

Just out of curiosity, what kernel are you using ('uname -a' will tell you).

I carried out the first two commands (they gave no output).
```
uname -a
Linux peter-laptop 2.6.24-24-generic #1 SMP Tue Aug 18 17:04:53 UTC 2009 i686 GNU/Linux

```
best regards,
Peter

---

### Post by imapostdoc on 2009-09-08
I carried out the first two commands (they gave no output), but the output of
```
lshw -C network

```
is the same as before (after a reboot).


```
uname -a
Linux peter-laptop 2.6.24-24-generic #1 SMP Tue Aug 18 17:04:53 UTC 2009 i686 GNU/Linux

```
best regards,
Peter

---

### Post by jw5801 on 2009-09-09
> **imapostdoc said:**
> I carried out the first two commands (they gave no output), but the output of
```
lshw -C network

```
is the same as before (after a reboot).

No output is exactly as expected and rebooting undoes what those commands just did, which is why lshw returns the same thing. You need to blacklist wl for any changes to persist, else it will continue to be loaded during bootup.

If you just remove the module and reload ndiswrapper (what those two commands do, they only output if there's a problem), your wireless should immediately start working, and lshw will report your wireless card being controlled by ndiswrapper. If this is true, then add a line containing 'blacklist wl' to /etc/modules.d/blacklist, by running:

```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

This will prevent the module from being loaded during boot, so you won't have to worry about it.

I've added a comment about this to the OP for future reference.

> ```
uname -a
Linux peter-laptop 2.6.24-24-generic #1 SMP Tue Aug 18 17:04:53 UTC 2009 i686 GNU/Linux

```
best regards,
Peter

Hmm... Seems like it's not actually part of the kernel at all. Google tells me that the wl module is included in ubuntu-restricted-extras, and is supposed to be for the 4315 chipset. It's claiming yours which isn't that chipset anyway though, which is annoying, but easily fixed.

---

### Post by imapostdoc on 2009-09-09
> **jw5801 said:**
> 
If you just remove the module and reload ndiswrapper (what those two commands do, they only output if there's a problem), your wireless should immediately start working, and lshw will report your wireless card being controlled by ndiswrapper. If this is true, then add a line containing 'blacklist wl' to /etc/modules.d/blacklist, by running:

```
echo blacklist wl | sudo tee -a /etc/modprobe.d/blacklist
```

This will prevent the module from being loaded during boot, so you won't have to worry about it.
yes, jw5801, that did it. I've blacklisted wl and I now detect the networks around after reboot. Thank you so much.

---

### Post by bano97 on 2009-12-29
** Before you read this, the problem is solved, read the edit at the bottom, thanks. **  Hi, I'm new to these forums and Ubuntu as well. Unfortunately I cannot connect my laptop to the internet via a wireless connection (Ubuntu 9.10 on a 32 bit system). This is very frustrating because I am tech-savy, but obviously my Windows knowledge is useless here. If I right click on the network icon (not sure what its called), the enable wireless button is greyed out. Left clicking on it reveals my working wired connection, but under the wireless section, "wireless is disabled."

I tried all different solutions from various forum posts - none worked. Eventually I reinstalled Ubuntu and followed this thread, step by step. The only thing I did differently was install ndiswrapper from Synaptic. I received no errors during installation, and my wireless light on my laptop lit up exactly when the guide said it should. It's still lit up now, and after rebooting it remains lit as well.

I have a Dell Inspiron e1705 with a Broadcom 4311 wireless card, the same card as the creator of this thread. I hope I'm just doing something small that is wrong and easily fixable. I have been trying to get connected wirelessly for hours, it's been a nightmare, I hope someone can help, I will be so very thankful! Here's all the output from the commands listed in the guide under the troubleshooting section:

lspci -nn | grep 14e4
```

03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

```[FONT=monospace]ndiswrapper -l[/FONT]
```
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4311) present (alternate driver: ssb)
```[FONT=monospace]ndiswrapper -v[/FONT]
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.31-16-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.31-16-generic SMP mod_unload modversions 586 

```lsmod | grep b43 (RETURNED NO OUTPUT)

lsmod | grep ndiswrapper
```
ndiswrapper           185404  0 

```ls -l /etc/rc.local
```
-rwxr-xr-x 1 root root 421 2009-12-29 01:24 /etc/rc.local

```cat /etc/rc.local
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## Loading ndiswrapper and b44 in correct order
modprobe -r b44
modprobe -r ssb
modprobe ndiswrapper
modprobe b44

exit 0

```lshw -C network
```
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:fc:53:bc:56
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,10/12/2006, 4.100. latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:efcfc000-efcfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:d3:19:04
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.8 latency=64 multicast=yes
       resources: irq:17 memory:ef9fe000-ef9fffff

```


EDIT: Oh wow, I really feel like a newbie now. After a good 4 - 5 hours of getting no where I posted on this thread, and 10 minutes later I found the solution. There was apparently some confusion between the hardware telling me the card was on and the software recognizing the card was on. I had disabled the wifi switch on my computer in the BIOS long ago (I never had a reason to turn WIFI off) so it was always on. After another desperate google search, I decided to enable the switch. Upon booting back into Ubuntu, I pressed the switch a few times and wireless kicked in immediately and connected just fine. That means the driver worked perfectly. Thanks for posting this guide!!

---

### Post by jw5801 on 2009-12-29
> **bano97 said:**
> ...

EDIT: Oh wow, I really feel like a newbie now. After a good 4 - 5 hours of getting no where I posted on this thread, and 10 minutes later I found the solution. There was apparently some confusion between the hardware telling me the card was on and the software recognizing the card was on. I had disabled the wifi switch on my computer in the BIOS long ago (I never had a reason to turn WIFI off) so it was always on. After another desperate google search, I decided to enable the switch. Upon booting back into Ubuntu, I pressed the switch a few times and wireless kicked in immediately and connected just fine. That means the driver worked perfectly. Thanks for posting this guide!!

I've actually had that problem myself! It's rather frustrating, especially when you know that all the outputs are telling you that the card is there and the drivers can talk to it fine but it's just not doing anything.

---

### Post by countingstarsx on 2010-01-19
I've gotten so far as the sudo apt-get install linux-ubuntu-modules-$(uname -r) command, and then it tells me:
 
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package linux-ubuntu-modules-2.6.31-14-generic
 
 
What do I do now?

---

### Post by countingstarsx on 2010-01-19
Well, I just pushed on and apparently that wasn't a problem? My wireless card is working now.

---

### Post by jw5801 on 2010-01-20
> **countingstarsx said:**
> Well, I just pushed on and apparently that wasn't a problem? My wireless card is working now.

Sounds good! I'm not sure what package ndiswrapper comes in these days. It used to be in linux-ubuntu-modules, but it sounds like that package doesn't exist any more. I've switched to Gentoo, so I can't really check. If you can do me a favour and run
```
apt-file search ndiswrapper.ko
```
and post the results, I'll update the how-to if I need to.

---

### Post by zaphabone on 2010-02-11
Ok, so I got the wifi light to come on on my Dell E1505 with this fix.  Now I'm at a point where I can see the other available networks around me, but when I try to connect to my wireless router it doesn't connect.  I'm using a WPA/WPA2 security password, and after I enter the password, the little connecting icon just spins and then it asks me for the authentication again.

I'm using ubuntu 9.10,
BCM4311 802.11b/g [14e4:4311] (rev 01)

Much thanks if someone can point me in the right direction!

---

### Post by jw5801 on 2010-02-11
> **zaphabone said:**
> Ok, so I got the wifi light to come on on my Dell E1505 with this fix.  Now I'm at a point where I can see the other available networks around me, but when I try to connect to my wireless router it doesn't connect.  I'm using a WPA/WPA2 security password, and after I enter the password, the little connecting icon just spins and then it asks me for the authentication again.

I'm using ubuntu 9.10,
BCM4311 802.11b/g [14e4:4311] (rev 01)

Much thanks if someone can point me in the right direction!

Try using another network manager. I (and a lot of other people) have never had much success using nm-applet (the default gnome network manager). I'd recommend wicd!

The other thing to try is (temporarily) removing encryption from your router and connecting that way, then putting encryption back up. I've occasionally had success doing that, it doesn't make any sense, but it works sometimes.

---

### Post by paperdiesel on 2010-06-07
What up JW!  I just logged back in here after a really long time and read through some of our old troubleshooting posts about dell wireless and ndiswrapper.  Brought back memories!  Just wanted to say hi.

Incidentally, since 8.04 or 8.10, it seems that most of the broadcom wireless issues have been resolved natively, so our methods are pretty obsolete :cool:.

---

### Post by dirkyboy on 2010-07-09
I have a Dell inspiron 1526 and am hosed.. I installed ndiswrapper and latest driver from Dell (R173592) for use with my wireless card (chipset is 14e4:4315). I run thru and sudo it, modprobe it and sais it starts. I goto iwconfig and get -
"lo        no wireless extensions.

eth0      no wireless extensions."
My networking manager has the tab greyed out and Network Management Disabled. My GUI for ndiswrapper sais bcmwl5 hardware present: Yes but when I click on Configure Network it sais:
"Could not find Network Configuration Tool."
Typed the command again - 
"mshorts@ubuntu:~$ sudo ndiswrapper -i bcmwl6.inf and get 
driver bcmwl6 is already installed"
 
B43 is blacklisted in my etc/~blacklist.txt. 
Please help as I'm getting very frustrated.. LOVE my new install of linux but DETEST this wireless card driver NIGHTMARE. Email is [email]mikeshorts@sbcglobal.net[/email]

---

### Post by jw5801 on 2010-07-10
> **paperdiesel said:**
> What up JW!  I just logged back in here after a really long time and read through some of our old troubleshooting posts about dell wireless and ndiswrapper.  Brought back memories!  Just wanted to say hi.

Incidentally, since 8.04 or 8.10, it seems that most of the broadcom wireless issues have been resolved natively, so our methods are pretty obsolete :cool:.

G'day paperdiesel! Yeah, I don't think it's really needed so much any more. I can't test thoroughly myself though, since I no longer have the laptop with the relevant card. I'm using Gentoo these days as well, so I'm not often on the Ubuntu forums, I still check back occasionally to see if anything interesting is going on though!

---

### Post by jw5801 on 2010-07-10
> **dirkyboy said:**
> I have a Dell inspiron 1526 and am hosed.. I installed ndiswrapper and latest driver from Dell (R173592) for use with my wireless card (chipset is 14e4:4315). I run thru and sudo it, modprobe it and sais it starts. I goto iwconfig and get -
"lo        no wireless extensions.

eth0      no wireless extensions."
My networking manager has the tab greyed out and Network Management Disabled. My GUI for ndiswrapper sais bcmwl5 hardware present: Yes but when I click on Configure Network it sais:
"Could not find Network Configuration Tool."
Typed the command again - 
"mshorts@ubuntu:~$ sudo ndiswrapper -i bcmwl6.inf and get 
driver bcmwl6 is already installed"
 
B43 is blacklisted in my etc/~blacklist.txt. 
Please help as I'm getting very frustrated.. LOVE my new install of linux but DETEST this wireless card driver NIGHTMARE. Email is [email]mikeshorts@sbcglobal.net[/email]

I can't say for sure, but I don't believe the 4315 chipset ever worked with ndiswrapper. This definitely isn't the thread to be following for it regardless.

I think you might have more luck looking here: [http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by dakota34 on 2010-08-14
just had some success with a dell 1390 broadcom 4311 today, and thought I'd report it here. I installed the b43 drivers using hardware drivers from system>Administration, rebooted, then -- no connection. Wireless light was on, and I could see my network in Network Manger under wireless networks, and it even looked like it was connected in Network Manager (even had the option to disconnect, but the radio-wave image kept moving like it was still in the process of connecting and I had no IP from the router. Tried installing the fwcutter program mentioned a few posts above, with no change. Went back to hardware drivers, and now only STA was listed, not the b43. Removed STA drivers, rebooted, and now it's working. Don't understand why, just thought it might help someone.



John

---

