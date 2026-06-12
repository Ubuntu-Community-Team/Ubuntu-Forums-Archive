---
title: "Over-partitioned hard drive"
date: 2015-06-18
forum: New to Ubuntu
---

### Post by jonathan87 on 2015-06-18
I am a complete novice with Linux and installed Ubuntu 14.04 today.

While I was eventually successful, two failed attempts have resulted in a 100GB and 67GB hard drive volumes left (visible in the ubuntu icons), each containing boot/etc/media folders but essentially empty. The crashes were from the install guide, shortly after selecting the hard drive space to be assigned to windows and ubuntu.

From running windows it is not obvious that these have been partitioned, but presumably these folders are now not available to it? Ideally I want those volumes reassigned to windows and am worried that they can't be..

Sorry for my naivity, will really appreciate any help!!

---

### Post by Bashing-om on 2015-06-18
jonathan87; Sure, can do .

Whereas linux ('buntu) is able to address Windows' file systems, to Windows there is no other operating system in existence, and Windows could care less about another installed operating system and will not "see" any other.

But yes, those old partitions can be deleted and re-purposed for use by Windows ( and 'buntu for that matter).
As these partitions were created from 'buntu, use 'buntu tools to delete them.
1st is to identify the partitions that you keep.
Find out what is mounted:
```

cat /etc/fstab

```
In the output are the UUID's of the devices ( partitions are also devices) . Now we want to match the UUID to the partition:
```

sudo blkid

```

We now know what partitions are in use, and have a good idea of what partitions may be eliminated.

The GUI way :
Activate ubuntu's partition editor GParted, and in this tool either delete the partitions or reformat to NTFS; and in Windows set up the new partitions.

If you require additional guidance, please provide the outputs - between code tags - and a screen shot of GParted's depiction .
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by cooleryawner on 2015-06-19
use Gparted to free up the space and then go to Windows Partition manager to eat up the empty space.

---

### Post by leunam12 on 2015-06-19
As has been said you can simply delete those partitions in gparted and then go to Windows and use the Disk Management tool to extend your Windows partition (press WINDOWSKEY+R and then type diskmgmt.msc and press enter to go to the disk management application). But before you do anything post the results of ```
sudo parted -l
``` and ```
lsblk
```and a screenshot of Gparted depiction of your drive, just to be sure that the unused partitions are right next to the Windows partition, just a precautionary step.

---

