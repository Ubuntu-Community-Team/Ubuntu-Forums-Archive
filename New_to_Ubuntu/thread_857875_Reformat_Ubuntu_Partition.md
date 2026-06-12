---
title: "Reformat Ubuntu Partition"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Gabzilla on 2008-07-12
I have a dell xps 400 and it dual boots XP and Ubuntu. I had my boyfriend install ubuntu since I wasn't sure what to do and somehow, the partition for Ubuntu is bigger than my XP partition. I just want to know how to make the Ubuntu partition smaller and the XP partition bigger. Right now, my XP partition is about 45GB and my Ubuntu one is I THINK abou 90GB. I'm a newbie so I'd appreciate simple directions. I'm extremely new to Ubuntu and I know almost nothing technical about it except that I like it a lot. :D

---

### Post by sandysandy on 2008-07-13
u can use gparted to resize partitions.

have a look here

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by Jim! on 2008-07-13
> sudo apt-get install gparted
> sudo gparted 

Just a quick way of installing it;) Gparted is excellent.

---

### Post by cdtech on 2008-07-13
I would use the "Live CD gparted" to resize your partitions. I used it to resize mine and it worked like a charm.

---

### Post by Gabzilla on 2008-07-13
> **cdtech said:**
> I would use the "Live CD gparted" to resize your partitions. I used it to resize mine and it worked like a charm.

I did that and the Ubuntu "ext3" partition is INSIDE some kind of bigger partition alongside the linuxswap... The problem is that this bigger partition is locked and it's preventing me from making my XP partition bigger. Is there any solution to this?

If there's no solution, then I wouldn't mind uninstalling Ubuntu. I want the previous version of Ubuntu. My wireless doesn't work on the latest one, but I found out that it works on the previous version. So if someone could tell me how to uninstall this version or downgrade to the previous version that'd be amazing! :D

---

### Post by WRDN on 2008-07-13
Depending upon the structure of the partitions, it may not be possible to resize both partitions easily.
Please enter the Terminal (Applications > Accessories > Terminal) and type "fdisk -l". Then, post the output here. Note that, if this is typed and no output is given, type, "sudo fdisk -l" (thats a lower case L, not the number 1).

It is important to know this because, you can only resize a partition into space to its extreme left/ right.
For example, if you had the following partitions:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4

If, for sake of example, the Ubuntu OS was stored on sda2, you could then shrink this. However, you could only use this space to add to the sda1 and sda3 partitions. Due to the fact sda4 is seperated and it is not continuing from sda2, it is not possible to use the extra space to resize sda4.

---

### Post by Gabzilla on 2008-07-13
> **WRDN said:**
> Depending upon the structure of the partitions, it may not be possible to resize both partitions easily.
Please enter the Terminal (Applications > Accessories > Terminal) and type "fdisk -l". Then, post the output here. Note that, if this is typed and no output is given, type, "sudo fdisk -l" (thats a lower case L, not the number 1).

It is important to know this because, you can only resize a partition into space to its extreme left/ right.
For example, if you had the following partitions:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4

If, for sake of example, the Ubuntu OS was stored on sda2, you could then shrink this. However, you could only use this space to add to the sda1 and sda3 partitions. Due to the fact sda4 is seperated and it is not continuing from sda2, it is not possible to use the extra space to resize sda4.


Disk /dev/sda: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe686f016 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           4       32098+  de  Dell Utility 
/dev/sda2   *           5        6498    52163055    7  HPFS/NTFS 
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ... 
/dev/sda4            6499       18846    99185310    5  Extended 
/dev/sda5            6499       18469    96157026   83  Linux 
/dev/sda6           18470       18846     3028221   82  Linux swap / Solaris 
 
Partition table entries are not in disk order

---

### Post by sandysandy on 2008-07-13
have a look at the gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

can u post a snapshot from gparted showing the partitions.

regards

---

### Post by WRDN on 2008-07-13
> **Gabzilla said:**
> Disk /dev/sda: 160.0 GB, 160000000000 bytes 
255 heads, 63 sectors/track, 19452 cylinders 
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0xe686f016 
 
   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1           4       32098+  de  Dell Utility 
/dev/sda2   *           5        6498    52163055    7  HPFS/NTFS 
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ... 
/dev/sda4            6499       18846    99185310    5  Extended 
/dev/sda5            6499       18469    96157026   83  Linux 
/dev/sda6           18470       18846     3028221   82  Linux swap / Solaris 
 
Partition table entries are not in disk order

Thanks.
According to the output, Windows is on sda2 and Linux is on sda5. 
This leads me to believe that, you will not be able to easily resize the partitions to make one smaller, and use the extra space for another.
As sandysandy said though, please take a screenshot of GParted as it will give a clearer image. Thanks.

---

### Post by Gabzilla on 2008-07-13
[IMG]http://www.isarapix.org/pix50/1215938560.png[/IMG]

Hope that helps.

---

### Post by kansasnoob on 2008-07-13
> /dev/sda1 1 4 32098+ de Dell Utility
/dev/sda2 * 5 6498 52163055 7 HPFS/NTFS
/dev/sda3 18847 19452 4867695 db CP/M / CTOS / ...
/dev/sda4 6499 18846 99185310 5 Extended
/dev/sda5 6499 18469 96157026 83 Linux
/dev/sda6 18470 18846 3028221 82 Linux swap / Solaris 

