---
title: "mounting problem"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Abu Noor-Eddin on 2008-09-27
Hi all,

While installing Ubuntu I choose to mount my data partition into /home now I want to mount it alone in a separate partition as it should be. How can I do so?

Here is its line in fstab
```

UUID=a63d7ed5-35d5-4cf5-bc83-9dd7f9384e17 /home           ext3    relatime        0       2

```

Another thing, Ubuntu sees my windows C partition twice, there is a two of my c. How to deal with this issue?

Thanks in advance.

---

### Post by bumanie on 2008-09-27
Please post the output of > cat /etc/fstab

---

### Post by Abu Noor-Eddin on 2008-09-27
> **bumanie said:**
> Please post the output of

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=0aa735fb-f700-4acd-a153-78a532a09183 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=a63d7ed5-35d5-4cf5-bc83-9dd7f9384e17 /home           ext3    relatime        0       2
# /dev/sda6
UUID=ff97b1a8-0995-4945-911d-e6d1e57f9277 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by bumanie on 2008-09-27
This may not be exactly what you are looking for, but as you have a separate / partition, your /home (also on a separate partition) is really acting the same as a data partition. The important thing is that /home and / are separate, so if anything drastic goes wrong with ubuntu, you only have to reinstall to / and all your data in /home is safe, as long as you choose manual at the partitioning stage and ensure you only format / during the reinstall. IMO a separate /home is the same as a data partition.

---

### Post by Abu Noor-Eddin on 2008-09-27
> **bumanie said:**
> This may not be exactly what you are looking for, but as you have a separate / partition, your /home (also on a separate partition) is really acting the same as a data partition. The important thing is that /home and / are separate, so if anything drastic goes wrong with ubuntu, you only have to reinstall to / and all your data in /home is safe, as long as you choose manual at the partitioning stage and ensure you only format / during the reinstall. IMO a separate /home is the same as a data partition.

How can I have my separate partition again?

---

### Post by bumanie on 2008-09-27
You would have to make a new partition as far as I can tell from your /etc/fstab output. You have /; /home; and /swap - depends how much space there is on your hard drive - either
A) make a new partition or 
B) if there is no space left, shrink /home and then make a separate data partition from the new unallocated space. 
I can't see any other way. A good tool to use is gparted > sudo apt-get install gpartedOnce installed, find it under System --> Tools --> Partition Editor. It has a simple GUI to follow.

---

