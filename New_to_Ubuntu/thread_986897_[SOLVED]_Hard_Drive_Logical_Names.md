---
title: "[SOLVED] Hard Drive Logical Names"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by eadwacer on 2008-11-19
SOLVED: Just installed a new Seagate 500GB HDD. Straight from vendor, no changes to jumpers. Partitioned with gparted, and am about to edit fstab. Something worries me:

lshw shows the new drive with the logical name sda1, while my original drive now shows as sdb1. However, when I open fstab, I see:

# /etc/fstab: static file system information.
#
# file system         mount point          type      options          dump       pass
proc	/proc	proc	defaults	0	0
/dev/mapper/ubuntu-root	/	ext3	defaults,errors=remount-ro	0	1
# /dev/sda1
UUID=9e92b6db-1f98-44ec-9305-803ec9ea45f9	/boot	ext3	defaults	0	2
/dev/mapper/ubuntu-swap_1	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	user,noauto	0	0

My noob question is, do I need to change fstab to tell it that the boot drive is now sdb1? Would swapping the SATA cables around change the names? If I leave fstab as is and just add something like:

/dev/sda /mnt/data ext3 defaults 0 0

will it know to boot from sdb1?

---

### Post by Tony Flury on 2008-11-19
as far as I know the fstab file does not define the boot order - that is effective defined by the BIOS and the order in which it selects the drives - i.e. it boots from the master first if it can.

the fstab file does define the mount points of the disks - and may need to be edited if the disks have changed orders.

I did have a smiliar situation a few weeks ago, when i used gparted to move my root partition - my system did still boot (and all the commands i tried worked), but the system had no idea where "/" was, and you could not do a "ls /" - editing fstab fixed that.

---

### Post by Elfy on 2008-11-19
fstab is using UUID - check that they haven't changed by running 

```
sudo blkid
``` and comparing

If necessary then change them.

---

### Post by hyper_ch on 2008-11-19
I rather prefer
```

ls -al /dev/disk/by-uuid

```
to find out what partition has what uuid.

---

### Post by eadwacer on 2008-11-19
I ran both blkid and ls -al..., they both provide similar information in different formats, and the important part is that they showed that the UUID for the boot drive hadn't changed, even though the logical names had. The logical name sda1, shown in fstab, was in a commented line and so had no impact on what was going on - the UUID was OK. So I mounted the 'new' sda1, rebooted, and all's right with the world. Thanks much.

Steve

---

### Post by Elfy on 2008-11-19
Cool - I did think it would be ok - I've just been through similar thing myself.

---

