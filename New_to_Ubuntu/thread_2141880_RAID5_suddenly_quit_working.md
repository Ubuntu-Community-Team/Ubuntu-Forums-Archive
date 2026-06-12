---
title: "RAID5 suddenly quit working"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by pathos_society on 2013-05-04
I've got a server running ubuntu with four 2TB HDDs in a RAID5 setup that's been working perfectly for two years.

Today, my wife woke me up to tell me the server was coming up "DEGRADED."  Upon checking Disk Utility, the worst possible result showed up - two of the four disks were showing faulty.

Trying not to panic, I shut down the machine and checked all the cables to see if, possibly, something came unplugged from inside the machine, and one of the SATA power plugs on one of the HDDs was a LITTLE bit loose, so I pushed it back in and restarted the machine.

The RAID is now showing up as "Not running; partially assembled," but all four disks are showing "Disk is healthy."

Stopping and starting the RAID again gets me this error message:

```
Error assembling array: mdadm exited with exit code 1: mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array.
```

So for some reason, mdadm isn't seeing all four disks, I'm guessing.  I don't know.  I've used up most of my meager linux knowledge troubleshooting this, and I'd like to know what y'all think I should do next or what y'all need me to screenshot/show code for/anything in the hopes I don't have two bad hard drives and can salvage 4.5 TB of data.

---

### Post by SaturnusDJ on 2013-05-04
What happens when you try a manual assemble like this:
```
mdadm --assemble --force --run /dev/md0 /dev/sd[a-d]1
```
Edit: I think it will fail.

Check disk health for all disks with:
```

smartctl -a /dev/sd...

```

---

### Post by pathos_society on 2013-05-04
```
ryangela@MELFINA:~$ sudo mdadm --assemble --force --run /dev/md0 /dev/sd[b-e]
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted
```

I assumed that I should put sd[b-e] without a 1 since the four disks used in the RAID are listed in Disk Utility as sdb-sde with no 1 afterwards.  sda is a fifth hard drive used only as a boot/OS disk.

I then ran smartctl:

First hard drive:
```
ryangela@MELFINA:~$ sudo smartctl -a /dev/sdb
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDS5C3020ALA632
Serial Number:    ML0220F313HLDD
Firmware Version: ML6OA580
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat May  4 11:12:55 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)    Offline data collection activity
                    was suspended by an interrupting command from host.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (23815) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   136   136   054    Pre-fail  Offline      -       93
  3 Spin_Up_Time            0x0007   180   180   024    Pre-fail  Always       -       305 (Average 306)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       114
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   146   146   020    Pre-fail  Offline      -       29
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       12126
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       114
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       141
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       141
194 Temperature_Celsius     0x0002   157   157   000    Old_age   Always       -       38 (Lifetime Min/Max 22/46)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

Second hard drive:
```
ryangela@MELFINA:~$ sudo smartctl -a /dev/sdc
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD56MGN
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat May  4 11:18:39 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 612) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x30b7)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   107   099   006    Pre-fail  Always       -       1392632
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       147
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   071   060   030    Pre-fail  Always       -       8615334501
  9 Power_On_Hours          0x0032   086   086   000    Old_age   Always       -       12841
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       129
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       9
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   063   049   045    Old_age   Always       -       37 (Lifetime Min/Max 36/37)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       81
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       191
194 Temperature_Celsius     0x0022   037   051   000    Old_age   Always       -       37 (0 20 0 0)
195 Hardware_ECC_Recovered  0x001a   013   004   000    Old_age   Always       -       1392632
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       142129057771037
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       1116743749
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3805655028

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

Third hard drive:
```
ryangela@MELFINA:~$ sudo smartctl -a /dev/sdd
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD204UI
Serial Number:    S2H7JD2B108865
Firmware Version: 1AQ10001
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Sat May  4 11:20:17 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (20400) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       777
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   067   066   025    Pre-fail  Always       -       10097
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       80
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       11802
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   252   252   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       113
181 Program_Fail_Cnt_Total  0x0022   100   100   000    Old_age   Always       -       17703603
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       87
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   057   000    Old_age   Always       -       35 (Lifetime Min/Max 20/43)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       5
223 Load_Retry_Count        0x0032   252   252   000    Old_age   Always       -       0
225 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       113

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Completed [00% left] (0-65535)
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```

