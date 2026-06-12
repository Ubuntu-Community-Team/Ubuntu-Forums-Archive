---
title: "[SOLVED] my mp3 player is not mounting"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by rahul_bhise on 2008-08-10
first my mp3 player was mounting all right but since yesterday is is not mounting after connecting it to a usb . but it is charging from the usb connection

---

### Post by fedex1993 on 2008-08-10
What kind of mp3 player do you have. Also you can force mount it. My mp3 player usually does not like to be mounted to i have to force it.

---

### Post by rahul_bhise on 2008-08-11
it is just some china made mp3 player called "emotion" it says it has samsung chip.  it work allright in xp and also in ubuntu for a week or so.
how to force mount it

---

### Post by finer recliner on 2008-08-11
does XP still recognize it, or do both operating systems have a problem with it?

---

### Post by rahul_bhise on 2008-08-11
yes both operating systems are having the same problem. but the mp3 is working fine

---

### Post by hessiess on 2008-08-11
> **rahul_bhise said:**
> it is just some china made mp3 player called "emotion" it says it has samsung chip.  it work allright in xp and also in ubuntu for a week or so.
how to force mount it
assuming you are using gnome, dose it show up in the places menu? if so clicking on it should mount it for you.

you can also mount a drive using the mount command

make a directory to mount to

```
sudo mkdir /media/mp3
```

then mount the device to that directory

```
sudo mount -t vfat /dev/sdb1 /media/mp3
```

assuming that your device is /dev/sdb1 and it has a fat32 file system

howeaver if it dosent work in windows or linux its eather dead or the file system is corrupted.

---

### Post by rockerphil on 2008-08-11
ok, first let's find out the drive label of the mp3 player when it's connected. so hook up the mp3 player through your USB port, then open up a terminal and run this:

sudo fdisk -l (l is a lower case L)

that'll list your partition table. if you've only got one HDD it should show up as /dev/sdb1. if i were to connect it to my system it would show up as /dev/sdc1 since i've got 2 internal hard drives. once you've got the drive label i'd create a mount point inside your home folder for the mp3 player to mount to, so again, in the terminal run this:

mkdir mp3

that will create a folder inside your home folder named mp3. once that's done you can simply mount the mp3 player to the mount point with this

sudo mount /dev/sdb1 ~/mp3

be sure to replace /dev/sdb1 with the actual drive label of the mp3, but that should do the trick, hope this helps,

Phil

---

### Post by finer recliner on 2008-08-11
plug the device into the computer (while booted in ubuntu)

type this command:
```
lsusb
```

and post the output

---

### Post by rahul_bhise on 2008-08-11
> **hessiess said:**
> howeaver if it dosent work in windows or linux its eather dead or the file system is corrupted.
yes in windows it dosent work at all but in ubuntu it works sometime and it dosent sometime. i have some screen shot about its mount point. is there some error

---

### Post by rahul_bhise on 2008-08-13
```
brahul@uhome:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
```

---

### Post by rahul_bhise on 2008-11-05
sorry for the late update i found out that my usb connector of the mp3 player was broken after soldering it, it worked fine.

---

