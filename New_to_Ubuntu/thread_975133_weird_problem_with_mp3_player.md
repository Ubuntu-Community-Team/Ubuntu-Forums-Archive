---
title: "weird problem with mp3 player"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2008-11-08
I have all my music on a seperate hard drive and got samsung mp3 player working on Amarok with the help of this forum. The problem is when I plug in the player it is recognised by Amarok and Rhythmbox (though not by gnome2), but when I plug in the hard drive it disconnects the player so I can't download music onto it. I have to download files onto the computer, disconnect the hard drive (the player then connects) and then download to the player. This works, but does anyone have an idea of what's going on? Also should I expect to see the player on the desktop or in 'places' as an icon when it is recognised? I expected that and wonder if that is related to the problem.
Cheers.

---

### Post by dracayr on 2008-11-08
do you use the MSC or the MTP USB mode? Could it be that the hdd and the player are both trying to mount at the same mount point?

dracayr

---

### Post by Dermot Doyle on 2008-11-08
The mp3 player is an mtp device. I have no idea what the hdd uses. Do you know how I can find out?

---

### Post by dracayr on 2008-11-08
since you use mtp, that doesn't matter anyway. Please execute ```
dmesg|tail -20
``` after you plugged the hdd in (with the player plugged in also). Also, run ```
mtp-detect
``` with both hdd and player plugged in. Post the outputs of both of the commands

dracayr

---

### Post by Dermot Doyle on 2008-11-09
Here it is. As you can see I had to download something after the 'mtp-detect' command

[   33.654581] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.688717] Bluetooth: RFCOMM socket layer initialized
[   33.688740] Bluetooth: RFCOMM TTY layer initialized
[   33.688744] Bluetooth: RFCOMM ver 1.8
[   38.376299] [drm] Initialized drm 1.1.0 20060810
[   38.380877] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   38.380894] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   38.381006] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.804998] eth0: no IPv6 routers present
[   71.345202] CPU0 attaching NULL sched-domain.
[   71.345209] CPU1 attaching NULL sched-domain.
[   71.358101] CPU0 attaching sched-domain:
[   71.358108]  domain 0: span 03
[   71.358110]   groups: 01 02
[   71.358113] CPU1 attaching sched-domain:
[   71.358115]  domain 0: span 03
[   71.358116]   groups: 02 01
[ 2248.660583] usb 7-4: new high speed USB device using ehci_hcd and address 2
[ 2248.792843] usb 7-4: config 1 interface 0 altsetting 0 endpoint 0x83 has an invalid bInterval 0, changing to 9
[ 2248.795101] usb 7-4: configuration #1 chosen from 1 choice
dermot@dell-desktop:~$ mtp-detect
The program 'mtp-detect' is currently not installed.  You can install it by typing:
sudo apt-get install mtp-tools
bash: mtp-detect: command not found
dermot@dell-desktop:~$ sudo apt-get install mtp-tools
[sudo] password for dermot: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  mtp-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.4kB of archives.
After this operation, 209kB of additional disk space will be used.
Get: 1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe mtp-tools 0.2.6.1-2ubuntu1 [35.4kB]
Fetched 35.4kB in 0s (81.0kB/s)
Selecting previously deselected package mtp-tools.
(Reading database ... 201295 files and directories currently installed.)
Unpacking mtp-tools (from .../mtp-tools_0.2.6.1-2ubuntu1_i386.deb) ...
Setting up mtp-tools (0.2.6.1-2ubuntu1) ...
dermot@dell-desktop:~$ mtp-detect
libmtp version: 0.2.6.1

Attempting to connect device(s)
PTP: Opening session
PTP_ERROR_IO: Trying again after re-initializing USB interface
inep: usb_get_endpoint_status(): Protocol error
outep: usb_get_endpoint_status(): Protocol error
usb_clear_halt() on IN endpoint: Protocol error
usb_clear_halt() on OUT endpoint: Protocol error
usb_clear_halt() on INTERRUPT endpoint: Protocol error
usb_claim_interface(): No such device
LIBMTP PANIC: Could not open session on device 1
LIBMTP PANIC: configure_usb_devices() error code: 7 on line 1599
Detect: There has been an error connecting. Exiting

Cheers

---

### Post by dracayr on 2008-11-09
I guess running mtp-detect with *sudo* outputs you the same error?

you use libmtp version 0.2.2.6.1, but the latest version is 0.3.3 (at least thats what the website says, strangely the package name is libmtp-0.3.1.
You'll have to install it from source though:```
wget http://mesh.dl.sourceforge.net/sourceforge/libmtp/libmtp-0.3.1.tar.gz
tar xvf libmtp-0.3.1.tar.gz
cd libmtp-0.3.1
./configure
make
sudo make install
```

then try again to run mtp-detect

dracayr

---

### Post by Dermot Doyle on 2008-11-09
Thanks for the help so far.

Using 'sudo mtp-detect' it just said that nothing was detected. I used your command and it finished as:

dermot@dell-desktop:~/libmtp-0.3.1$ 

I put in 'mtp-detect' and it said no such file or directory. I closed the terminal and reopened it, put in mtp-detect and got:

mtp-detect: error while loading shared libraries: libmtp.so.8: cannot open shared object file: No such file or directory

Any ideas?

---

### Post by dracayr on 2008-11-09
> **Dermot Doyle said:**
> Thanks for the help so far.

Using 'sudo mtp-detect' it just said that nothing was detected. I used your command and it finished as:

dermot@dell-desktop:~/libmtp-0.3.1$ 

I put in 'mtp-detect' and it said no such file or directory. I closed the terminal and reopened it, put in mtp-detect and got:

mtp-detect: error while loading shared libraries: libmtp.so.8: cannot open shared object file: No such file or directory

Any ideas?

create the file /etc/udev/rules.d/libmtp.rules (with sudo gedit, sudo vim, sudo echo, or however you want) with these contents: ```
SUBSYSTEM!="usb_device", ACTION!="add", GOTO="libmtp_rules_end"

