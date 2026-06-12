---
title: "unable to burn"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Doorslammer on 2008-07-24
if  insert a blank CD-R, It does not mount or start the CD-burn application.
but if in insert a music cd or data cd it will mount & read it  

I know the hardware works , it worked under windows & also ubuntu 7.10 
but after upgrade it has not worked I&#7743; running 8.04

---

### Post by RomeReactor on 2008-07-24
Hi. When you say the CD doesn't mount do you mean you don't get an icon on the desktop? Maybe it's a problem with fstab; post the output of this:
```
cat /etc/fstab
```

It could also just be hardware failure; I've had DVD drives that refused to load blank CDs, but could read data or audio CDs perfectly. How long have you had the drive?

---

### Post by Dylock on 2008-07-24
You cant mount a blank cd.

---

### Post by jidol on 2008-07-24
Hi there,

I also had a problem some months before.I tried all sort of things to solve this problem but i fail.At lastly I have to call my vendor.He suggest me to change the CD ROM.Now I get rid off this problem.So I suggest you the same.Hope my suggestion help you out.

---

### Post by Doorslammer on 2008-07-24
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=ac643651-38da-4459-849f-472b83fab5d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda9
UUID=209336f4-1acd-492d-85ae-89af3d8859ec none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda5 /media/hda5 vfat auto,user,uid=1000,gid=100,umask=007 0 0
/dev/sda6 /media/hda6 vfat auto,user,uid=1000,gid=100,umask=007 0 0
/dev/sda7 /media/hda7 vfat auto,user,uid=1000,gid=100,umask=007 0 0
/dev/sda8 /media/hda8 vfat auto,user,uid=1000,gid=100,umask=007 0 0

```


ok maybe I was not clear  as it was late last night when I posted 
if I insert a blanks cdr in to my cdr writer  it does nothing 
it does not open cd crator  ! if I right click on a file to write to cd  it will keep asking me for  blank media  ( there is already a blank in there,  I changed blanks cd&#347;  still nothing )
ok you others  I used the wrong  words , all I&#7743; trying to do is be able to use my cd burner 
 no need to change hardware 
like I said it worked under windows & also gusty

btw the file I&#7743; trying to burn is an iso of 8.04.1  so I can update this beast

---

### Post by editrix on 2008-07-26
Hardy has all kinds of problems burning CDs. I've been searching for weeks for a solution but have yet to find one. You could try [www.uboontu.com](www.uboontu.com) and search for error messages or just "burn CD"--maybe you'll have better luck.

In the meantime, you don't need to burn an iso to update to 8.04.1. Just update via synaptic or apt--not sure exactly what you update: the kernel, I think--and you'll end up with 8.04.1. But it won't solve the cd burning problems :-(

---

### Post by Doorslammer on 2008-07-26
it's a good thing I still have  gusty as my main  computer 
this 8.04 seems like a rush job  & it's been nothing but problems .
should still be beta  LOL 
I'll keep gusty  my kubuntu install of gusty 7.10 is Rock solid

I have been reading that you can install k3b  burning app  
maybe I'll try that

---

### Post by mc4man on 2008-07-26
You may want to ck. this for duplicate entries of your cd/dvd drives (an ide entry and a scsi entry)
Do it from a maximized terminal or it will be hard to read
```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by sailor2001 on 2008-07-26
I've had problems with different burners.... k3b has been very consistent for me.

---

### Post by Doorslammer on 2008-09-14
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# HITACHI_DVD-ROM_GD-5000 (pci-0000:00:04.1-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# PLEXTOR_CD-R_PX-W2410A (pci-0000:00:04.1-ide-1:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:1", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:1", SYMLINK+="cdrw1", ENV{GENERATED}="1"
# CD-R_PX-W2410A (pci-0000:00:04.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:1:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:1:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
# DVD-ROM_GD-5000 (pci-0000:00:04.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="dvd3", ENV{GENERATED}="1"

```
it&#347; been a little while since I fired up  this computer  but here is whats listed 
I spend my time on my other ubuntu box with 7.10 on it ;) as this 8.04 has nothing to offer me yet 
I&#314;l keep working on it

---

### Post by Doorslammer on 2008-09-14
well I just tried bresero & it did burn the cd 
only got an error at the end about not being able to eject the cd 
but the cd did burn & all files are good

---

### Post by twa1296 on 2008-09-15
I've just had the same problem as the OP. Neither the CD/DVD Creator nor Brasero recognized the empty media in my (external) burner. Installed k3b and it worked without any problems.

---

