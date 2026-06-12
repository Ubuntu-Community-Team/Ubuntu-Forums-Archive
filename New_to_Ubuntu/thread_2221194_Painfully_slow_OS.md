---
title: "Painfully slow OS"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by mks4 on 2014-05-01
Hi,

 Newbie here, and apologies if this is in the wrong place. After a year of constantly having to reinstall Windows 8, it finally died (including the partition restore files) and I installed Ubuntu. Now it seems really good but it's painfully slow, with the windows "greying out" which makes it virtually unusable. The odd thing is, is if I run it from the USB it's super quick.

Any help would be gratefully appreciated as the USB version of the OS is really impressive.

Many thanks.

---

### Post by bapoumba on 2014-05-01
Please give specifications of the computer and the ubuntu version you installed.

Greyed out apps mean the system is busy and they wait for it to continue working. Could be several things. How much memory do you have, how much swap ?

Shots in the dark :
```
sudo fdisk -l
free
df -h
```

---

### Post by mks4 on 2014-05-01
[TABLE]
[TR]
[TD="class: label"]Thanks for the response. The specs of the laptop are:

2.4 Mhz Processor, 4GB DDR3 SRam, 500MB HDD and I installed Ubuntu 14.04 LTS.
[/TD]
[TD="class: value"][/TD]
[/TR]
                                                                                             [TR="class: size-weight"]
[/TR]
[TR="class: size-weight"]
[TD="class: value"][/TD]
[/TR]
[TR="class: item-model-number"]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"]Processor Speed
[/TD]
[TD="class: value"]2.4 GHz[/TD]
[/TR]
          [TR]
[TD="class: label"]Processor Count
[/TD]
[TD="class: value"]2
[/TD]
[/TR]
          [TR]
[TD="class: label"]RAM Size
[/TD]
[TD="class: value"]4 GB
[/TD]
[/TR]
          [TR]
[TD="class: label"]Computer Memory Type
[/TD]
[TD="class: value"]DDR3 SDRAM
[/TD]
[/TR]
          [TR]
[TD="class: label"]Hard Drive Size
[/TD]
[TD="class: value"]500 GB
[/TD]
[/TR]
          [TR]
[TD="class: label"]Graphics Card Description
[/TD]
[TD="class: value"]Integrated
[/TD]
[/TR]
          [TR]
[TD="class: label"]Graphics RAM Type
[/TD]
[TD="class: value"]DDR3 SDRAM
[/TD]
[/TR]
          [TR]
[TD="class: label"]Wireless Type
[/TD]
[TD="class: value"]802.11B, 802.11G, 802.11n
[/TD]
[/TR]
[/TABLE]

---

### Post by mks4 on 2014-05-01
[TABLE]
[TR]
[TD="class: label"]

[/TD]
[TD="class: value"][/TD]
[/TR]
[TR="class: size-weight"]
[/TR]
[TR="class: size-weight"]

[/TR]
[TR="class: item-model-number"]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[TR]
[TD="class: label"][/TD]
[TD="class: value"][/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: label"]Thanks for the response. The specs of the laptop are:

2.4 Mhz Processor, 4GB DDR3 SRam, 500MB HDD and I installed Ubuntu 14.04 LTS.
[/TD]
[/TR]
[/TABLE]

And sorry for making a mess of your forum!

---

### Post by bapoumba on 2014-05-01
OK thanks, does not look like you are on low specs :)
Could you please post the output to the other commands ? I may not be able to help you but others will, thanks.

