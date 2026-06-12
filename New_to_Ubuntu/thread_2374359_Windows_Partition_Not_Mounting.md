---
title: "Windows Partition Not Mounting"
date: 2017-10-15
forum: New to Ubuntu
---

### Post by szacpp on 2017-10-15
Hello Everyone,
I'm using Dell n5010 Laptop...HDD 320GB...HDD Partitioned are 5...I reinstall dual boot ubuntu 14.04...it was not detecting Windows OS...when I installed first time. it was detecting Windows OS partition...to solve detecting windows os problem i searched forums and apply diffrent methods like "sudo os-prober", "fdisk -l" and gparted etc.
when I executed gparted it destroyed windows bootloader...so windows is not booting now...then i used disks utility and changed windows partition type to NTFS after restart ubuntu is not mounting  for some reason i don't know. but my windows OS partition is showing in disks utility not mounted...
here is the image of disks utility.
 [ATTACH=CONFIG]277128[/ATTACH]   

only three partitions are mounting as you can see in above pic
now gparted is not showing any partitions except unallocated space 397GB

here is fdisk -lu result
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000559cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   246019409   123009673+  42  SFS
/dev/sda2       246019410   373286339    63633465   ee  GPT
/dev/sda3       373286340   625140399   125927030   42  SFS
/dev/sda4   *           0           0           0    0  Empty

Disk /dev/sdb: 3963 MB, 3963617280 bytes
255 heads, 63 sectors/track, 481 cylinders, total 7741440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0041cb2c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7741439     3869696    c  W95 FAT32 (LBA)


```

My Question is how can I mount Windows OS partition?

Thanks in advance.

---

### Post by ajgreeny on 2017-10-15
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and should give us some clues about what is on your computer at present and how best to proceed.

However, a search has shown that the SFS filesystem id that shows on your sda1 and sda3 is the Microsoft dynamic partition identity shortcut, and I am aware that such partitions are invisible to Linux, hence probably your problem.

Regrettably I do not have any answers for you about solving the problem but I hope others may be able to help so just keep looking back here.

---

### Post by szacpp on 2017-10-15
Thanks [**[COLOR=#C61919][B]ajgreeny**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=27747") for your response.
here is my boot-repair summary
[http://paste.ubuntu.com/25745656/](http://paste.ubuntu.com/25745656/)
> However, a search has shown that the SFS filesystem id that shows on  your sda1 and sda3 is the Microsoft dynamic partition identity shortcut,  and I am aware that such partitions are invisible to Linux, hence  probably your problem.

NO sda1 and sda 3 is visible but  WinOS partition (/dev/sda4) is not mounting  as above picture showed. I want to recover or mount /dev/sda4, that partition has some important files. 

please help.

---

### Post by 0N3 on 2017-10-15
Are you using windows 10 on the partition not mounting? If so by any chance and have you fast startup turned on?

---

### Post by oldfred on 2017-10-15
SFS is Windows dynamic partitions. Somewhat like LVM where logical partitions are inside physical partitions.
It seems Ubuntu finally has a driver that will see dynamic partitions, but it is proprietary to Microsoft and not recommended even if just using Windows.

You show sda4 as empty. And your sda3 SFS is the last physical partition on drive and uses all the space to the end of the drive.
You data may be inside the sda3 physical partition.

General rule is to use Linux tools for Linux & Windows tools for Windows. 
Or gparted to edit Linux partitions and Windows own or third party tools for NTFS.

Somehow you have sda4 and it has boot flag.
Boot flag should only be on the Windows bootable partition. Grub does not use boot flag.

You also show a gpt partition.
MBR and gpt do not mix, you have one or the other as entire drive must be MBR or entire drive must be gpt.
And Windows only boots from MBR partitioned drives with BIOS. And only from gpt partitioned drives with UEFI.

New UEFI systems using gpt have a protective MBR, and normally have one entry saying gpt, so old partition tools do not see drive as blank when really gpt. So gpt entry is only for one partition on gpt drives. You should not see it on MBR drives, except in rare case of hybrid drives which are not recommended but used by older EFI Macs booting Windows in BIOS mode.

Probably best to use Windows third party tools to correct drive. They can undo dynamic and should work better than Windows own partitioning tools.
       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 
   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by szacpp on 2017-10-15
Thanks ON3 for response.
> Are you using windows 10 on the partition not mounting? If so by any chance and have you fast startup turned on?
No Im using windows 7

---

