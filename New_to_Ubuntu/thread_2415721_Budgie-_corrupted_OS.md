---
title: "Budgie- corrupted OS?"
date: 2019-03-30
forum: New to Ubuntu
---

### Post by xbccoffee on 2019-03-30
Hi.
Today I installed budgie.
I got error for ext4 mounting so i did xfs.
now i have the "mounting on /dev on /root/dev failed: input/output error"
did i corrupt ubuntu? if so, can i fix it?
thanks in advance.

---

### Post by Frogs Hair on 2019-03-30
Hello and Welcome !

What version have you installed, how have you installed, and on what computer ?

---

### Post by xbccoffee on 2019-03-30
> **Frogs Hair said:**
> Hello and Welcome !

What version have you installed, how have you installed, and on what computer ?

Hi!
I've installed 18.04 LTS by DVD and installed it on external hard drive (generic seagate hard drive)

I'm reviving a  dell inspiron 530 with the latest BIOS revision.

---

### Post by oldfred on 2019-03-30
Better to use ext4 and resolve that issue. Perhaps a drive issue, so format does not matter?

I have this in my notes, but may be older.
       if / or /boot not ext4, then insmod may be required in /EFI/ubuntu/grub.cfg & .mod file copied. Bug on xfs
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822)

---

### Post by xbccoffee on 2019-03-30
> **oldfred said:**
> Better to use ext4 and resolve that issue. Perhaps a drive issue, so format does not matter.
I have this in my notes, but may be older.
       if / or /boot not ext4, then insmod may be required in /EFI/ubuntu/grub.cfg & .mod file copied. Bug on xfs
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1652822)

Thanks! Just a question and a problem:
1. Do i need to remount or reinstall? How do I do that?

2.If i do ext4 on live media, it says that my disk is offset and performance is poor. remounting does nothing. continuing leads to an error saying no root directory found. i did it according  to the installation guide, the partitions are mounted correctly. Any help?

---

### Post by oldfred on 2019-03-30
Your installer is FAT32.
But full install is ext4 for / and FAT32 if UEFI for ESP, then if you want data partition(s), you probably can make those any format you want, but I have always used ext4.
For UEFI install, see link in my signature below.

---

### Post by xbccoffee on 2019-03-31
> **oldfred said:**
> Your installer is FAT32.
But full install is ext4 for / and FAT32 if UEFI for ESP, then if you want data partition(s), you probably can make those any format you want, but I have always used ext4.
For UEFI install, see link in my signature below.

Windows Vista Home Premium doesn't have a disk tool. Any alternatives?

Also, I have no idea what  a UEFI is, nor can I understand the guide :(

---

### Post by oldfred on 2019-03-31
If an old BIOS system, then UEFI does not matter, skip all that.
The installer is still FAT32, but for BIOS boots with syslinux, a Windows type BIOS boot loader. 
You have to select in BIOS to boot from USB flash drive. But my systems showed flash drive installer under the hard drive list, not any USB devices.

You can use gparted.
Newer Windows should use Windows tools for Windows, and Linux tools for Linux.
Gparted normally works on NTFS partitions that are not hibernated nor need repairs, but those rare times it does not, users blame Linux when it usually is a NTFS issue. So we alway suggest using Windows tools for Windows.

---

### Post by xbccoffee on 2019-03-31
> **oldfred said:**
> If an old BIOS system, then UEFI does not matter, skip all that.
The installer is still FAT32, but for BIOS boots with syslinux, a Windows type BIOS boot loader. 
You have to select in BIOS to boot from USB flash drive. But my systems showed flash drive installer under the hard drive list, not any USB devices.

You can use gparted.
Newer Windows should use Windows tools for Windows, and Linux tools for Linux.
Gparted normally works on NTFS partitions that are not hibernated nor need repairs, but those rare times it does not, users blame Linux when it usually is a NTFS issue. So we alway suggest using Windows tools for Windows.

Yeah I have old BIOS.

I've decided to reinstall it as my mounting was messed up and i didn't have any data.

So I formatted in ext4, only to get this:

The partition (insert all sdb partitions) starts at an offset of 3584 bytes of minimum alignment, causing poor performance.

My partition:

/boot= 500 MB (displayed as 469 MB though)
/=30 GB (29963 MB)
/swap=4596 MB (4.5 GB in my PC, displayed as 4563 MB)
/home=965044

Could you help? I'm getting really tired of errors and as a newbie this isn't giving me good first impressions of ubuntu.

---

### Post by oldfred on 2019-03-31
Up until Windows 7, all partitioning tools started sda1 at sector 63. 
Then it changed to sector 2048 for compatibility with new 4K drives & SSDs.
Linux tools like gparted changed soon after.
Poor performance would only apply if drive is newer 4K configuration. But best to convert now, to avoid all the warnings.
       
Partition does not start on physical sector boundary.
First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Post this:
       sudo parted /dev/sda unit s print 
    
 Most desktops do not need separate /boot partition. It becomes one more partition to manage to make sure it is not full.
A few old BIOS only could boot from first 137GB of a drive, but if using 30GB for / at beginning of drive and rest as /home then no /boot required.
Also new versions of Ubuntu use a swap file, so no swap partition required. But swap partition will be used if found during install.

---

### Post by xbccoffee on 2019-03-31
```
ubuntu-budgie@ubuntu-budgie:~$ sudo parted /dev/sdb unit s print
Model: Seagate Expansion+ (scsi)
Disk /dev/sdb: 1953525167s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 


Number  Start      End          Size         Type      File system  Flags
 1      65535s     97647149s    97581615s    primary   xfs          boot
 2      97712683s  1953467279s  1855754597s  extended
 5      97712685s  98630174s    917490s      logical   xfs
 6      98695710s  1953467279s  1854771570s  logical   xfs



```

That's my output. I changed it to sdb 'cause i'm installing it there.

Ignore the xfs. That was my original mounting (and problem). I can't save the new one (ext4) due to the error.

Also, I'm running Vista so the Windows 7 matters do not affect me.

Thanks for all the help so far! I'm a big noob at this, I know!

Also, should I *really* remove /boot? It says to create the partiton in the official Budgie install guide.

UPDATE: Removed /boot. Budgie now saying it's 1024 bytes (from 3000~) offset. Interesting.

---

### Post by xbccoffee on 2019-03-31
IT WORKED!!!

I got another guide to help, and I did it! 

Thanks for all the help! you're awesome.

---

