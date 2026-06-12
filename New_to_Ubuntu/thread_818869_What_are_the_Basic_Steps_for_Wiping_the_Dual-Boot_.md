---
title: "What are the Basic Steps for Wiping the Dual-Boot System?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by raydanator on 2008-06-04
So I have an Ubuntu-Windows dual boot on my 98 desktop. I want to install Windows again, getting rid of Ubuntu and the Grub booter. 

For your information_*I'm not giving up on Ubuntu/Linux*_I just want to start over with a fresh copy of Windows.

I've never actually reinstalled/formated my drive before, and am wondering what the basics are. (Yah, I know I'm a noob)

---

### Post by django0909 on 2008-06-04
Alter your BIOS to boot from CD, stick your Windows disk in and away you go.

---

### Post by iaculallad on 2008-06-04
You can use your Ubuntu LiveCD's Gparted Partition manager to delete all your existing partitions (be it of windows or Ubuntu). Be sure to backup all your important data prior to doing this.

---

### Post by raydanator on 2008-06-04
I'm a little lost. I've gotten into the fdisk part of the install, but should I install a fat32 or fat16? If fat16, what options do I choose to wipe the whole thing?

---

### Post by Lord Xeb on 2008-06-04
Go with FAT32. It allows for a max file size of 4GB and is supported everywhere.

---

### Post by raydanator on 2008-06-04
What do I do when I get to this setup?

[B]1. Create DOS partition or Logical DOS Drive
2. Set active partition
3. Delete partition or Logical DOS Drive
4. Display partition information
5. Change current fixed disk drive 
  (this option is only available if you 
   have two physical hard disks in the computer
[/B]
If I choose to delete the partition what do I then choose?
[B]
1. Delete Primary DOS Partition
2. Delete Extended DOS Partition
3. Delete Logical DOS Drive(s) in the Extended DOS Partition
4. Delete Non-DOS Partition[/B]


I'm just wanting to wipe the drive. Is this the right way?

---

