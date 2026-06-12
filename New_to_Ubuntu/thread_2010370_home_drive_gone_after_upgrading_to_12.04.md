---
title: "home drive gone after upgrading to 12.04"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by vaah on 2012-06-25
Hi guys,
I had been using ubuntu 10.10 until a few minutes ago when I decided to take the plunge and upgrading to 12.04. Now I am regretting this because my /home drive is suddenly gone. At first after completing the upgrade, i was able to access my home dir, then after i restart then it's stuck with warning message saying something like ubuntu unable to mount home. This shocked me, then I skip tmounting and login.

 After I check my home drive in "disk utility", apparently my drive listed as free (unallocated). I just lost 500gb worth of data for no reason.:cry::cry: I didn't do anything that should cause this. :confused::confused:

Do you have any idea what i should do to recover my drive? The filesystem type was ext4

---

### Post by Paqman on 2012-06-25
> **vaah said:**
> 
Do you have any idea what i should do to recover my drive? The filesystem type was ext4

Shutdown immediately, just in case anything is writing to that drive. Book up into your LiveCD, see if you can mount that drive and get your data off. If not install testdisk and run the data recover tool photorec:
```
sudo photorec
```
This will allow you to get everything that hasn't been overwritten off that drive onto some backup media.

Are you sure you upgraded from 10.10 to 12.04? You would have had to do three upgrades to do that, you can only go from 10.04 or 11.10 straight to 12.04.

---

### Post by vaah on 2012-06-25
> **Paqman said:**
> Shutdown immediately, just in case anything is writing to that drive. Book up into your LiveCD, see if you can mount that drive and get your data off. If not install testdisk and run the data recover tool photorec:
```
sudo photorec
```This will allow you to get everything that hasn't been overwritten off that drive onto some backup media.

Are you sure you upgraded from 10.10 to 12.04? You would have had to do three upgrades to do that, you can only go from 10.04 or 11.10 straight to 12.04.

Yeah pretty sure, when I boot up with 12.04 startup disk. I got 4 options to choose from and ine of those is upgrade. Hmm..any idea on how to installing testdisk on livecd? I got this error:

```

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ sudo apt-get install photorec
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package photorec

```fyi, my home drive and filesystem drive are separated. So I am able to boot into ubuntu but It still see my home drive as unallocated, this is also the case when i check this in "disk utility" within livecd environment.

Please kindly help me. thanks.

---

### Post by Paqman on 2012-06-25
Testdisk is in the Universe repository, so check Software Sources and make sure that's enabled, then reload your sources.

---

### Post by Cheesemill on 2012-06-25
> **vaah said:**
> ```

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package testdisk
ubuntu@ubuntu:~$ sudo apt-get install photorec
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package photorec

```
You need to update your sources first:
```
sudo apt-get update
```

I think you have this problem because you installed 12.04 over the top of 11.10, completely replacing it. It's not possible to upgrade from 11.10 directly to 12.04 as well as it not being possible to upgrade at all using a Live CD.

---

### Post by vaah on 2012-06-25
Yeah i didnt know this would be a problem since the option is there at the installation menu. -_-

do i have to reinstall testdisk to my usb livecd if i shutdown the pc? I'm guessing this is gonna take a long time to recover since i have more or less 400gb data.

---

### Post by alphacrucis2 on 2012-06-25
Something slightly odd here. It shouldn't be possible to upgrade from 10.10 to 12.04. You would have to go via 11.04 - 11.10 first. Otherwise it would effectively be a fresh install rather than upgrade. 


Edit Whoops. I see Cheesemill already pointed this out. Sounds like a bug in the install CD which should be reported

---

### Post by oldfred on 2012-06-25
If partition is still in partition table you may just need to run e2fsck. If that does not work then testdisk to see what it says. Photorec is part of testdisk and would be the last thing to try. Photorec only recovers file extensions as file tables are gone & it just scans hard drive for anything that looks like a file by type. 

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by vaah on 2012-06-26
> **oldfred said:**
> If partition is still in partition table you may just need to run e2fsck. If that does not work then testdisk to see what it says. Photorec is part of testdisk and would be the last thing to try. Photorec only recovers file extensions as file tables are gone & it just scans hard drive for anything that looks like a file by type. 

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1
Hi oldfred,

I tried ur suggestion and got this error message:

```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdc1
e2fsck: No such file or directory while trying to open /dev/sdc1
Possibly non-existent device?
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdc
e2fsck: Bad magic number in super-block while trying to open /dev/sdc
/dev/sdc: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdc1
e2fsck 1.42 (29-Nov-2011)
e2fsck: No such file or directory while trying to open /dev/sdc1
Possibly non-existent device?
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sdc
e2fsck 1.42 (29-Nov-2011)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdc

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ 

```

Perhaps I should try running test disk..

---

### Post by vaah on 2012-06-26
Hi all 
I wanna try using parted and rescue command maybe this way the partition table might be repaired? i wanna avoid using photorec if at all possible cause all folder structure and file names are gibberish.
 but i dont understand which sector should i put into rescu command.

