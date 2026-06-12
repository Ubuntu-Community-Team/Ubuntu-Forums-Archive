---
title: "SATA drive partition moved to Ubuntu after XP reinstall"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by berylmichael on 2008-05-17
I do apologize if this has been discussed before. I've read through some of the forums but haven't found a similar problem. I am running a dual boot using Windows XP and Ubuntu 8.04. I had my Ubuntu setup on a 20GB IDE drive, XP on an 80GB IDE drive and a 320GB SATA secondary drive, divided into a two partitions for data backup (a 100GB partition for Ubuntu and 200GB partition for Windows). Everything was working fine until I reformatted Windows XP. Now the 200GB partition has shown up in Ubuntu but is not seen in Windows.

The following are the drive specifications in Ubuntu:
hd1 - the original 100GB backup partition that I was using for Ubuntu
hdb1 - the 20Gb drive that Ubuntu is installed on
sd1 - the 200GB partition that used to be in Windows for data backup 
     (Note, the backed up data from Windows is still shown in the partition and I can access it from Ubuntu).

Is there a relatively easy way to put back the 200GB partition in Windows or will I have to backup all the data onto another drive and "reinstall" the 320GB drive again? I do not want to lose the data that is there!

Any suggestions will be appreciated!

Thank you before hand,
Michael

---

### Post by prshah on 2008-05-17
> **berylmichael said:**
> 
The following are the drive specifications in Ubuntu:
hd1 - the original 100GB backup partition that I was using for Ubuntu
hdb1 - the 20Gb drive that Ubuntu is installed on
sd1 - the 200GB partition that used to be in Windows for data backup 
     (Note, the backed up data from Windows is still shown in the partition and I can access it from Ubuntu).


sd1 cannot be a partition; it has to be sda1 or sdb1 or so on...

Further, I suspect that your sda1 is formatted as ext2/3; in which case you need to install (in windows) ext2/3 IFS drivers to read that partition.

A quick post pf the output of the below command (from ubuntu) will go a long way to actually pinpointing and hence clearing the problem;
```

sudo fdisk -l
```

---

### Post by Crossroads on 2008-05-17
So Windows XP (on the 80GB disk) cannot now see the 200GB partition?

I'm not clear:
- what did you reformat and how?
- what does Windows Explorer and Widnows Disk Management show for disks/paritiions?

---

### Post by berylmichael on 2008-05-17
Thank you for your reply!

PRShah: You were right, the 200GB partition is labeled sda1. I ran the command that you gave and here is what it showed:

[INDENT][INDENT]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a65a6b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       24972   200587558+   7  HPFS/NTFS
/dev/sda2           45691       60428   118382985   83  Linux
/dev/sda3           60429       60801     2996122+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
238 heads, 28 sectors/track, 23454 cylinders
Units = cylinders of 6664 * 512 = 3411968 bytes
Disk identifier: 0xb7b9ef35

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23454    78147608    7  HPFS/NTFS

Disk /dev/sdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bec1beb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        2432    19535008+  83  Linux
[/INDENT][/INDENT]

The 200GB partition is still showing as NTFS, which is good, I suppose.


Crossroads: Correct, Windows cannot see the 200GB partition. Maybe I should have used another term besides formatted - reinstalled would be a better word. I had a lot of files on my system (the disk was getting full) and I was having problems with the networking - it wouldn't detect the network all the time. Perhaps I had some spyware, viruses, adware, etc on the drive so instead of attempting to clean it up, I inserted the Windows XP CD and reinstalled Windows, wiping out the drive and putting a fresh Windows install on it. Both Windows Explorer and the Disk Manager show that I have Disk 0 (C: drive, NTFS) with 74.53GB space, a Disk 1 with 18.63GB space, and a DVD (D: drive). That's it!

I want to thank you both for responding. Hopefully, with the added information shown above, you can provide further suggestions.

Michael

---

### Post by prshah on 2008-05-18
> **berylmichael said:**
>  Both Windows Explorer and the Disk Manager show that I have Disk 0 (C: drive, NTFS) with 74.53GB space, a Disk 1 with 18.63GB space, and a DVD (D: drive). That's it!

OK that means that the entire 500Gb drive is not seen in Windows. I'm now guessing that the 80Gb and 20Gb are IDE drives, and the 500Gb either SATA or external USB... can you confirm?

Further confirmation: Are you running XP SP1? That has a limit of 127Gb. SP2 is OK.

---

### Post by Crossroads on 2008-05-18
This could be it:

I'm pretty sure that a Windows XP installation does not install SATA drivers. You have to have the SATA drives on a floppy disk and install them from there  at some point during the XP install.

Quite often the motherboard manual will explain how to create the SATA driver floppy disk from the motherboard's CD and when to use it suring the Windows XP install.

---

### Post by berylmichael on 2008-05-18
> **prshah said:**
> OK that means that the entire 500Gb drive is not seen in Windows. I'm now guessing that the 80Gb and 20Gb are IDE drives, and the 500Gb either SATA or external USB... can you confirm?

Further confirmation: Are you running XP SP1? That has a limit of 127Gb. SP2 is OK.


Yes, the entire 500GB drive isn't seen in Windows (It looks like there are 3 partitions: approximately 2- 200GB partitions and 1-100GB partition. One 200 GB is NTFS, the other one seems to be a Linux Swap file and the 100GB partition is Linux). The drive is an internal SATA drive. The 80 and 20 GB are IDE drives. I am running XP SP3 (I was running XP SP2 previously). For whatever reason that I am not sure of, Linux took over the drives when I reinstalled XP.

---

### Post by berylmichael on 2008-05-18
> **Crossroads said:**
> This could be it:

I'm pretty sure that a Windows XP installation does not install SATA drivers. You have to have the SATA drives on a floppy disk and install them from there  at some point during the XP install.

Quite often the motherboard manual will explain how to create the SATA driver floppy disk from the motherboard's CD and when to use it suring the Windows XP install.


I do have an installation CD for the SATA drive but I am hesitant to use it since I have data installed on one of the partitions which is in Linux now. But I may have to move the data over to another drive or some space and re-install the SATA drive.

Michael

---

### Post by prshah on 2008-05-19
> **berylmichael said:**
> I do have an installation CD for the SATA drive 


I don't think the problems are related to SATA drivers, now that I know you are using XP SP2+.

Besides which, SATA drivers will come with the motherboard and/or SATA addon-card, _not_ with the SATA drive.

Can you check your Windows event viewer for entries that might seem related? Click Start-Run, then ```
eventvwr.msc
``` and check under "System" as well as "Applications".

Under ideal conditions, your 500Gb HDD should show up in "diskmgmt.msc"; can you post a screenshot of that. Your NTFS partition should be accessible in Windows too; unless it is not "initialized". To initialize (_not_ format) it should show up in diskmgmt.msc.

---

### Post by berylmichael on 2008-05-21
PRShah and Crossroads: I was able to get Windows to recognize my SATA drive. You were correct, the SATA drivers do come with the motherboard; however, when I reinstalled Windows, the drivers were erased. Once I re-installed the drivers, the SATA drive with all of the partitions showed up in Windows. And the data was there as well! 

I want to thank you for all your help!

Michael

---

