---
title: "Write cache: enabled, read cache: enabled, doesn't support DPO or FUA"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by sangeetha821 on 2013-01-29
My hard drive partition are gone. my hard drive is detecting but showing unallocated. 
dmesg | grep sda shows as

 4.505930] sd 2:0:1:0: >[sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.539667]  sda: unknown partition table

---

### Post by tgalati4 on 2013-01-30
If you have SMART monitoring then you can check the status of the drive.  Boot from a Live DVD, then open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

Post the output.

---

### Post by sangeetha821 on 2013-01-30
while booting showing no bootable device please insert live cd... so i using through live usb only.
```
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.5.0-17-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.10
Device Model:     ST3160215AS
Serial Number:    6RAAPY7N
Firmware Version: 4.AAB
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jan 30 05:10:20 2013 UTC
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
data collection:         (  430) seconds.
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
recommended polling time:      (  54) minutes.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   079   079   020    Old_age   Always       -       21665
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       297374346
  9 Power_On_Hours          0x0032   094   094   000    Old_age   Always       -       6129
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   078   078   020    Old_age   Always       -       23309
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       3667
189 High_Fly_Writes         0x003a   080   080   000    Old_age   Always       -       20
190 Airflow_Temperature_Cel 0x0022   057   050   045    Old_age   Always       -       43 (Min/Max 30/43)
194 Temperature_Celsius     0x0022   043   050   000    Old_age   Always       -       43 (0 27 0 0 0)
195 Hardware_ECC_Recovered  0x001a   079   074   000    Old_age   Always       -       79400836
197 Current_Pending_Sector  0x0012   001   001   000    Old_age   Always       -       3420
198 Offline_Uncorrectable   0x0010   001   001   000    Old_age   Offline      -       3420
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 3758 (device log contains only the most recent five errors)
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

Error 3758 occurred at disk power-on lifetime: 6025 hours (251 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a3 35 13 e9  Error: UNC at LBA = 0x091335a3 = 152253859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 9d 35 13 e9 00      00:02:05.792  READ DMA
  c8 00 08 05 b7 b4 e8 00      00:02:05.792  READ DMA
  c8 00 20 dd 4d 3f e8 00      00:02:05.710  READ DMA
  ea 00 00 af 9e a1 a0 00      00:02:05.709  FLUSH CACHE EXT
  27 00 00 00 00 00 e0 00      00:02:05.709  READ NATIVE MAX ADDRESS EXT

Error 3757 occurred at disk power-on lifetime: 6025 hours (251 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a3 35 13 e9  Error: UNC at LBA = 0x091335a3 = 152253859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 9d 35 13 e9 00      00:02:05.792  READ DMA
  ca 00 08 75 bc 37 e9 00      00:02:05.792  WRITE DMA
  ea 00 00 9c 35 13 a0 00      00:02:05.710  FLUSH CACHE EXT
  c8 00 08 95 35 13 e9 00      00:02:05.709  READ DMA
  ca 00 60 15 bc 37 e9 00      00:02:05.709  WRITE DMA

Error 3756 occurred at disk power-on lifetime: 6025 hours (251 days + 1 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 a3 35 13 e9  Error: UNC at LBA = 0x091335a3 = 152253859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 00 35 35 13 e9 00      00:02:00.670  READ DMA
  c8 00 00 35 34 13 e9 00      00:02:00.668  READ DMA
  c8 00 00 35 33 13 e9 00      00:02:00.666  READ DMA
  c8 00 00 35 32 13 e9 00      00:02:00.665  READ DMA
  c8 00 00 35 31 13 e9 00      00:02:00.663  READ DMA

Error 3755 occurred at disk power-on lifetime: 5923 hours (246 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 de 6d 88 e7  Error: UNC at LBA = 0x07886dde = 126381534

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 dd 6d 88 e7 00      00:00:54.937  READ DMA
  c8 00 b0 5d de 60 ea 00      00:00:54.919  READ DMA
  c8 00 10 6d db 17 ea 00      00:00:54.856  READ DMA
  c8 00 08 3d a0 b7 e9 00      00:00:54.851  READ DMA
  c8 00 00 f5 60 5f ea 00      00:00:54.844  READ DMA

Error 3754 occurred at disk power-on lifetime: 5923 hours (246 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 de 6d 88 e7  Error: UNC at LBA = 0x07886dde = 126381534

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 08 dd 6d 88 e7 00      00:00:51.401  READ DMA
  c8 00 00 45 90 5f ea 00      00:00:51.400  READ DMA
  c8 00 08 d5 6d 88 e7 00      00:00:51.400  READ DMA
  c8 00 b8 8d 8f 5f ea 00      00:00:51.393  READ DMA
  c8 00 08 cd 6d 88 e7 00      00:00:51.393  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      6125         -
# 2  Extended offline    Interrupted (host reset)      90%      6120         -
# 3  Short offline       Completed without error       00%      6120         -

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

---

