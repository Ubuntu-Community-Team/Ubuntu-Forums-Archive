---
title: "SMART results"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by mamamia88 on 2013-12-05
I have a harddrive that is really freaking loud.  But I'm not sure if it's from old age or if it's actually dieing.  So I ran a smart test on it but have no idea how to understand the results.  Could somebody please take a look at these and give me a general idea?  
```
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-13-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Deskstar 7K80
Device Model:     HDS728080PLA380
Serial Number:    PFDBU0ELT0H8SX
LU WWN Device Id: 5 000cca 30fdc6860
Firmware Version: PF2OA63A
User Capacity:    80,000,000,000 bytes [80.0 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA/ATAPI-7 T13/1532D revision 1
Local Time is:    Wed Nov 27 12:58:03 2013 CST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x85)	Offline data collection activity
					was aborted by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		( 1828) seconds.
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
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (  31) minutes.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   016    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0004   100   100   050    Old_age   Offline      -       0
  3 Spin_Up_Time            0x0007   103   103   024    Pre-fail  Always       -       194 (Average 192)
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       1179
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000a   100   100   067    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0004   142   142   020    Old_age   Offline      -       28
  9 Power_On_Hours          0x0012   099   099   000    Old_age   Always       -       9627
 10 Spin_Retry_Count        0x0012   100   100   060    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1171
192 Power-Off_Retract_Count 0x0032   099   099   050    Old_age   Always       -       1325
193 Load_Cycle_Count        0x0012   099   099   050    Old_age   Always       -       1325
194 Temperature_Celsius     0x0002   171   171   000    Old_age   Always       -       32 (Min/Max 11/44)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
No Errors Logged
```

---

### Post by philinux on 2013-12-05
Rows 5 and 197 show no bad sectors so I'd say it ok.

I usually open dash type disk and use Disks to look at smart data there. If it says passed I dont look any further.

---

### Post by mamamia88 on 2013-12-05
> **philinux said:**
> Rows 5 and 197 show no bad sectors so I'd say it ok.

I usually open dash type disk and use Disks to look at smart data there. If it says passed I dont look any further.

I'm using xubuntu is there something similar on xubuntu?

---

### Post by Dennis N on 2013-12-05
Same utility is on Xubuntu. 

**Settings Manager > Hardware > Disks**

---

### Post by philinux on 2013-12-05
Ah. It's gnome-disk-utility not sure what it depends on.

---

### Post by tgalati4 on 2013-12-05
They are called "DeathStars" for a reason.  Back up your data.  SMART captures about 2/3 of failure modes.  The remaining 1/3 are spontaneous failures.  You could try running some short and long tests using *smartctl*.  Are you sure it is not a cooling fan making the noise?  With 10k hours it's old, but I have some 20 GB drives with 50k hours--still spinning!  

```
sudo smartctl -t short /dev/sda
sudo smartctl -t long /dev/sda
```

To read the results (after waiting the required amount of time to complete):

```
sudo smartctl -a /dev/sda
```

---

### Post by mamamia88 on 2013-12-06
> **tgalati4 said:**
> They are called "DeathStars" for a reason.  Back up your data.  SMART captures about 2/3 of failure modes.  The remaining 1/3 are spontaneous failures.  You could try running some short and long tests using *smartctl*.  Are you sure it is not a cooling fan making the noise?  With 10k hours it's old, but I have some 20 GB drives with 50k hours--still spinning!  

```
sudo smartctl -t short /dev/sda
sudo smartctl -t long /dev/sda
```

To read the results (after waiting the required amount of time to complete):

```
sudo smartctl -a /dev/sda
```

The results from the first one were from the longest one.  And I'm sure it's the harddrive the noise it makes always corresponds to the hd indicator on the front and it's not really a sound a fan would make.

---

### Post by andyfied on 2013-12-06
+1 for  tgalati4's advice. Back up your data. Probably get a new drive as well. It might survive for a long while yet, but why take the risk? They are cheap enough for 80GB ones.

---

### Post by codenine75a on 2013-12-06
If your equipment is loud try to dampen the it by looking at the wire wraps inside the rig.  They are usually cheap plastic and you can replace them with string.  Sometimes SMART results come up as a failing drive when there is not enough power to run the drive effectively.

---

### Post by tgalati4 on 2013-12-06
Keep an eye on the temperature of the drive when it is in heavy use.  Loud, whining noise usually indicates a worn or failing motor bearing.  The temperature will rise as the current increases to overcome the increasing bearing friction.  As long as the drive still works, the noise is an annoyance, but don't expect to get another 10K hours out of it.

---

### Post by philinux on 2013-12-06
> **tgalati4 said:**
> Keep an eye on the temperature of the drive when it is in heavy use.  Loud, whining noise usually indicates a worn or failing motor bearing.  The temperature will rise as the current increases to overcome the increasing bearing friction.  As long as the drive still works, the noise is an annoyance, but don't expect to get another 10K hours out of it.

+1 temps are displayed in the disks utility or choice of psensor or what I use is conky.

---

### Post by mamamia88 on 2013-12-06
> **andyfied said:**
> +1 for  tgalati4's advice. Back up your data. Probably get a new drive as well. It might survive for a long while yet, but why take the risk? They are cheap enough for 80GB ones.

Anything wrong with a laptop drive?  I have about 5 of them in my drawer and newegg had a 2.5 to 3.5" adatpor for free after rebate the other day that I ordered.   Probably not going to replace the hard drive though until it fails for sure.   Too lazy for that right now.   All my really important stuff is on dropbox anyway

---

### Post by tgalati4 on 2013-12-06
You could use a laptop drive, but you really need a new desktop drive.  Laptop drives don't have the robustness of a desktop drive.

---

