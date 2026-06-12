---
title: "/home not ready or not present"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by klqd on 2012-05-25
xubuntu takes ages to boot up, and then i get that message. if i skip mounting it i can still log in but only as a guest.

there's some fairly important [not life saving but many hours worth of] documents that i can't access.


thanks.

---

### Post by klqd on 2012-05-25
i don't seem able to boot from live-usb. it at least takes a very long time.

---

### Post by steeldriver on 2012-05-25
you can run these commands in a terminal:

```
sudo fdisk -l

mount

```to show you what drives (partitions) are available on your system and where it is trying to mount them

did you select the option to encrypt your home dir?

---

### Post by klqd on 2012-05-25
the /home drive is dev/sda5. there is no sda4, incase that's important. no i don't think i asked it to encrypt the home drive.

when i press m for manual recovery at boot up, i can try to mount it but i get a long error message ending with

```
Buffer I/O error on device sda5, logical block 47
```

sorry i can't think of a way of posting the whole message.

edit actually, i now have access to my documents so am copying them to a new directory /copy

i will probably once that is done try a fresh install, so let me know if there's an easy alternative!

---

### Post by NikTh on 2012-05-25
> **klqd said:**
> xubuntu takes ages to boot up, and then i get that message. if i skip mounting it **i can still log in but only as a guest.**

there's some fairly important [not life saving but many hours worth of] **documents that i can't access.**


thanks.

You cannot access as a guest , but you can access them as the owner i guess. When you are logged in as guest open terminal and try to change user.. ```
su <your username>
password: 
``` give your username and password .

---

### Post by trivialpackets on 2012-05-25
At the very least, if you can boot into a live ubuntu cd, you should be able to plug in a usb drive and manually move the files from your user that you can't access to the usb drive, provided of course that you did not encrypt the drive.  

It sounds to me like you may have some bad sectors on that drive, so I would recommend backing up your data as soon as possible.  After this, I would use a utility to test the drive and consider replacing the drive, but that's me.  SMART utility I think is one that you could use.

Here's a link on checking the hard drive with an ubuntu live cd.

