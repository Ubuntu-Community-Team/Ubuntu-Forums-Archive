---
title: "Ubuntu HDD kill bug?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ipatec on 2008-04-27
I read on some blogs that there is a kind of bug or something that may cause hdd usage...
I checked to see if my laptop is affected but I don't know what that querry means. Here is the output:
> 
ipatec@ipatec-laptop:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   177   177   000    Old_age   Always       -       71503



Can someone help me please? Thanks!

PS: My laptop is about 1 year old... :)

Later:
Here is the full querry after a reboot:
> 
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0003   190   189   021    Pre-fail  Always       -       1500
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1669
  5 Reallocated_Sector_Ct   0x0033   191   191   140    Pre-fail  Always       -       65
  7 Seek_Error_Rate         0x000e   100   253   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3283
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1604
192 Power-Off_Retract_Count 0x0032   198   198   000    Old_age   Always       -       1597
193 Load_Cycle_Count        0x0032   177   177   000    Old_age   Always       -       71505
194 Temperature_Celsius     0x0022   098   086   000    Old_age   Always       -       49
196 Reallocated_Event_Count 0x0032   188   188   000    Old_age   Always       -       12
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

The Load_Cycle_Count grow with 2 in about 30 minutes

---

### Post by southernman on 2008-04-27
Is that the entire output of the command? If not, don't be stingy with it now! Let us have the whole thing.

---

### Post by FredB on 2008-04-27
The interesting part is LCC / numbers of hours powered on :      71505 / 3283 = 21.78 per hours.

Not a lot. Under 30, it is very good.

For your info, mine, a PC bought 2 months ago :

```
fred@fred-laptop:~$ sudo smartctl -a `mount | grep '/ ' | cut -d' ' -f1 | sed -e 's#[0-9]##'` | egrep 'Cycle|Power'
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       689
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       179
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       8
193 Load_Cycle_Count        0x0012   100   100   000    Old_age   Always       -       9596
```

LCC / hours = 13.92

---

### Post by southernman on 2008-04-27
Nothing really wrong that I see. Always keep backups, computers/hdd's can go south at any time. Just a nature of the beast. Spare HDD's are good too.

---

### Post by ipatec on 2008-04-27
Here is the all output:
> 
ipatec@ipatec-laptop:~$ sudo smartctl -a /dev/sda
[sudo] password for ipatec: 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio family
Device Model:     WDC WD1200BEVS-75LAT0
Serial Number:    WD-WXEZ06367755
Firmware Version: 02.06M02
User Capacity:    120,034,123,776 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sun Apr 27 16:34:10 2008 EEST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (6000) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  78) minutes.
Conveyance self-test routine
recommended polling time: 	 (   6) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   200   200   051    Pre-fail  Always       -       1
  3 Spin_Up_Time            0x0003   190   189   021    Pre-fail  Always       -       1500
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1669
  5 Reallocated_Sector_Ct   0x0033   191   191   140    Pre-fail  Always       -       65
  7 Seek_Error_Rate         0x000e   100   253   051    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3284
 10 Spin_Retry_Count        0x0012   100   100   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   051    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1604
192 Power-Off_Retract_Count 0x0032   198   198   000    Old_age   Always       -       1597
193 Load_Cycle_Count        0x0032   177   177   000    Old_age   Always       -       71522
194 Temperature_Celsius     0x0022   098   086   000    Old_age   Always       -       49
196 Reallocated_Event_Count 0x0032   188   188   000    Old_age   Always       -       12
197 Current_Pending_Sector  0x0012   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   051    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1313         -
# 2  Short offline       Completed without error       00%         1         -
# 3  Short offline       Completed without error       00%         0         -

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

ipatec@ipatec-laptop:~$ 


The laptop has one year but it was used every day at least 4-5 hours
Thanks for your answers!

---

