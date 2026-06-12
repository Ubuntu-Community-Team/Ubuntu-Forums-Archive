---
title: "sharing files between dual boot? Confused :S"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Kestol on 2008-11-08
Hey people,

If read alot about sharing files between XP and Ubuntu on a dual boot and i found out that i could do that by partioting following:

Windows XP(NTFS)
Ubuntu (EXT3)
Sharing Data (FAT32)
Linux Swap (EXT3)

My question is... WTF is Linux Swap Oo... I cant find a good explanation on it.. And how to create it?? Or does ubuntu automaticly create it at the setup??? 
Another thing is.. How do i get the one partition to be FAT32???
If i remember correctly, when installing windows you can partition the drives... But only as NTFS and NTFS (fast)...

Can anybody help :(

---

### Post by Paqman on 2008-11-08
Swap is a small area of hard disk space that the system can use for memory if it runs out of actual RAM memory. Windows does the same with something called the page file (you can also set  up Linux to use a swap file instead of a swap partition if you like)

To share a partition yu simply need to pick a filesystem both OSes can read/write to.

[list]
[*]Ext3: The default Linux filesystem. Windows needs [extsifs](http://www.fs-driver.org/) to read/write to it
[*]NTFS the default Win filesystem. Both Linux and Windows can read/write to this out of the box
[*]FAT32, the old Windows filesystem. Everything (even Macs) can use this, which is why flash drives are formatted this way. It's not really recommended for whole hard drive partitions these days, as it's obsolete and has some major drawbacks compared to a more modern fs like NTFS. You'll still see it recommended by some for compatibility reasons, though.
[/list]

---

### Post by kellemes on 2008-11-08
> **Kestol said:**
> Hey people,

If read alot about sharing files between XP and Ubuntu on a dual boot and i found out that i could do that by partioting following:

Windows XP(NTFS)
Ubuntu (EXT3)
Sharing Data (FAT32)
Linux Swap (EXT3)

My question is... WTF is Linux Swap Oo... I cant find a good explanation on it.. And how to create it?? Or does ubuntu automaticly create it at the setup??? 
Another thing is.. How do i get the one partition to be FAT32???
If i remember correctly, when installing windows you can partition the drives... But only as NTFS and NTFS (fast)...

Can anybody help :(

For sharing you better create a **separate** partition, so a partition not used by the os's to function.
*Paqman* explains the choices you have in filesystems.
As long as you don't need to store files bigger as 4Gb, FAT32 is a safe choice.

Edit: By the way, swap space isn't partitioned EXT3, it has it's own filesystem.

---

### Post by ugm6hr on 2008-11-08
> **Kestol said:**
> Another thing is.. How do i get the one partition to be FAT32???
If i remember correctly, when installing windows you can partition the drives... But only as NTFS and NTFS (fast)...

With the Ubuntu LiveCD, open GParted (System->Administration->Partition Editor)

It is pretty intuitive how to create and format partitions.

I would recommend this order:
1. Create partitions.
2. Install Windows (get Windows to reformat the NTFS partition before installing)
3. Install Ubuntu - manual install - mountpoints: "/" = EXT3 for Ubuntu; "swap" = swap partition.

---

### Post by Kestol on 2008-11-08
Still a litte confused :S

1. So i dont need to make a FAT32? An NTSF would be better???
2. Windows creates the page file itselft.. So does linux create that swap partition by itself???

---

### Post by Paqman on 2008-11-08
> **Kestol said:**
> 
1. So i dont need to make a FAT32? An NTSF would be better???


Both will work. NTFS has the advantage that it can handle large files, and suffers from reduced fragmentation. I would recommend NTFS.

It was only in the last couple of years that Linux has had the ability to write to NTFS partitions by default, so you'll still see people advising the use of FAT32 sometimes. IMO that's obsolete advice.

> 
2. Windows creates the page file itselft.. So does linux create that swap partition by itself???

Yes, the installer will create one, unless you do your partitioning manually. If you partition manually one of the partitions you create should be a small swap partition. It's pretty straightforward.

---

### Post by Kestol on 2008-11-08
Ok :D

Thx alot then... Helped me out alot...

And the Data sharing partition running with NTFS is visible right from the first launch in Win and Linux?

---

### Post by Paqman on 2008-11-08
> **Kestol said:**
> 
And the Data sharing partition running with NTFS is visible right from the first launch in Win and Linux?

Yep.

---

### Post by Kestol on 2008-11-08
Thx alot Paqman!

Last thing...
Sharing files between linux and Win on a partition for itself wont slow anything down with transfer speed or anything? Right?
Since that Sharing partition is also used as libary in WinXp windows Media player to stream movies to my PS3

---

### Post by Paqman on 2008-11-10
> **Kestol said:**
> 
Last thing...
Sharing files between linux and Win on a partition for itself wont slow anything down with transfer speed or anything? Right?
Since that Sharing partition is also used as libary in WinXp windows Media player to stream movies to my PS3

Nope it'll be fine. WinXP and your PS3 will be none the wiser about Linux occasionally mounting the partition.

---

