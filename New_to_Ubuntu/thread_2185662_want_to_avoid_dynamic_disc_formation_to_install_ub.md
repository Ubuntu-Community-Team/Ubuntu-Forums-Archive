---
title: "want to avoid dynamic disc formation to install ubuntu"
date: 2013-11-03
forum: New to Ubuntu
---

### Post by albaqui on 2013-11-03
[COLOR=#000000] have issue in installation of Ubuntu in Windows 7. I have already 4 basic discs, System, C large, Recovery and HP_Tools. I wanted to install Ubuntu in partitioned C. When I partitioned it became 5 disks and became dynamic which I don't want. How can I install Ubuntu Without making dynamic discs.[/COLOR]

[COLOR=#000000]Thanks[/COLOR]

---

### Post by deadflowr on 2013-11-03
Don't install it via [WUBI]("https://help.ubuntu.com/community/Wubi") if you want to avoid dynamic disks.
Do a proper dual-boot
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2013-11-03
If you did convert to dynamic you have to undo that first. 

 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by albaqui on 2013-11-03
Thank you for email. As I mentioned that big partition C is now under Windows 7. If I partition it then it would be 5. Other 3 partitions are important. So how to do it. To be honest I am new. So can you help me a bit more precisely, step by stem. I appreciate.
 
Thanks

---

### Post by bcbc on 2013-11-03
> **deadflowr said:**
> Don't install it via [WUBI]("https://help.ubuntu.com/community/Wubi") if you want to avoid dynamic disks.
Do a proper dual-boot
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Wubi will never result in dynamic disks.

There are a lot of good reasons to avoid Wubi, but that's not one of them.

---

### Post by Mark Phelps on 2013-11-03
>  So can you help me a bit more precisely, step by stem. I appreciate.

Oldfred's post already has the steps in the link under this question: My laptop already has 4 primary partitions: how can I install Ubuntu?

---

### Post by albaqui on 2013-11-03
Thanks a lot. I hope I can do it following you guy's instruction. Thank you once again.

---

### Post by mastablasta on 2013-11-04
after removing dynamic partitioning...
i would just like to say that regarding this link: 
My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/14982...install-ubuntu]("http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu")


i opted to use Partition Wizard MiniTool instead. i changed the system partition (c:\) into extended (secondary) and then shrank it. the emtpy space that was left there was picked up by linux as i told it to install there. i kpet the HP tools - the HP linux (fastboot thingy), HP recovery and boot partition. all intact. i didn't delete anything or move anyhtign arround (as i see often suggested). I can restore to factory settings if i needed to.

i still made a System recovery disk as well as full disk image using external USB drive and Redo backup. just in case something went wrong. but it didn't.

---

### Post by coffeecat on 2013-11-04
> **mastablasta said:**
> 
i opted to use Partition Wizard MiniTool instead. i changed the system partition (c:\) into extended (secondary) and then shrank it.

I think you mean logical partition, but that's a creative way of doing it. With the Windows boot partition on a primary partition, Windows will still boot.

Changing a primary partition into a logical within constraints imposed by the MBR partition table is also possible with [Fixparts]("http://www.rodsbooks.com/fixparts/"). I might try that as an experiment on my HP netbook - restore the machine to its default factory condition and see if that works using Fixparts.

---

