---
title: "How to format disk correctly ( ext4 )"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by rami5 on 2013-10-06
Hi
I noticed ( when starting up from Ubuntu installation disk ) that there was a partition option from the CD startup menu.
There were Items in the list:
- Something called "swap"
- And another item

Can i just delete both items to format/ erase the disk correctly?

---

### Post by adamitj on 2013-10-06
What do you want to do, exactly? You want to rip off everything in the entire disk?

---

### Post by ibjsb4 on 2013-10-06
If you have dual boot (windows & linux) and you delete the install, your box will not boot.

---

### Post by fantab on 2013-10-06
To be clear post the output of:

```
sudo fdisk -l
sudo parted -l
```

Or post the Screenshot of your partitions from Gparted. You can use the Live Ubuntu to do so.

If you are formatting your entire Hard Disk to reinstall Ubuntu or whatever then 'YES' you can Delete all the partitions and reformat the HDD. But be warned that by re-formatting or deleting Partitions you WILL lose all your DATA. Have good Backups if you need to preserve any DATA.

SWAP partition: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq) 
With large size of RAM (4-8GB) SWAP is not a necessity but it is recommended that you have small SWAP partition about atleast 2GB.

Good Luck

---

### Post by rami5 on 2013-10-06
Thanks for the link, that was very helpfull! :)

I do not have a dual boot, the only OS on this computer shuld be a Linux OS, so i guess i can just go ahead and delete the partitions then ( ive just recently installed, and dont need anything from the hardrive  ).
I do have 4GB ram.

...

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00082429

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1945405439   972701696   83  Linux
/dev/sda2      1945407486  1953523711     4058113    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5      1945407488  1953523711     4058112   82  Linux swap / Solaris

...

Model: ATA ST1000LM014-1EJ1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  996GB   996GB   primary   ext4            boot
 2      996GB   1000GB  4156MB  extended
 5      996GB   1000GB  4156MB  logical   linux-swap(v1)

---

### Post by fantab on 2013-10-06
Since you have a 1TB HDD I would say have a 4GB SWAP. With msdos Partition Table you can have only 4 Primary Partitions. If you need more than 4 then make the fourth partition as EXTENDED.. just a suggestion, HDD scheme looks neat that is all.

---

### Post by rami5 on 2013-10-06
So i wont mess anything up if i delete/ format the two partitions and install, say, Lubuntu then?

---

### Post by DuckHook on 2013-10-06
> **rami5 said:**
> So i wont mess anything up if i delete/ format the two partitions and install, say, Lubuntu then?
Hi rami5

Just install Lubuntu and choose "use whole disk" at the point in the install process where it asks how you want to partition.

---

### Post by rami5 on 2013-10-06
I see, so it will automatically format the disk i assume.
What if i wnat to alter the size of the SWAP partition after installation, can i do this from Gparted ( whatever that is )?

---

### Post by DuckHook on 2013-10-06
It will automatically delete your existing partitions and install a clean one. However, it will use the whole disk and employ defaults that are generally reasonable. If you want to change the size of partitions afterwards, you will have to do so from a LiveDVD/USB using *gparted*. Therefore, if you want to do anything other than using the whole disk, or if you want something other than a 4GB swap, you should choose "Some else" at the point in the install process dealing with partitioning. If you make this choice, you should figure out beforehand what sort of partitioning scheme you want so that you are not flustered in the middle of your install.

Again, if I may be so bold, based on your previous postings, I would recommend that you just "Use whole disk" along with its defaults. A 4GB partition is very reasonable in your case, so no need to change it.

---

### Post by rami5 on 2013-10-06
Did it!
Thanks all, issue solved!
Lubunto looks much cleaner than Ubuntu, and much more responsive on my machine
just my oppinion off cource

---

### Post by DuckHook on 2013-10-06
It *will* be much more responsive. It is missing the fancy effects of Ubuntu (3D spinning desktops, wobbly windows, etc.) but I would rather have a fast responsive computer than eye candy. I happen to share your opinion.

---

