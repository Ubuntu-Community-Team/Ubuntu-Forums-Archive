---
title: "Smartd to check SSD Disk Health"
date: 2020-01-16
forum: New to Ubuntu
---

### Post by giobaxx on 2020-01-16
Hello all

I'm experiencing a boot problems with an ubuntu desktop where the boot process  drops to the busybox shell . I run fsck from a live version and at that point the system seems booting correctly but i found a lot of ata error running dmesg and in the syslog file like this:

```

Kernel: [18756.192066] ata5.00: exception Emask 0x0 SAct 0xc000 SErr 0x0 action 0x0kernel: [18756.192072] ata5.00: irq_stat 0x40000008
kernel: [18756.192077] ata5.00: failed command: READ FPDMA QUEUED
kernel: [18756.192085] ata5.00: cmd 60/00:70:e0:08:1b/01:00:14:00:00/40 tag 14 ncq dma 131072 in
kernel: [18756.192085]          res 41/40:70:70:09:1b/00:01:14:00:00/00 Emask 0x409 (media error) <F>
kernel: [18756.192088] ata5.00: status: { DRDY ERR }
kernel: [18756.192091] ata5.00: error: { UNC }
kernel: [18756.193158] ata5.00: configured for UDMA/133
kernel: [18756.193166] sd 4:0:0:0: [sda] tag#14 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [18756.193167] sd 4:0:0:0: [sda] tag#14 Sense Key : Medium Error [current] 
kernel: [18756.193169] sd 4:0:0:0: [sda] tag#14 Add. Sense: Unrecovered read error - auto reallocate failed
kernel: [18756.193170] sd 4:0:0:0: [sda] tag#14 CDB: Read(10) 28 00 14 1b 08 e0 00 01 00 00
kernel: [18756.193171] print_req_error: I/O error, dev sda, sector 337316208
kernel: [18756.193179] ata5: EH complete
kernel: [18756.291949] ata5.00: exception Emask 0x0 SAct 0x3f80 SErr 0x0 action 0x0
kernel: [18756.291951] ata5.00: irq_stat 0x40000008
kernel: [18756.291953] ata5.00: failed command: READ FPDMA QUEUED
kernel: [18756.291955] ata5.00: cmd 60/08:38:70:09:1b/00:00:14:00:00/40 tag 7 ncq dma 4096 in
kernel: [18756.291955]          res 41/40:08:70:09:1b/00:00:14:00:00/00 Emask 0x409 (media error) <F>
kernel: [18756.291956] ata5.00: status: { DRDY ERR }
kernel: [18756.291957] ata5.00: error: { UNC }
kernel: [18756.292911] ata5.00: configured for UDMA/133
kernel: [18756.292916] sd 4:0:0:0: [sda] tag#7 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
kernel: [18756.292917] sd 4:0:0:0: [sda] tag#7 Sense Key : Medium Error [current] 
kernel: [18756.292318] sd 4:0:0:0: [sda] tag#7 Add. Sense: Unrecovered read error - auto reallocate failed
kernel: [18756.292919] sd 4:0:0:0: [sda] tag#7 CDB: Read(10) 28 00 14 1b 09 70 00 00 08 00
kernel: [18756.292220] print_req_error: I/O error, dev sda, sector 337316208
kernel: [18756.292927] ata5: EH complete
```

but i don't know how to interpret these errors, they are hardware problems? With gsmartcontrol i run also a self-short test with no errors but with this reports:

