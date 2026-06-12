---
title: "Impossible to fsck or recover superblock; dying HDD?"
date: 2015-04-27
forum: New to Ubuntu
---

### Post by samosater on 2015-04-27
Though I still consider myself "new to Ubuntu", I've been trying to study Ubuntu and Linux (some Debian) since I last posted here, when you folks helped me recover some 3TB worth of data from an ST4000DM000 I had pulled from a dead NAS which is not worth mentioning. One of my first measures after that episode was to acquire an identical HDD (should have picked a different model) to keep a backup and update it every week (one of the wonders of rsync). There's little to say about the new drive, except that it did save the day, and that it lies mostly on the shelf, until the day I can afford to set up a ZFS box and deliver myself from Seagate.

As for the old drive, I created a couple files on it some two days ago, which had disappeared completely and mysteriously. I'd seen it before, and the filesystem should be ok after an fsck. It wasn't. The command and the output went like this:

```
$ sudo fsck -aMv /dev/sdb
fsck de util-linux 2.25.2
fsck.ext2: Bad magic number in super-block tentando abrir [trying to open*] /dev/sdb
/dev/sdb: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```
**rough translation from Portuguese*.

I did try to run e2fsck with alternate values 8193, 32768 and a dozen others I got from running mkfs with the -n tag; they all returned the same error message from above.

I was always able to mount the partitions of sdb and see their contents, but it took a long time and a long, rsync-attempted copy of a particular folder got stalled for three hours until I killed it. Yesterday morning, for some reason, fsck worked and returned a message that sdb1 (the only partition, ext4) was ok. The time it took to mount and see its contents still suggested otherwise.

Knowing I had a synchronised backup from the week before, I got tired of troubleshooting, and deleted sdb1 and the partition table. I created a new partition table and ext4 partition on sdb, only to find the same problems were still there. Though it made no strange noises or clicks, I started to assume I had a dying drive on my hands, and decided to give it a long spin at badblocks before trying to make the partition again:

```
$ sudo badblocks -svw -b 4096 -c 32768 -o /media/log/2015.04.27.sdb.c2ed7578-a487-4316-b574-9cc2b52f0a79.badblocks.log /dev/sdb
Verificando por blocos defeituosos em modo de leitura e escrita [Checking for defective blocks in read/write mode]
A partir do bloco [From block] 0 ao [to]  976754645
Testando com padrão [Testing with pattern] 0xaa: done                                                 
Lendo e comparando [Reading and comparing]:   0.01% done, 9:58:58 elapsed. (0/0/0 errors)
```

Now, elapsed time was right during 0xaa write: it took 8 hours and 2 minutes. Then, as soon as it started reading and comparing, the counter nearly froze: it's been some four hours since and the counter and progress of badblocks is still exactly as above.

So is this drive dying? Is it dead already? Is it something else? Do you folks recommend any other tests or tricks?

Thank you all again.

---

### Post by oldfred on 2015-04-28
If you go into Disks or Disk Utility if older Ubuntu and check Smart Status. With newest versions of Disks you click on a tiny icon in upper right corner and choose Smart Status.
It also can run many tests, but I do not know much except that passed is good and just about anything else is a new drive.

---

### Post by samosater on 2015-04-28
Thanks, Oldfred! I'd so forgotten about checking SMART status that I tried a number of things before reading your reply.

Yesterday morning I decided to use gparted to create a new partition table and a "test" ntfs partition, so that I could run Seatools from Windows. It took quite some time to do, and Windows wasn't able to detect the drive either as a device or as a partition.

Back to the drive this evening: BIOS detected it, so it was worth digging some more. On Gparted, I ignored a report on the ntfs partition being messed up: new gpt table and "test" ext4 partition. To my surprise, fsck reported nothing:


```
/dev/sdb1: LABEL="teste" UUID="47f96a95-46cb-4f6f-9cfe-6f725e01f67a" TYPE="ext4" 

$ sudo fsck -aMv /dev/sdb1
fsck de util-linux 2.20.1
teste: clean, 11/244195328 files, 15377150/976754176 blocks
```


I couldn't believe it, and pushed it with -f:


```
/dev/sdb1: LABEL="teste" UUID="47f96a95-46cb-4f6f-9cfe-6f725e01f67a" TYPE="ext4"

$ sudo fsck -aMvf /dev/sdb1
fsck de util-linux 2.20.1

          11 inodes used (0.00%, out of 244195328)
           0 non-contiguous files (0.0%)
           0 non-contiguous directories (0.0%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 3
    15377150 blocks used (1.57%, out of 976754176)
           0 bad blocks
           1 large file

           0 regular files
           2 directories
           0 character device files
           0 block device files
           0 fifos
           0 links
           0 symbolic links (0 fast symbolic links)
           0 sockets
------------
           2 files

```


To make things better, the drive passed the short test on Disks, but the extended test was interrupted at around 10%, with no error message displayed. Intriguing. I decided to run this extended test from the terminal:

