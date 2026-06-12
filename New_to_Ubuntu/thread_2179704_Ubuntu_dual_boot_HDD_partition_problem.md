---
title: "Ubuntu dual boot HDD partition problem"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by Weedoobs on 2013-10-09
Well, basicly, I have Win 8 64 bit, and I want to install dual boot Ubuntu. I tried couple of times but Ubuntu seems to not recodnise my partitions, only shows as 750gb free space. I tried backtrack and fedora, and It's the same problem. Then i tried to defrag, check for errors etc, did some magic with fixparts and gpart and now it shows SOME of the partitions, but shows them as free space and some error on them. It's kinda messy. Can you help me please? <3 Thank you <3

[IMG]http://store.picbg.net/pubpic/5E/57/1057202eb3645e57.png[/IMG]

---

### Post by sandyd on 2013-10-09
Hi, have you tried resizing the Windows partitions from Windows itself before installing Ubuntu?

---

### Post by Weedoobs on 2013-10-09
Yes, this is my Windows, as you can see, in Ubuntu i don't see the free space and driver U:
[IMG]http://store.picbg.net/pubpic/5A/12/aa80f992e8f75a12.png[/IMG]

---

### Post by sandyd on 2013-10-09
Can you post the output of
```

sudo fdisk -l
```

Thanks

---

### Post by westie457 on 2013-10-09
Looking at your screen shot you haave exceeded the 4 primary partition limit of a MSDOS partition table. All of your partitions are now 'Dynamic' and consequently nothing can be installed to that hard drive, not even Windows.

Best course of action for you right now is for you to boot into Windows and get all of your personal files backed-up to DVD\USB Flash drive or external drive.
Re-partition the drive and reinstall Windows from scratch. Then take another look at installing Ubuntu.

You might possibly give this a try, no guarantees that it will work. [http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

### Post by Weedoobs on 2013-10-09
[IMG]http://store.picbg.net/pubpic/73/F6/ee7e0e2bff0073f6.png[/IMG]

---

### Post by sandyd on 2013-10-09
> **Weedoobs said:**
> [IMG]http://store.picbg.net/pubpic/73/F6/ee7e0e2bff0073f6.png[/IMG]

yep - its not ntfs - its SFS, you will have to convert back to a normal disk first before you can install.

---

### Post by Weedoobs on 2013-10-09
So i must do as [COLOR=#000000]westie457 said? And I'm ok?[/COLOR]

[COLOR=#000000][/COLOR]

---

### Post by sandyd on 2013-10-09
> **Weedoobs said:**
> So i must do as [COLOR=#000000]westie457 said? And I'm ok?[/COLOR]

[COLOR=#000000][/COLOR]
Yes, make sure everything is backed up

---

### Post by Weedoobs on 2013-10-09
Well the things from the link did not work (I have no such options in disk manager or EaseUS) So i guess I will preinstall, but how to make sure to create basic, and not dynamic?

[IMG]http://store.picbg.net/pubpic/31/92/f043c2b3a92c3192.png[/IMG]

---

### Post by oldfred on 2013-10-09
It is when you try to create more than 4 primary partitions with Windows. It uses dynamic not the extended partition with an unlimited number of logical partitions.

Some other tools.
       Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)


 Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

---

### Post by madankrishna2012 on 2013-10-10
> **Weedoobs said:**
> Well the things from the link did not work (I have no such options in disk manager or EaseUS) So i guess I will preinstall, but how to make sure to create basic, and not dynamic?

[IMG]http://store.picbg.net/pubpic/31/92/f043c2b3a92c3192.png[/IMG]

   Hi Weedoobs,

I also went through the same problem as urs while dual booting. Here are the steps I followed to make it work.
 
[LIST=1]
[*]Take all the data backup in external HDD or DVD or any other 	media because you have to delete all the drive to convert it from 	dynamic to basic.

[*]Now boot the dive with the windows boot-able CD and delete 	all the partition and make only 4 partition (if you make more 	windows will convert all the partition into dynamic as before). Two 	partition for Windows (System Boot & Windows C Drive), One for 	the other files to be stored in your computer and last one for the 	Ubuntu partition.

[*]Install Window first as you do before. After you have 	finished installing the Windows now boot from the Ubuntu CD or 	Bootable pendrive.

[*]Install the Ubuntu in the Last partition (as you cannot make 	more than 4 partition).
[/LIST]
 


 I think this will work out for you for the dual booting the PC.
 


 If you come across any problem regarding boot as I have encountered while booting (after installing ubuntu the PC directly boot from Ubntun without giving the option for the user) do search for the Boot- Repair and follow the instructions. I have also given the link of it below if you need it.
 


 [https://help.ubuntu.com/community/Boot-Repair]("https://Hi Weedoobs,  I also went through the same problem as urs while dual booting. Here are the steps I followed to make it work. 1. Take all the data backup in external HDD or DVD or any other media because you have to delete all the drive to convert it from dynamic to basic. 2. Now boot the dive with the windows boot-able CD and delete all the partition and make only 4 partition (if you make more windows will convert all the partition into dynamic as before). Two partition for Windows (System Boot & Windows C Drive), One for the other files to be stored in your computer and last one for the Ubuntu partition. 3. Install Window first as you do before. After you have finished installing the Windows now boot from the Ubuntu CD or Bootable pendrive. 4. Install the Ubuntu in the Last partition (as you cannot make more than 4 partition).  I think this will work out for you for the dual booting the PC.  If you come across any problem regarding boot as I have encountered while booting (after installing ubuntu the PC directly boot from Ubntun without giving the option for the user) do search for the Boot- Repair and follow the instructions. I have also given the link of it below if you need it.  https://help.ubuntu.com/community/Boot-Repair")

 
Madan Pradhan

---

### Post by Weedoobs on 2013-10-10
But when I install Ubuntu i need to make /swap, /root, /home and /boot, that's more partitions?

---

### Post by oldfred on 2013-10-10
Most desktop installs do not need /boot. But Linux works just fine from logical partitions. You create logical partitions in one of the primary partitions that becomes an extended partition. Windows is the one that only works from primary partitions.

       Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by madankrishna2012 on 2013-10-12
> **Weedoobs said:**
> But when I install Ubuntu i need to make /swap, /root, /home and /boot, that's more partitions?

You need that but its an option (you can make it or not its your choice). But in this case of dual boot you should not create one as you have mentioned. Do install the Ubuntu as I have mentioned in my previous post, it will help you.

Madan Pradhan

---

