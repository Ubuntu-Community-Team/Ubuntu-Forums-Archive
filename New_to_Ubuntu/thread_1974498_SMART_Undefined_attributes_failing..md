---
title: "SMART Undefined attributes failing."
date: 2012-05-06
forum: New to Ubuntu
---

### Post by Dondermans on 2012-05-06
**Problem**
Diskutility reports harddisk errors from time to time.  The attributes that are failing are all listed as 'undefined' in  diskutility. I am not quite sure how something that is not defined can  be failing, as 'undefined' implies there is no definition of failure. If  a screenshot helps to shed light on the problem, I am willing to  provide it. I will have to wait for the error to come up again.

When refreshing the SMART data in Diskutility it reports 'the disk has been used outside design parameters in the past'.

**Technical data of hardware involved**
Technical data of the harddisk is pasted below between ```
 tags.

**Actions taken**
I searched this forum and found the thread 'Hard disk problem detected' ([http://ubuntuforums.org/showpost.php?p=11832735&postcount=3]("http://[URL")). I executed the SMART-self test, results below: 

[code]
~$ sudo smartctl -a /dev/sda
[sudo] password for [username]: 
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-19-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD161HJ
Serial Number:    [serial number]
LU WWN Device Id: 5 0000f0 09b617481
Firmware Version: JF100-15
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Sun May  6 13:17:26 2012 CEST
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
data collection:         ( 3044) seconds.
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
recommended polling time:      (  51) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   253   253   025    Pre-fail  Always       -       4480
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       4190
  5 Reallocated_Sector_Ct   0x0033   253   253   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   253   253   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   253   253   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       22976
 10 Spin_Retry_Count        0x0033   253   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   253   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3068
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       50707722
184 End-to-End_Error        0x0033   253   253   099    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   253   253   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   253   253   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   163   130   000    Old_age   Always       -       25 (Min/Max 1/36)
194 Temperature_Celsius     0x0022   163   001   000    Old_age   Always       -       25 (Min/Max 0/37)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       50707722
196 Reallocated_Event_Count 0x0032   253   253   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   253   253   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   253   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   100   100   000    Old_age   Always       -       0
202 Data_Address_Mark_Errs  0x0032   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     22976         -
# 2  Extended offline    Completed without error       00%     22561         -
# 3  Short offline       Completed without error       00%     22525         -
# 4  Short offline       Completed without error       00%     10937         -
# 5  Short offline       Completed without error       00%        21         -

Note: selective self-test log revision number (0) not 1 implies that no selective self-test has ever been run
SMART Selective self-test log data structure revision number 0
Note: revision number not 1 implies that no selective self-test has ever been run
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.
```&#65279;

**Question**
Should I replace the disk? I read the article on [https://en.wikipedia.org/wiki/S.M.A.R.T](https://en.wikipedia.org/wiki/S.M.A.R.T). and the correlation between SMART failures and disk failures appears to be questionable.

**Backup**
I do make backups which are stored on Ubuntu One.

---

### Post by Paqman on 2012-05-06
Tbh, the raw values for your SMART parameters seem fine. However, it's clear that the drive isn't communicating some of the SMART data accurately. Where is the error? In the raw data or the interpretation of it? It's impossible to say.

If you've got a solid backup plan you've nothing to lose by continuing to use the disk. Since you're getting what may be a lot of false positives you can prevent Disk Utility from nagging about it by checking the box for "do not report this drive".

Having said that, the drive may pack up tomorrow. I'm of the opinion that it's always best to assume they will even if there's nothing scary showing in SMART. If you don't have a good backup plan, now is the time to have a think about it.

---

### Post by Dondermans on 2012-05-06
Thank you for your reply.

I do make both onsite and offsite backups of critical data. I found the article below to be particularly helpful: 
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

This string of events makes a good excuse to go for an SSD.

---

