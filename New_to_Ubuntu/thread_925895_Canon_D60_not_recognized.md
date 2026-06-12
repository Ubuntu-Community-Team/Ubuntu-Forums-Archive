---
title: "Canon D60 not recognized"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by waste301 on 2008-09-21
Hi, I'm on Hardy Heron and when I plug my Canon EOS D60 in using my USB cable, it is recognized but I get an error message "Could not claim the USB device."  It is not showing up as a drive that needs to be mounted, or anything like that.

My forum search turned up some advice but I am afraid it was a little too technical.  If anyone can help me get ubuntu to recognize my camera and import import these photos I would be eternally grateful, and post some pictures of spelunking in Laurel Caverns and some neat shots made hiking through the Appalachians :)

---

### Post by waste301 on 2008-09-21
bump

---

### Post by phidia on 2008-09-21
With the camera plugged in what does "lspci" entered in a terminal output?
Most cameras are plug&play in Ubuntu. Do other usb devices mount in your install?

---

### Post by waspbr on 2008-09-21
ins't the code lsusb instead of lspci?

---

### Post by oldsoundguy on 2008-09-21
I ceased plugging still cameras into any computer a long time ago.  I spent under 20 bucks and use a USB universal card reader.  Installed in Ubuntu right out of the box.  Saves wear and tear on the camera and cable and connections and it also saves batteries.

A quick forum search indicates that there are issues with Nikon cameras and the drivers for same.  Another reason for the card reader.

---

### Post by phidia on 2008-09-21
Yeah, sorry, I should have said enter > lsusb you could also give the output of > mount.

---

### Post by twisted_steel on 2008-09-21
> **oldsoundguy said:**
> I ceased plugging still cameras into any computer a long time ago.  I spent under 20 bucks and use a USB universal card reader.  Installed in Ubuntu right out of the box.  Saves wear and tear on the camera and cable and connections and it also saves batteries.

A quick forum search indicates that there are issues with Nikon cameras and the drivers for same.  Another reason for the card reader.

I used a SanDisk CF reader for my Canon Rebel XT rather than just plugging in the camera.  This is the model:

[http://www.amazon.com/Sandisk-SDDR-99-ImageMate-Reader-Package/dp/B00064V6SK/](http://www.amazon.com/Sandisk-SDDR-99-ImageMate-Reader-Package/dp/B00064V6SK/)

It's worked for a few years through the different versions of Ubuntu.

---

### Post by waste301 on 2008-09-21
> **phidia said:**
> With the camera plugged in what does "lspci" entered in a terminal output?
Most cameras are plug&play in Ubuntu. Do other usb devices mount in your install?

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)


That is what it says.  If there is any way to plug in my camera and have it read as a USB flashdrive that would be perfect.  I'd take my pics and save them, then edit them for contrast and publish.

---

### Post by waste301 on 2008-09-21
> **phidia said:**
> Yeah, sorry, I should have said enter  you could also give the output of .

Mount =

/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/storage type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda3 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda2 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by phidia on 2008-09-21
Are you selecting the file transfer mode when you plug your camera in and turn it on?
It really seems like that camera should automount.

Added:
You could make a mount point, for example: "sudo mkdir /mnt/canond60" then if sdb1 is the camera's storage device 
you would enter: "sudo mount /dev/sdb1 /mnt/canonsd60" and if the filesystem is recognized it should mount.

---

### Post by FrankVdb on 2008-09-22
Why make yourself life so difficult? Card readers are dirt-cheap these days.

I bought my D60 in April 2002 and have never connected it to my PC.

---