Edit : please do not try to draw tables, just paste the text in here, and wrap [noparse]```

```[/noparse] around it : [http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by mks4 on 2014-05-01
output as below...

```
paul@paul-X55A:~$ sudo fdisk -l
[sudo] password for paul: 


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0ba9735f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```
```
paul@paul-X55A:~$ free
             total       used       free     shared    buffers     cached
Mem:       3929228     807396    3121832     111920      39484     391368
-/+ buffers/cache:     376544    3552684
Swap:      4075516          0    4075516
```
```
paul@paul-X55A:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       455G   54G  378G  13% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           384M  1.3M  383M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G   76K  1.9G   1% /run/shm
none            100M   36K  100M   1% /run/user
/dev/sda1       511M  3.4M  508M   1% /boot/efi
```

---

### Post by bapoumba on 2014-05-01
I'm not familiar with uefi boot mode. Please wait someone steps in, thanks.

---

### Post by fkkroundabout on 2014-05-01
since you say that windows 8 just 'died' along with the partition table, and that ubuntu is exceptionally slow, would make me think that your hard drive may well be failing

the fact that the whole computer works fast with a USB flash drive furthers my belieif that your hard drive is the problem.

i would suggest you either call up whatever brand name your computer is and ask them for a new hard drive replacement - if your computer is under warranty and if you  don't mind them giving you a basic hard drive - or buy a new hard drive yourself, or even a solid state drive if you really like the speed of the USB stick. then replace the hard drive yourself - it's not difficult, you should be OK with a little reading

simple benchmarks for hard drives can be found here: [http://harddrivebenchmark.net/hdd_list.php](http://harddrivebenchmark.net/hdd_list.php)

---

### Post by mks4 on 2014-05-01
Thought that maybe the case. Thanks FK.

---

### Post by QIII on 2014-05-01
Hello!

Please install smartmontools

```
sudo apt-get install smartmontools
```

If this is a SATA drive (assuming sda is the device your OS is installed on), run

```
sudo smartctl -a -d ata /dev/sda
```

Highlight all of the resulting text in the terminal and press CTRL+SHIFT+C to copy it.

Paste the text back here between code tags:

If you are using New Reply button - highlight text and use the # button in the text box header.

If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

That should give us a pretty good indication of the health of your disk.

---

### Post by bapoumba on 2014-05-01
QIII thanks :)

---

### Post by mks4 on 2014-05-01
Thanks QIII

```

=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MQ01ABD...
Device Model:     TOSHIBA MQ01ABD050
Serial Number:    826KSIMDS
LU WWN Device Id: 5 000039 435f81901
Firmware Version: AX002J
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS (minor revision not indicated)
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu May  1 11:51:45 2014 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (  25)    The self-test routine was aborted by
                    the host.
Total time to complete Offline 
data collection:         (  120) seconds.
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
recommended polling time:      ( 119) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   099   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1039
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       5803
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       9448
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       3141
 10 Spin_Retry_Count        0x0033   215   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       5712
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       601
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       54
193 Load_Cycle_Count        0x0032   098   098   000    Old_age   Always       -       23687
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       31 (Min/Max 14/47)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       938
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       6928
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   093   093   000    Old_age   Always       -       2880
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       172
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 17872 (device log contains only the most recent five errors)
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

Error 17872 occurred at disk power-on lifetime: 3141 hours (130 days + 21 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 80 17 11 40  Error: WP at LBA = 0x00111780 = 1120128

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  61 00 20 00 05 51 40 00      00:08:52.366  WRITE FPDMA QUEUED
  61 00 18 00 01 51 40 00      00:08:52.366  WRITE FPDMA QUEUED
  61 00 10 00 fd 50 40 00      00:08:52.365  WRITE FPDMA QUEUED
  61 00 08 00 f9 50 40 00      00:08:52.365  WRITE FPDMA QUEUED
  60 08 00 80 17 11 40 00      00:08:50.089  READ FPDMA QUEUED

Error 17871 occurred at disk power-on lifetime: 3139 hours (130 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 00 0f 10 40  Error: UNC at LBA = 0x00100f00 = 1052416

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 00 0f 10 40 00      00:50:27.594  READ FPDMA QUEUED
  60 30 08 58 0e 10 40 00      00:50:27.381  READ FPDMA QUEUED
  60 48 00 08 0e 10 40 00      00:50:27.381  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:50:27.381  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:50:27.380  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

Error 17870 occurred at disk power-on lifetime: 3139 hours (130 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 00 08 0f 10 40  Error: UNC at LBA = 0x00100f08 = 1052424

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 48 10 08 0e 10 40 00      00:50:23.436  READ FPDMA QUEUED
  60 30 08 58 0e 10 40 00      00:50:23.436  READ FPDMA QUEUED
  60 00 00 08 0f 10 40 00      00:50:23.436  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      00:50:23.436  SET FEATURES [Enable SATA feature]
  27 00 00 00 00 00 e0 00      00:50:23.435  READ NATIVE MAX ADDRESS EXT [OBS-ACS-3]

Error 17869 occurred at disk power-on lifetime: 3139 hours (130 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 18 00 0f 10 40  Error: UNC at LBA = 0x00100f00 = 1052416

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 08 0f 10 40 00      00:50:17.182  READ FPDMA QUEUED
  60 48 00 08 0e 10 40 00      00:50:17.182  READ FPDMA QUEUED
  60 78 18 90 0e 10 40 00      00:50:17.182  READ FPDMA QUEUED
  60 30 10 58 0e 10 40 00      00:50:17.182  READ FPDMA QUEUED
  60 d8 08 30 0d 10 40 00      00:50:17.103  READ FPDMA QUEUED

Error 17868 occurred at disk power-on lifetime: 3139 hours (130 days + 19 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 30 f8 18 10 40  Error: UNC at LBA = 0x001018f8 = 1054968

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 48 10 78 19 10 40 00      00:50:08.524  READ FPDMA QUEUED
  60 68 08 08 19 10 40 00      00:50:08.524  READ FPDMA QUEUED
  60 08 48 00 1a 10 40 00      00:50:08.524  READ FPDMA QUEUED
  60 18 40 e0 19 10 40 00      00:50:08.524  READ FPDMA QUEUED
  60 10 38 c8 19 10 40 00      00:50:08.524  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Aborted by host               90%      3140         -

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

### Post by QIII on 2014-05-02
Wow.  Sorry.  Forgot about this!  My apologies.

You have a pretty high number of reallocated sectors, which could indicate a failing drive.

If you are running vanilla Ubuntu, go to the Dash Home and type "Disk Utility", highlight your OS drive and look for the button labeled "SMART Data".  Click that for a nice GUI.

You may need to run/refresh the test.  

The GUI will give you some explanatory warnings if there are any.

---