```

smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-64-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF INFORMATION SECTION ===
Device Model:     SK hynix SC308 SATA 512GB
Serial Number:    FJ6AN56621040AO1Q
Firmware Version: 30001P10
User Capacity:    512.110.190.592 bytes [512 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Jan 16 17:29:48 2020 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x02)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   4)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  105) seconds.
Offline data collection
capabilities:              (0x19) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0002)    Does not save SMART data before
                    entering power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  40) minutes.


SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1   Raw_Read_Error_Rate     0x000f   166   166   006    Pre-fail  Always       -       53
  5   Reallocated_Sector_Ct   0x0032   253   100   036    Old_age   Always       -       0
  9   Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       21729
 12  Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       89
100 Unknown_Attribute       0x0032   098   098   000    Old_age   Always       -       89390658
171 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0030   100   100   000    Old_age   Offline      -       44
175 Program_Fail_Count_Chip 0x0032   253   253   000    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   253   253   000    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0032   037   037   000    Old_age   Always       -       677
178 Used_Rsvd_Blk_Cnt_Chip  0x0032   100   100   000    Old_age   Always       -       96
179 Used_Rsvd_Blk_Cnt_Tot   0x0032   100   100   000    Old_age   Always       -       578
180 Unused_Rsvd_Blk_Cnt_Tot 0x0032   100   100   000    Old_age   Always       -       10430
181 Program_Fail_Cnt_Total  0x0032   253   253   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   253   253   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   253   253   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       57
188 Command_Timeout         0x0032   253   253   000    Old_age   Always       -       0
191 Unknown_SSD_Attribute   0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   035   000   000    Old_age   Always       -       35 (Min/Max 12/67)
195 Hardware_ECC_Recovered  0x0032   086   001   000    Old_age   Always       -       598249198
199 UDMA_CRC_Error_Count    0x0032   253   253   000    Old_age   Always       -       0
201 Unknown_SSD_Attribute   0x000e   100   100   000    Old_age   Always       -       53
204 Soft_ECC_Correction     0x000e   001   001   000    Old_age   Always       -       408369
231 Temperature_Celsius     0x0033   037   037   010    Pre-fail  Always       -       64
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       735787569568
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       30390826955
242 Total_LBAs_Read         0x0032   100   100   000    Old_age   Always       -       34100204301
250 Read_Error_Retry_Rate   0x0032   100   100   000    Old_age   Always       -       40172041


SMART Error Log Version: 1
ATA Error Count: 94 (device log contains only the most recent five errors)
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


Error 94 occurred at disk power-on lifetime: 21727 hours (905 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 30 c0 99 0d 40 40   2d+00:31:18.750  READ FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+00:31:18.740  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0   2d+00:31:18.740  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0   2d+00:31:18.740  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0   2d+00:31:18.740  IDENTIFY DEVICE


Error 93 occurred at disk power-on lifetime: 21727 hours (905 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 10 c0 99 0d 40 40   2d+00:31:18.700  READ FPDMA QUEUED
  60 08 08 b8 99 0d 40 40   2d+00:31:18.700  READ FPDMA QUEUED
  60 08 00 b0 99 0d 40 40   2d+00:31:18.700  READ FPDMA QUEUED
  60 08 f0 a8 99 0d 40 40   2d+00:31:18.700  READ FPDMA QUEUED
  60 08 e8 a0 99 0d 40 40   2d+00:31:18.700  READ FPDMA QUEUED


Error 92 occurred at disk power-on lifetime: 21727 hours (905 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 18 e0 96 0d 40 40   2d+00:31:18.610  READ FPDMA QUEUED
  61 08 10 c0 63 90 40 40   2d+00:31:18.610  WRITE FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+00:31:18.610  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0   2d+00:31:18.610  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0   2d+00:31:18.610  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]


Error 91 occurred at disk power-on lifetime: 21727 hours (905 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 e8 e0 96 0d 40 40   2d+00:31:18.560  READ FPDMA QUEUED
  60 08 e0 d8 96 0d 40 40   2d+00:31:18.560  READ FPDMA QUEUED
  60 08 d8 d0 96 0d 40 40   2d+00:31:18.560  READ FPDMA QUEUED
  60 08 d0 c8 96 0d 40 40   2d+00:31:18.560  READ FPDMA QUEUED
  60 08 c8 c0 96 0d 40 40   2d+00:31:18.560  READ FPDMA QUEUED


Error 90 occurred at disk power-on lifetime: 21727 hours (905 days + 7 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 38 8b 0d 40 40   2d+00:31:18.490  READ FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+00:31:18.490  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0   2d+00:31:18.480  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0   2d+00:31:18.480  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0   2d+00:31:18.480  IDENTIFY DEVICE


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     21727         -
# 2  Short offline       Completed without error       00%         0         -


Selective Self-tests/Logging not supported



```

Could someone tell me how learn these report? i'm really confused also because running the short test no errors appears. 


Tanks a lot

---

### Post by CatKiller on 2020-01-16
The short SMART test isn't comprehensive.

Inconsistent data meaning that you're forced to run fsck, and failed SMART tests, certainly sounds like hard drive failure to me.

---

### Post by oldrocker99 on 2020-01-16
Have you been running a trim operation on the SSD? If you haven't, that **could** be the problem.

---

