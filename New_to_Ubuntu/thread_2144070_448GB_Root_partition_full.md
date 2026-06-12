---
title: "448GB Root partition full"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by digital7 on 2013-05-11
Hi all,

I am helping someone out that has Unbuntu 10.04 installed.  They have a 500GB hard drive and only 12.9 GB is being shown used in Disk Usage Analyzer.  However Disk Usage Analyzer says Total filesystem capcity is 446.8 GB and 424.1 GB in use.  I provided a screenshot here:

[ATTACH=CONFIG]242446[/ATTACH]

Here are results from a df -h command as well:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             448G  425G  973M 100% /
none                  1.9G  264K  1.9G   1% /dev
none                  1.9G  316K  1.9G   1% /dev/shm
none                  1.9G  100K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw

It appears that the person who set this up installed it wrong, but I am not that familiar with Unbuntu to know who to find the 425 GB in use.  Or I am just over looking something.

Hopefully you all can point me in the right direction.  Thanks in advance!

---

### Post by fantab on 2013-05-11
First of all Ubuntu 10.04 has reached its '[end of life]("https://wiki.ubuntu.com/Releases")', which means it will no longer be supported with 'security upgrades' among other upgrades. Your friend must seriously consider installing one of the [latest versions of ubuntu]("http://www.ubuntu.com/download/desktop"). 

Post the out of command:
```
sudo fdisk -l
```

You might find this: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670) useful to sort your present problem. However, I suggest you advice your friend to install latest Ubuntu ASAP. If you can provide us with more info about the System Hardware we will be able to guide you accordingly. Information, such as, processor, RAM, Graphics will be useful.

Note... the colored text has links.

---

### Post by digital7 on 2013-05-11
Here are the results:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005f7dc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59387   477017088   83  Linux
/dev/sda2           59387       60802    11366401    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5           59387       60802    11366400   82  Linux swap / Solaris


Disk /dev/sdb: 1000.2 GB, 1000204885504 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc64673ed


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS



And here are the specs
Memory - 4GB
CPU - iCore i5-2400
Not sure on graphics card.  It's embedded in motherboard

---

### Post by grahammechanical on 2013-05-11
It is confusing, is it not? Disk Usage Analyser always shows the root Directory to be 100% full. It is showing it now on my machine and it lists the size as 4.8GB when the partition is actually 21GB. I have several installations of Ubuntu ranging from 12.04 through 12.10 and 13.04 to 13.10. And it does not matter what the size of the / partition, Disk Usage Analyser will show root directory as 100% full. This is what it does. You are seeing it on 10.04. I am seeing it on 13.10.

There is not a problem. Do not worry about it. Install some applications and you will see that the root directory has got bigger but it will still show as 100% full. The utility is not showing the partition or hard disk size but the size of the root directory and the directories under the root directories. Add up the percentages used of those other folders and you will see that the total comes close to 100%. That is what the utility is recording.

Regards.

---

### Post by digital7 on 2013-05-11
> **grahammechanical said:**
> It is confusing, is it not? Disk Usage Analyser always shows the root Directory to be 100% full. It is showing it now on my machine and it lists the size as 4.8GB when the partition is actually 21GB. I have several installations of Ubuntu ranging from 12.04 through 12.10 and 13.04 to 13.10. And it does not matter what the size of the / partition, Disk Usage Analyser will show root directory as 100% full. This is what it does. You are seeing it on 10.04. I am seeing it on 13.10.

There is not a problem. Do not worry about it. Install some applications and you will see that the root directory has got bigger but it will still show as 100% full. The utility is not showing the partition or hard disk size but the size of the root directory and the directories under the root directories. Add up the percentages used of those other folders and you will see that the total comes close to 100%. That is what the utility is recording.

Regards.

Thanks!  But I am sharing a folder to others PCs on the network and they are all saying there is only 875 MB left of the 488GB hard drive on the Ubuntu machine.  They try to save data and then it eats up the last 800 MB real quick and they can't dave any more so something is eating up over 450 GB of disk space.  Or something was configured incorrectly...

---

### Post by prodigy_ on 2013-05-11
To find out which files are consuming space on your root partition: ```
sudo find / -xdev -type f -exec du -b '{}' \; | sort -rn | less
``` This command outputs the list of all files sorted by file size in bytes. You can navigate the list with up/down or pgup/pgdn keys. (You'll see nothing in terminal for a while because **less** has to wait for **find** and **sort** first.)

---

