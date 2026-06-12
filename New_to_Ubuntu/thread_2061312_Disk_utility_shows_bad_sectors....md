---
title: "Disk utility shows bad sectors..."
date: 2012-09-22
forum: New to Ubuntu
---

### Post by krishna.988 on 2012-09-22
Hi Everyone,

This morning I saw that Disk utility is showing bad sectors.. Is there a reason to worry ?

I scanned in Windows 7 with chkdsk and was ok before installing ubuntu..

Please clarify..

Please see the screenshots

---

### Post by Cheesemill on 2012-09-22
This usually means your hard drive is on it's way out, make sure that you have all of your important data backed up and prepare yourself to have purchase a new hard drive.

---

### Post by jerrrys on 2012-09-22
I have an HDD with bad sectors for a year now.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=bad+sectors&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=bad+sectors&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Lyfang on 2012-09-22
I recommend to backup all personal files immediately.

---

### Post by krishna.988 on 2012-09-23
> **Lyfang said:**
> I recommend to backup all personal files immediately.


But I noticed that in Windows 7 there are no bad sectors..only ubuntu disk utility is showing bad sectors..I also checked with Surface test in 
**EaseUS® Partition Master Home Edition for Windows**



and Zero bad sectors.. What might be the reason for this??


And also is Disk utility reliable??  I also remember that it had some bugs...

---

### Post by mips on 2012-09-23
> **krishna.988 said:**
> 
And also is Disk utility reliable??  I also remember that it had some bugs...

Disk utility gets the SMART data as reported by the drives onboard controller. It's not something it gets via a scan.

If you want to verify this in windows install one of these free utilities [http://www.techsupportalert.com/best-free-disk-health-monitoring-utility.htm](http://www.techsupportalert.com/best-free-disk-health-monitoring-utility.htm) and compare the SMART output with that provided by Disk Utility.

---

### Post by mcduck on 2012-09-23
In my experience Disc Utility has always been accurate, but of course the most relaible option is to get the SMART tool from your hard drive's manufacturer and use that. Pretty much every drive manufacturer has one available for download somewhere on their websites.

Anyway, the amount of bad sectors isn't that high yet, soemthing like that could still be caused by some once-only shock damage to the drive, and thus might not mean that the drive is failing.

Of course you should keep on checking the value in case it's still increasing, as that would be a sign of the drive approaching it's end-of-life. And make sure you have a proper backup (which you of course should already have anyway... ;)).

edit: One reason why you might get different results from different tools is that modern hard drives will automatically map out bad sectors, after which any tool scanning the disc won't be able to see them any more, they will only be visible in the SMART data from the disc itself. (see the "reallocated sectors" count in SMART data). Because of this a few bad sectors aren't a problem, and things only start getting serious when the dik runs out of extra space and can't reallocate any more sectors.

---

### Post by NikTh on 2012-09-23
Hello , 

IF you don't trust Disk Utility then you can run smartmontools and see the results ( I assume will be the same) 

```
sudo apt-get install smartmontools --no-install-recommends
``` 
```
sudo smartctl -a /dev/sda
``` 

Post the results of 2nd command here. Please put the results between the brackets **[noparse]```
Here
```[/noparse]**

Thanks

---

### Post by krishna.988 on 2012-09-23
> **NikTh said:**
> Hello , 

IF you don't trust Disk Utility then you can run smartmontools and see the results ( I assume will be the same) 

```
sudo apt-get install smartmontools --no-install-recommends
``````
sudo smartctl -a /dev/sda
```Post the results of 2nd command here. Please put the results between the brackets **[noparse]```
Here
```[/noparse]**

Thanks

These are the results of the second command:

 ```

$ sudo smartctl -a /dev/sda

smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-31-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST3320418AS
Serial Number:    5VM5YZX7
LU WWN Device Id: 5 000c50 01e925c48
Firmware Version: CC44
User Capacity:    320,071,851,520 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Sun Sep 23 17:04:27 2012 IST
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
data collection:         (  642) seconds.
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
recommended polling time:      (  74) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   114   099   006    Pre-fail  Always       -       71724239
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   099   099   020    Old_age   Always       -       1543
  5 Reallocated_Sector_Ct   0x0033   098   098   036    Pre-fail  Always       -       119
  7 Seek_Error_Rate         0x000f   078   060   030    Pre-fail  Always       -       4369523194
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       1395
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1543
183 Runtime_Bad_Block       0x0000   100   100   000    Old_age   Offline      -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   094   000    Old_age   Always       -       42950328930
189 High_Fly_Writes         0x003a   001   001   000    Old_age   Always       -       588
190 Airflow_Temperature_Cel 0x0022   064   050   045    Old_age   Always       -       36 (Min/Max 29/36)
194 Temperature_Celsius     0x0022   036   050   000    Old_age   Always       -       36 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   047   035   000    Old_age   Always       -       71724239
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   199   000    Old_age   Always       -       1044
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       23669564773756
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3647402291
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       3241027925

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1394         -
# 2  Extended offline    Aborted by host               90%      1394         -
# 3  Short offline       Completed without error       00%      1378         -
# 4  Conveyance offline  Aborted by host               80%      1318         -
# 5  Conveyance offline  Aborted by host               90%       956         -
# 6  Short offline       Aborted by host               80%       551         -
# 7  Short offline       Completed without error       00%         0         -

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

### Post by Mopar1973Man on 2012-09-23
I also have a drive with errors on it... So far it holding up just fine and I keep an eye on the driver with the dish tool. No changes in months now and going to continue using this drive.

---

### Post by NikTh on 2012-09-23
Hi , 

I think you can see the fail of the disk. Here is the explanation of the results - values. [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T). 

But no one nows when the disk will fail. You can keep working on this disk BUT , backup your important data and don't leave important data in this disk.

Thanks

---

### Post by Mopar1973Man on 2012-09-23
Well... As of today I just moved my Ubuntu Data into another partition and continuing forward. Since I don't have any backups it might be smarter to give up and let the drive be use for storage or minor data or just retire it for spare...;)

---