### Post by giobaxx on 2020-01-17
No, i don't think so ...i mean is not my computer....and i don't know what he did. During the boot process it drops in busybox and i run the fsck to fix the filesystem. After that the system booted correctly but i think it has hardware problems, i mean the disk.

But frankly i'm not so good to read the smart report to understand if i'm facing hardware or software problems(file system) on the disk

---

### Post by mastablasta on 2020-01-17
this will help you understand the values: [https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)

Disk looks fine (hardware wise).

see here on how to verify trim is working and being done: [https://askubuntu.com/questions/1034169/is-trim-enabled-on-my-ubuntu-18-04-installation](https://askubuntu.com/questions/1034169/is-trim-enabled-on-my-ubuntu-18-04-installation)

also note that poorly connected or faulty disk cables can cause errors that appear as if disk is bad. had it once, and almost went crazy troubleshooting it. by chance i got an idea that maybe cable is malfunctioning. i changed the SATA cable and it hasn't crashed since 2005 until today.

---

### Post by TheFu on 2020-01-17
I think it is a cable or PSU issue.  Swap out the connecting cable or at least re-seat the connection.

---

### Post by giobaxx on 2020-01-18
Tanks to Everyone!!!! On Monday i will try to unmount and remount the SSD...and i will update the post

---

### Post by giobaxx on 2020-01-21
Update:

I've xc checked the Trim Service and is Running and i have also re-seat the connection cable and the things seems going in the right way. We didn't receive any smartd alert via mail anymore, and in dmesg it does not appear the ata5 erros. Also the smart report has changed with the Soft Read Error Rate changed in the RAW Value from 53 to 0

```
martctl 6.6 2016-05-31 r4324 [x86_64-linux-4.15.0-64-generic] (local build)Copyright (C) 2002-16, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF INFORMATION SECTION ===
Device Model:     SK hynix SC308 SATA 512GB
Firmware Version: 30001P10
User Capacity:    512.110.190.592 bytes [512 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Form Factor:      2.5 inches
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2 (minor revision not indicated)
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Tue Jan 21 13:14:02 2020 CET
SMART support is: Available - device has SMART capability.
SMART support is: Enabled


=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED


General SMART Values:
Offline data collection status:  (0x06)    Offline data collection activity
                    was aborted by the device with a fatal error.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (  113) seconds.
Offline data collection
capabilities:              (0x19) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    No Conveyance Self-test supported.
                    No Selective Self-test supported.
SMART capabilities:            (0x0002)    Does not save SMART data before
                    entering power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      (  40) minutes.


SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   166   166   006    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0032   253   100   036    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   076   076   000    Old_age   Always       -       21844
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       90
100 Unknown_Attribute       0x0032   098   098   000    Old_age   Always       -       89557139
171 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
172 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
174 Unknown_Attribute       0x0030   100   100   000    Old_age   Offline      -       44
175 Program_Fail_Count_Chip 0x0032   253   253   000    Old_age   Always       -       0
176 Erase_Fail_Count_Chip   0x0032   253   253   000    Old_age   Always       -       0
177 Wear_Leveling_Count     0x0032   037   037   000    Old_age   Always       -       678
178 Used_Rsvd_Blk_Cnt_Chip  0x0032   100   100   000    Old_age   Always       -       96
179 Used_Rsvd_Blk_Cnt_Tot   0x0032   100   100   000    Old_age   Always       -       578
180 Unused_Rsvd_Blk_Cnt_Tot 0x0032   100   100   000    Old_age   Always       -       10430
181 Program_Fail_Cnt_Total  0x0032   253   253   000    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   253   253   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   253   253   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       57
188 Command_Timeout         0x0032   253   253   000    Old_age   Always       -       0
191 Unknown_SSD_Attribute   0x0032   253   253   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   029   000   000    Old_age   Always       -       29 (Min/Max 12/67)
195 Hardware_ECC_Recovered  0x0032   086   001   000    Old_age   Always       -       601307169
199 UDMA_CRC_Error_Count    0x0032   253   253   000    Old_age   Always       -       0
201 Unknown_SSD_Attribute   0x000e   100   100   000    Old_age   Always       -       0
204 Soft_ECC_Correction     0x000e   062   001   000    Old_age   Always       -       2385
231 Temperature_Celsius     0x0033   037   037   010    Pre-fail  Always       -       64
234 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       737161747424
241 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       30426218811
242 Total_LBAs_Read         0x0032   100   100   000    Old_age   Always       -       34274508669
250 Read_Error_Retry_Rate   0x0032   100   100   000    Old_age   Always       -       40205059


SMART Error Log Version: 1
ATA Error Count: 190 (device log contains only the most recent five errors)
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


Error 190 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 40 18 40 7f 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 48 10 f0 7e 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 08 08 e0 7e 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 50 00 88 7e 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 08 90 c0 99 0d 40 40   2d+02:29:23.530  READ FPDMA QUEUED


Error 189 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 c0 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 48 b8 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 40 b0 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 38 a8 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 30 a0 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED


Error 188 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 c0 78 60 43 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  60 10 b8 20 60 43 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  60 08 b0 10 60 43 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  60 08 48 e0 96 0d 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+02:29:23.440  READ LOG DMA EXT


Error 187 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 e0 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 00 d8 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 f0 d0 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 e8 c8 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 e0 c0 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED


Error 186 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 c0 38 8b 0d 40 40   2d+02:29:23.340  READ FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+02:29:23.340  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0   2d+02:29:23.340  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0   2d+02:29:23.340  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0   2d+02:29:23.340  IDENTIFY DEVICE


SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     21842         234869464
# 2  Extended offline    Completed: read failure       90%     21842         162334216
# 3  Extended offline    Completed: read failure       90%     21842         45290872
# 4  Extended offline    Completed: read failure       90%     21745         45291120
# 5  Short offline       Completed without error       00%     21727         -
# 6  Short offline       Completed without error       00%         0         -


Selective Self-tests/Logging not supported
```

What i still dont understand these error below, are old errors?

*IE: Error 190 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours) --> it means that this error is happened 905 days and 9 hour since the SSD is online?*

