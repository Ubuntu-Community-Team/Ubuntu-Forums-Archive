---
title: "Windows-Ubuntu Shared partition"
date: 2012-12-14
forum: New to Ubuntu
---

### Post by algrossi on 2012-12-14
I am trying to use a Shared partition to contain data from Windows-7 and Ubuntu, the following is my setup. Ubuntu sees the arpartition but Windows does not. I have tried a few partition editors and two (which come with Windows), to assign a Drive Letter to the Shared Partition. Has anyone managed to accomplish such a thing?
[FONT=Courier New][SIZE=1]
[/SIZE][/FONT][FONT=Courier New][SIZE=1]Partition     Capacity     Used              Unused          File System Type     Status[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]*:SYSTEM       199.00 MB     30.82 MB    168.18 MB    [SIZE=1][/SIZE]NTFS              Primary  Active & Boot[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]C:                   152.82 GB    117.17 GB    35.65 GB      NTFS              Primary  System[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]*:Shared         98.53 GB     49.30 MB    98.48 GB      FAT32            Primary  None[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]*:RECOVERY     17.13 GB     14.65 GB     2.47 GB      NTFS              Logical  None[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]*:                     27.94 GB     24.31 GB     3.50 GB      Ext2              Logical  None (Ubuntu)
[/SIZE][/FONT][FONT=Courier New][SIZE=1]*:                     24.77 MB      0 B            24.77 MB      Unallocated Logical  None[/SIZE][/FONT]
[FONT=Courier New][SIZE=1]*:                       1.45 GB      4.00 KB      1.45 GB      Linux       Swap    Logical  None[/SIZE][/FONT]
 
Thank you;
Al;;

---

### Post by oldfred on 2012-12-14
In this thread we suggested NTFS, but you created FAT32?
[http://ubuntuforums.org/showthread.php?t=2092682](http://ubuntuforums.org/showthread.php?t=2092682)

I have not used FAT32 with Windows 7, but it did work with XP. But FAT32 has a limit of 4GB per file, so you cannot save large files and has no journal, so repair can be difficult. It is ok for small partitions or external devices that are small but not really for larger partitions.

---

### Post by algrossi on 2012-12-14
I started the other thread you indicated in your link, but I did not indicate my disk structure. This thread has the correct structure and I hope someone can make sense of this. I originally used NTFS as the file structure of the shared partition but it made no difference. I am quite new to Ubuntu and I want to use Ubuntu as my primary OS, except for my Income Tax program and for VHS-to-DVD video transfers. I may as well keep checking this thread because I included the partition structure in it.
Thank you;
Al;

---

### Post by algrossi on 2012-12-16
I found the solution at the following site. Thanks to all for participating.
[http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/35eee15b-69c0-4927-856a-3f0622893074](http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/35eee15b-69c0-4927-856a-3f0622893074)
Al

---

### Post by Bucky Ball on 2012-12-16
Once more, please mark threads as 'Solved' to help others when they are ... thanks.

---