# Creative Zen VisionSpecial:Recentchanges
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="411f", SYMLINK+="libmtp-%k", MODE="666"
# Creative Portable Media Center
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4123", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen Xtra (MTP mode)
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4128", SYMLINK+="libmtp-%k", MODE="666"
# Second generation Dell DJ
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="412f", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen Micro (MTP mode)
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4130", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen Touch (MTP mode)
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4131", SYMLINK+="libmtp-%k", MODE="666"
# Dell Pocket DJ (MTP mode)
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4132", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen Sleek (MTP mode)
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4137", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen MicroPhoto
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413c", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen Sleek Photo
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413d", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen Vision:M
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="413e", SYMLINK+="libmtp-%k", MODE="666"
# Creative Zen V Plus
SYSFS{idVendor}=="041e", SYSFS{idProduct}=="4152", SYMLINK+="libmtp-%k", MODE="666"
# Samsung:YH-820
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="502e", SYMLINK+="libmtp-%k", MODE="666"
# Samsung YH-925
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="502f", SYMLINK+="libmtp-%k", MODE="666"
# Samsung YP-T7J
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5047", SYMLINK+="libmtp-%k", MODE="666"
# Samsung YH-999 Portable Media Center
SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="5a0f", SYMLINK+="libmtp-%k", MODE="666"
# Intel Bandon Portable Media Center
SYSFS{idVendor}=="045e", SYSFS{idProduct}=="00c9", SYMLINK+="libmtp-%k", MODE="666"
# iRiver Portable Media Center
SYSFS{idVendor}=="1006", SYSFS{idProduct}=="4002", SYMLINK+="libmtp-%k", MODE="666"
# iRiver Portable Media Center
SYSFS{idVendor}=="1006", SYSFS{idProduct}=="4003", SYMLINK+="libmtp-%k", MODE="666"
# JVC Alneo XA-HD500
SYSFS{idVendor}=="04f1", SYSFS{idProduct}=="6105", SYMLINK+="libmtp-%k", MODE="666"
# Philipps HDD6320
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="01eb", SYMLINK+="libmtp-%k", MODE="666"
# Philipps HDD6320 2
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="014b", SYMLINK+="libmtp-%k", MODE="666"
# Philipps HDD1630/17
SYSFS{idVendor}=="0471", SYSFS{idProduct}=="014c", SYMLINK+="libmtp-%k", MODE="666"
# SanDisk Sansa c150
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7410", SYMLINK+="libmtp-%k", MODE="666"
# SanDisk Sansa e200
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7420", SYMLINK+="libmtp-%k", MODE="666"
# SanDisk Sansa e260
SYSFS{idVendor}=="0781", SYSFS{idProduct}=="7420", SYMLINK+="libmtp-%k", MODE="666"
# iRiver T10
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1113", SYMLINK+="libmtp-%k", MODE="666"
# iRiver T20 FM
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1114", SYMLINK+="libmtp-%k", MODE="666"
# iRiver U10
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1116", SYMLINK+="libmtp-%k", MODE="666"
# iRiver T10
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1117", SYMLINK+="libmtp-%k", MODE="666"
# iRiver T20
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1118", SYMLINK+="libmtp-%k", MODE="666"
# iRiver T30
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="1119", SYMLINK+="libmtp-%k", MODE="666"
# iRiver H10
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="2101", SYMLINK+="libmtp-%k", MODE="666"
# iRiver H10
SYSFS{idVendor}=="4102", SYSFS{idProduct}=="2102", SYMLINK+="libmtp-%k", MODE="666"
# Dell DJ Itty
SYSFS{idVendor}=="413c", SYSFS{idProduct}=="4500", SYMLINK+="libmtp-%k", MODE="666"
# Toshiba Gigabeat MEGF-40
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="0009", SYMLINK+="libmtp-%k", MODE="666"
# Toshiba Gigabeat
SYSFS{idVendor}=="0930", SYSFS{idProduct}=="000c", SYMLINK+="libmtp-%k", MODE="666"

