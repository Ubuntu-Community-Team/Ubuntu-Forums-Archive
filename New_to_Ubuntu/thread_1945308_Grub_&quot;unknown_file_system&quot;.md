---
title: "Grub: &quot;unknown file system&quot;"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by dayzman on 2012-03-22
Hi guys

This morning my hard drive was stuck in lots of I/O activities, so I hard booted the machine. Now, I can only rarely boot into Ubuntu. I can see grub, but after choosing Ubuntu, I get:

> error: unknown filesystem.
error: couldn't read file.

Press any key to continue...

Sometimes my keyboard loses input at this point, but when it does have input, I either get bounced back to grub or proceed to Ubuntu. Quite unpredictable. Sometimes I get this instead:

> error: hd0 out of disk.

Press any key to continue...

Does anyone know how to fix this? I've tried running boot-repair, but that didn't help. Here's what my partitions look like:

[IMG]http://s13.postimage.org/nu5fy2gcl/Screenshot_at_2012_03_23_03_38_53.png[/IMG]

Please help!

---

### Post by QIII on 2012-03-22
Lots of disk noise?

---

### Post by dayzman on 2012-03-23
> **QIII said:**
> Lots of disk noise?

This morning, yes. There weren't actually much I/O activities according to my system monitor, but just a lot of I/O wait. Not sure what happened.

Now, there's no noise, but can't boot properly.

---

### Post by QIII on 2012-03-23
Does your BIOS include SMART?   Let's get disk health ruled out and take a further look.  While running a live session, can you check the drive?

After that, fsck may do the trick.  But don't run it while your hdd is mounted.

---

### Post by dayzman on 2012-03-23
> **QIII said:**
> Does your BIOS include SMART?   Let's get disk health ruled out and take a further look.  While running a live session, can you check the drive?

After that, fsck may do the trick.  But don't run it while your hdd is mounted.

Yes, it has SMART. I'm not quite familiar with the output, but except 'Raw_Read_Error_Rate' corresponds to bad sectors, right? It seems to have 0.

> smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.0.0-12-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Caviar Black
Device Model:     WDC WD1001FALS-00J7B0
Serial Number:    WD-WMATV0981872
LU WWN Device Id: 5 0014ee 0011d9cd7
Firmware Version: 05.00K05
User Capacity:    1,000,203,804,160 bytes [1.00 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Mar 23 16:33:20 2012 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x84)	Offline data collection activity
					was suspended by an interrupting command from host.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		(19200) seconds.
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
recommended polling time: 	 ( 221) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   238   226   021    Pre-fail  Always       -       8091
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       947
  5 Reallocated_Sector_Ct   0x0033   199   199   140    Pre-fail  Always       -       1
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   065   065   000    Old_age   Always       -       25751
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       349
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       270
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       935
194 Temperature_Celsius     0x0022   112   102   000    Old_age   Always       -       38
196 Reallocated_Event_Count 0x0032   199   199   000    Old_age   Always       -       1
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   200   200   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       2
200 Multi_Zone_Error_Rate   0x0008   200   200   000    Old_age   Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%     24694         -
# 2  Short offline       Aborted by host               80%     24694         -
# 3  Short offline       Aborted by host               80%     24694         -

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


Should I run fsck using a live CD?

Thanks

---

### Post by dayzman on 2012-03-24
I've just run fsck, but there were no errors.

Thanks

---

