---
title: "Grub Error 17"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by joe78 on 2014-02-27
I have had a dual boot setup on my laptop for several years and it would bring me to a Grub loader page for 5 seconds on bootup and then default to Windows if I didn't manually select Linux.  For an unknown reason, I am suddenly getting a Grub Error 17 message.  I've tried to work through many suggestions, but am stuck.  

I have a Damn Small Linux boot disk and luckily can see my files saved in Windows.  I would like to fix this so that I can boot to Windows XP.  

When I run sudo fdisk -l, I get two sections.  Disk /dev/sda1 and then a second section with /devhda1 all the way up to /dev/hda7 (without 3 or 4).  hda5 and hda7 are listed as Linux and Hda6 is listed as Linux swap.  During bootup in expert mode in DSL, I note that it says it booting from the swap partition.  Not sure if this is important.  

I can't mount hda1 (relocation error).  But I can mount sda1.  

Any thoughts on next thing to try?  Or do you need more information?

---

### Post by sandyd on 2014-02-27
Your hard drive may be doing bad - have you tried running smartmontools to retrieve the smart status?

You can gather drive information by running
```

smartctl -H /dev/hda
smartctl --test=short /dev/hda
smartctl -a /dev/hda
```
You may have to install smartmontools if it is not already installed

---

### Post by Bucky Ball on 2014-02-27
What release of Ubuntu have you got installed?

---

### Post by oldfred on 2014-02-28
That error is from grub legacy which Ubuntu has not used since 9.04 as the standard. But grub legacy is still available. Also if drives are shown as hda not sda you must have a very old install. 

Some suggestions:
17 : Cannot mount selected partition
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

---

### Post by joe78 on 2014-03-02
```
=== START OF INFORMATION SECTION ===
Device Model:     ST960812A
Serial Number:    5PJ1QQF7
Firmware Version: 3.05
User Capacity:    60,011,642,880 bytes [60.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   6
ATA Standard is:  ATA/ATAPI-6 T13 1410D revision 2
Local Time is:    Sun Mar  2 20:01:40 2014 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (  426) seconds.
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
                    No General Purpose Logging support.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  39) minutes.
SCT capabilities:            (0x0001)    SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0002   097   096   000    Old_age   Always       -       0
  4 Start_Stop_Count        0x0033   098   098   020    Pre-fail  Always       -       2763
  5 Reallocated_Sector_Ct   0x0033   098   098   036    Pre-fail  Always       -       104
  7 Seek_Error_Rate         0x000f   087   060   030    Pre-fail  Always       -       586903202
  9 Power_On_Hours          0x0032   067   067   000    Old_age   Always       -       29518
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0033   098   098   020    Pre-fail  Always       -       2739
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       11795
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   060   040   045    Old_age   Always   In_the_past 40 (0 238 47 38)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       220
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       741083
194 Temperature_Celsius     0x0022   040   060   000    Old_age   Always       -       40 (0 14 0 0)
195 Hardware_ECC_Recovered  0x001a   076   045   000    Old_age   Always       -       213616967
197 Current_Pending_Sector  0x0012   099   099   000    Old_age   Always       -       27
198 Offline_Uncorrectable   0x0010   099   099   000    Old_age   Offline      -       27
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 4286 (device log contains only the most recent five errors)
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

Error 4286 occurred at disk power-on lifetime: 29518 hours (1229 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 38 90 6a 47 e5  Error: UNC 56 sectors at LBA = 0x05476a90 = 88566416

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 38 90 6a 47 e5 00      01:50:15.439  READ DMA
  ec 00 00 00 00 00 a0 02      01:50:15.432  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:50:10.824  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      01:47:20.829  IDENTIFY DEVICE
  c8 00 38 90 6a 47 e5 00      01:47:20.610  READ DMA

Error 4285 occurred at disk power-on lifetime: 29518 hours (1229 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 38 90 6a 47 e5  Error: IDNF 56 sectors at LBA = 0x05476a90 = 88566416

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 38 90 6a 47 e5 00      01:50:15.439  READ DMA
  ec 00 00 00 00 00 a0 02      01:50:15.432  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:50:10.824  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      01:47:20.829  IDENTIFY DEVICE
  c8 00 40 08 6c 47 e5 00      01:47:20.610  READ DMA

Error 4284 occurred at disk power-on lifetime: 29518 hours (1229 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 40 08 6c 47 e5  Error: UNC 64 sectors at LBA = 0x05476c08 = 88566792

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 08 6c 47 e5 00      01:50:15.439  READ DMA
  ec 00 00 00 00 00 a0 02      01:50:15.432  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:50:10.824  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      01:47:20.829  IDENTIFY DEVICE
  c8 00 40 08 6c 47 e5 00      01:47:20.610  READ DMA

Error 4283 occurred at disk power-on lifetime: 29518 hours (1229 days + 22 hours)
  When the command that caused the error occurred, the device was doing SMART Offline or Self-test.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  10 51 40 08 6c 47 e5  Error: IDNF 64 sectors at LBA = 0x05476c08 = 88566792

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 40 08 6c 47 e5 00      01:46:02.345  READ DMA
  b0 d4 00 01 4f c2 00 00      01:46:02.345  SMART EXECUTE OFF-LINE IMMEDIATE
  b0 d0 01 00 4f c2 00 00      01:50:10.824  SMART READ DATA
  ec 00 01 00 00 00 00 00      01:47:20.829  IDENTIFY DEVICE
  ec 00 01 00 00 00 00 00      01:47:20.610  IDENTIFY DEVICE

Error 4282 occurred at disk power-on lifetime: 29518 hours (1229 days + 22 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 05 87 6b 4b e4  Error: UNC 5 sectors at LBA = 0x044b6b87 = 72051591

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 05 87 6b 4b e4 00      01:08:35.783  READ DMA
  ec 00 00 00 00 00 a0 02      01:08:35.769  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 02      01:08:35.751  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 02      01:08:35.745  IDENTIFY DEVICE
  c8 00 01 85 6b 4b e4 00      01:08:33.858  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed: read failure       90%     29518         14755481
# 2  Short offline       Completed: read failure       90%     29512         72051589
# 3  Short offline       Completed: read failure       90%     29512         72051589
# 4  Short offline       Completed: read failure       90%     29510         8549974
# 5  Short offline       Completed: electrical failure 90%     29510         102863437

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

### Post by joe78 on 2014-03-02
I just downloaded and installed Ubuntu 12.04.4 LTS.  Above is the result of the smartmontools output as suggested.

---

### Post by oldfred on 2014-03-02
If it says passed that is all I know. All the other detail is just to confirm that, but may give more info for those that understand that detail.

Have you tried fsck on all Linux formatted partitions?

 #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by joe78 on 2014-03-03
Thanks all for your help.  I'm resigned to the fact that my hard drive is toast.  I've tried mounting it on a few different computers and it it not recognized.  The Ubuntu Disk Check Utility showed several items outside of acceptable parameter values.  I may look deeper into how to recover files, but a run on Recuva found no files.  Any final thoughts are appreciated, but otherwise this can be closed.

---

### Post by Bucky Ball on 2014-03-03
Just mark as solved to help others by following the instructions in the link in my signature. The thread won't be closed by doing this so people can still add final thoughts.

---

