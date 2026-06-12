---
title: "3Tb drive - 4096 sector partition alignment"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by discmeister on 2012-09-29
Hi all,

I'm in the process of setting up Ubuntu 12.04 LTS Server for my home server, and am installing a Seagate Barracuda 3Tb drive as the data drive called /dev/sdb (Ubuntu is happily installed on an SSD - /dev/sda).

I've realised that I have to use parted because fdisk doesn't like drives larger than 2Tb.

I've run parted -a optimal /dev/sdb, then created a primary partition over all of the drive. Seems to work okay.

Within parted, the align check always comes back as aligned.

I then use mkfs.ext4 to create an ext4 filesystem on that single partition. Again, it seems to work fine.

However, if I do a sudo fdisk -l, it tells me under /dev/sdb that Partition 1 does not start on the physical sector boundary.

Which program is telling the truth?

Hope someone can help. This drive will be storing all of our movies, photos etc, so I don't want to take any chance with the partition being out of alignment and it becoming unstable or slow.

Regards, and thanks in advance for any help,

Discy

---

### Post by 2F4U on 2012-09-29
Don't use fdisk on partitions > 2TB because it can't work with them. Use parted instead.

[http://www.webhostingskills.com/articles/how_to_create_a_partition_size_larger_than_2tb_linux](http://www.webhostingskills.com/articles/how_to_create_a_partition_size_larger_than_2tb_linux)

---

### Post by oldfred on 2012-09-29
You can use parted.

But the fdisk equivalent for gpt drives is gdisk. It is in the repository or you can download the latest version from the developer:
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/download.html#obs](http://www.rodsbooks.com/gdisk/download.html#obs)

[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)
Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

---

### Post by discmeister on 2012-09-29
Sorry, but you can see from my original post that I *have* used parted. I only used fdisk -l to check the drives. Are you saying that it's useless for even that? So its report on the incorrect alignment (the precise opposite of what parted is telling me) is a load of nonsense?

To recap, I've used parted. Parted tells me everything is aligned.

But if I happen to do a sudo fdisk -l then it tells me that it's not.

Which should I believe?

Discy

---

### Post by oldfred on 2012-09-29
Fdisk is not gpt aware, so anything it says is useless. With gpt, it creates what is called a protective MBR. It has one partition entry just so fdisk (and other old tools)  sees entire drive partitioned with a gpt partition, but that is all fdisk reports. You want info from gpt partition table not protective MBR partition table.

If you do not like the info from parted then run gdisk. 

sudo gdisk -l /dev/sda

---

