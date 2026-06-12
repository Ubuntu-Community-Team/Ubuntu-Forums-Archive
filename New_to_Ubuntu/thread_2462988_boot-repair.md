---
title: "boot-repair"
date: 2021-05-31
forum: New to Ubuntu
---

### Post by bitsc on 2021-05-31
hello there im new from windwos  and now im trying to install ubuntu now after install we need boot repair 
after repair it show this can not solved?!
[https://paste.ubuntu.com/p/c2F3BJ6Trn/](https://paste.ubuntu.com/p/c2F3BJ6Trn/)

thank you for help

---

### Post by grahammechanical on 2021-05-31
We need more explanation. Please provide information about your computer and the operating systems on it. Also you need to tell us why you needed Boot Repair in the first place. Also you need to tell us what is happening when you switch on the computer?

Boot Repair claims that the re-install of the Linux boot loader (Grub) was successful. So, what is happening when you switch on the computer? Boot Repair says you should do this:

> Please do not forget to make your BIOS boot on sdb (ATA SAMSUNG HD105SI) disk!

Have you done that? Have you entered the BIOS setting utility and set the Samsung hard drive first in the boot priority? Is the WDC hard drive still got the boot priority? Is Ubuntu loading? Is Windows 7 loading?

How did you create the partition to put Ubuntu in (sdb7)? We use Windows tools to delete, shrink, move, create Windows partitions and then we run Windows defrag. We use Linux tools to create, shrink, move, delete Linux partitions. If we do not do this we get problems.

Boot Repair also says this:

> SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.

If I remember correctly, Microsoft dynamic discs/partitions are incompatible with installing Linux distributions such as Ubuntu. It is a long time ago that people were wanting to dual boot Ubuntu with Windows 7 that I have forgotten a lot that I learnt from those days.

[https://docs.microsoft.com/en-us/windows/win32/fileio/basic-and-dynamic-disks](https://docs.microsoft.com/en-us/windows/win32/fileio/basic-and-dynamic-disks)

Regards

---

### Post by oldfred on 2021-05-31
[http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS in fdisk, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx) & 
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) & 
[http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html](http://manpages.ubuntu.com/manpages/trusty/man1/ldmtool.1.html)

---