this is my photorec output:
```

PhotoRec 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdc - 500 GB / 465 GiB (RO) - WDC WD5000AAKS-00YGA0

     Partition                  Start        End    Size in sectors
      Unknown                  0   0  1 60801  47 29  976771055 [Whole disk]
> 1 P MS Data                  0   0 35 52277 218 11  839843716 [Home]
  2 P MS Data              52277 218 12 60801  80 30  136929385 [Music]







```I originally have 2 partition 1 for /home  and one for music. The home partition is ext4 and music is ntfs.

Any idea?

---

### Post by cmcanulty on 2012-06-26
I had this happen once. It isn't clear but if you don't format your home you still have to click the box to mount that partition as /Home at install or it isn't shown as home after upgrade.

---

### Post by vaah on 2012-06-26
> **cmcanulty said:**
> I had this happen once. It isn't clear but if you don't format your home you still have to click the box to mount that partition as /Home at install or it isn't shown as home after upgrade.
It was shown as home after the upgrade, I was able to browse the home. Then I found out that my sound didn't work so I decided to reboot. That's when my home partition couldn't be mounted.

---

### Post by oldfred on 2012-06-26
Testdisk is showing it as MSdata? /home has to be a Linux format. Did partition get changed somehow. Sometimes it can just be the flag in the partition table.

Post this:

sudo fdisk -lu

e2fsck would not work it partition is seen as NTFS. If actually NTFS it cannot be /home and you have to use chkdsk from Windows to repair.

---

### Post by vaah on 2012-06-26
> **oldfred said:**
> Testdisk is showing it as MSdata? /home has to be a Linux format. Did partition get changed somehow. Sometimes it can just be the flag in the partition table.

Post this:

sudo fdisk -lu

e2fsck would not work it partition is seen as NTFS. If actually NTFS it cannot be /home and you have to use chkdsk from Windows to repair.
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000411b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda2        39070080   234436544    97683232+  83  Linux

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf3684793

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930276351  1465137152    7  HPFS/NTFS/exFAT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   976773167   488386583+  ee  GPT

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0005d172

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  1953523711   976760832    7  HPFS/NTFS/exFAT

Disk /dev/sde: 1500.3 GB, 1500300828160 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930275055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x453c2a7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              63  2930272064  1465136001    7  HPFS/NTFS/exFAT

Disk /dev/sdf: 2013 MB, 2013564416 bytes
62 heads, 62 sectors/track, 1023 cylinders, total 3932743 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00088f02

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          62     3932411     1966175    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```

the home is ext4 and music is ntfs as mentioned before. I don't know what msdata mean. what is it?

---

### Post by oldfred on 2012-06-26
Since you have gpt partitioned large drives, fdisk does not work. It is just for MBR(msdos) partitioned drives.

Use parted or download and run gdisk, if drive is sdc or list each drive: With gpt drives both Linux & Windows data partitions may be shown the same gpt data type but formats will still be different.

sudo parted /dev/sdc unit s print
or
sudo gdisk -l /dev/sdc

---

### Post by vaah on 2012-06-26
> **oldfred said:**
> Since you have gpt partitioned large drives, fdisk does not work. It is just for MBR(msdos) partitioned drives.

Use parted or download and run gdisk, if drive is sdc or list each drive: With gpt drives both Linux & Windows data partitions may be shown the same gpt data type but formats will still be different.

sudo parted /dev/sdc unit s print
or
sudo gdisk -l /dev/sdc
I did what u told me:
```

augie@yuki:~
$ sudo parted /dev/sdc unit s print
Warning: /dev/sdc contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? y                                                                 
Error: Invalid argument during seek for read on /dev/sdc                  
Retry/Ignore/Cancel? r                                                    
Error: Invalid argument during seek for read on /dev/sdc                  
Retry/Ignore/Cancel? c  

```
do i need to do anything now that i am able to access home partition? The warning above worries me now...
Also any idea on what to do to restore my ntfs partition? its still lost.

---

### Post by oldfred on 2012-06-26
That seems to be saying you have issues even if it is gpt. Did you format it as gpt, even with gpt it is supposed to have the protective MBR table so MBR(msdos) tools do not corrupt the gpt data.

I do not know much about repairing gpt. See this link:

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by vaah on 2012-06-26
I never format it as GPT, actually this is the first time i heard of it. hmm...I was about to do fresh install of 12.04 and it doesn't detect my home partition when i wanna set my current home as /home. It's just listed as /sdc while others are sdb/--sdb1/--sdb2/ ... Strange..

---

### Post by oldfred on 2012-06-26
If you start with a empty drive somewhere over 1TB the Ubuntu installer installs to gpt. You only have to have gpt if the drive is over 2TB, but if between 1 & 2TB  you have to format in advance to use MBR(msdos).

I am using gpt with BIOS boot but have to have a 1MB unformated bios_grub partition for grub2 to install correctly.

---

### Post by vaah on 2012-06-27
> **oldfred said:**
> If you start with a empty drive somewhere over 1TB the Ubuntu installer installs to gpt. You only have to have gpt if the drive is over 2TB, but if between 1 & 2TB  you have to format in advance to use MBR(msdos).

I am using gpt with BIOS boot but have to have a 1MB unformated bios_grub partition for grub2 to install correctly.
I think i should mark this thread as solved tho my music partition(ntfs) ended up lost. I just couldnt bother to find solution, now that I was able to finally recover my home. :D:D I used testdisk, create log> analyse. :D then wrote it to my partition table.

---

