---
title: "HowTo get Grub back to normal?"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-02-07
I installed Xubunt next to Ubuntu (both 12.04) and Xubuntu took up too much room (I did not partition properly). It took up Two large partitions and 2/3 of the HDD. For some reason gparted would not resize the Xubuntu partition, so I deleted all but the Ubuntu partition and reinstalled Xubuntu, letting it do the partitioning. Once it was reinstalled, I could resize it normally.

Meanwhile, back at the ranch, I forgot all about the Grub menu. I have made a mess of it. I did not think I would be able to boot Ubuntu at all, but it, finally, came up.

How do I fix Grub?

---

### Post by sudodus on 2014-02-07
Please post the output of the following commands

```
sudo parted -l
```
and
```
df
```
It will help us give relevant advice.

If you also ***attach*** a copy of the file **/boot/grub/grub.cfg**, we will understand even better.

---

### Post by bc.haynes on 2014-02-07
```
ben@MissionControl:~$ sudo parted -l
[sudo] password for ben: 
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  177GB  177GB   primary   ext4            boot
 2      177GB   500GB  323GB   extended
 6      177GB   338GB  161GB   logical   ext4
 5      496GB   500GB  4022MB  logical   linux-swap(v1)
```

```
ben@MissionControl:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      169628684 6092392 154912988   4% /
udev             1851348       4   1851344   1% /dev
tmpfs             744312     900    743412   1% /run
none                5120       0      5120   0% /run/lock
none             1860776     488   1860288   1% /run/shm
```

---

### Post by bc.haynes on 2014-02-07
Is this right? (See attachment.) If you can see the extended partition, it goes into the unallocated area. I believe I have messed up again.

---

### Post by brokenhachi on 2014-02-07
are you not able to get the grub menu at all? seems like you just need to reinstall grub. Boot into the livecd and try this: [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UvVzrIWFJ1c](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UvVzrIWFJ1c)

---

### Post by bc.haynes on 2014-02-07
I found this I-don't-know-where and it worked
```
sudo update-grub
```
Xubuntu boots slower now, but Ubuntu boots a little faster.

---

### Post by sudodus on 2014-02-08
> **bc.haynes said:**
> ```
ben@MissionControl:~$ sudo parted -l
[sudo] password for ben: 
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  177GB  177GB   primary   ext4            boot
 2      177GB   500GB  323GB   extended
 6      177GB   338GB  161GB   logical   ext4
 5      496GB   500GB  4022MB  logical   linux-swap(v1)
```

There is unallocated space between partition 6 and 5.
> 
```
ben@MissionControl:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      169628684 6092392 154912988   4% /
udev             1851348       4   1851344   1% /dev
tmpfs             744312     900    743412   1% /run
none                5120       0      5120   0% /run/lock
none             1860776     488   1860288   1% /run/shm
```

You have booted into /dev/sda1, and from /boot/grub/grub.cfg it seems that you only boot into that partition. There is no entry for /dev/sda6, the other ext4 partition. I can see only one UUID.

> **bc.haynes said:**
> I found this I-don't-know-where and it worked
```
sudo update-grub
```
Xubuntu boots slower now, but Ubuntu boots a little faster.

Congratulations! When I woke up after a good night's sleep, you had found the solution, the grub configurations scripts work for you, and
```
sudo update-grub
``` solved your problem :KS

I suggest that you use gparted to create a partition from the unallocated space. Since you have only linux in the computer, I suggest that you make a small partition for testing new versions and flavours of Ubuntu and use the rest of it as a data partition (also an ext4 partition, but give it the label ***data***, which makes it easier to identify). It is a good idea to keep photos, multimedia and other already compressed files in a separate data partition, that can be ***easily backed up*** by copying the files to an external drive with ***rsync*** or some graphical backup program.

---