```
$ sudo smartctl --test=long /dev/sdb
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 548 minutes for test to complete.
Test will complete after Wed Apr 29 08:02:47 2015
```

I'll update you folks then.

---

### Post by samosater on 2015-04-29
This is interesting. On CLI, smartctl printed this:

```

$ sudo smartctl -H /dev/sdb
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
190 Airflow_Temperature_Cel 0x0022   068   026   045    Old_age   Always   In_the_past 32 (135 229 32 30 0)
```

However, as soon as I closed that terminal, a Plasma 5 GUI message warns of a possible pre-failure condition:

*"The hard disk health status has changed. This could mean that hard drive failure is imminent."*

Nothing serious, I suppose, against the more detailed smartctl and gnome-disk-utility. Time to run badblocks one last time:

```

$ sudo badblocks -svn -b 4096 -c 4096 -o /media/ilb/sys.admin/log/2015.04.29.47f96a95-46cb-4f6f-9cfe-6f725e01f67a.badblocks.log /dev/sdb
```

Here things turn for the worst. After a few hours, and at less than 3%, more than 400 errors. No wonder fsck was again unable to check the "test" filesystem. The drive seems dead, for what it's worth, but not for this detailed smartctl report:

```

$ sudo smartctl -a /dev/sdb
smartctl 6.4 2014-10-07 r4002 [x86_64-linux-3.19.0-15-generic] (local build)
Copyright (C) 2002-14, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Desktop HDD.15
Device Model:     ST4000DM000-1F2168
Serial Number:    W3007YS0
LU WWN Device Id: 5 000c50 06082810b
Firmware Version: CC52
User Capacity:    4.000.787.030.016 bytes [4,00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5900 rpm
Form Factor:      3.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Wed Apr 29 19:42:03 2015 BRT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  612) seconds.
Offline data collection
capabilities:              (0x73) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 548) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x1085)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   119   099   006    Pre-fail  Always       -       220038288
  3 Spin_Up_Time            0x0003   097   091   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   037   037   020    Old_age   Always       -       65535
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   080   060   030    Pre-fail  Always       -       111479101
  9 Power_On_Hours          0x0032   090   090   000    Old_age   Always       -       8761
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1200
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       8 8 8
189 High_Fly_Writes         0x003a   096   096   000    Old_age   Always       -       4
190 Airflow_Temperature_Cel 0x0022   068   026   045    Old_age   Always   In_the_past 32 (135 229 32 32 0)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   001   001   000    Old_age   Always       -       327175
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       378406
194 Temperature_Celsius     0x0022   032   074   000    Old_age   Always       -       32 (128 0 0 0 0)
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       4348h+59m+48.790s
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       44349170314
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       84667419293

SMART Error Log Version: 1
ATA Error Count: 2
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2 occurred at disk power-on lifetime: 8742 hours (364 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 00 00 00  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 00 00 00 00 00 00 04      00:17:51.320  NOP [Abort queued commands]
  b0 d4 00 82 4f c2 00 00      00:17:20.553  SMART EXECUTE OFF-LINE IMMEDIATE
  b0 d0 01 00 4f c2 00 00      00:17:20.284  SMART READ DATA
  ec 00 01 00 00 00 00 00      00:17:20.269  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      00:17:20.268  IDENTIFY DEVICE

Error 1 occurred at disk power-on lifetime: 8742 hours (364 days + 6 hours)
  When the command that caused the error occurred, the device was in an unknown state.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 51 00 00 00 00 00  Error: ABRT

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  00 00 00 00 00 00 00 04      00:03:54.334  NOP [Abort queued commands]
  b0 d4 00 82 4f c2 00 00      00:03:23.868  SMART EXECUTE OFF-LINE IMMEDIATE
  b0 d0 01 00 4f c2 00 00      00:03:23.601  SMART READ DATA
  ec 00 01 00 00 00 00 00      00:03:23.586  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      00:03:23.586  IDENTIFY DEVICE

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      8753         -
# 2  Extended captive    Interrupted (host reset)      90%      8742         -
# 3  Extended captive    Interrupted (host reset)      90%      8742         -
# 4  Extended offline    Interrupted (host reset)      00%      8742         -
# 5  Extended offline    Interrupted (host reset)      00%      8740         -
# 6  Extended offline    Interrupted (host reset)      00%      8740         -
# 7  Conveyance offline  Completed without error       00%      8740         -
# 8  Extended offline    Interrupted (host reset)      00%      8740         -
# 9  Extended offline    Interrupted (host reset)      00%      8740         -
#10  Short offline       Completed without error       00%      8739         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

Confusing, isn't it?

---

### Post by oldfred on 2015-04-29
Some have posted that smart status is not always correct.
But beyond that I have no more suggestions.

---

### Post by oldfred on 2015-04-29
Some have posted that smart status is not always correct.
But beyond that I have no more suggestions.

---

### Post by samosater on 2015-04-30
Thanks, Oldfred. I'd read something like that too. The drive is really dead. Ran the set of commands from a different SATA port and cable, just to be sure. It's good that fellow members be warned about this model.

---

