---
title: "remove ubuntu"
date: 2019-06-19
forum: New to Ubuntu
---

### Post by pratap73 on 2019-06-19
i have installed multiple ubuntu 18.04 in my laptop so i want to remove them

---

### Post by mastablasta on 2019-06-19
backup the data you need and reformat the disk where Ubuntu is installed to your preferred file system.

---

### Post by Rubi1200 on 2019-06-19
What exactly do you mean by multiple?

You need to provide much more information if you want us to help you.

Computer make/model?

Specifications, e.g. RAM, graphics card, etc.?

How did you install?

Are you dual-booting with Windows?

From a command terminal CTRL+ALT+T please post output:

```
sudo fdisk -l
```

---

### Post by pratap73 on 2019-06-29
here is the result of the given command:
```
Disk /dev/loop0: 53.7 MiB, 56328192 bytes, 110016 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 38.9 MiB, 40804352 bytes, 79696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 205.3 MiB, 215252992 bytes, 420416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 202.3 MiB, 212099072 bytes, 414256 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 89.4 MiB, 93720576 bytes, 183048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 88.4 MiB, 92733440 bytes, 181120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 202.9 MiB, 212713472 bytes, 415456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 89.3 MiB, 93581312 bytes, 182776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x21f01fe7

Device Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 493133567 493131520 235.1G 83 Linux
/dev/sda2 493133822 976771071 483637250 230.6G 5 Extended
/dev/sda5 973676544 976771071 3094528 1.5G 82 Linux swap / Solaris
/dev/sda6 493133824 973676543 480542720 229.1G 83 Linux

Partition 2 does not start on physical sector boundary.
Partition table entries are not in disk order.




Disk /dev/loop8: 191 MiB, 200249344 bytes, 391112 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
```

---

### Post by TheFu on 2019-06-29
sda appears to be 100% Linux.  Using any partitioning tool from any OS and delete all the partitions.  Then load any OS you want.  There doesn't appear to be any other non-Linux OSes on it.

If you are using LVM and want to remove specific LVs, but keep some others, then we'd need to see the output from 
```
lsblk
sudo lvs
sudo vgs

```to get started.

Also, when posting output from commands, please, please use "code tags" like I did above so things are readable. Columns should line up.

---

### Post by pratap73 on 2019-06-29
Please recommand some best partitioning tool for ubuntu 18.04

---

### Post by ajgreeny on 2019-06-29
What do you want to do with this machine after removing Ubuntu?

As mastsblasta says above it may be simpler to just install the new OS using the whole disk; if you do that there is no need to remove the current OS before installing a new one.

---

### Post by pratap73 on 2019-06-29
installed ubuntu os into two partitions so technically i've installed two ubuntu os on my machine so all i want to remove one of them!!

---

### Post by TheFu on 2019-06-29
> **pratap73 said:**
> installed ubuntu os into two partitions so technically i've installed two ubuntu os on my machine so all i want to remove one of them!!

This is some of the important parts.
```

Device Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 493133567 493131520 235.1G 83 Linux
/dev/sda2 493133822 976771071 483637250 230.6G 5 Extended
/dev/sda5 973676544 976771071 3094528 1.5G 82 Linux swap / Solaris
/dev/sda6 493133824 973676543 480542720 229.1G 83 Linux
```

Boot into the Ubuntu you want to keep. Use a partitioning tool to delete the partitions that are not being used by it.  fdisk, parted, gparted are some tools for this. Beware. If you delete a wrong partition, then that data is lost.

Also, if you are using LVM, we cannot tell from the provided information and deleting the  partitions would effectively remove any LVs, which could be bad.  That is why I asked for specific data already. That data hasn't been provided.

---

### Post by uRock on 2019-06-29
Gparted is not installed by default, but it is my favorite tool for this kind of task. You can install it through the Ubuntu Software or via terminal with **sudo apt install gparted**

It should show which partitions are currently mounted. You can select to delete those partitions. Once deleted you have to update grub so it will boot correctly. To do so, run sudo update-grub in a terminal.

---

### Post by Impavidus on 2019-06-29
Better to reinstall grub. If the Ubuntu you delete is the one in control of grub, the system will no longer boot. So, while running the Ubuntu you want to keep, reinstall grub:```
sudo grub-install /dev/sda
```I'm not sure grub gets updated automatically at the same time, but it won't harm to do it again.

You can use gparted on the Ubuntu you want to keep to delete partition of the Ubuntu you want to remove, but you cannot use it to resize the partition of the Ubuntu you want to keep. You cannot modify a partition while it's in use. So to reclaim the space from the partition you're going to delete, you'll need a live disk.

---

### Post by TheFu on 2019-06-29
> **Impavidus said:**
> You cannot modify a partition while it's in use. So to reclaim the space from the partition you're going to delete, you'll need a live disk.

True.

But this might be a good time to make better partition allocations for a system where you can keep a base install and have 5-10 play boot Linux areas while reducing the chance of harming your HOME directory.  There are lots of forum threads here where people ask about partitioning and recommended sizes for the different partitions commonly used.
For example, I see little reason for the OS to ever be larger than 25G in size.  Usually less than half that size is used on really bloated installs. 25G is way, way, way larger than necessary.  

Create a separate /home/ partition for user files. Lots of good reasons to do that on a desktop install.
If you need a place to share storage/working areas with multiple users, then that would be a different partition.
If you need a place for media (music/videos), that would be a different partition.

The type of files stored lead to the best backup solution. Backups generally happen on a partition level, at least in my world.  I don't backup the OS, just the OS settings and very specific data areas.  I do backup /home/ using versioned backups.  
Media backups are not versioned, since media files tend to be created once and never modified. For those, a simple rsync-mirror is a sufficient backup to me.

Anyways, lots of options. Also, since partitioning is sorta inflexible, very hard to change, it might be worth considering using LVM.  Then you have logical volumes that can be easily resized as needed, often without any impact on a running system.  Also with LVM, you have access to snapshots which can make backups 100% quiesced, so there is ZERO chance of a failed backup due to a file changing while it is being backed up. That's sorta a big thing if you run any DBMS at all.  LVM is powerful, but it has to be setup at install time to provide the greatest flexibility.

---

### Post by kurt18947 on 2019-06-30
> **uRock said:**
> Gparted is not installed by default, but it is my favorite tool for this kind of task. You can install it through the Ubuntu Software or via terminal with **sudo apt install gparted**

It should show which partitions are currently mounted. You can select to delete those partitions. Once deleted you have to update grub so it will boot correctly. To do so, run sudo update-grub in a terminal.

This would be my choice.

---

### Post by oldrocker99 on 2019-06-30
The best partition manager, usable over every format, from DOS16 to ext4, is GParted. You can't use it on a system disk; use a live session for that. It will also allow you to reinstall. Make a 64GB partition for /, formatted ext4, and format the rest of the disk ext4, and mount it as /home. Then you won't have to copy files over to the /home folder, and you'll have the maximum amount for /home, **which can never be too big.**

---

### Post by ajgreeny on 2019-07-02
I would agree with TheFu that the root partition for a standard desktop machine does not need to be larger than 20-25G, and even that size is unlikely to fill up by more than 30-40%, so 64 is HUGE and unnecessarily wastes space.

---

