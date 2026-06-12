---
title: "HOWTO: UDEV/SCSI Scanner Configuration"
date: 2005-01-18
forum: Outdated Tutorials &amp; Tips
---

### Post by gbusse on 2005-01-18
I really hope this information will help others as it was a real head scratcher for me. I have an HP Scanjet 6100C SCSI scanner attached to an Adaptec AHA-7850 based PCI SCSI card. I have never had much luck getting my scanner to work under Linux without having to change permissions on some device file which always seemed kind of wrong to me. I never believed that I should have to do that manually. I have spent hours reading posts on this forum with all of them basically saying to change the permissions on the device. Well I figured, especially with UDEV that there had to be a better way. And with a little bit of basic UDEV help from [here](http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html)  I have found that way. Complete the instructions below and hopefully you too will soon be happily scanning in Ubuntu with your SCSI scanner...  :D 

First, load the SCSI Generic (sg) module.
```
gordo@neo:~ $ sudo modprobe sg
```
Next, add sg to the bottom of /etc/modules.
```
gordo@neo:~ $ sudo gedit /etc/modules
``````
# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

psmouse
mousedev
ide-cd
ide-disk
ide-generic
lp
sg
```
Next, install the sane-utils package.
```
gordo@neo:~ $ sudo apt-get install sane-utils
```
Next, run sane-find-scanner to detect your scanner device.
```
gordo@neo:~ $ sudo sane-find-scanner

found SCSI processor "HP C2520A 3644" at /dev/sg0
  # Your SCSI scanner was detected. It may or may not be supported by SANE. Try
  # scanimage -L and read the backend's manpage.

found USB scanner (vendor=0x05a9, product=0xa511) at libusb:003:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program
```
Next, run udevinfo as follows to find out the exact model name of your scanner substituting your scanners device for sg0.
```
udevinfo -a -p /sys/class/scsi_generic/sg0
```
Look for the line starting with "SYSFS{model}" as illustrated below then write down the exact model name ignoring any trailing spaces. For example the model name of my scanner is exactly "C2520A" minus the quotes.
```
follow the class device's "device"
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:1e.0/0000:02:03.0/host0/0:0:1:0':
    BUS="scsi"
    ID="0:0:1:0"
    SYSFS{detach_state}="0"
    SYSFS{device_blocked}="0"
    **SYSFS{model}="C2520A          "**
    SYSFS{queue_depth}="2"
    SYSFS{rev}="3644"
    SYSFS{scsi_level}="3"
    SYSFS{state}="running"
    SYSFS{timeout}="0"
    SYSFS{type}="3"
    SYSFS{vendor}="HP      "
```
Next, run the following to backup your current udev.rules file.
```
sudo cp /etc/udev/udev.rules /etc/udev/udev.rules.backup
```
Next, run the following to edit the udev.rules file.
```
sudo gedit /etc/udev/udev.rules
```
And below these two lines.
```
# permissions for SCSI sg devices
BUS="scsi", KERNEL="s[grt][0-9]*", SYSFS_type="5", NAME="%k", MODE="0660", GROUP="cdrom"

```
Add these two new lines substituting the exact model name of your scanner for C2520A. The SYMLINK="scanner" portion is optional. It is only needed if you actually want to have a /dev/scanner symlink that will always point to your actual scanner device.
```
# permissions for SCSI scanner
BUS="scsi", SYSFS{model}="C2520A", NAME="%k", SYMLINK="scanner", MODE="0660", GROUP="scanner"
```

Now make sure your user is a member of the scanner group, reboot then run XSane. Your SCSI scanner should hopefully be detected and working properly as a regular user. 

But, just because this procedure works perfectly fine for me doesn't mean it will for you. Hopefully it will work for you. I am interested in hearing back from people about thier experiences. Also any constructive comments about this HOWTO are welcome and appreciated.

Gordo

---

### Post by AndyGates on 2005-03-01
Great article and very clear.

But... the ScanJet 5P was also supplied with a Symbios SYM20403 card - a wacky triangular ISA card.  You don't know where drivers for that one are available, by any chance?  (The ones at driverguide.com don't untar)

---

