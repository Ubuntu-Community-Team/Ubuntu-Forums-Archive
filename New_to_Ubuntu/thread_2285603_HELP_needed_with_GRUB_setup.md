---
title: "HELP needed with GRUB setup"
date: 2015-07-07
forum: New to Ubuntu
---

### Post by rashidmgmail.com on 2015-07-07
Hello.

I've been playing around with W7 and Ubuntu on one disk (/dev/sdc) and, finally, ruined bootmanager. While installing Ubuntu, I've chosen boot partition to be the same as W7's partition, Ubuntu didi boot. After that I tried to reinstall Microsoft's MBR back onto W7 partition and now neither MBR, nor GRUB.

All I have is a Ubuntu 15.04 installation usb key.

What I want is to have Microsoft's MBR to be the default boot manager for both W7 and Ubuntu (I was intending to accomplish that by running some utility from inside the Windows -- which I cannnot boot into now).

So the minimal result for me would be to reinstall MBR boot W7. And the maximum result is to use it to boot both W7 and Ubuntu. My partition info is stored here [http://paste.ubuntu.com/11833426](http://paste.ubuntu.com/11833426)
Any help is highly appreciated, thank you!

---

### Post by grahammechanical on 2015-07-07
Here is the situation as I see it. The Windows 7 boot files are in sdc1 but the grub boot loader is in sdc and is will looking at /boot/grub/ for its boot configuration file but Ubuntu is not installed.

You have an extended partition (sdc2) but you do not have a logical partition inside the extended partition with Ubuntu in the logical partition. That logical partition would have been either sdc3 or sdc4 which are both missing. The only logical partition is sdc5 which is swap.

So, there are no Grub configuration files from which to create a boot menu and in turn direct Grub to the boot files of either Windows 7 or Ubuntu.

You only have 1 OS on the machine and it is Windows 7 and it has a boot loader installed in sda and sdb but not sdc. In theory, you should be able to enter the BIOS and direct it to look at either the first (sda) or second (sdb) hard disk and that might boot windows 7 for you. Or you should restore the Windows boot loader to sdc.

Regards.

---

### Post by rashidmgmail.com on 2015-07-07
> **grahammechanical said:**
> ...
You only have 1 OS on the machine and it is Windows 7 and it has a boot loader installed in sda and sdb but not sdc. In theory, you should be able to enter the BIOS and direct it to look at either the first (sda) or second (sdb) hard disk and that might boot windows 7 for you. Or you should restore the Windows boot loader to sdc.

Regards.

Thank you. Somehow I managed to destroy Ubuntu's Ext4 partition on sdc* partition.

---

### Post by oldfred on 2015-07-09
If you used Windows to modify partitions, it does not see Linux partitions, and rewrites partition table without the Linux partition.

You show unallocated space in the extended partition which probably was your Linux partition. From live installer add testdisk and restore the missing partition. Some have just been able to boot with only the partition restore. Others needed to reinstall grub.

       Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You also show SFS on sdb. That is Windows proprietary dynamic partitioning. It does not work with Linux nor even some Windows repair tools. Best to undo that.
       
 Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

