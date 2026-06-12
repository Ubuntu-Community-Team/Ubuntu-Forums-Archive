---
title: "GNU Grub issue"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by Crackow on 2013-04-03
After a clean reinstallation of Windows 7, I can't reinstall Grub2. Even after reinstalling my Linux distros, nothing doing. I have tried many things, but none so far have solved my problem. I have a laptop with 2 hard drives. Sda is my storage drive, while sdb is my system. At one point in time I reformatted my hard drive so that I had a boot partition to install to, but still nothing. Currently, I have Windows 7, Ubuntu, and Mint installed with extra space left over for Debian. My hard drive is fromatted as thus:
 unallocated (was Boot as Fat16) 650 MiB
/dev/sdb2 ntfs ExtraSpace 175Gib
/dev/sdb5 ntfs Windows 25GiB
/dev/sdb6 swap 2.25 GiB
/dev/sdb7 ext4 Ubuntu 10GiB
/dev/sdb8 ext4 Mint 10GiB
/dev/sdb9 ext4 Debian(unused) 10GiB
Please help me.

---

### Post by oldfred on 2013-04-04
We need lots of detail with multple drives and multple installs.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by AndyOpie150 on 2013-04-04
Until more help arives try and burn these to a cd:

[ Boot-Repair Disk]("http://sourceforge.net/p/boot-repair-cd/home/Home/")

[Hirens Boot CD]("http://www.hirensbootcd.org/") This has a virtual xp and Windows 7 OS that will let you run the chkdsk command.



Edit: Ninja'd by master oldfred

---

### Post by Crackow on 2013-04-05
Okay then. I've gotten Ubuntu up and running again. Thanks for that. Update-Grub recognizes Mint, but nothing past that. I tried to make a custom entry to run Windows 7, but it wouldn't work. Thanks again for your help.

[http://paste.ubuntu.com/5678704/](http://paste.ubuntu.com/5678704/)

---

### Post by oldfred on 2013-04-05
A Windows boot partition cannot be used by Linux and vice-versa.

It looks like you overwrote the Windows boot partition in sdb1 and now have no Windows boot files. Your Windows install is in sdb5 which is a logical partition. Windows only boots from primary partitions, so we cannot just repair your install in sdb5. 
You can either reinstall Windows into a primary partition, create a small 100MB NTFS boot partition with boot flag and repair it to have Windows boot files, or maybe rearrange partitions so sdb5 becomes a primary which then could be repaired to be directly bootable.

Fixparts may let you redefine sdb5 to be a primary and make all the other logical partitions inside the extended. This only works in your case as sdb5 is at the start of the extended and you have one more available primary partition.

       To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it.
Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

### Post by Crackow on 2013-04-06
I'll restore my sdb1 (designated as boot) as NTFS, and then install the Windows 7 MBR onto it. I will do this in a mo', but will this reopen access to my installation of Mint? Also, somehow boot-repair changed something in my system that it really should not have done. Although I was sure to not include my flash drive in any of the options given through it, now when I try to boot into my flash drive it opens the grub for my hard drive, and not the flash drive's. The grub.cfg on the device is unchanged, however. Can anyone explain this?

EDIT: Nevermind. I think I'll just reinstall everything. I would like to reorganize and possibly remove 7 completely. I will install Debian, but read up on Ubuntu commands so that I can be savvy with the easiest with Deb. I don't know why I've made this so complicated. Thank you for your help!

---

