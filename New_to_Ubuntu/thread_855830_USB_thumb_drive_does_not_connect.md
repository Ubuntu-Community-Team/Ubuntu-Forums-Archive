---
title: "USB thumb drive does not connect"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by happyisland on 2008-07-10
I am at my wits end about this one.

I have a new iriver lplayer music player. In apple and xandros it connects and works fine. For the first few days I had it it worked on my home pc too (ubuntu). Now when I plug it in here nothing happens. No errors, nothing.

Please someone help me figure out how to get this thing to work. 

PS: USB is working for other devices - mouse, camera...

---

### Post by cosine352 on 2008-07-10
try this
> fdisk -l

you will get the device name (for example sda1)

then type
> mkdir /mnt/harddrive
mount -t vfat /dev/sda1 /mnt/harddrive

then 
> sudo gnome-open /mnt/harddrive

---

### Post by ChameleonDave on 2008-07-10
Plug it in, then go to a terminal and enter these commands.  Post their output here.

```

sudo blkid
cat /etc/fstab

```

---

### Post by happyisland on 2008-07-10
Thanks for the quick reply!

Nothing happens when I do fdisk -l in though. Weird. 

Anyway, shouldn't the usb drive just mount automatically the way it does on my eeepc which uses xandros?

---

### Post by happyisland on 2008-07-10
the output of sudo blkid:

/dev/sda1: UUID="dae8be2e-a454-4781-ba04-a4d6b591be25" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="e8e71b1a-a20f-429e-ae90-538c744c01ba" 
/dev/sdb1: UUID="02935972-1f1f-4c8b-892a-2a0571995ee3" TYPE="ext3" 
/dev/sde: LABEL="LPLAYER" UUID="0000-0000" TYPE="vfat" 


cat /etc/fstab yields:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=dae8be2e-a454-4781-ba04-a4d6b591be25 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e8e71b1a-a20f-429e-ae90-538c744c01ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#for extra internal sata disk
/dev/sdb1	/media/scsidisk-1  ext3	defaults	0	0

---

### Post by happyisland on 2008-07-10
ok, thanks to the two helpful posters above I was able to get my player connected. Many thanks! Now I won't have to drive to work with no music in my car...


I still don't understand why I have to manually mount the player though where before it used to *just work*. Weird.

---

### Post by hurricanesfan66 on 2008-07-10
Same problem here with an iRiver e100.  Mounted fine on my Mac, it 'appears' with lsusb and I see it grayed out on VirtualBox.  Tried these tips, to no avail.

Here is lsusb:

Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 014: ID 4102:1141 iRiver, Ltd. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 413c:a005 Dell Computer Corp. 
Bus 001 Device 001: ID 0000:0000  

Here is sudo blkid:

/dev/sda1: UUID="61b53096-208c-427f-8c3b-a23a24999a55" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="1eb9fe78-240f-4336-93f7-685d7d7fdbd1" 

Here is cat /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=61b53096-208c-427f-8c3b-a23a24999a55 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1eb9fe78-240f-4336-93f7-685d7d7fdbd1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=1001, devmode=664 0 0

---

### Post by ChameleonDave on 2008-07-10
> **happyisland said:**
> Thanks for the quick reply!

Nothing happens when I do fdisk -l in though. Weird. 

Anyway, shouldn't the usb drive just mount automatically the way it does on my eeepc which uses xandros?

The other poster forgot to mention that you have to run that command as the superuser, i.e. "sudo fdisk -l".

Yes, it should automount.  My media automount just fine.  It's some software called "HAL" which handles the automounting.  It must be malfunctioning for you.  I don't know why.  If you add an fstab entry for the device, it may help HAL to find it.  It will certainly make it simpler to mount it from the command line.

A line somewhat like this should be added to /etc/fstab:

```

LABEL="LPLAYER"  /media/lplayer  vfat  defaults,rw,user,umask=0000  0  0

```

Create the mount point:

```

sudo mkdir /media/lplayer
mount /media/lplayer

```

---

### Post by ChameleonDave on 2008-07-10
> **hurricanesfan66 said:**
> Same problem here with an iRiver e100.  Mounted fine on my Mac, it 'appears' with lsusb and I see it grayed out on VirtualBox.  Tried these tips, to no avail.
The following commands might gather more information:

```

sudo lshw -sanitize -C disk
sudo fdisk -l

```

---

### Post by hurricanesfan66 on 2008-07-11
> **ChameleonDave said:**
> The following commands might gather more information:

```

sudo lshw -sanitize -C disk
sudo fdisk -l

```

first line:

  *-disk                  
       description: ATA Disk
       product: SAMSUNG HM080II
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: YE10
       serial: [REMOVED]
       size: 73GiB (78GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=e686f016
  *-cdrom
       description: DVD writer
       product: DVD+-RW DW-Q58A
       vendor: SONY
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: UDS2
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=open

2nd line:

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9172    73674058+  83  Linux
/dev/sda2            9173        9546     3004155    5  Extended
/dev/sda5            9173        9546     3004123+  82  Linux swap / Solaris

---

### Post by ChameleonDave on 2008-07-11
Hurricanesfan66,

Ubuntu is recognising that a USB device is attached, but is not recognising it as a standard Mass Storage Device.

[The Wikipedia article on your player]("http://en.wikipedia.org/wiki/Iriver_e100") leads me to believe that your player has two modes: Mass Storage and [Media Transfer Protocol]("http://en.wikipedia.org/wiki/Media_Transfer_Protocol#GNU.2FLinux_MTP_support").  Perhaps it is not working because it is trying to connect in the wrong way, and you need to press a button to make it communicate with the PC differently.

Maybe the following software could help to mount it with MTP:

```

sudo apt-get install **mtpfs mtp-tools**
```

---

