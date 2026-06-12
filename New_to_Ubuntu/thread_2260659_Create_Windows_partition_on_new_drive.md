---
title: "Create Windows partition on new drive"
date: 2015-01-13
forum: New to Ubuntu
---

### Post by bob_t2 on 2015-01-13
I am running unix on a ssd drive and it works fine.
I added a second drive and tried to install Windows 7 from the original install dvd.
Windows sees the partitions in my unix drive and shows the new ssd as totally unallocated.
When I select the new SSD to install windows on I get a message saying drivers are needed.

Is there some way I could create a Windows partitions in unix (gpart?)

Thanks
bob

---

### Post by deadflowr on 2015-01-13
Well, I don't know about unix, but in Ubuntu you can download gparted, open it and in the top corner toggle the hard drive to show the one you want to work on.
Then go to the menu area and find the dropdown for Create new partition table, then find the entry for New, and in the popup dialog box mark you can make the changes you need, resize, make it an ntfs system, et al.
When all is set click OK, and then in the main gparted window click on Apply Operations.
You'll at least have an ntfs system in place,
But then again, I do not know what *drivers needed* might mean, so there is that point to look at...

---

### Post by grahammechanical on 2015-01-13
It will be possible to create a partition but then you will need to use the Windows install disk to format the partition. And with a Windows formatted partition or partitions available the Windows installer should see it and allow you to install Windows on to that partition.

At least that was the procedure that I had to follow when I installed Windows 8 preview edition. And that is the limit of my Windows experience. Unless you want advice on Windows 98. :)

Regards.

---

### Post by oldfred on 2015-01-14
Did you install Ubuntu in UEFI or BIOS boot mode?
 And then you must boot Windows 7 installer in same boot mode. 
If UEFI you have to copy to flash drive and do some minor updates to make it UEFI bootable.

Windows is not good about seeing Linux partitions. In BIOS mode it often overwrites the partition table and leaves off Linux partition in partition table. And in BIOS mode Windows must be installed to a primary partition, formatted NTFS with the boot flag.

---