[http://mikebeach.org/2011/05/21/how-to-check-your-hard-drives-smart-status-using-a-ubuntu-live-cd/](http://mikebeach.org/2011/05/21/how-to-check-your-hard-drives-smart-status-using-a-ubuntu-live-cd/)

---

### Post by klqd on 2012-05-25
it actually does boot now i manually mounted it! i'll post again if there's any problems or if i did do a fresh install...

---

### Post by oldfred on 2012-05-25
I might still run e2fsck on /home

Must be unmounted:
Try "e2fsck -f /dev/sda5". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.


#From liveCD so everything is unmounted,swap off if necessary, change example shown with sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors:
sudo e2fsck -f -y -v /dev/sda5

---

### Post by klqd on 2012-05-25
well it's unbearably slow as user, and i can't see me ever copying anything to an external drive as user. but su does not work as guest, and otherwise i do not have privileges for the new directory that i think i created. also, it does mount /home now, so i do not have the option of using the command line before logging on, which seemed to have been working ok.

thanks.

---

### Post by klqd on 2012-05-25
> #From liveCD so everything is unmountedi only tried once but this does not work.

is there any way to have access to the command line before log in?


to clarify:
don't have access to documents as guest
everything impossibly slow as user [a few minutes to open a folder]
live-usb doesn't seem to boot.

---

### Post by matt_symes on 2012-05-25
Hi

...and check the SMART status of the hard drive as well.

From a LiveCD, open disk utility and select the drive.

Hit the "view smart data button". In the window that appears hit "Run self test" and select the extended option.

It will take a good while to run. When it's completed check its status again.

I tend to do this and run fsck (sometimes using the dry run option), if i suspect drive problems, as a matter of course.

Kind regards

---

### Post by klqd on 2012-05-25
there is no disk utility on xubnutu and i don't seem able to install it when using usb-live [which now works]

running e2fsck i get the following error

```
error reading block 47 (attempt to read block from filesystem resulted in short read). ignore error<y>?
```


i told it not to ignore the error, then when resize inode not valid, i recreated.
free blocks count wrong twice, which i told it to fix.

then the command finished, after saying sda5 was 4.6$ non contiguous.

should i do a fresh install - i backed up my files.
thanks.

---

### Post by klqd on 2012-05-25
managed to now login as user as normally. there is a crash report with executable path /usr/lib/i386-linux-gnu/tumbler-1/timblerd


everything seems as yet to be working as normal.

edit there was another crash report on usr/Thunar.

---

### Post by matt_symes on 2012-05-25
Hi

You can check the smart status from the command line (I did not realise there was no disk utility in xubutu and that is why i normally give command line instructions).

```
sudo apt-get install smartmontools
```

```
sudo smartctl -t long /dev/sda
```

This assume sda is your hard drive.

When it has finished....

```
sudo smartctl -a /dev/sda
```

... will print out a report of your hard drive.

You can post it back here if you want.

Hopefully the fsck suggestion from oldfred will have fixed your problems though.

Kind regards

---

### Post by klqd on 2012-05-25
cheers guys!
> Hopefully the fsck suggestion from oldfred will have fixed your problems though.yes it did - thanks!

not sure why i couldn't boot with live-usb at first; i erased the usb and reinstalled and it went fine.

will try that extra check suggested later this evening.


:guitar:

---

### Post by klqd on 2012-05-26
i would try to do that check you suggested but i've had to reset the computer 4 or 5 times in a row because it's frozen trying to load safari. also, i tried live-usb and the mouse wouldn't move on bootup [though i could still use the keyboard to tell it how to shut down].


thanks.

edit i can't do that check either. it freezes at 0% checking dependency tree.

---

### Post by klqd on 2012-05-26
i think this worked, i had to quit the terminal before asking for a print out. not sure why firefox takes like ten minutes to load.


```
=== START OF INFORMATION SECTION ===
Model Family:     Toshiba 2.5" HDD MK..65GSX
Device Model:     TOSHIBA MK1665GSX
Serial Number:    50E3S4L7S
LU WWN Device Id: 5 000039 28570449f
Firmware Version: GJ002J
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Sat May 26 16:06:27 2012 BST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 241)    Self-test routine in progress...
                    10% of test remaining.
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
recommended polling time:      (  45) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   093   093   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1171
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       2047
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       670
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   083   083   000    Old_age   Always       -       7169
 10 Spin_Retry_Count        0x0033   140   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       995
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       104
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       81
193 Load_Cycle_Count        0x0032   091   091   000    Old_age   Always       -       98155
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       40 (Min/Max 13/49)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       598
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       870
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       39
222 Loaded_Hours            0x0032   088   088   000    Old_age   Always       -       5180
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       264
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

SMART Error Log Version: 1
ATA Error Count: 3246 (device log contains only the most recent five errors)
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

Error 3246 occurred at disk power-on lifetime: 7169 hours (298 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 02 db 45 f9 67  Error: UNC at LBA = 0x07f945db = 133776859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 d8 45 f9 40 08      01:10:09.601  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      01:10:09.601  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      01:10:09.601  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      01:10:09.600  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      01:10:09.600  SET FEATURES [Set transfer mode]

Error 3245 occurred at disk power-on lifetime: 7169 hours (298 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 8a db 45 f9 67  Error: UNC at LBA = 0x07f945db = 133776859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 88 d8 45 f9 40 08      01:09:55.401  READ FPDMA QUEUED
  61 10 80 68 56 4a 40 08      01:09:55.401  WRITE FPDMA QUEUED
  61 10 78 90 36 94 40 08      01:09:55.401  WRITE FPDMA QUEUED
  61 a0 70 30 42 04 40 08      01:09:55.401  WRITE FPDMA QUEUED
  61 08 68 70 59 c0 40 08      01:09:55.401  WRITE FPDMA QUEUED

Error 3244 occurred at disk power-on lifetime: 7169 hours (298 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 02 db 45 f9 67  Error: UNC at LBA = 0x07f945db = 133776859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 d8 45 f9 40 08      01:09:43.645  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      01:09:43.645  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      01:09:43.645  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      01:09:43.644  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      01:09:43.644  SET FEATURES [Set transfer mode]

Error 3243 occurred at disk power-on lifetime: 7169 hours (298 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 02 db 45 f9 67  Error: UNC at LBA = 0x07f945db = 133776859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 d8 45 f9 40 08      01:09:31.778  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      01:09:31.778  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      01:09:31.777  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      01:09:31.777  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      01:09:31.777  SET FEATURES [Set transfer mode]

Error 3242 occurred at disk power-on lifetime: 7169 hours (298 days + 17 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 41 02 db 45 f9 67  Error: UNC at LBA = 0x07f945db = 133776859

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 08 00 d8 45 f9 40 08      01:09:20.333  READ FPDMA QUEUED
  ef 10 02 00 00 00 a0 00      01:09:20.333  SET FEATURES [Reserved for Serial ATA]
  27 00 00 00 00 00 e0 00      01:09:20.333  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      01:09:20.333  IDENTIFY DEVICE
  ef 03 45 00 00 00 a0 00      01:09:20.332  SET FEATURES [Set transfer mode]

SMART Self-test log structure revision number 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


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

### Post by klqd on 2012-05-26
hi, 

since this crash at the start of the session [say 20 minutes] everything runs unusably slow. and then everything goes back to normal and it works.

what should i do?

---

### Post by klqd on 2012-05-26
now i can't log into xubuntu. i geta a black screen with a few lines of messages, ending with "checking battery" :(


i'll let you know if anything changes!

---

### Post by klqd on 2012-05-26
i tried a fresh install and it crashed saying there was a problem with the hard drive D:

is this fixable without a new drive?

---