Fourth hard drive:
```
ryangela@MELFINA:~$ sudo smartctl -a /dev/sde
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     ST2000DL003-9VT166
Serial Number:    5YD5670X
Firmware Version: CC32
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat May  4 11:21:23 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          ( 653) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
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
recommended polling time:      ( 255) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x30b7)    SCT Status supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   101   099   006    Pre-fail  Always       -       3372136
  3 Spin_Up_Time            0x0003   093   092   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       78
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   054   053   030    Pre-fail  Always       -       661455794701
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       12071
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       119
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       4
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   059   055   045    Old_age   Always       -       41 (Lifetime Min/Max 39/41)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       75
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       118
194 Temperature_Celsius     0x0022   041   045   000    Old_age   Always       -       41 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   010   003   000    Old_age   Always       -       3372136
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       65863323495538
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       4194924103
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2526861005

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

All four hard drives say "SMART overall-health self-assessment test result: PASSED."  Should this give me hope?  Admittedly I'm worried about all the things that say "Pre-fail" and "Old_Age."

---

### Post by SaturnusDJ on 2013-05-04
That's a high amount of errors, but it doesn't always mean the worst.

The drives are never tested. You can do this with
```
smartctl -t short /dev/sd...
```
Instead of short, long and sometimes conveyance are also possible. Long may take half a day however.

Back to raid...
If sdb fails, you should be able to start it degraded with:
```
mdadm --assemble --force --run /dev/md0 /dev/sdc /dev/sdd /dev/sde
```

Now I wonder if /dev/sdb really is missing the superblock.
What does this command return:
```
mdadm --examine /dev/sd*
```

---

### Post by pathos_society on 2013-05-04
```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sdb
mdadm: No md superblock detected on /dev/sdb.
```

However, when I put a 1 afterwards, I get:
```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : b2b9b38b:dc6944ee:63ce601a:c50a0be5
           Name : :DATA OVERMIND
  Creation Time : Sun Oct  9 12:58:20 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 11721064704 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907021568 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 92274bc1:d251084e:38d255cf:0ecd26fd

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  3 20:39:59 2013
       Checksum : 6354e488 - correct
         Events : 23680

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
```

So I tried this:

```
ryangela@MELFINA:~$ sudo mdadm --assemble --force --run /dev/md0 /dev/sd[b-e]1
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: /dev/sdd1 has no superblock - assembly aborted
```

Then I checked sdd1:

```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : b2b9b38b:dc6944ee:63ce601a:c50a0be5
           Name : :DATA OVERMIND
  Creation Time : Sun Oct  9 12:58:20 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 11721064704 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907021568 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 492acdf3:08284f79:26e99ac7:21d62f44

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  3 22:23:04 2013
       Checksum : 69f5c3 - correct
         Events : 23716

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : ..AA ('A' == active, '.' == missing)

```

Not sure if I'm doing something wrong with the code or what.  I tried testing sdb1 and got:

```
ryangela@MELFINA:~$ sudo smartctl -t short /dev/sdb1
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Sat May  4 12:06:16 2013

Use smartctl -X to abort test.
```

It's now been five minutes and nothing's come up.  Should I keep being patient or is there something else I need to do?

---

### Post by SaturnusDJ on 2013-05-04
Okay. Now run "mdadm --examine" for every array member.
Also run "cat /proc/mdstat".
The best is not to start the array because it looks like there is a big data gab between sdb1 and sdd1.

After invoking smart tests, use again smartctl -a /dev/sdb to read the results. Also, smart tests are per device (sdb), not per partition (sdb1). ;)

---

### Post by pathos_society on 2013-05-04
```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : b2b9b38b:dc6944ee:63ce601a:c50a0be5
           Name : :DATA OVERMIND
  Creation Time : Sun Oct  9 12:58:20 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 11721064704 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907021568 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 92274bc1:d251084e:38d255cf:0ecd26fd

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  3 20:39:59 2013
       Checksum : 6354e488 - correct
         Events : 23680

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 1
   Array State : AAAA ('A' == active, '.' == missing)
