---
title: "Root filesystem going to Read-only Mode frquently"
date: 2021-08-09
forum: New to Ubuntu
---

### Post by muralikris39 on 2021-08-09
I have been facing read-only filesystem error issue for past few weeks  after my SMPS failure. I replaced SMPS with new one and system started  to boot up. But quite frquently I am experiencing my primary hard disk  partition /dev/sda1 goes to read-only mode for some unknown reasons. I  was on Kubuntu 18.04 when i faced the issue.

I tried fsck ,e2fsck smartmontools as resolution steps those worked temporarily to get  into read-write mode. e2fsck or smarmontools does not reveal any bad  blocks either and test results show passed. I am attaching report of boot repair summary of my grub  configuration.[https://paste.ubuntu.com/p/jRTVMSSMkJ/](https://paste.ubuntu.com/p/jRTVMSSMkJ/)
  
But whenever i start fresh again (booting up the system after a while) i  begin to experience same issue again and again. I somehow managed to  upgrade to 20.04 LTS and did grub update also. But read-only issue seem  to happen again afraid this issue going to get worse resulting in hard  disk failure.



murali@murali-kubuntu:~$ dmesg | grep -i ext4 
```
[    2.021017] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null) 
[    5.087078] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro


murali@murali-kubuntu:~$ cat /var/log/syslog | grep sda1 
Aug  9 00:01:29 murali-kubuntu kernel: [    1.088521]  sda: sda1 sda2 sda3 sda4 < sda5 s
da6 > 
Aug  9 00:01:29 murali-kubuntu kernel: [    2.050626] EXT4-fs (sda1): mounted filesystem
 with ordered data mode. Opts: (null) 
Aug  9 00:01:29 murali-kubuntu kernel: [    5.133534] EXT4-fs (sda1): re-mounted. Opts: 
errors=remount-ro

Aug  9 07:54:11 murali-kubuntu kernel: [    2.021017] EXT4-fs (sda1): mounted filesystem
 with ordered data mode. Opts: (null) 
Aug  9 07:54:11 murali-kubuntu kernel: [    5.087078] EXT4-fs (sda1): re-mounted. Opts: 
errors=remount-ro 
Aug  9 07:54:11 murali-kubuntu kernel: [    5.436163] lp: driver loaded but no devices f
ound
```

Will share any more specific outputs for guidance on better troubleshooting

murali@murali-kubuntu:/var/log$ sudo smartctl -a /dev/sda 
```
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-80-generic] (local build) 
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org) 

=== START OF INFORMATION SECTION === 
Model Family:     Seagate Barracuda 7200.14 (AF) 
Device Model:     ST1000DM003-1SB10C 
Serial Number:    Z9A07LT5 
LU WWN Device Id: 5 000c50 0871fdddd 
Firmware Version: CC41 
User Capacity:    1,000,204,886,016 bytes [1.00 TB] 
Sector Sizes:     512 bytes logical, 4096 bytes physical 
Rotation Rate:    7200 rpm 
Form Factor:      3.5 inches 
Device is:        In smartctl database [for details use: -P show] 
ATA Version is:   ACS-3 T13/2161-D revision 3b 
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s) 
Local Time is:    Mon Aug  9 09:49:40 2021 IST 
SMART support is: Available - device has SMART capability. 
SMART support is: Enabled 

=== START OF READ SMART DATA SECTION === 
SMART overall-health self-assessment test result: PASSED 

General SMART Values: 
Offline data collection status:  (0x82) Offline data collection activity 
                                        was completed without error. 
                                        Auto Offline Data Collection: Enabled. 
Self-test execution status:      (   0) The previous self-test routine completed 
                                        without error or no self-test has ever  
                                        been run. 
Total time to complete Offline  
data collection:                (    0) seconds. 
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
recommended polling time:        (   1) minutes. 
Extended self-test routine 
recommended polling time:        ( 110) minutes. 
Conveyance self-test routine 
recommended polling time:        (   2) minutes. 
SCT capabilities:              (0x10a5) SCT Status supported. 
                                        SCT Data Table supported. 

SMART Attributes Data Structure revision number: 10 
Vendor Specific SMART Attributes with Thresholds: 
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED R
AW_VALUE 
  1 Raw_Read_Error_Rate     0x000f   073   063   006    Pre-fail  Always       -       21890300 
  3 Spin_Up_Time            0x0003   099   097   000    Pre-fail  Always       -       0 
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3362 
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0 
  7 Seek_Error_Rate         0x000f   079   060   045    Pre-fail  Always       -       88889325 
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4927 
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0 
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3375 
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0 
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0 
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0 
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0 
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0 
190 Airflow_Temperature_Cel 0x0022   058   054   040    Old_age   Always       -       42 (Min/Max 34/44) 
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       3368 
194 Temperature_Celsius     0x0022   042   024   000    Old_age   Always       -       42 (0 24 0 0 0) 
195 Hardware_ECC_Recovered  0x001a   003   001   000    Old_age   Always       -       21890300 
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0 
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0 
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0 
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       4919h+32m+26.645s 
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       11894977732 
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       18096867819 

SMART Error Log Version: 1 
No Errors Logged 

SMART Self-test log structure revision number 1 
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_firs
t_error 
# 1  Extended offline    Completed without error       00%      4927         - 
# 2  Short offline       Completed without error       00%      4923         - 
# 3  Extended offline    Interrupted (host reset)      00%      4920         - 
# 4  Short offline       Completed without error       00%      4918         - 
# 5  Extended offline    Aborted by host               90%      4918         - 

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

### Post by TheFu on 2021-08-09
Those error rates are huge.  Replace the cable.
And be 100% certain you have excellent backups.  Sometimes disks fail without any warning first.

---

### Post by muralikris39 on 2021-08-10
Thanks for the reply, yes i have replaced the SATA cable yesterday and updated the BIOS also. Seems to be ok now i did not get any RO error after. Will keep posted if i get same error again.

But sharing the output again . Out of curiosity just want to understand how you are saying error rates are huge , which values indicate these issues? Please clarify

[FONT=monospace][COLOR=#54ff54]**murali@murali-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo smartctl -a /dev/sda [/COLOR]
[sudo] password for murali:  
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-80-generic] (local build) 
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org") 
```

=== START OF INFORMATION SECTION === 
Model Family:     Seagate Barracuda 7200.14 (AF) 
Device Model:     ST1000DM003-1SB10C 
Serial Number:    Z9A07LT5 
LU WWN Device Id: 5 000c50 0871fdddd 
Firmware Version: CC41 
User Capacity:    1,000,204,886,016 bytes [1.00 TB] 
Sector Sizes:     512 bytes logical, 4096 bytes physical 
Rotation Rate:    7200 rpm 
Form Factor:      3.5 inches 
Device is:        In smartctl database [for details use: -P show] 
ATA Version is:   ACS-3 T13/2161-D revision 3b 
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s) 
Local Time is:    Tue Aug 10 10:17:51 2021 IST 
SMART support is: Available - device has SMART capability. 
SMART support is: Enabled 

