---
title: "gparted/swap partitions"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-17
my gparted is confusing.  have vista on sda1, nothing on 2?, ubuntu on 3 but it boots first from grub, and debian on sda4 but it's commented out of grub and I want to replace it with arch.  But back to gparted- THere are two skinny swap partitions sandwiched between the debian and ubuntu.  I don't know if this is an accident or what.   but I seem to have more memory than I know what to do with or is thie swap partitions working?.

---

### Post by carlinuxlearner on 2008-08-17
Could you post a picture of your partition table? That would help a lot in explaining things.

C@RL

---

### Post by adamogardner on 2008-08-17
please excuse the color settings.  thanks for looking this over.  does vista look way too big?

---

### Post by carlinuxlearner on 2008-08-17
OK, your first partition "/dev/sda1" is your windows install (NTFS).
The second one on the list is 902.00 Mib (basically MB) of unallocated space on your hard drive, meaning it's not partitioned to be used by a filesystem, so at this moment that part cannot store anything.
Your second partition "/dev/sda2" is your root partition "/"
Your third partition "/dev/sda3" is a extended partition (it doesn't store anything it self, it just stores the extra partitions)
Your forth partition "/dev/sda4" is some 11GB partition probably for debian or ubuntu.
Your fifth and sixth partitions "/dev/sda5" and "/dev/sda6" are both swap partitions, which put together consist of about 3.5GB of swap space, which I can't imagine you use (you could never fill all that up). And they are the partitions you should join together (just delete one, and then resize the other to fill the space)
Also you should resize your NTFS partition to take up that extra 902MB of unallocated space.


So basically you want it to look like this

"
/dev/sda1   ntfs        146.5 GiB
/dev/sda2   ext3        72.29 GiB
/dev/sda3   extended     3.62 GiB
/dev/sda5   linux-swap   3.62 GiB
/dev/sda4   ext3        11.46 GiB
"
(the numbers in the upper figure are just estimates)


C@RL

---

### Post by adamogardner on 2008-08-17
> **carlinuxlearner said:**
>  And they are the partitions you should join together (just delete one, and then resize the other to fill the space)
Also you should resize your NTFS partition to take up that extra 902MB of unallocated space.

C@RL

easier said than done  but this is the goal.  exactly.

---

### Post by carlinuxlearner on 2008-08-18
If you use the Ubuntu Live disk, you can use "gparted" with that partitioner you can just right click on the partition (like say, NTFS) and click resize, then just drag the little rectangular box to fill in the extra space.

      And for the swap partitions, just right click, unmount, right click and delete the second one (/dev/hda6), then right click, resize the first one (/dev/hda5) like you did the NTFS partition.

      you could also use the [gparted live disk]("http://gparted.sourceforge.net/download.php") (if you don't want to download Ubuntu (assuming you don't already have it)

C@RL

---

### Post by adamogardner on 2008-08-18
> **carlinuxlearner said:**
> If you use the Ubuntu Live disk, you can use "gparted" with that partitioner you can just right click on the partition (like say, NTFS) and click resize, then just drag the little rectangular box to fill in the extra space.
And for the swap partitions, just right click, unmount, right click and delete the second one (/dev/hda6), then right click, resize the first one (/dev/hda5) like you did the NTFS partition.C@RL

I tried this before.  so I boot from live cd?  or stick it in when running? (not an easy thing to do unless your carrying the computer with you)
what will I see?  do I have to start ubuntu then use gparted or is g-parted in the first menu of options?  the rest sounds easy.  can I shrink my vista partition?  I just defragged it or did my ubuntu install intelligently partition the spaces and I should leave that alone?  There is that empty space from hp recovery too.  I copied it to disk and deleted that whole thing.  Was that stupid?  I should pull ubuntu unto that?  or windows into that making it bigger?  Ubuntu wors great in the small space it has  is the sda4 slot enough for arch?  or anythting for that matter?

---

### Post by kansasnoob on 2008-08-18
If you shrink Vista with Gparted there's a good chance you'll need to fix the mbr and boot:

[http://www.winvistatips.com/fix-mbr-a116.php](http://www.winvistatips.com/fix-mbr-a116.php)

No disc? No problem:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

But I always use Vista's own tools to resize Vista partitions:

[http://www.ehow.com/how_2262528_extend-ntfs-partitions-windows-vista.html?ref=fuel&utm_source=yahoo&utm_medium=ssp&utm_campaign=yssp_art](http://www.ehow.com/how_2262528_extend-ntfs-partitions-windows-vista.html?ref=fuel&utm_source=yahoo&utm_medium=ssp&utm_campaign=yssp_art)

As far as combining/sharing SWAP (or even resizing/moving Ubuntu partitions) you may have to make some tweaks to the uuid:

[http://ubuntuforums.org/showthread.php?t=879192](http://ubuntuforums.org/showthread.php?t=879192)

It's all pretty simple.

---

### Post by kansasnoob on 2008-08-18
> so I boot from live cd? or stick it in when running?

Gparted needs to be run from the live CD! You'll find it under System > Administration > Partition Editor. One of my initial stumbling blocks was not realizing that I had to right click whatever swap partition I was working on and tick swapoff. This can also lock extended partitions.

Basically if there is a "keyring" towards the left side of the partition in the Gparted gui it can't be moved/resized/deleted, etc.

---

