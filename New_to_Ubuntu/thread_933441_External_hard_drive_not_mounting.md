---
title: "External hard drive not mounting?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by simonbondar on 2008-09-29
Hi, 

I am very new to Ubuntu, but loving it so far. But the only problem I have run into is that it doesn't seem to mount or recognise that a usb external (mains powered) hard drive is connected.

This is the results of sudo fdisk -l

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41df41de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       33813   271602891    7  HPFS/NTFS
/dev/sda2           33814       38913    40965750    f  W95 Ext'd (LBA)
/dev/sda5           33814       38913    40965718+   7  HPFS/NTFS

```

sda1 is my main Windows XP partition, sd5 appears to be my web server (no idea what sda2 is).

But for whatever reason my Freecom 400gig external hd isn't showing up.

Any takers?

---

### Post by WWSmith36 on 2008-09-29
I believe fdisk can only read connected drives with a formated filesystem.  Is this a brand new external hard drive that has not been formated yet?

---

### Post by bumanie on 2008-09-29
There is no linux partitions, have you installed via wubi? sda2 looks as though it is an extended partition that has sda5 inside it. Ensure you have formatted the drive and put a filesystem on it.

---

### Post by simonbondar on 2008-09-29
It has an NTFS file system formatted in Windows XP Pro. As I wanted to be able to have access to my files whether using XP or Ubuntu. 

I did use the wubi installer. I also installed Ubuntu using the wubi installer on my girlfriend's laptop and her external drive works fine.

---

### Post by simonbondar on 2008-09-29
I should mentioned that the fdisk is showing the results of my internal drive, as far as I can tell. The external driving isn't showing up, thus my problem. :)

---

### Post by bumanie on 2008-09-29
Sorry, don't know much about wubi installations, but ubuntu should see your external drive? Is it the same model as your girlfriend's external drive. Have you tried it in her computer? Although linux/ubuntu has drivers for most devices, I have read of others having difficulty with 'proprietary' external hard drives not working in linux. When they have contacted the manufacturer, the manufacturer has said "We don't support Linux". If it is a very new model external drive, it is possible that there are no open source drivers written yet. This may not help, but at least it will show if ubuntu recognizes that the drive is plugged in or not. In terminal > lsusb without the external plugged in then > lsusb again with the external plugged in - see if it is recgnized at all.

---

### Post by mindoms on 2008-09-29
after plugging it in run in terminal
```
dmesg | tail -n 15
```

and post the output please

---

### Post by simonbondar on 2008-09-29
> **bumanie said:**
> Sorry, don't know much about wubi installations, but ubuntu should see your external drive? Is it the same model as your girlfriend's external drive. Have you tried it in her computer? Although linux/ubuntu has drivers for most devices, I have read of others having difficulty with 'proprietary' external hard drives not working in linux. When they have contacted the manufacturer, the manufacturer has said "We don't support Linux". If it is a very new model external drive, it is possible that there are no open source drivers written yet. This may not help, but at least it will show if ubuntu recognizes that the drive is plugged in or not. In terminal  without the external plugged in then  again with the external plugged in - see if it is recgnized at all.

The ext hd is about a year and half old. I have the 400gig version of this: [http://www.freecom.com/ecproduct_detail.asp?ID=3618&CatID=8020&sCatID=1146263&ssCatID=1146557](http://www.freecom.com/ecproduct_detail.asp?ID=3618&CatID=8020&sCatID=1146263&ssCatID=1146557)

> **mindoms said:**
> after plugging it in run in terminal
```
dmesg | tail -n 15
```

and post the output please

Here's the output:

```

[ 5052.439311] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 5052.439312]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 5052.439313]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5052.439316] ata1.00: status: { DRDY }
[ 5052.439334] ata1: soft resetting link
[ 5053.010002] ata1.00: configured for UDMA/33
[ 5053.010015] ata1: EH complete
[ 5308.202194] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 5308.202205] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 5308.202206]          cdb 1e 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 5308.202207]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 5308.202209] ata1.00: status: { DRDY }
[ 5308.202227] ata1: soft resetting link
[ 5308.772891] ata1.00: configured for UDMA/33
[ 5308.772906] ata1: EH complete


```

---

### Post by remshad on 2008-09-29
Its Not Functioning    :guitar:    :popcorn:

---

### Post by simonbondar on 2008-09-29
> **remshad said:**
> Its Not Functioning    :guitar:    :popcorn:
It is under XP. Hence why I am asking for help. :)

---

### Post by mindoms on 2008-09-29
Sorry, i cant halp you there.
maybe your HDD or hdd-controller is not fully supported by the driver. or some functions, like dma should be disabled.

---

### Post by Crafty Kisses on 2008-09-29
I'd like to see the results of your fstab:
```
gksu gedit /etc/fstab
```
Post the results here, you may also want to try the following:
```
sudo mount -a
```

---

### Post by simonbondar on 2008-09-30
> **Codename said:**
> I'd like to see the results of your fstab:
```
gksu gedit /etc/fstab
```
Post the results here, you may also want to try the following:
```
sudo mount -a
```

fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

sudo mount -a doesn't seem to do anything.

---

### Post by walkingthecow on 2008-09-30
Well, first you need to figure out what device it is, then you need to mount the system. You can also add it to your /etc/fstab if you'd like, so that it automounts. 

sudo mkdir /mnt/whatever
mount /dev/yourdevice (sda often) -t ntfs /mnt/whatever

and then add it to /etc/fstab

/dev/yourdevice /mnt/whatever ntfs user,uid=<username> 0 0

You could try doing the mount command with /dev/sda1 and see what happens.

---

### Post by simonbondar on 2008-09-30
> **walkingthecow said:**
> Well, first you need to figure out what device it is, then you need to mount the system. You can also add it to your /etc/fstab if you'd like, so that it automounts. 

sudo mkdir /mnt/whatever
mount /dev/yourdevice (sda often) -t ntfs /mnt/whatever

and then add it to /etc/fstab

/dev/yourdevice /mnt/whatever ntfs user,uid=<username> 0 0

You could try doing the mount command with /dev/sda1 and see what happens.

I have no idea how to do that...

At the moment the external is empty. So is there a particular file system that would work best? I just need the drive to work in Windows XP and Ubuntu, so that I can store all my files on the external. 

At the moment its a NTFS system, with a logical partition.

---

### Post by bumanie on 2008-09-30
The problem seems to be that for whatever reason, ubuntu does not recognise the drive. Trying to add it to /etc/fstab is futile when the OS is not seeing it. You have been struggling with this for hours - unfortunately, I am out of ideas other than you could go to launchpad, which is the bug reporting site for ubuntu and search for issues pertaining to your drive make and model and see if there is any type of work around to get it going. You could also put in a bug report yourself and a programmer would, at some point, look at the problem. I guess you could try to format the hard drive again - ntfs should be fine, but I get your point that it works in windows and this is unlikely to help. I still think looking at lsusb with it not plugged in and then again with it plugged in may be helpful - even if it confirms that ubuntu can't 'see' the drive - the more information for a developer/programmer to go on the better. Sorry I can't be more helpful.

---