```

```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : b2b9b38b:dc6944ee:63ce601a:c50a0be5
           Name : :DATA OVERMIND
  Creation Time : Sun Oct  9 12:58:20 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 11721064704 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907021568 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 1691d75c:c89f831f:eb2ff0c5:7778529a

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  3 20:39:59 2013
       Checksum : 6422a51c - correct
         Events : 23680

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
```

```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : b2b9b38b:dc6944ee:63ce601a:c50a0be5
           Name : :DATA OVERMIND
  Creation Time : Sun Oct  9 12:58:20 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 11721064704 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907021568 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 492acdf3:08284f79:26e99ac7:21d62f44

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  3 22:23:04 2013
       Checksum : 69f5c3 - correct
         Events : 23716

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 2
   Array State : ..AA ('A' == active, '.' == missing)
```

```
ryangela@MELFINA:~$ sudo mdadm --examine /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : b2b9b38b:dc6944ee:63ce601a:c50a0be5
           Name : :DATA OVERMIND
  Creation Time : Sun Oct  9 12:58:20 2011
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 11721064704 (5589.04 GiB 6001.19 GB)
  Used Dev Size : 3907021568 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 28e6b2c5:f15fe2f4:cd9e452a:45be4af7

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri May  3 22:23:04 2013
       Checksum : 63a88758 - correct
         Events : 23716

         Layout : left-symmetric
     Chunk Size : 64K

   Device Role : Active device 3
   Array State : ..AA ('A' == active, '.' == missing)
```

Things I noticed:  sdb1 and sdc1 report all array components as active, but sdd1 and sde1 list the first two as missing.

```
ryangela@MELFINA:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[2] sde1[4]
      3907021954 blocks super 1.2
       
unused devices: <none>
```

cat /proc/mdstat also doesn't see sda1 or sdb1.

```
ryangela@MELFINA:~$ sudo smartctl -t short /dev/sdb
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Short self-test routine immediately in off-line mode".
Drive command "Execute SMART Short self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 1 minutes for test to complete.
Test will complete after Sat May  4 12:25:58 2013

