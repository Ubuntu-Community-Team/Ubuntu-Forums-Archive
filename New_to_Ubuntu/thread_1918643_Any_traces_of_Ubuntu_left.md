---
title: "Any traces of Ubuntu left ?"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by desgnr on 2012-02-01
How do i find if Unbutu is on my HD after i removed it ?


I just installed Windows 7
I had about 4 g of space left.
I only added Microsoft Office 2007,Quicken & WinZip
All should total about 300 mg.
I looked & only had 900 mg. free
I selected to delete system restore except the last restore point because this always freeded up space on my PC
Now i only have 700mg.
I tried it again ,now i only have 300 mg.
How can i be losing space every time i try it .
Also in the past i was having trouble installing Ubuntu.
Then i decided on Windows 7 & when i installed it ,it didn't give me the Option to
 format the drive,it just started installing.
Is the any chance there past files or os on the SSD ?
All sugestion's greatly appreciated.

If you had Ubuntu installed there is a very good chance that it is still there.
 Use you USB flash drive to boot into Ubuntu & take a look at you HD to see what is there. 
You may very well have a Win 7 & a Ubuntu partition. Linux does a very good job of seeing other types of 
partitions. 
Ubuntu will let you delete & change the format from ext 4 to NTFS.

If i boot into Ubuntu how will i know if anything is on the ssd & not just the program on the Flash drive

you might be better off asking these questions in our Ubuntu section not the Mini 9 section

---

### Post by Elfy on 2012-02-01
Can you specify please what are questions here and what are quotes from somewhere else.

Thanks :)

---

### Post by desgnr on 2012-02-01
I had it posted on Dell Mini Forum & they suggested i ask here how to tell if anything is left from the Ubuntu installation that was uninstalled.

---

### Post by Paqman on 2012-02-01
Just do as they suggest. Boot up into your Live CD/USB and open Gparted. This will show you what partitions you have on the disk. Ubuntu will have created partitions listed as ext4, swap and extended. You can go ahead and delete them all, then expand your NTFS partition/s into the free space.

Unless you installed Ubuntu using Wubi, in which case it wouldn't have made a partition, and you can be sure that Ubuntu is gone if you uninstalled it from within Windows.

---

