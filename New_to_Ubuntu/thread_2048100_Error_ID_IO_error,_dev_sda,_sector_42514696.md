---
title: "Error ID I/O error, dev sda, sector 42514696"
date: 2012-08-26
forum: New to Ubuntu
---

### Post by vks.itbhu on 2012-08-26
from the last few days, i am facing this issue that after some time of working my ubuntu just freezes. it starts closing each app and then remain blank in desktop. i can't shutdown also and i have to hold the power button to kill the machine. 
on the screen tty2, it shows the following machine:
      Error ID I/O error, dev sda, sector 42514696

since i am not very much into ubuntu till now i don't know what this means and how to fix this issue.
Please tell me how to fix this, any help is appreciated.

---

### Post by mlentink on 2012-08-26
Ther error points to a failure on your first harddisk (_s_ata _d_evice _a_). If I were you, i check that disk for error thoroughly.

---

### Post by Paqman on 2012-08-26
Normally the drive itself will take care of bad sectors by marking them out of use. 

Have a look in Disk Utility at the drive and check the SMART data. Note the number of bad sectors under categories such as "Reallocated Sectors", "Pending Reallocation" and "Offline Uncorrectable". It may be that your disk has so many bad sectors that it's unable to adapt, or that it has a problem with the heads. If you don't understand the SMART data take a screenshot and post it here for us to have a look at.

---

### Post by Hadaka on 2012-08-26
Hi, over time the magnetic areas of the disk become wider,causing the read head
to have a problem reading data, this command will rewrite the entire drive back
on its self and create nice tight magnetic patterns while avoiding sectors that are
truly damaged.

```
dd if=/dev/sda of=/dev/sda 
```

nothing like a good massage to get the kinks out.

---

### Post by Paqman on 2012-08-26
> **Hadaka said:**
> Hi, over time the magnetic areas of the disk become wider,causing the read head
to have a problem reading data, this command will rewrite the entire drive back
on its self and create nice tight magnetic patterns while avoiding sectors that are
truly damaged.

```
dd if=/dev/sda of=/dev/sda 
```

nothing like a good massage to get the kinks out.

That's a good idea, but before doing a big write across the whole of a drive that might be defective in some unknown way I'd strongly suggest backing up your data.

---

### Post by vks.itbhu on 2012-08-26
thanx for reply. here is the output of smartdata.
please see and tell me what to do.
 [PHP]smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-24-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.4
Device Model:     ST9250827AS
Serial Number:    5RG5GS8G
LU WWN Device Id: 5 000c50 011682c39
Firmware Version: 3.AAA
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Aug 26 21:10:50 2012 IST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 121)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		(  426) seconds.
Offline data collection
capabilities: 			 (0x5b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					No General Purpose Logging support.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  92) minutes.
SCT capabilities: 	       (0x0001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   253   006    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   095   095   020    Old_age   Always       -       5155
  5 Reallocated_Sector_Ct   0x0033   049   049   036    Pre-fail  Always       -       2067
  7 Seek_Error_Rate         0x000f   064   060   030    Pre-fail  Always       -       515752179081
  9 Power_On_Hours          0x0032   088   088   000    Old_age   Always       -       10792
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   096   096   020    Old_age   Always       -       5048
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       36134
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       220
190 Airflow_Temperature_Cel 0x0022   052   024   045    Old_age   Always   In_the_past 48 (1 119 76 14)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       220
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       1202
193 Load_Cycle_Count        0x0022   035   035   000    Old_age   Always       -       131605
194 Temperature_Celsius     0x001a   048   076   000    Old_age   Always       -       48 (0 14 0 0)
195 Hardware_ECC_Recovered  0x0012   060   040   000    Old_age   Always       -       47058896
197 Current_Pending_Sector  0x0010   099   099   000    Old_age   Offline      -       31
198 Offline_Uncorrectable   0x003e   099   099   000    Old_age   Always       -       31
199 UDMA_CRC_Error_Count    0x0000   200   200   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x0032   100   253   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0000   100   253   000    Old_age   Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 36149 (device log contains only the most recent five errors)
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

Error 36149 occurred at disk power-on lifetime: 10782 hours (449 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 98 65 e0  Error: UNC at LBA = 0x00659842 = 6658114

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 40 98 65 e0 00      00:57:12.287  READ DMA EXT
  ec 00 00 00 00 00 a0 00      00:57:12.282  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:57:12.271  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:57:12.266  IDENTIFY DEVICE
  25 00 08 40 98 65 e0 00      00:57:09.350  READ DMA EXT

Error 36148 occurred at disk power-on lifetime: 10782 hours (449 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 98 65 e0  Error: UNC at LBA = 0x00659842 = 6658114

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 40 98 65 e0 00      00:57:12.287  READ DMA EXT
  ec 00 00 00 00 00 a0 00      00:57:12.282  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:57:12.271  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:57:12.266  IDENTIFY DEVICE
  25 00 08 40 98 65 e0 00      00:57:09.350  READ DMA EXT

Error 36147 occurred at disk power-on lifetime: 10782 hours (449 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 98 65 e0  Error: UNC at LBA = 0x00659842 = 6658114

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 40 98 65 e0 00      00:57:12.287  READ DMA EXT
  ec 00 00 00 00 00 a0 00      00:57:12.282  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:57:12.271  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:57:12.266  IDENTIFY DEVICE
  25 00 08 40 98 65 e0 00      00:57:09.350  READ DMA EXT

Error 36146 occurred at disk power-on lifetime: 10782 hours (449 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 98 65 e0  Error: UNC at LBA = 0x00659842 = 6658114

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 40 98 65 e0 00      00:57:03.480  READ DMA EXT
  ec 00 00 00 00 00 a0 00      00:57:03.452  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:57:03.451  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:57:03.450  IDENTIFY DEVICE
  25 00 08 40 98 65 e0 00      00:57:09.350  READ DMA EXT

Error 36145 occurred at disk power-on lifetime: 10782 hours (449 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 42 98 65 e0  Error: UNC at LBA = 0x00659842 = 6658114

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 08 40 98 65 e0 00      00:57:03.480  READ DMA EXT
  ec 00 00 00 00 00 a0 00      00:57:03.452  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:57:03.451  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:57:03.450  IDENTIFY DEVICE
  25 00 08 40 98 65 e0 00      00:57:03.441  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%     10707         409311298
# 2  Short offline       Completed: read failure       90%     10707         409311298
# 3  Short offline       Completed: read failure       90%      6100         488345202
# 4  Short offline       Completed without error       00%      3629         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.[/PHP]

---

### Post by cryptotheslow on 2012-08-26
That is a massive number of seek errors meaning that the heads aren't positioning correctly with the stored data tracks.

Hadaka's suggested command may well help, but if it were my disk I'd be backing everything up off it and expecting it to completely fail imminently.

---

### Post by vks.itbhu on 2012-08-26
oh ok thanks for the response. will do exactly that.

---

### Post by Paqman on 2012-08-26
> **cryptotheslow said:**
> That is a massive number of seek errors meaning that the heads aren't positioning correctly with the stored data tracks.

Hadaka's suggested command may well help, but if it were my disk I'd be backing everything up off it and expecting it to completely fail imminently.

+1 to this

Over 2000 fixed bad sectors with another 31 uncorrectable is also not good, but if the heads are knackered then you could get all sorts of false positives.

Back up now before any more data is corrupted!

---