Use smartctl -X to abort test.
```

Waiting on this.  How long should it take?

---

### Post by SaturnusDJ on 2013-05-04
After running "mdadm --stop /dev/md0" you're most likely able to assemble a working/running array from the disks with force and run flags. I think however it's better to go a bit more in depth about the health of the disks first.

In the terminal with smartctl, can you press enter? It should only inform you about what it will do and when results are available, the process itself runs in background.
So you start the test and should be able to directly gain back control of the terminal.

---

### Post by pathos_society on 2013-05-04
Yeah, after running "sudo smartctl -t short /dev/sdb" and giving me that information, it goes straight back to the "ryangela@MELFINA:~$" prompt.  Nothing else is happening.  Do I need to run smartctl and then just leave Terminal untouched for a while and then the results will appear?  Am I cancelling the test by continuing to do things?

I tried stopping the array and restarting it and got:

```
ryangela@MELFINA:~$ sudo mdadm --assemble --force --run /dev/md0 /dev/sd[b-e]1
mdadm: forcing event count in /dev/sdc1(0) from 23680 upto 23716
mdadm: forcing event count in /dev/sdb1(1) from 23680 upto 23716
mdadm: failed to add /dev/sdb1 to /dev/md0: Device or resource busy
mdadm: failed to add /dev/sdd1 to /dev/md0: Device or resource busy
mdadm: failed to add /dev/sde1 to /dev/md0: Device or resource busy
mdadm: failed to RUN_ARRAY /dev/md0: Input/output error
mdadm: Not enough devices to start the array.
```

---

### Post by SaturnusDJ on 2013-05-04
That's because, as I tried to explain, you do the command, and the rest happens in background. So after ~1 minute you may run "smartctl -a" for the tested device and see the newly obtained information from the smart test.

Hmm strange. How does "cat /proc/mdstat" look after that?

---

### Post by pathos_society on 2013-05-04
Ah, ok.  Here:

```
ryangela@MELFINA:~$ sudo smartctl -a /dev/sdb
[sudo] password for ryangela: 
smartctl 5.40 2010-07-12 r3124 [x86_64-unknown-linux-gnu] (local build)
Copyright (C) 2002-10 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     Hitachi HDS5C3020ALA632
Serial Number:    ML0220F313HLDD
Firmware Version: ML6OA580
User Capacity:    2,000,398,934,016 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sat May  4 13:11:00 2013 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:          (23815) seconds.
Offline data collection
capabilities:              (0x5b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      ( 255) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   136   136   054    Pre-fail  Offline      -       93
  3 Spin_Up_Time            0x0007   180   180   024    Pre-fail  Always       -       305 (Average 306)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       114
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   146   146   020    Pre-fail  Offline      -       29
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       12128
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       114
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       141
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       141
194 Temperature_Celsius     0x0002   157   157   000    Old_age   Always       -       38 (Lifetime Min/Max 22/46)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     12127         -
# 2  Short offline       Completed without error       00%     12127         -
# 3  Short offline       Completed without error       00%     12127         -
# 4  Short offline       Completed without error       00%     12127         -
# 5  Short offline       Completed without error       00%     12127         -
# 6  Short offline       Completed without error       00%     12127         -

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

I'm guessing the "SMART Self-test log structure revision number 1" part shows the test results?  I may have tried doing it six times because nothing was coming up.  Oops.

```
ryangela@MELFINA:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdb1[1] sde1[4] sdd1[2]
      5860532931 blocks super 1.2
       
unused devices: <none>
```

Ok, cat now sees sdb1, which is a step in the right direction.

I tried stopping the array in Disk Utility and then running mdadm force/run again, and got:

```
ryangela@MELFINA:~$ sudo mdadm --assemble --force --run /dev/md0 /dev/sd[b-e]1
mdadm: /dev/md0 has been started with 4 drives.
```

And now the RAID5 is listed as "Running" and "Resyncing," and I can access all the data that was stored on the RAID.  So I'm not sure how, but things seem to be working again.  Is there anything else I should run/check real quick to make sure that everything isn't about to die again?

I'm also assuming from all the "Old_Age" and "Pre-fail" results that all four of my hard drives are getting ready to cack themselves and should be replaced post-haste?

---

### Post by SaturnusDJ on 2013-05-04
That's right.

That's the result (successful assembly) I was expecting to see one post earlier. :)

Do you have a backup of important data? If not, now is your chance.

None of the attributes with high counts, are considered critical. So it's hard to say if the disks are really dying. Only thing I know, I've not seen such high counts before. But /dev/sdb looks healthy.
"G-Sense_Error_Rate" for the third disk caught my eye. Other attributes also suggest a possible mechanical damage/malfunction. Is it possible the disks/server dropped physically?

After backup of data, run the 'long' smart test for the drives, and keep an eye at the smart data. (You can run smartctl -A /dev/sd... to only get the attributes data printed out.) Then you can see if the "Seek_Error_Rate" and other attributes increase.

---

### Post by pathos_society on 2013-05-04
Ok, will do.  Thank you for all your help!

---

### Post by RJARRRPCGP on 2013-05-04
The HDD for /dev/sde is faulty. Unusual "Hardware ECC Recovered" attribute of "010"! 

And the worst value reported was only "003"!

Looks like the HDD board is fubar. 

MHDD and Victoria cannot fix this HDD. Sorry.

---

