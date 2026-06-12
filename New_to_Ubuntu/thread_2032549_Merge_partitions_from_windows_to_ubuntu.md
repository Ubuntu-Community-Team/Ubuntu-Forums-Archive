---
title: "Merge partitions from windows to ubuntu"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by Arpitha on 2012-07-24
I have both windows 7 and ubuntu 10.04 on my laptop. I want to merge an unallocated partition (18.69GiB) on windows with sda6 on ubuntu. I tried using GParted and there's a screen shot of how the drives look. Can someone tell me what has to be done? Absolute beginner here!

---

### Post by muteXe on 2012-07-24
One quick way:
Format as ext4, then edit the fstab so it's mounted on boot. you should be able to see it as another drive then. 

fstab info: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Arpitha on 2012-07-24
Can't I merge it with sda6?

---

### Post by audiomick on 2012-07-24
Yes, you can merge it, but it means a bit of mucking around. The 18GB of free space is "to the left of" the extended partition that sda6 is in. What you have to do is shuffle the free space down the line until it is adjacent to the partition that you want to add the free space to.

In your case, you will have to

move the left side of the extended partition to the left in order to move the free space to inside the extended partition. The free space will be at the left hand end of the extended partition, adjacent to the ntfs partition.

Move the left border of the ntfs partition to the left so that it once again starts at the beginning of the extended partition. The free space has now become part of the ntfs partition.

Move the right side of the ntfs partition to the left to free up the amount of space you want to add the sda6. You will now have a free space adjacent to sda6.

Move the left side of sda6 to the left to incorporate the free space into sda6.

As I said, it is a bit of messing around. It will take a little time, and you don't want to rush it if it is the first time you have done this.

DO MAKE BACKUPS OF ANYTHING IMPORTANT THAT IS ON THE COMPUTER. The procedure is "safe", but it is accepted good practice to always do backups before doing any partitioning work at all.

---

### Post by Cheesemill on 2012-07-24
> **Arpitha said:**
> Can't I merge it with sda6?
You can, but it will take a while.

1 - Boot from a Live CD and fire up gparted.
2 - Right click on sda7 and select Swapoff.
3 - Resize sda2 all the way to the left.
4 - Move sda5 all the way to the left (this will take several hours).
5 - Resize sda6 to include all of the unallocated space.

Make sure you have a backup before attempting this as any operations involving moving or resizing partitions carries an element of risk.

---

