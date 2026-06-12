---
title: "RAID5 MDADM reports inactive after power outage"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by agentofcode on 2013-03-31
Since a power outage I  have been unable to  get my RAID5 back in business. I  found a similar [solved post here in the forums]("http://ubuntuforums.org/showthread.php?t=1887913") and followed the steps but appear to have a slightly different situation. The following is all the output I've received while following the other thread. I'm running **smartmontools** on my drives now but won't be done for a few hours. Based on the following information, what steps should I take to get this thing back together correctly?[INDENT][COLOR=#b22222][I][B]
Sidenote:[/B][/I][/COLOR]
sda1 is my OS which is not part of my RAID5.
[/INDENT]
 

**cat /proc/mdstat** Returns:
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[2] sdc1[1] sdb[3](S)
      5852806232 blocks super 1.2
 
unused devices: <none>
**mdadm -D /dev/md0** Returns:
> /dev/md0:
        Version : 1.2
  Creation Time : Sun Mar 17 17:38:43 2013
     Raid Level : raid5
  Used Dev Size : 1949708800 (1859.39 GiB 1996.50 GB)
   Raid Devices : 3
  Total Devices : 3
    Persistence : Superblock is persistent
 
    Update Time : Sat Mar 30 22:44:16 2013
          State : active, degraded, Not Started
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
 
         Layout : left-symmetric
     Chunk Size : 512K
 
           Name : Animus:0  (local to host Animus)
           UUID : 5bd54288:789b690a:1dd058db:49e92aa5
         Events : 191100
 
    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
 
       3       8       16        -      spare   /dev/sdb[INDENT][COLOR=#b22222]***Sidenote:***[/COLOR]
sdb1 now appears as a spare because a Google search found a suggestion to try...
[B]/sbin/mdadm /dev/md0 --fail /dev/sdb1 --remove /dev/sdb1
/sbin/mdadm /dev/md0 --add /dev/sdb1[/B]

But the drive would not go back into the array because...
 **mdadm: Cannot open /dev/sdb1: Device or resource busy**

[/INDENT]
 [HR][/HR]
When I try...
[B]sudo -i
mdadm --stop /dev/md0
mdadm --assemble --force /dev/md2 /dev/sd[bcd]
[/B]
I get...
> 
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted
[INDENT][COLOR=#b22222]***Sidenote:***[/COLOR]
The superblock error has changed to different drives on different reboots. So I assume all have no superblock?
[/INDENT]

**mdadm -E /dev/sd[bcd]** Returns:
> /dev/sdb:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5bd54288:789b690a:1dd058db:49e92aa5
           Name : Animus:0  (local to host Animus)
  Creation Time : Sun Mar 17 17:38:43 2013
     Raid Level : raid5
   Raid Devices : 3
 
 Avail Dev Size : 3906767024 (1862.89 GiB 2000.26 GB)
     Array Size : 3899417600 (3718.77 GiB 3993.00 GB)
  Used Dev Size : 3899417600 (1859.39 GiB 1996.50 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 2d922d0a:b528c3db:7be647c2:81567ac8
 
    Update Time : Sat Mar 30 22:44:16 2013
       Checksum : 3e601ebd - correct
         Events : 0
 
         Layout : left-symmetric
     Chunk Size : 512K
 
   Device Role : spare
   Array State : .AA ('A' == active, '.' == missing)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   3899688960 sectors at         2048 (type fd)
Partition[1] :      7335938 sectors at   3899693054 (type 05)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   3899680768 sectors at         2048 (type fd)
Partition[1] :      7333890 sectors at   3899684862 (type 05)


Thanks in advance!

---

### Post by agentofcode on 2013-04-01
I accidentally closed my terminal so I did not see the results of the drive test from smartmontools. I am rerunning it now. Should I be seeing HDD activity during this process? Because I don't.

And when I run **smartctl -l selftest **on any of the drives to check the status:

I get...
> SMART Self-test Log not supported
...any ideas on this one?

---

### Post by rubylaser on 2013-04-02
Since you have removed /dev/sdb1, you will need to re-add it to get it back into the array.  Since your info is referencing the wrong location, can you run these commands for me?

```
cat /proc/mdstat
cat /etc/mdadm/mdadm.conf
mdadm -E /dev/sd[bcd]1
```

---

### Post by darkod on 2013-04-02
To add to rubylaser's question, your very first cat /proc/mdstat shows sdb, sdc1 and sdd1 as members of the array. Which means, on purpose or not, you used the whole disk /dev/sdb, and the partitions /dev/sdc1 and /dev/sdd1 to create the array. That is not good practice, you usually use all partitions or all disks. In fact, you should use only partitions, not disks as devices for mdadm. The disk can still have only one large partition on it, but use the partition designator like /dev/sdc1 and not the disk designator like /dev/sdc.

Depending on the output of the command above, rubylaser will probably know which commands to suggest.

---

### Post by agentofcode on 2013-04-02
**cat /proc/mdstat** Returns:
> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdd1[2](S) sdc1[1](S) sdb[3](S)
      5852806232 blocks super 1.2

unused devices: <none>



**cat /etc/mdadm/mdadm.conf** Returns:
> # mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#
 
# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers
 
# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes
 
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
 
# instruct the monitoring daemon where to send mail alerts
MAILADDR root
 
# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=5bd54288:789b690a:1dd058db:49e92aa5 name=Animus:0
 
# This file was auto-generated on Sun, 17 Mar 2013 17:41:29 -0400
# by mkconf $Id$
**mdadm -E /dev/sd[bcd]1** Returns
> /dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5bd54288:789b690a:1dd058db:49e92aa5
           Name : Animus:0  (local to host Animus)
  Creation Time : Sun Mar 17 17:38:43 2013
     Raid Level : raid5
   Raid Devices : 3
 
 Avail Dev Size : 3899426816 (1859.39 GiB 1996.51 GB)
     Array Size : 3899417600 (3718.77 GiB 3993.00 GB)
  Used Dev Size : 3899417600 (1859.39 GiB 1996.50 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : e988ff80:353b0cdf:474c3fad:8b38fad0
 
    Update Time : Sat Mar 30 22:44:16 2013
       Checksum : ab826f1f - correct
         Events : 0
 
         Layout : left-symmetric
     Chunk Size : 512K
 
   Device Role : spare
   Array State : .AA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5bd54288:789b690a:1dd058db:49e92aa5
           Name : Animus:0  (local to host Animus)
  Creation Time : Sun Mar 17 17:38:43 2013
     Raid Level : raid5
   Raid Devices : 3
 
 Avail Dev Size : 3899426816 (1859.39 GiB 1996.51 GB)
     Array Size : 3899417600 (3718.77 GiB 3993.00 GB)
  Used Dev Size : 3899417600 (1859.39 GiB 1996.50 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 04302cb8:c8783173:cddeef6f:9dc858f6
 
    Update Time : Sat Mar 30 22:44:16 2013
       Checksum : 5ee560df - correct
         Events : 191100
 
         Layout : left-symmetric
     Chunk Size : 512K
 
   Device Role : Active device 1
   Array State : .AA ('A' == active, '.' == missing)
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5bd54288:789b690a:1dd058db:49e92aa5
           Name : Animus:0  (local to host Animus)
  Creation Time : Sun Mar 17 17:38:43 2013
     Raid Level : raid5
   Raid Devices : 3
 
 Avail Dev Size : 3899418624 (1859.39 GiB 1996.50 GB)
     Array Size : 3899417600 (3718.77 GiB 3993.00 GB)
  Used Dev Size : 3899417600 (1859.39 GiB 1996.50 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active

---

### Post by agentofcode on 2013-04-02
> **darkod said:**
> To add to rubylaser's question, your very first cat /proc/mdstat shows sdb, sdc1 and sdd1 as members of the array. Which means, on purpose or not, you used the whole disk /dev/sdb, and the partitions /dev/sdc1 and /dev/sdd1 to create the array. That is not good practice, you usually use all partitions or all disks. In fact, you should use only partitions, not disks as devices for mdadm. The disk can still have only one large partition on it, but use the partition designator like /dev/sdc1 and not the disk designator like /dev/sdc.

Depending on the output of the command above, rubylaser will probably know which commands to suggest.

Strange thing is it used to show up as **sdb1** and not **sdb**. Not sure why/how it changed. Thanks for pointing out best practices also. When I created the RAID5 my intention was to use the entire partitions. Obviously I did something incorrect during that process. Hopefully I can recover from this and get to a point to where I can set it up correctly.

---

### Post by agentofcode on 2013-04-02
Results of **smartctl -l selftest /dev/sdb**
> === START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%     18375         2631941936
# 2  Extended offline    Completed: read failure       40%     18349         2631941936
# 3  Extended offline    Interrupted (host reset)      90%     18343         -
# 4  Extended offline    Interrupted (host reset)      90%     18343         -
Results of **smartctl -l selftest /dev/sdc**
> === START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     17092         -
# 2  Extended offline    Completed without error       00%     17066         -
# 3  Extended offline    Interrupted (host reset)      90%     17057         -
# 4  Extended offline    Interrupted (host reset)      90%     17057         -
# 5  Short offline       Completed without error       00%         1         -

Results of **smartctl -l selftest /dev/sdd**
> === START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     16091         -
# 2  Extended offline    Completed without error       00%     16065         -
# 3  Extended offline    Interrupted (host reset)      90%     16056         -
# 4  Extended offline    Interrupted (host reset)      90%     16056         -

As you can tell, **sdb** has read errors. Does this simply mean its due to be replaced or what?

---

### Post by rubylaser on 2013-04-03
Can you show us the whole smartctl -a /dev/sdb report?
```
smartctl -a /dev/sdb
```
It looks like /dev/sdb is bad, but it would be nice to see the whole report before passing judgement. Also, /dev/sdb1 has mdadm superblock metadata on it, so that would be the proper device to assemble your array with, not /dev/sdb.

---

### Post by agentofcode on 2013-04-03
**smartctl -a /dev/sdb** Returns:
> === START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA1970067
LU WWN Device Id: 5 0014ee 057d8ac55
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Apr  3 17:13:02 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 116) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline
data collection:                (39300) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   166   021    Pre-fail  Always       -       1058
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2310
  5 Reallocated_Sector_Ct   0x0033   193   193   140    Pre-fail  Always       -       144
  7 Seek_Error_Rate         0x002e   200   198   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18416
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       163
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       102
193 Load_Cycle_Count        0x0032   189   189   000    Old_age   Always       -       33380
194 Temperature_Celsius     0x0022   120   108   000    Old_age   Always       -       30
196 Reallocated_Event_Count 0x0032   195   195   000    Old_age   Always       -       5
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       27
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       19
199 UDMA_CRC_Error_Count    0x0032   200   137   000    Old_age   Always       -       26837
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       19

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%     18375         2631941936
# 2  Extended offline    Completed: read failure       40%     18349         2631941936
# 3  Extended offline    Interrupted (host reset)      90%     18343         -
# 4  Extended offline    Interrupted (host reset)      90%     18343         -

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


---

### Post by rubylaser on 2013-04-03
That didn't format very well, but it looks like you have a whole bunch of UDMA CRC Errors ([COLOR=#000000]*26837)*[/COLOR] which almost always point to a bad SATA cable.  Try replacing the cable with a known working one, and then run a long smart test on the disk again.  If it still fails the long test after doing that, then you need to replace the disk.

---

### Post by agentofcode on 2013-04-03
*[COLOR=#b22222]**Note to self**:[/COLOR]*
Using **hdparm -i /dev/sdb** displays HDD information including its serial.

I used this to get the serial of the HDD to match with the physical drive in the case to determine which cable needed to be switched.

---

### Post by agentofcode on 2013-04-04
**smartctl -s on -t long /dev/sdb **ran on alternate SATA cable and port

**smartctl -a /dev/sdb** Returns

> === START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Green (Adv. Format)
Device Model:     WDC WD20EARS-00MVWB0
Serial Number:    WD-WMAZA1970067
LU WWN Device Id: 5 0014ee 057d8ac55
Firmware Version: 51.0AB51
User Capacity:    2,000,398,934,016 bytes [2.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Apr  4 07:01:09 2013 EDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82) Offline data collection activity
                                        was completed without error.
                                        Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 116) The previous self-test completed having
                                        the read element of the test failed.
Total time to complete Offline
data collection:                (39300) seconds.
Offline data collection
capabilities:                    (0x7b) SMART execute Offline immediate.
                                        Auto Offline data collection on/off support.
                                        Suspend Offline collection upon new
                                        command.
                                        Offline surface scan supported.
                                        Self-test supported.
                                        Conveyance Self-test supported.
                                        Selective Self-test supported.
SMART capabilities:            (0x0003) Saves SMART data before entering
                                        power-saving mode.
                                        Supports SMART auto save timer.
Error logging capability:        (0x01) Error logging supported.
                                        General Purpose Logging supported.
Short self-test routine
recommended polling time:        (   2) minutes.
Extended self-test routine
recommended polling time:        ( 255) minutes.
Conveyance self-test routine
recommended polling time:        (   5) minutes.
SCT capabilities:              (0x3035) SCT Status supported.
                                        SCT Feature Control supported.
                                        SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   253   166   021    Pre-fail  Always       -       1050
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2312
  5 Reallocated_Sector_Ct   0x0033   193   193   140    Pre-fail  Always       -       144
  7 Seek_Error_Rate         0x002e   200   198   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   075   075   000    Old_age   Always       -       18429
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       165
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       102
193 Load_Cycle_Count        0x0032   189   189   000    Old_age   Always       -       33509
194 Temperature_Celsius     0x0022   121   108   000    Old_age   Always       -       29
196 Reallocated_Event_Count 0x0032   195   195   000    Old_age   Always       -       5
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       27
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       19
199 UDMA_CRC_Error_Count    0x0032   200   137   000    Old_age   Always       -       26837
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       19

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%     18424         2631941936
# 2  Extended offline    Completed: read failure       40%     18375         2631941936
# 3  Extended offline    Completed: read failure       40%     18349         2631941936
# 4  Extended offline    Interrupted (host reset)      90%     18343         -
# 5  Extended offline    Interrupted (host reset)      90%     18343         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.***[COLOR=#b22222][/COLOR]***

---

### Post by agentofcode on 2013-04-05
Correct me if I am wrong but assuming I posted the most current log, it appears that sdb is bad. If this is the same version log, then I am unsure on how to select an alternate "SMART Error Log Version". Also I just discovered the dependability issues with using green drives in a RAID. Not enough preliminary research on my part, rookie mistake. Since discovering this, I have gone ahead and ordered replacement drives to build a dependable RAID5.

Now my goal is to get this broken RAID5 back to functional status so I can back up the data prior to setting up the new RAID5 with more dependable HDDs.

---

### Post by agentofcode on 2013-04-05
Since I determined sdb is bad I decided to try:

[B]mdadm --stop /dev/md0
mdadm --assemble --force /dev/md0 /dev/sd[cd][/B]

to reassemble the RAID with out sdb.

Returns:
> mdadm: Cannot assemble mbr metadata on /dev/sdc
mdadm: /dev/sdc has no superblock - assembly aborted

**Where do I go from here?**

---

### Post by rubylaser on 2013-04-05
You need to assemble with the partitions on those disks like this.
```
**mdadm --assemble --force /dev/md0 /dev/sd[cd]1**
```

---

### Post by agentofcode on 2013-04-05
Just tried **mdadm --assemble --force /dev/md0 /dev/sd[bcd]1**

Returns:
> mdadm: /dev/md0 has been started with 2 drives (out of 3) and 1 rebuilding.

** Why would sdb1 begin working again? Does the output not state it is bad?**

---

### Post by agentofcode on 2013-04-05
**cat /proc/mdstat**

Returns:
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdb1[3] sdd1[2] sdc1[1]
      3899417600 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/2] [_UU]
      [=>...................]  recovery =  7.6% (149796000/1949708800) finish=258.9min speed=115848K/sec
 
unused devices: <none>


[B][COLOR=#b22222]UPDATE: 4/5/13, 10:51PM est
[/COLOR][/B]The assembly came back with sdb1[F]. I understand this indicates that the drive  failed. So I stopped and started the RAID again with just sdc1 and sdd1 per recommendation.
RAID is now assembled but still not accessible.

---

### Post by agentofcode on 2013-04-05
When I start up a terminal I notice a message:
> Could not chdir to home directory /home/*username*: No such file or directory
And when I try to access my files via webmin, nothing is in the home directory. Seems as though the RAID5 forgot what directory it was linked up with.

---

### Post by agentofcode on 2013-04-05
**fdisk -l** Returns
 > 
Disk /dev/sda: 60.0 GB, 60021399040 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117229295 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001d60b
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   109893631    54945792   83  Linux
/dev/sda2       109895678   117227519     3665921    5  Extended
/dev/sda5       109895680   117227519     3665920   82  Linux swap / Solaris
 
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000edfb2
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3899691007  1949844480   fd  Linux raid autodetect
/dev/sdc2      3899693054  3907028991     3667969    5  Extended
/dev/sdc5      3899693056  3907028991     3667968   82  Linux swap / Solaris
 
Disk /dev/sdd: 2000.4 GB, 2000394706432 bytes
255 heads, 63 sectors/track, 243200 cylinders, total 3907020911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000740d4
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3899682815  1949840384   fd  Linux raid autodetect
/dev/sdd2      3899684862  3907018751     3666945    5  Extended
/dev/sdd5      3899684864  3907018751     3666944   82  Linux swap / Solaris
 
Disk /dev/md0: 3993.0 GB, 3993003622400 bytes
2 heads, 4 sectors/track, 974854400 cylinders, total 7798835200 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 1048576 bytes
Disk identifier: 0x00000000
 
Disk /dev/md0 doesn't contain a valid partition table

---

### Post by agentofcode on 2013-04-05
I referred back to the [original solved thread]("http://ubuntuforums.org/showthread.php?t=1887913") I mentioned in my first post and discovered I needed to mount it.

```
mount /dev/md0 /home
```

That did the trick :)
I should be good until I get my new drives and can back up my data and rebuild a more dependable RAID, **THANKS!**

**P.S.** I intend to follow your [APC UPS tutorial]("http://zackreed.me/articles/40-ups-protect-your-files") as well. Hope to prevent this from ever happening again.

---

