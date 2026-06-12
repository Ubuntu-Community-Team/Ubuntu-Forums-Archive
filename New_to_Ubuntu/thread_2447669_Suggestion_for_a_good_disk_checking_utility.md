---
title: "Suggestion for a good disk checking utility?"
date: 2020-07-23
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-07-23
Hello all,

Following on from some previous posts, do any of you gentlemen (or ladies) have any suggestions for a good tool to check my Seagate SSD?

It's been playing up a bit, and it is one that my dad passed on to me so I have no idea of it's history, I need a SSD to backup to but I'd like to rule out some sort of software / driver issue before forking out for a new one as it seemed to work fine on Ubuntu 18.04 and Windows 8.1 on my laptop, but it doesn't seem to like my desktop running Ubuntu 20.04.

I guess the first step is to check the disk to see if it is in some way faulty?

---

### Post by mrdc76 on 2020-07-23
Gnome Disks.

---

### Post by ActionParsnip on 2020-07-23
hdparm is good

If you download the Ultimate Boot CD it will have checkers and tools from the main drive manufacturers including Seagate (seatools etc)

---

### Post by Holger_Gehrke on 2020-07-23
If the SSD implements SMART (Self-Monitoring and Reporting Technology) you can use 'smartctl' to make it test itself extensively. Gnome Disks offers some access to these facilities, too.

Holger

---

### Post by TheFu on 2020-07-23
Gnome-disks has all sorts of problems. Best to purge that from our systems.
**smartctl** and **badblocks** are the tools to be used.  But having daily, automatic, versioned, backups is really the "killer application" for anything related to data.  SMART data doesn't always show anything prior to a failure.  Smartclt can be scripted and run periodically via root's crontab. Store the output in date-based files, so you can review the changes over time in the results using something like **meld** or **sdiff**.

However, why use any SSD for backup storage?  That's crazy wasteful and expensive. Use cheap spinning rust - for $40, a 2TB HDD will backup all the critical data that any home would normally have.  $40 seems to be the cost for any new HDD from 80GB - 2TB, so probably best to just get an 2TB backup disk.
There are many, many, many, better uses for SSDs.

---

### Post by jcdenton1995 on 2020-07-23
> **TheFu said:**
> **smartctl** and **badblocks** are the tools to be used.

I installed the smartmontools package and ran...
```
smartctl -a /dev/sda
```
however this returned the error "Read Device Identity failed: scsi error unsupported field in scsi command", the same error is returned when running...
```
smartctl -d scsi --test=long /dev/sda
```
I've searched online and there is some reference to others having the same issues when trying to run long tests, but I'm afraid at this time the answers are beyond my understanding.

Could this possibly indicate a problem with the drive in itself?

It's worth mentioning that I have no problem reading the smart data from my main drive which is an M.2 NVME ssd.

[B]Edit: Some progress, I managed to read the smart data from the drive by following the steps outlined within the first answer of [this thread]("https://askubuntu.com/questions/637450/cannot-perform-smart-data-and-self-test-on-external-hard-drive"), however I still get the same error when trying to run a short test (weird).

What I would like to know is how to read (understand) the 'vendor specific smart attributes and thresholds' section, I have posted it's output below...[/B]

```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       2
  2 Throughput_Performance  0x0026   252   252   000    Old_age   Always       -       0
  3 Spin_Up_Time            0x0023   090   090   025    Pre-fail  Always       -       3181
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5910
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       938
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       4
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       987
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       174
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   064   000    Old_age   Always       -       31 (Min/Max 5/44)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       180
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       4
225 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       31843
```

**I'm seeing the words 'pre-fail' and 'old age' a lot but as I don't know how to correctly interpret the output, I'm unsure as to what this means. A glancing over by a trained eye would be appreciated!**

---

### Post by TheFu on 2020-07-23
The manpage has all the different devices supported.  There is an options to have it guess too.  Different controllers have been the problem I've seen.   -d sat  -t long