```
=== START OF READ SMART DATA SECTION === 
SMART overall-health self-assessment test result: PASSED 

```

General SMART Values: 
Offline data collection status:  (0x82) Offline data collection activity 
                                        was completed without error. 
                                        Auto Offline Data Collection: Enabled. 
Self-test execution status:      (   0) The previous self-test routine completed 
                                        without error or no self-test has ever  
                                        been run. 
Total time to complete Offline  
data collection:                (    0) seconds. 
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
recommended polling time:        (   1) minutes. 
Extended self-test routine 
recommended polling time:        ( 110) minutes. 
Conveyance self-test routine 
recommended polling time:        (   2) minutes. 
SCT capabilities:              (0x10a5) SCT Status supported. 
                                        SCT Data Table supported. 

```

```

SMART Attributes Data Structure revision number: 10 
Vendor Specific SMART Attributes with Thresholds: 
SMART Attributes Data Structure revision number: 10 
Vendor Specific SMART Attributes with Thresholds: 
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE 
  1 Raw_Read_Error_Rate     0x000f   080   063   006    Pre-fail  Always       -       115573290 
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0 
  4 Start_Stop_Count        0x0032   097   097   020    Old_age   Always       -       3519 
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0 
  7 Seek_Error_Rate         0x000f   079   060   045    Pre-fail  Always       -       89076755 
  9 Power_On_Hours          0x0032   095   095   000    Old_age   Always       -       4932 
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0 
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3532 
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0 
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0 
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0 
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0 0 0 
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0 
190 Airflow_Temperature_Cel 0x0022   067   054   040    Old_age   Always       -       33 (Min/Max 29/33) 
193 Load_Cycle_Count        0x0032   099   099   000    Old_age   Always       -       3525 
194 Temperature_Celsius     0x0022   033   024   000    Old_age   Always       -       33 (0 24 0 0 0) 
195 Hardware_ECC_Recovered  0x001a   003   001   000    Old_age   Always       -       115573290 
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0 
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0 
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0 
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       4923h+40m+02.492s 
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       11929895406 
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       18155633135

```
SMART Error Log Version: 1 
No Errors Logged 


SMART Self-test log structure revision number 1 
```

Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error 
# 1  Conveyance offline  Completed without error       00%      4927         - 
# 2  Extended offline    Completed without error       00%      4927         - 
# 3  Short offline       Completed without error       00%      4923         - 
# 4  Extended offline    Interrupted (host reset)      00%      4920         - 
# 5  Short offline       Completed without error       00%      4918         - 
# 6  Extended offline    Aborted by host               90%      4918         - 

```

SMART Selective self-test log data structure revision number 1 
 ```

SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS 
    1        0        0  Not_testing 
    2        0        0  Not_testing 
    3        0        0  Not_testing 
    4        0        0  Not_testing 
    5        0        0  Not_testing

```
Selective self-test flags (0x0): 
  After scanning selected spans, do NOT read-scan remainder of disk. 
If Selective self-test is pending on power-up, resume after 0 minute delay.
[/FONT]

---

### Post by TheFu on 2021-08-10
When posting data that is in a column, please use code tags, or we can't read it. Also ensure that line wraps are where they make sense.

[Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code)

---

### Post by muralikris39 on 2021-08-10
Thanks for the information, hope the previous post is fine to read now

---

### Post by TheFu on 2021-08-10
> **muralikris39 said:**
> Thanks for the information, hope the previous post is fine to read now

Thanks.  Typically, the command AND the output would be put into a single code tag, so we know it is all 1 thing. Showing the exact command and all options is very important.

Look at the table - see the "error rates" rows? See the raw numbers?  Cable issues are common when those.  They have to be fixed either through CRC validations or re-reading.  Much better and faster to have cables that don't crunch the data.

You can google any of those SMART parameters for what they mean. Some are specific to the exact model of storage, but most are shared across the different vendors.

Best to run short smart tests weekly and a long smart test monthly. With smart data, it is about the changes over time, not necessarily about the raw number.  Whenever I see relocated blocks, I start pricing new HDDs. When the number of relocated blocks hits 10, I retire that drive.  When the number of pending relocation events shows as 1 or more for more than a few hours, I know data loss has already happened.

---

### Post by muralikris39 on 2021-08-19
Thanks for your suggestions. I have taken backup of HDD to be on safer side. After SATA cable replacement , i did not face the read-only file system issue again and i am able to boot up and  use my desktop as usual without any issues.

---