LABEL="libmtp_rules_end"
```

apparently, libmtp didn't install correctly. We'll try to install it manually:```
sudo cp -f ~/libmtp-0.3.1/src/.libs/libmtp.so* /usr/lib/
```


dracayr

---

### Post by Dermot Doyle on 2008-11-09
Started doing as you said, when I tried to save the document it asked if I wanted to overwrite an existing one of the same name. Do I? If so I'll do it and go onto the next command.
Thanks

---

### Post by dracayr on 2008-11-09
Well if the document already exists, it's probably already configured and you shouldn't overwrite it.

dracayr

---

### Post by Dermot Doyle on 2008-11-09
Right. Sorry to take up your time, but I,ve done something pretty dim. I misread your instructions and overwrote the document. Now when I plug in the mp3 player, Rhythmbox flickers open and then immediately closes and Amarok opens, I go to devices and press connect and a small dialogue box comes up:

could not launch mail client
KDElnit could not launch 'kmail'
could not find 'kmail' executable

I found the document in case I could do something as simple as 'undo' to restore it, but I couldn't. Do I need to uninstall and reinstall something to get back to where I was?

---

### Post by dracayr on 2008-11-11
did you follow the 2nd part of my post, after you overwrote the file? If not, do so now.

dracayr

---

### Post by Dermot Doyle on 2008-11-11
When I put in:

Code:

sudo cp -f ~/libmtp-0.3.1/src/.libs/libmtp.so* /usr/lib/

nothing happens, I just get straight back to the opening command line. I don't have the mp3 player with me this evening so I can't try it or try 'mtp-detect'. I'll bring it home tomorrow and see what happens.
Cheers.

---

### Post by Dermot Doyle on 2008-11-12
I,ve plugged in the mp3 player and it is exactly as my post before trying again your second command suggestion. With the external hd plugged in it is not recognised at all. When I turn it off the player connects. 'mtp-detect finds it and pours out a mass of information. Amarock can't find it and puts up the dialogue box:

could not launch mail client
KDElnit could not launch 'kmail'
could not find 'kmail' executable

then shuts down and both Rhythmbox and Gnomad2 flicker open and then disappear.

Any ideas? Is it possible to uninstall and then reinstall libmtp? I have to admit I don't even really know what that is or what it does.

---

### Post by Dermot Doyle on 2008-11-14
bump!

---

### Post by Dermot Doyle on 2008-11-16
bump again!!! If I can't get a reply I'll have to start a new thread.

---