```
Error 190 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 40 18 40 7f 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 48 10 f0 7e 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 08 08 e0 7e 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 50 00 88 7e 43 40 40   2d+02:29:23.530  READ FPDMA QUEUED
  60 08 90 c0 99 0d 40 40   2d+02:29:23.530  READ FPDMA QUEUED


Error 189 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 50 c0 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 48 b8 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 40 b0 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 38 a8 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED
  60 08 30 a0 99 0d 40 40   2d+02:29:23.490  READ FPDMA QUEUED


Error 188 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 c0 78 60 43 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  60 10 b8 20 60 43 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  60 08 b0 10 60 43 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  60 08 48 e0 96 0d 40 40   2d+02:29:23.440  READ FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+02:29:23.440  READ LOG DMA EXT


Error 187 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 08 e0 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 00 d8 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 f0 d0 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 e8 c8 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED
  60 08 e0 c0 96 0d 40 40   2d+02:29:23.400  READ FPDMA QUEUED


Error 186 occurred at disk power-on lifetime: 21729 hours (905 days + 9 hours)
  When the command that caused the error occurred, the device was active or idle.


  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 00 00 00  Error: UNC at LBA = 0x00000000 = 0


  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 c0 38 8b 0d 40 40   2d+02:29:23.340  READ FPDMA QUEUED
  47 00 01 30 08 00 a0 a0   2d+02:29:23.340  READ LOG DMA EXT
  ef 10 02 00 00 00 a0 a0   2d+02:29:23.340  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 e0   2d+02:29:23.340  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]
  ec 00 00 00 00 00 a0 a0   2d+02:29:23.340  IDENTIFY DEVICE
```

and this errors at the end of the report  after I run a test with gsmartcontrol an extended test.  It always finish in few minutes instead of the 40 minutes it say with the following error:

```
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     21842         234869464
# 2  Extended offline    Completed: read failure       90%     21842         162334216
# 3  Extended offline    Completed: read failure       90%     21842         45290872
# 4  Extended offline    Completed: read failure       90%     21745         45291120
# 5  Short offline       Completed without error       00%     21727         -
# 6  Short offline       Completed without error       00%         0         -
```

All of these errors mentioned because historically happened? and are they just for keeping track along the life cycle of the disk?

---

### Post by mastablasta on 2020-01-21
you would have to see what these tests mean. i wish i could help more, but i never used an SSD :) (yet). 

[https://serverfault.com/questions/296024/does-this-smart-selftest-indicate-a-failing-drive](https://serverfault.com/questions/296024/does-this-smart-selftest-indicate-a-failing-drive)

---

### Post by TheFu on 2020-01-21
too hard to read the new output.  Use CODE TAGS!

---

