---
title: "Mounting questions"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Commander_Keen on 2008-10-07
Good day.
  If this question has already been asked I appologize as I couldn't find it.

So I installed Ubunto a few days ago.  I have 4 partitions.
OS (30gbs), Swap (15gb) Drive A (30)<Fat32> Drive B(30)<Fat32>

On Drive B, has my persoanl data, Email for Thunderbird.

Here is what I would like to do.
I would like to install Thunderbird on the OS drive. 
I would like for all the data to be on Drive B.
I would like to Link the Data, from Drive B to the OS.

what's Occuring:
  Every time I boot up, and start Thunderbird, Thunderbird starts with a fresh setup. Now if I reboot and double click on Drive B, and then start thunderbird, it will conttain the correct data.
  How do I setup the OS, so when I boot up the OS and start Thunder It already contains the correct data.

---

### Post by kpkeerthi on 2008-10-07
YOu need to configure /etc/fstab to mount drive B automatically at startup. To do this, post the output of the below commands:
```
sudo blkid
```
```
cat /etc/fstab
```
```
sudo fdisk -l
```

* Post the output between [code] tags.

---

### Post by Commander_Keen on 2008-10-07
> **kpkeerthi said:**
> YOu need to configure /etc/fstab to mount drive B automatically at startup. To do this, post the output of the below commands:
```
sudo blkid
```
/dev/sda1: UUID="449a2a16-e64c-4388-a94d-9bab0bc784ed" TYPE="reiserfs" 
/dev/sda2: TYPE="swap" UUID="1a8b641c-99d9-4954-b62f-0b098f143c68" 
/dev/sda3: UUID="45A9-5471" TYPE="vfat" 
/dev/sda4: LABEL="NEW VOLUME" UUID="4CF0-E55D" TYPE="vfat" 


```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=449a2a16-e64c-4388-a94d-9bab0bc784ed /               reiserfs notail,relatime 0       1
# /dev/sda2
UUID=1a8b641c-99d9-4954-b62f-0b098f143c68 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
jrothschild@Ubunto:~$ 


```
sudo fdisk -l
```Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x345e345d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3647    29294496   83  Linux
/dev/sda2            3648        5924    18290002+  82  Linux swap / Solaris
/dev/sda3            5925        9876    31744440    c  W95 FAT32 (LBA)
/dev/sda4            9877       13828    31744440    c  W95 FAT32 (LBA)
jrothschild@Ubunto:~$ 


* Post the output between [code] tags.
Here are the results as requested.

---

### Post by kpkeerthi on 2008-10-08
1. Your OS drive (the root partition)is /dev/sda1. Follow the instructions [here]("http://www.funnestra.org/ubuntu/hardy/#thunderbird"). This will install thunderbird to /dev/sda1. 
**Note: **If your thunderbird installation method was different from this, you may want to completely uninstall it before you start step 1.

**Mounting the FAT32 Volumes /dev/sda3 & /dev/sda4 :**

1. Create folders where the partitions will be mounted:
```
sudo mkdir /media/Drive{A,B}
```

2. Open /etc/fstab:
```
gksudo gedit /etc/fstab
```

3. Add these lines to the end of the file:
```

/dev/sda3    /media/DriveA    vfat    user,auto,fmask=0111,dmask=0000    0    0
/dev/sda4    /media/DriveB    vfat    user,auto,fmask=0111,dmask=0000    0    0

```

3. Save and exit the editor.

4. To test if the partitions are mounting, type this command:
```
sudo mount -a
```
You should now see the shortcuts to the partitions on your desktop. They should also be accessible from GNOME Menu -> Places (a reboot might be required) and in File Browser (nautilus).

Post back the errors if the partitions fail to mount.

5. The partitions should automount next time you reboot.
(For all the gory details about mounting partition, see [this]("https://help.ubuntu.com/community/AutomaticallyMountPartitions") link)

Optionally, you may want to label your FAT32 partitions, so the partition shortcuts on the Desktop will be named using their labels. See this [link]("https://help.ubuntu.com/community/RenameUSBDrive#FAT16%20and%20FAT32") for more info.

---

### Post by Commander_Keen on 2008-10-08
thanks for the heads up.
I was wonding about the Label, that was actually my next question, once I fixed the mounting.

---