OK, your numbers are different than mine, but look at my Gparted screenshot:

[ATTACH]77582[/ATTACH]

You see my sda2 should look like your sda4, our sda5 & sda6 should look about the same.

Now if I want to resize my sda2 (equivalent to your sda4) I must first resize sda5, save that change, and then resize sda2 (again akin to your sda4). Now to accomplish this any partition I'm resizing must be "unmounted", thus the need to use either a Gparted Live CD or to use Gparted from your Ubuntu Live CD.

Only after resizing the Ubuntu partitions (sda4, 5, and 6 in your case) would I be able to resize the Windows partition which appears to be sda2.

Now, if you decide to downgrade from 8.04 to 7.10 I'm sorry to say that you'll have to remove 8.04 completely and then install 7.10. You can do that just like resizing only choose to delete sda5, then 6, and then 4. Again any partition you work on must be unmounted!

Just don't delete sda1, 2, or 3 as these all appear to be related to your Dell/Windows install! And be patient when resizing!

I'm inclined to think that your wireless issue can be worked out.

---

### Post by Gabzilla on 2008-07-13
> **kansasnoob said:**
> OK, your numbers are different than mine, but look at my Gparted screenshot:

[ATTACH]77582[/ATTACH]

You see my sda2 should look like your sda4, our sda5 & sda6 should look about the same.

Now if I want to resize my sda2 (equivalent to your sda4) I must first resize sda5, save that change, and then resize sda2 (again akin to your sda4). Now to accomplish this any partition I'm resizing must be "unmounted", thus the need to use either a Gparted Live CD or to use Gparted from your Ubuntu Live CD.

Only after resizing the Ubuntu partitions (sda4, 5, and 6 in your case) would I be able to resize the Windows partition which appears to be sda2.

Now, if you decide to downgrade from 8.04 to 7.10 I'm sorry to say that you'll have to remove 8.04 completely and then install 7.10. You can do that just like resizing only choose to delete sda5, then 6, and then 4. Again any partition you work on must be unmounted!

Just don't delete sda1, 2, or 3 as these all appear to be related to your Dell/Windows install! And be patient when resizing!

I'm inclined to think that your wireless issue can be worked out.

Thanks! I actually tried to delete those partitions but I couldn't. I tried to unmount them, but that option wasn't available to me. Is there any fix for that?

---

### Post by WRDN on 2008-07-13
I don't think you will be able to easily resize both partitions due to the layout. However, there is an alternative.
You could resize /dev/sda5 which has Linux on it. Take off whatever space you would have given back to Windows, then create a new partition and format it to NTFS. You can then use this for Windows, and you don't have to resize the Windows partition.

---

### Post by kansasnoob on 2008-07-13
> Thanks! I actually tried to delete those partitions but I couldn't. I tried to unmount them, but that option wasn't available to me. Is there any fix for that?

Are you using Gparted from a Live CD? You can't "unmount" if you're using Gparted from within your running Ubuntu OS.

---

### Post by Gabzilla on 2008-07-13
> **WRDN said:**
> I don't think you will be able to easily resize both partitions due to the layout. However, there is an alternative.
You could resize /dev/sda5 which has Linux on it. Take off whatever space you would have given back to Windows, then create a new partition and format it to NTFS. You can then use this for Windows, and you don't have to resize the Windows partition.

That's the thing. I can resize /dev/sda5 but I can't resize /dev/sda4 which I need to resize to expand the XP partition. So even if I tried to make a new partition and format it to NTFS, there'd be no room for it.

---

### Post by Gabzilla on 2008-07-13
> **kansasnoob said:**
> Are you using Gparted from a Live CD? You can't "unmount" if you're using Gparted from within your running Ubuntu OS.

I'm using Gparted from the Ubuntu Live CD.

---

### Post by sandysandy on 2008-07-13
as u can see sda5 (LINUX) & sda 6 (swap) are within the extended partitions sda 4. sda 2 is ur windows partition.

try to shrink sda 5 (Linux) to right to free some space in the extended partition sda4.

once free space is generated there in sda 4 u can shift it to right.

then increase sda2 to right to fill free space.

PLEASE use gparted live CD.

regards

---

### Post by kansasnoob on 2008-07-13
> **sandysandy said:**
> as u can see sda5 (LINUX) & sda 6 (swap) are within the extended partitions sda 4. sda 2 is ur windows partition.

try to shrink sda 5 (Linux) to right to free some space in the extended partition sda4.

once free space is generated there in sda 4 u can shift it to right.

then increase sda2 to right to fill free space.

PLEASE use gparted live CD.

regards

That should work!

---

### Post by Gabzilla on 2008-07-13
> **sandysandy said:**
> as u can see sda5 (LINUX) & sda 6 (swap) are within the extended partitions sda 4. sda 2 is ur windows partition.

try to shrink sda 5 (Linux) to right to free some space in the extended partition sda4.

once free space is generated there in sda 4 u can shift it to right.

then increase sda2 to right to fill free space.

PLEASE use gparted live CD.

regards


IT WORKED! :D Thanks so much!

---

### Post by UniverseA7X on 2008-07-14
Hi, I'm on the phone with the OP, and she just reinstalled 7.10 to get her wireless dongle supported, and at the boot screen, she's getting a grub error 15. Is there any fix for this. I'm on the phone with her right now.

---

