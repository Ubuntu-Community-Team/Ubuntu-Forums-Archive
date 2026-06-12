---
title: "Dual Boot Ubuntu SSD/HDD + Windows 8 HDD"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by Renan_Tardelli on 2015-02-10
I Have a 500gb HDD + 24gb SSD laptop, and I came with Windows  pre-installed, I want to know how to change my partitions in a way that  Ubuntu keeps roughly 2/3 or more of the HDD disk, and about the SSD, it  already has a 2 partitions, if I left it this way will Ubuntu make full  use of the SSD or I need to change these partitions too? 
  ```
How it is now:
Disk0:
100 MB (EFI System Partition)
900 MB Healthy (Recovery Partition)
183.40 GB - OS (C:) - NTFS - Healthy (boot, Page File, Crash Dump, Primary Partition)
261.25 GB - Data (D:) - NTFS - Healthy (Primary Partition)
20 GB Healthy (Recovery Partition)

Disk1:
8 GB - Healthy (OEM Partition)
12.97 GB - Healthy (Primary Partition)

```
 To summarize, I will Shrink roughly 260gb HDD from both OS (C:) and  Data (D:) (I don't know if I can Shrink Recovery Partitions) and about  the SSD, I intend to shrink all but OEM (I dont know if I can or if I  will have problems in future), so Ubuntu can make fully use of my SSD (I  assumed it and I don't know nothing about partitions, is it right?). 
  And about the so called, swap area, is it better to be in the SSD  partition ? What would be better for Ubuntu to be partitioned in the SSD  ? 
  How I intend to do: First One Large partition for Ubuntu, Second  other larger Partition for my home partition and a Third smaller for my  swap space (the tutorial I'm following says it should be 1.5 ~ 2x my  RAM, then 12gb, is it right?, It is the whole Primary partition of the  SSD). Is it the best way to make Ubuntu fully use my computer resources?

---

### Post by oldfred on 2015-02-10
Is your SSD really Intel SRT or just boot cache for Windows. That usually uses only the same amount as your RAM and rest of SSD is not used.

  Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)
For GPT systems, this needs to have a type GUID of D3BFE2DE-3DAF-11DF-BA-40-E3A556D89593. 
For MBR systems, you need a partition type of 0x84[2].
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)
[http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf](http://download.intel.com/support/motherboards/desktop/sb/rapid_start_technology_user_guide.pdf)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

If primarily a Linux user, some have installed just / (root) to SSD. Some with larger SSD keep SRT and still have a smaller / on SSD. If primarily a Windows user they just install everything to hard drive.

You do need to install Ubuntu in UEFI boot mode either  way.
      
 Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

What brand/model computer & what video card/chip?
But Intel SRT seems to be the same across vendors since just Intel.

And newer Linux versions seem to work better and just install. Some have posted just changing to AHCI allows Ubuntu to install. Before you have to remove SRT's RAID data on drives.


 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