---

### Post by jcdenton1995 on 2020-07-23
> **TheFu said:**
> The manpage has all the different devices supported.  There is an options to have it guess too.  Different controllers have been the problem I've seen.   -d sat  -t long

Thanks! I tried the long test and it started successfully! I can't run the whole thing now however I will run it tomorrow and see what it throws up...

---

### Post by TheFu on 2020-07-23
> **jcdenton1995 said:**
> Thanks! I tried the long test and it started successfully! I can't run the whole thing now however I will run it tomorrow and see what it throws up...

Smart tests can be run anytime without impacting existing work.  Just need to leave the computer on and powered for the duration.  Most of mine need under 300 minute - so 5 hours.

Or schedule it to run at midnight. Tomorrow morning, you can look at the results.  You can even have the system shutdown when it is done.
Long tests that fail to complete are likely due to failing - mostly dead - storage. [https://www.youtube.com/watch?v=xbE8E1ez97M](https://www.youtube.com/watch?v=xbE8E1ez97M) ;)

---

### Post by jcdenton1995 on 2020-07-24
Argh I got it wrong, its not a SSD, Its a HDD! it's just physically much smaller and quieter than any of the HDDs I have come across (which is not many). I was trying to fathom why "sudo smartctl -a" was putting out info like 'spin up time' and 'start stop count', believing it was something I was doing wrong, turns out it's a hard disk.

Just waiting on the results of the long test...

---

### Post by jcdenton1995 on 2020-07-24
> **TheFu said:**
> Or schedule it to run at midnight. Tomorrow morning, you can look at the results.  You can even have the system shutdown when it is done.
Long tests that fail to complete are likely due to failing - mostly dead - storage. [https://www.youtube.com/watch?v=xbE8E1ez97M](https://www.youtube.com/watch?v=xbE8E1ez97M) ;)

Haha I was expecting the link to be an instructional video, what show is that from?

Anyway the long test has finished, as stated above I realised that the drive is a HDD not an SSD, but no matter. I've posted some of the results below, specifically the ones that give cause for concern according to the table of SMART attributes on [the SMART Wikipedia page]("https://en.wikipedia.org/wiki/S.M.A.R.T.#ATA_S.M.A.R.T._attributes").

```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0023   090   090   025    Pre-fail  Always       -       3162
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       174
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       180
```

I don't suppose if anyone more experienced can confirm if these values could indicate an impending drive failure?

---

### Post by TheFu on 2020-07-24
Nope. Those values are common for laptop drives.  Without seeing the full set, can't say anything.

---

### Post by jcdenton1995 on 2020-07-24
> **TheFu said:**
> Nope. Those values are common for laptop drives.  Without seeing the full set, can't say anything.

Apologies, I just thought I'd try and identify the relevant info :)

```
=== START OF INFORMATION SECTION ===
Model Family:     Seagate Samsung SpinPoint M8 (AF)
Device Model:     ST1000LM024 HN-M101MBB
Serial Number:    S30CJADF416082
LU WWN Device Id: 5 0004cf 20d0f5cb4
Firmware Version: 2BA30001
User Capacity:    1,000,204,886,016 bytes [1.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    5400 rpm
Form Factor:      2.5 inches
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 6
SATA Version is:  SATA 3.0, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Jul 24 15:06:11 2020 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

```

```
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   051    Pre-fail  Always       -       2
  2 Throughput_Performance  0x0026   056   056   000    Old_age   Always       -       11885
  3 Spin_Up_Time            0x0023   090   090   025    Pre-fail  Always       -       3178
  4 Start_Stop_Count        0x0032   095   095   000    Old_age   Always       -       5914
  5 Reallocated_Sector_Ct   0x0033   252   252   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   252   252   051    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0024   252   252   015    Old_age   Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       945
 10 Spin_Retry_Count        0x0032   252   252   051    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       4
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       991
191 G-Sense_Error_Rate      0x0022   100   100   000    Old_age   Always       -       174
192 Power-Off_Retract_Count 0x0022   252   252   000    Old_age   Always       -       0
194 Temperature_Celsius     0x0002   064   057   000    Old_age   Always       -       31 (Min/Max 5/44)
195 Hardware_ECC_Recovered  0x003a   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   252   252   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   252   252   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   252   252   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0036   100   100   000    Old_age   Always       -       1
200 Multi_Zone_Error_Rate   0x002a   100   100   000    Old_age   Always       -       180
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       4
225 Load_Cycle_Count        0x0032   097   097   000    Old_age   Always       -       31911

```

---

### Post by TheFu on 2020-07-24
Power_On_Hours seems really low for most of the other numbers.
Are there any errors shown below the table?

---

### Post by Impavidus on 2020-07-24
On my 9 year old hard drive, the power-on time has increased from 390 to 450 hours over the past 18 months. It's my main system, it runs several hours each day. Seems there's a conversion factor off. Could be happening here too.

---

### Post by TheFu on 2020-07-24
I'm used to seeing Power_On_Hours like these:
```
smart.2020-05-30-sda:           9 Power_On_Hours   82413
smart.2020-05-30-sdb:           9 Power_On_Hours   88082
smart.2020-05-30-sdc:           9 Power_On_Hours   32910
smart.2020-05-30-sdd:           9 Power_On_Hours   55283
smart.2020-05-30-sde:           9 Power_On_Hours   62061
smart.2020-05-30-sdf:           9 Power_On_Hours   62061
smart.2020-05-31-300G:          9 Power_On_Hours   41018
smart.2020-06-28.sda:           9 Power_On_Hours   88770
smart-2020-07-17-Data-r2-A:     9 Power_On_Hours   63219
smart-2020-07-17-Data-r2-B:     9 Power_On_Hours   63220
smart-2020-07-17-raid-A:        9 Power_On_Hours   56442
smart-2020.07-failing-toshiba-2tb-romulus-raid: 9 Power_On_Hours  33888
smart-2020.07-failing-toshiba-2tb-romulus-raid-B:9 Power_On_Hours 56320
[B]smart-2020.07-2TB-romulus-HGST-original: 9 Power_On_Hours  0
smart-2020.07-newHGST-DC:       9 Power_On_Hours   62[/B]
**smart-2020-07-17-raid-B:        9 Power_On_Hours   183**
smart.backups-2020-06-27.sdg:   9 Power_On_Hours   68328
smart.data_1.5T-sde:            9 Power_On_Hours   46920
smart.data_1tb.1tb-sdb:         9 Power_On_Hours   61640
smart.data_r2-2tb-sdf:          9 Power_On_Hours   35613
smart.data_r2-2tb-sdg:          9 Power_On_Hours   35613
smart.misc_mybook-2tb-sdh:      9 Power_On_Hours   32567
smart.misc_mybook-2tb-sdh-2020: 9 Power_On_Hours   55576
smart.raid1.2tb-sdc:            9 Power_On_Hours   6435
smart.raid1.2tb-sdd:            9 Power_On_Hours   28808
smart.root.300g-sda:            9 Power_On_Hours   59297
```
The HDDs with less than 5000 hrs were added earlier this month.

Heck, my 18 month old SSD has 9574 Power_On_Hours.  The Power_Cycle_Count counts here are pretty small, usually between 15 and 100 regardless of years of service. ;)

---

### Post by jcdenton1995 on 2020-07-24
> **TheFu said:**
> Power_On_Hours seems really low for most of the other numbers.
Are there any errors shown below the table?

No no errors, it specifically said the test completed with no errors.

What is strange is that many of the power on hours I believe come from it being permanently being attached to the back of my dad's mack, he didn't even use the thing that much, just for the occasional backup, or so he believes.

Edit: sorry just to be clear its an external USB drive, so perhaps that is why the power on hours are comparatively low?

---

