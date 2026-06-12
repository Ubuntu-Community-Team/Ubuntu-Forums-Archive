---
title: "After installing Ubuntu 14.04 for dual boot with 8.1 i am facing problem"
date: 2015-08-01
forum: New to Ubuntu
---

### Post by Roshan_Dangol on 2015-08-01
I am new to ubuntu and I installed ubuntu 14.04 for dual boot with 8.1. After the completion of boot, my laptop directly loads ubuntu and does not show any option to choose windows 8.1. I cant understand what the problem is. Any help will be appreciated

---

### Post by Bucky Ball on 2015-08-01
Welcome. Try hitting shift just after install. Does a list of options appear? Is Windows on it?

Failing that, boot to Ubuntu, open a terminal and type in:

```
sudo update-grub
```

Hit enter. You might see an entry for Windows flashing by in the output. Once that is finished and you are back at a cursor, reboot, hit shift to get to the list if you need to. Is Windows there?

---

### Post by Roshan_Dangol on 2015-08-01
after tying that command i get 
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by Bucky Ball on 2015-08-01
Hmm. Well, you certainly have Ubuntu installed. Could you now open a terminal and paste in:

```
sudo blkid
```

Post the output back here, please.

---

### Post by howefield on 2015-08-01
Are you sure that you haven't over written your windows partition?

What is the output of 

```
sudo fdisk -l
```

---

### Post by Roshan_Dangol on 2015-08-01
te output is

```
roshan@roshan-Inspiron-3543:~$ sudo blkid
[sudo] password for roshan: 
/dev/sda1: UUID="f535a3b4-cb53-45b1-8c35-b66b6e69252d" TYPE="swap" 
/dev/sda2: UUID="5dd86047-c588-468b-97dc-67a7a8575e49" TYPE="ext4" 
/dev/sdb1: UUID="BC70-8CD6" TYPE="vfat" 
roshan@roshan-Inspiron-3543:~$
```

---

### Post by Roshan_Dangol on 2015-08-01
its output is 

```
roshan@roshan-Inspiron-3543:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2688c49d

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 4040 MB, 4040748544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7892087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         128     7891967     3945920    b  W95 FAT32
roshan@roshan-Inspiron-3543:~$
```

---

### Post by Bucky Ball on 2015-08-02
Yep, looks like you have over-written the Windows install. You have three partitions on the drive:

```
/dev/sda1: UUID="f535a3b4-cb53-45b1-8c35-b66b6e69252d" TYPE="swap" 
/dev/sda2: UUID="5dd86047-c588-468b-97dc-67a7a8575e49" TYPE="ext4" 
/dev/sdb1: UUID="BC70-8CD6" TYPE="vfat"
```

Windows lives on a partition that has the NTFS filesystem. There isn't one here. The first is your /swap partition; the second, sda2, is where Ubuntu is installed and the third, sdb1, I'm not sure of. This is on another drive as it is labelled 'sdb*'. :-k

One things seems certain: there is no Win install shown on the drive sda in your output. :|

Note: sdb could contain Win, but wasn't aware that could live on a FAT partition, which sdb1 is. It looks more likely to be the EFI partition.

---

### Post by Roshan_Dangol on 2015-08-02
Then can you suggest me any solution to this problem what do i do

---

### Post by howefield on 2015-08-02
> **Roshan_Dangol said:**
> Then can you suggest me any solution to this problem what do i do

What is it that you want to do ?

If it is to get into Windows, you will need to reinstall it using your recovery media. You do have recovery media, yes?

---

