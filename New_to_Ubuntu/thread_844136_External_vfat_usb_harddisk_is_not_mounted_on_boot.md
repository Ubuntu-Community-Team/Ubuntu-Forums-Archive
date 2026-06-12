---
title: "External vfat usb harddisk is not mounted on boot"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by th00ht on 2008-06-29
output of fdisk -l
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6271337b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001    c  W95 FAT32 (LBA)

```

output of 
sudo mkdir /media/TREKSTOR
sudo mount /dev/sda1 /media/TREKSTOR
<none> disk is mounted without problem

So the disk is ok it mounts ok it just not mounts when I switch on the machine. And it mounts fine when I log on to the GNOME desktop, but I need to have it available always.

How do I make the external usb vfat formatted disk available after boot without logging on to the machine (just like microsoft WinXP)?

---

### Post by vanadium on 2008-06-29
For this to happen, you will need to mount it the "traditional" way, i.e. by including it in /etc/fstab. For an external disk, this is not a very good idea, though, except if you are sure it is always available at boot time (for example, a large external disk connected to a desktop system).

The how-to from psychocats ([http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)) is still relevant for what you want to do. Finally, your line will look like

> 
/dev/sda1 /media/TREKSTOR vfat iocharset=utf8,umask=000 0 0


Some comments you might want to consider

1) On modern systems, device names are not necessarily constant between boots. e.g. if an USB stick is connected at boot time, it might get the /dev/sda1 designation instead of your fat drive. To avoid this "confusion", I advise you to use the disk label or the UUID instead of the device name.

To see UUID and label of your drive, run

```

sudo blkid

```

Copy either the "UUID=" or "LABEL=" part of the line for your drive and substitute that for the device name in your /etc/fstab.  e.g. the above line could then become:

```

LABEL="TREKSTOR" /media/TREKSTOR vfat iocharset=utf8,umask=000 0 0

```

2) If you do not want to see an icon for the drive on your desktop, then mount it under /mnt/ insted of under /media. Thus, you would create a mount point under /mnt and change the line in fstab accordingly:

```

sudo mkdir /mnt/TREKSTOR

```

and in /etc/fstab:

```

LABEL="TREKSTOR" /mnt/TREKSTOR vfat iocharset=utf8,umask=000 0 0

```

---

### Post by th00ht on 2008-06-29
Thanks vanadium,
So if I understand you correctly there is no way to mount the external harddisk when it is switch on or connected. 

I was able to circumvent the "random"  assignment of scsi volume s by creating a 10-local.rules entry. This way I always know under which device name it will be available.

But your trick is more elegant (until I have another "TREKSTOR" drive obviousle :-)

Currently my fstab contains:
```
/dev/usbhdd1                                    /usb0           vfat            auto,async,rw,nosuid,nodev,umask=000,uid=1000
   0       0
```

as the /etc/udev/rules.d/10-local.rules contains:
```

BUS=="usb", KERNEL=="sd?1", SYSFS{manufacturer}=="Trekstor", NAME="%k", SYMLINK+="usbhdd1"

```

Yet the drive is not available at boot. I have to type manually the mount commando to make it available.

---

### Post by th00ht on 2008-07-01
Actually I have an understanding problem with the fstab file. In the option field one can enter auto or noauto. With noauto the volume will not be mounted at boot but the auto options claims to mount the device at boot.

the line 
```
LABEL=TREKSTOR                                  /usb0           vfat            auto,async,rw,nosuid,nodev,umask=000,uid=1000   0       0
```

the device is mounted perfectly when I enter 
```
sudo mount -a
```

What puzzles me is why the device is not mounted automatically. What else do i have to specify where to have the volume mounted at boot time? 

Apparently (dis)connecting external usb disks are not fully supported by debian or ubuntu as there are so many feeble attempts to mount external usb devices. pmount+hal, usbmount, udev rules etc. This all seems kind of messy to me. If one asks the question of how optimally connect an external usb harddisk to three different experts one is likely to get three different answers.

---

### Post by Victormd on 2008-07-01
In fact, you shouldn't need to add anything to fstab. I have an external drive that mounts automatically and I've never had any problems with it (it's formatted as ntfs though). Most of the problems I've seen with external drives are when they're formatted as fat/fat32 (I've no idea why this is...) Try formatting it as ntfs or ext3 and see if you have the same issues.

---

