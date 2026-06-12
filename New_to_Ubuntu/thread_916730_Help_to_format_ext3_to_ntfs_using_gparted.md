---
title: "Help to format ext3 to ntfs using gparted"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by nehc on 2008-09-11
So i tried to format vista but it went bad. Now when i try to install vista, i can see the partition i want to format but it wont let me do it. So i though that if i install ubuntu i will be able to make a new partition in ntfs, fat32 or any format windows can use and then install vista on it. So i successfully installed Ubuntu and got gparted but when i select the hard drive, the new, delete or format option is not available. How can i fix my hard drive for microsoft? Why dont microsoft just format ext3 to their ntfs? Or why my hard drive doesnt want to format to ntfs?

---

### Post by Elfy on 2008-09-11
You won't be able to change it using gparted if it's installed in ubuntu and the drive is mounted.

First can you post the result of this from a terminal

```
sudo fdisk -l
```

It might be possible to unmount it, if that's not possible you'll need to use the partition editor on the livecd.

---

### Post by nehc on 2008-09-11
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

---

### Post by Elfy on 2008-09-11
I guess you want to remove ubuntu then as there are only linux partitions which is why you can't delete the partition - it's being used to run the program you are trying to delete it with.

You will have to do it with the livecd, or get the gparted livecd from their site.

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by nehc on 2008-09-11
Sorry but i am going to add another problem. i went to that page and downloaded the file gparted-live-0.3.7-7.iso and burn it in a disk. I put the disk and this is what opened. What do i have to do, do i have to install something from this disk? if so, how i do it. I am an ignorant in this because I just installed ubuntu to make the ntfs partition. You know... I am used to the automatic setup thing.

---

### Post by Infinity-al on 2008-09-11
> **nehc said:**
> Sorry but i am going to add another problem. i went to that page and downloaded the file gparted-live-0.3.7-7.iso and burn it in a disk. I put the disk and this is what opened. What do i have to do, do i have to install something from this disk? if so, how i do it. I am an ignorant in this because I just installed ubuntu to make the ntfs partition. You know... I am used to the automatic setup thing.
You have to reboot with it inside.

---

### Post by nehc on 2008-09-11
I was going to say i figure it out how to run the cd but you where faster hehe. I am doing the partition now, will post the results later. Hope everything goes alright.

---

### Post by nehc on 2008-09-11
I have good and bad news. I kind of successfully made the partition. here is the 
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6097    48974121   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda3            6098       18701   101241630    7  HPFS/NTFS
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order

The problem is that windows still cannot install in the ntfs partition. Neither vista nor xp. On the side...I am going to school right now i wont be able to answer fast, but i will try your solution once i come back.
Henry

---

### Post by Julita on 2008-09-11
I had a very similar problem (later I have decided to get rid of any M$ products). The only thing that helped was Acronis Disk Director Suite. If you have your Ubuntu installed, you can burn an iso image, and then boot from it. Acronis does a good job, and quite fast.

---

### Post by Elfy on 2008-09-11
Hi I would have given slightly differnt help if I had known that you wished to keep the ubuntu and install vista.

You will need to do this in the gparted livecd - quicker to boot :)

Delete your new ntfs partition
Shrink the extended partition from the left

There should now be a gap between sda1 and your extended partition

Move sda1 to the right so that you now have the unallocated space at the front (left) of the partition.

The screen should now like like

Unallocated Space|sda1|sda2|sda3

Leave the unallocated space as it is without formatting it. Boot with the vista disc and see if it sees the space now, if not try a format to ntfs with gparted.

Windows likes to install on a primary partition - you made a logical partition for it.

---

### Post by Bulat Sirazetdinov on 2008-09-11
> **nehc said:**
> So i tried to format vista but it went bad. Now when i try to install vista, i can see the partition i want to format but it wont let me do it.
If you do not need data stored in that partition, just delete it and let Vista create a new one.

By the way, as far as I know Vista installer also allow you to delete and create partitions - you do not need Linux for that.

---

### Post by nehc on 2008-09-12
Bulat Sirazetdinov: I wish vista could easily do that, it just doesnt want to do it.

For now i will try forestpixie metod. Will post my results later.
Nehc

---

### Post by nehc on 2008-09-12
I didnt delete ubuntu because i wasnt sure the partition was going to work. So now i decided to delete everything and now i can install vista without problem. Dont really understand how it happened but really thanks for all your help.
Nehc

---

