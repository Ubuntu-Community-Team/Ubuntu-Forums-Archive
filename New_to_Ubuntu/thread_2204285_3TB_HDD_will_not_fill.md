---
title: "3TB HDD will not fill"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by lfoden on 2014-02-07
Hi, 
I have a 3TB HDD installed in my ubuntu box. It has been formatted to 3TB, but is complaining that it only has 1TB which is nearly filled.
It is detected as a 3TB drive and seems to not have any issues, but has just recently started flagging errors in the disk usage application.

I'm fairly new to ubuntu, so any help would be appreciated.

If it makes a difference, this is not the boot HDD, just a media store, with an SSD as the boot, which is not filling yet.

Any help is greatly appreciated, as I think this is causing problems using programs like transmission, which uses the HDD as its store for files.

Thanks

Luke

---

### Post by theDaveTheRave on 2014-02-07
If you are storing media files only on the external drive, what happens to them when you delete these same files?

I had the experience where the 'trash' directory was causing me to not be able to save on my HDD. The solution was to simply empty the trash.

I have had the same problem with USB keys that suddenly seem 'full' and it comes down to the hidden trash folder.

David

---

### Post by Bashing-om on 2014-02-07
lfoden; Hi !

Let's take a close look at the drive(s)
Post the output - between code tags - of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sdb unit s print

```
Which will give an idea of what is going on, and where to look next.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by whitesmith on 2014-02-07
Your problem probably lies in the way the 3 TB drive was formatted. Large drives cannot achieve full capacity if the older MBR was chosen as the formatting structure; GPT must be used instead. According to hard drive manufacturer Seagate ([http://knowledge.seagate.com/articles/en_US/FAQ/218575en](http://knowledge.seagate.com/articles/en_US/FAQ/218575en)), "Linux, like other operating systems, has a 2.2TB limitation in the Master Boot Record (MBR). Partitions greater than 2.2TB will need to utilize the GUID Partition Table (GPT) structure." The MBR/GUID incompatibility could have been avoided if manufacturers had been less inclined to stick with tried and true insights. Another lurking headache: If I recall correctly gparted cannot handle GPT, so you'll need to find something newer that can -- gdisk will do the job. Regards.

---

### Post by oldfred on 2014-02-08
I have used gparted to create gpt drives since 10.10, so that is not an issue. But MBR is usually the default.
 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning as first step before starting to partition.

 
If you may want to ever install a system, I would leave room at beginning of drive or an 300MB efi partition and a 1 or 2MB bios_grub partition. The efi would be for a new system with UEFI booting and the bios_grub for older systems that still boot with BIOS. With gpt Windows will only boot with UEFI, but Ubuntu will boot with UEFI or BIOS. The space for the efi & bios_grub are not large and can save major backup and reformatting issues if adding a system to drive.

I do like to have a system on every drive even if primarily for data.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

### Post by whitesmith on 2014-02-08
> **lfoden said:**
> I have a 3TB HDD installed in my ubuntu box. It has been formatted to 3TB, but is complaining that it only has 1TB which is nearly filled.My response was based on information supplied by a hard drive manufacturer. Other issues that could cause the problem are legacy kernels and BIOSes. See the href with my first post for details. **oldfred** is right about the advanced option in gparted. I hadn't bothered to check it out when I responded. Cheers.

---

### Post by lfoden on 2014-02-17
Hi Guys,

Thanks for the quick reply. Apologies I haven't been quite so speedy, due to work commitments.

My output to the 3 commands is as below. Hope this helps!

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000689d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   108531711    54264832   83  Linux
/dev/sda2       108533758   125044735     8255489    5  Extended
/dev/sda5       108533760   125044735     8255488   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


sudo parted -l

Model: ATA SanDisk SDSSDHP0 (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  55.6GB  55.6GB  primary   ext4            boot
 2      55.6GB  64.0GB  8454MB  extended
 5      55.6GB  64.0GB  8454MB  logical   linux-swap(v1)


Model: ATA TOSHIBA DT01ABA3 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  ntfs

sudo parted /dev/sdb unit s print

Model: ATA TOSHIBA DT01ABA3 (scsi)
Disk /dev/sdb: 5860533168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name  Flags
 1      2048s  5860532223s  5860530176s  ntfs

Thanks for your help so far

Luke

---

### Post by lfoden on 2014-02-17
Hi Guys,

Thanks for the quick reply. Apologies I haven't been quite so speedy, due to work commitments.

My output to the 3 commands is as below. Hope this helps!

```

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000689d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   108531711    54264832   83  Linux
/dev/sda2       108533758   125044735     8255489    5  Extended
/dev/sda5       108533760   125044735     8255488   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


sudo parted -l

Model: ATA SanDisk SDSSDHP0 (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  55.6GB  55.6GB  primary   ext4            boot
 2      55.6GB  64.0GB  8454MB  extended
 5      55.6GB  64.0GB  8454MB  logical   linux-swap(v1)


Model: ATA TOSHIBA DT01ABA3 (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  3001GB  3001GB  ntfs

sudo parted /dev/sdb unit s print

Model: ATA TOSHIBA DT01ABA3 (scsi)
Disk /dev/sdb: 5860533168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End          Size         File system  Name  Flags
 1      2048s  5860532223s  5860530176s  ntfs

```

Thanks for your help so far

Luke

---

### Post by sudodus on 2014-02-18
To me it looks like there is a correct partition with 3 TB and an NTFS file system. Parted does not tell us about the quality of the file system. Can you connect the drive to a computer with Windows, and use ***a Windows tool*** to check that the file system is good, or use Bart PE or Windows 7 PE?

```
chkdsk
``` or if you want to let it repair file system errors, ```
chkdsk /f
``` or some GUI version doing basically the same thing.

--
[COLOR=#696969]Use Linux tools to manage linux and Windows tools to manage Windows (and the NTFS file system is part of Windows).[/COLOR]

---

### Post by lfoden on 2014-03-04
Hi,

Thanks for your help there. Finally managed to get it plugged into a Windows box.

```
C:\Windows\system32>chkdsk e: /fThe type of the file system is NTFS.
Volume label is Media.


CHKDSK is verifying files (stage 1 of 3)...
  5366 file records processed.
File verification completed.
  204 large file records processed.
  0 bad file records processed.
  0 EA records processed.
  0 reparse records processed.
CHKDSK is verifying indexes (stage 2 of 3)...
  6650 index entries processed.
Index verification completed.
  0 unindexed files scanned.
  0 unindexed files recovered.
CHKDSK is verifying security descriptors (stage 3 of 3)...
  5366 file SDs/SIDs processed.
Security descriptor verification completed.
  642 data files processed.
Windows has checked the file system and found no problems.


   2861586 MB total disk space.
 981426640 KB in 4470 files.
      1544 KB in 644 indexes.
         0 KB in bad sectors.
    161259 KB in use by the system.
     65536 KB occupied by the log file.
1948675644 KB available on disk.


      4096 bytes in each allocation unit.
 732566271 total allocation units on disk.
 487168911 allocation units available on disk.
```

There doesn't seem to be any problems with it in a windows box. Detects full capacity and allows me to copy and paste to it as I should.

---