### Post by kstamper on 2005-03-05
Excellent article.  I just used it to install my HP ScanJet 4c with an AHA-7850, and everything worked perfectly.

A suggestion to speed up the install process: instead of rebooting, you can use

```
sudo modprobe -r sg
sudo modprobe sg

```

That will reload the SCSI module quickly.

---

### Post by trash on 2005-03-05
Excellent, i had given up on my old astra1220s after trying to get it working(non root).

I'll give it a try soon.

Thanks!

---

### Post by bpaultre on 2005-06-11
Just my own experience with my Epson Expression800, to avoid 
the reboot and not have to be root I had to manually change the 
group on /dev/sg0 to scanner.

Thanks for the writeup I can't say how great the ubuntu community 
has been.

-Ben :smile:

---

### Post by epedersen on 2005-08-21
This is fantastic!  I've spent hours trying to find the correct place to edit device permisions, and here it is.

Thanks for the wonderful step-by-step guide - it works on Hoary Hedgehog as well!

Regards,

Eric

---

### Post by groovywombat on 2005-11-29
Awesome!  now my scanjet 4c works
thanks

---

### Post by abeverley on 2005-12-22
Works great with my Umax Astra scanner, but I can't get my Minolta F-2800 SCSI slide scanner to work. I'm guessing it's not supported by Sane - anyone have any ideas to get it working?

Andy

---

### Post by mikelietz on 2006-01-14
Worked for me and my 6100C also! I've got an AHA-2109B, I believe.

---

### Post by ivolinux on 2006-04-29
You are a genius scanjet 4p (C5110A) work very well!
I'll writhe a wiki for ubuntu italian comunity ;) 
thank I serched a lot without result :D

---

### Post by lsiden on 2006-06-25
UDev creates a device node for my SCSI scanner (UMAX Vista) called /dev/sg0 as long as my scanner is on when Linux boots.  But I can't for the life of me get it to recognize the scanner and create a dev node if I turn the scanner on after Linux has booted.   I've tried "/etc/init.d/udev restart".  Also, I've made sure that module sg is loaded.  Is there a trick?

---

### Post by zeroconf on 2006-08-25
I have Kubuntu 6.06 and this HP ScanJet 5p does not work. I posted also this into Kubuntu forum - [http://kubuntuforums.net/forums/index.php?topic=8244.0](http://kubuntuforums.net/forums/index.php?topic=8244.0)

udev has changed and so this howto does not work at 6.06 version of Ubuntu :(

If somebody does have any ideas....

---

### Post by Yorgos Kourtakis on 2006-11-05
> **gbusse said:**
> 
Next, run the following to edit the udev.rules file.
Gordo

My OS is Ubuntu 6.10 and I'm not able to find udev.rules file!

---

### Post by marvinthesad on 2006-11-09
In ubuntu 6.10 udev seems to be located at 

/etc/udev/rules.d/*

permission rules seem to be in all files that start with one from the 40ies, like 40-permissions.rules, or 45-libsane.rules

cheers, marvin

---

### Post by nagrath on 2008-04-30
> **marvinthesad said:**
> In ubuntu 6.10 udev seems to be located at 

/etc/udev/rules.d/*

permission rules seem to be in all files that start with one from the 40ies, like 40-permissions.rules, or 45-libsane.rules

cheers, marvin
I need some "Hardy Heron" help. I'm new to Ubuntu but am very impressed by it. Trying to get a microtek scanner working and have gotten to the udev rules section. (40-permissions.rules) however things there do not look much like what is described above. Does anyone know how to properly edit the udev rules in 8.04? Many thanks in advance. This tutorial is the best thing I have found yet regarding setting up a scanner but it doesn't quite get me there yet!

John, Ubuntu/Linux newbie, running 8.04

---

### Post by bdalzell on 2008-05-10
When I was using Edgie my scanner spontaneously decided to work. However when I upgraded to Hardy I had the computer freez up in the middle of the ugrade and I ended up having to install Hardy into my / partition as a new install (I still had /home in a different partition).  Of course then the scanner (an SCSI Epson Perfection 636 did not work. Thanks to the post at the beginning of this thread it now works! I did have to reboot and I also had to create the file /etc/udev/udev.rules it did not seem to exist in my Hardy installation.

---

