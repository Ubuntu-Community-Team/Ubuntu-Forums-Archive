---
title: "Creating disk partition in Windows 7 for Ubuntu; file system type?"
date: 2013-04-21
forum: New to Ubuntu
---

### Post by asmith2306 on 2013-04-21
Hi,

I have a 320GB HDD on my laptop.  It has two partitions C:, which has windows 7 installed on it and D:, which is free to use.  Both have 150GB total space.  I used windows disk management to make another partition out of D.  I am in the wizard now and have been asked what file system type to use for the new volume, exFAT or NTFS?  Which is ok to use for Ubuntu?  I have been using wubi for a while and want to have a proper installation of Ubuntu alongside windows.

Thanks,
Alan

---

### Post by prodigy_ on 2013-04-21
You don't have to create any partitions for Linux in Windows. Any Linux installer can handle that. Though if you want to create partitions in advance - it's OK. Leave them unformatted (you can't install Ubuntu on NTFS without Wubi).

---

### Post by Impavidus on 2013-04-21
Win7 cannot create the partition type you need for Ubuntu. You can leave the space unallocated and have the installer create an Ubuntu partition, or let the installer itself delete any empty windows partition. Just make sure you don't use the Ubuntu installer to shrink your windows partition.

---

### Post by oldfred on 2013-04-21
Whatever you do, do not create partitions in Windows as it converts to dynamic partitions which do not work with Linux. Use Windows to shrink the Windows install to make free space and reboot to let it make repairs due to new size. Then use installer to install into unallocated space if you have not used all 4 primary partitions.

       Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

---

### Post by prodigy_ on 2013-04-21
> **oldfred said:**
> Whatever you do, do not create partitions in Windows as it converts to dynamic partitions which do not work with Linux.
I think you're a bit confused here, mate. :) Windows does not convert individual partitions (logical volumes) to dynamic. You either convert the entire physical disk or nothing. And Windows does not convert automatically. I have several HDDs partitioned with Win7 and they're all "basic disks" and I certainly do have Linux installed on them as well.

---

### Post by oldfred on 2013-04-21
It used to be that Ubuntu would not even install once a drive was converted from basic to dynamic. From Linux you still see the partitions, but the dynamic is an overlay something like LVM in Linux. It seems to only happen when you reach the 4 primary partition limit and Windows does not convert to an extended, but then goes dynamic. Since almost all Windows 7 systems have all 4 primary any new partition then converts to dynamic.

I am not sure how they did it but we have seen users post with one or two partitions that are still dynamic. Maybe they deleted some with one of the Windows third party partition tools that do work with dynamic partitions. And if space was on drive they then installed Ubuntu but grub does not install and they cannot mount NTFS partitions.

Windows even now converts gpt partitioned drives to dynamic called LDM, but with gpt you can create up to 128 partitions as standard.

---

### Post by prodigy_ on 2013-04-22
Hmm, I see. Well, I've never tried to create more than 4 primary partitions on an MBR drive. I guess you still get a confirmation dialog before it's actually converted. Need to check. :)

---

### Post by oldfred on 2013-04-22
It supposedly says it will convert from basic to dynamic, but does not tell you that you cannot turn back.
I think some of the cases I have seen were where users shrunk Windows creating unallocated space. But then wanted to create partitions for Ubuntu not knowing that they could not create Linux partitions and Windows just changes to dynamic.

       Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx")

            Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)

---

