---
title: "usb not detected"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by MADinMelbourne on 2012-07-10
Hi, very much a beginner here, I do follow instructions and am willing to learn... however a lot of code is waaay over my head, so please be patient with my questions.

Plugged in NexStar CX and I don't see it... although on terminal it is showing up as connected: (have two plugs into laptop, one into the unit as per instructions from the CX) 

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1784:0004 TopSeed Technology Corp. RF Combo Device
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b043 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


sudo fdisk -l  shows this:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe346e890

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10240000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1276       19086   143066857+  83  Linux
/dev/sda3           19087       19457     2980057+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 3963 MB, 3963617280 bytes
1 heads, 16 sectors/track, 483840 cylinders
Units = cylinders of 16 * 512 = 8192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *           9      483840     3870655+   c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.


Thank you in advance for taking time to look into this.

---

### Post by Redblade20XX on 2012-07-11
Do you know what file system the device is formatted on?

- Red

---

### Post by MADinMelbourne on 2012-07-11
No, where do I find that?

---

### Post by NikTh on 2012-07-11
Open a terminal and write
```
watch -n 1 "dmesg | tail"
``` then plug your usb and see the messages. Post them here. 
Also as you have pluged in your usb you can give ```
sudo parted -l
```Post any results here inside code tags [CODE] , use the # symbol in top of message pane.

---

### Post by MADinMelbourne on 2012-07-11
so far nothing shown since the code below... waited 20 mins thought I'd done something wrong so I started again.

```


[  172.302336] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  172.303859] sd 4:0:0:0: [sdb] 7821312 512-byte logical blocks: (4.00 GB/3.72
GiB)
[  172.305474] sd 4:0:0:0: [sdb] Write Protect is off
[  172.305483] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  172.305490] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  172.309344] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  172.309356]  sdb: sdb1
[  172.320236] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  172.320248] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  211.598043] usb 2-3: USB disconnect, address 2



```

waiting for messages to show, so far nothing (15mins later), light is on the hard drive case and there's a white box flashing at the bottom of the terminal window.

Thanks for your help and for showing me how to # code.

---

### Post by NikTh on 2012-07-11
1) Unplug the usb
2) open terminal and write the command 
```

watch -n 1 "dmesg | tail -n 20"
```3) plug the usb and wait few second , not minutes to see any **new messages**
4) Ctr+c to exit. Then run ```
sudo parted -l
``` post results here.

**ADD:**
From the above results that you posted i think that your usb device is /dev/sdb . So you can try this also..
```
sudo mkdir /media/usbflash
sudo mount /dev/sdb /media/usbflash
```

---

### Post by MADinMelbourne on 2012-07-11
```

[  172.305474] sd 4:0:0:0: [sdb] Write Protect is off
[  172.305483] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  172.305490] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  172.309344] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  172.309356]  sdb: sdb1
[  172.320236] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  172.320248] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[  211.598043] usb 2-3: USB disconnect, address 2
[ 8914.362050] UDF-fs: Partition marked readonly; forcing readonly mount
[ 8914.434685] UDF-fs INFO UDF: Mounting volume 'TRAFFIC_P4', timestamp 2001/07/
31 18:46 (1258)


```

nothing else showed on the screen

```


reality@reality-laptop:~$ watch -n 1 "dmesg | tail"
reality@reality-laptop:~$ sudo parted -1
[sudo] password for reality: 
parted: invalid option -- '1'
Usage: parted [-hlmsv] [-a<align>] [DEVICE [COMMAND [PARAMETERS]]...]
reality@reality-laptop:~$ 


```

---

### Post by MADinMelbourne on 2012-07-11
```

reality@reality-laptop:~$ sudo mkdir /media/usbflash
mkdir: cannot create directory `/media/usbflash': File exists
reality@reality-laptop:~$ sudo mount /dev/sdb /media/usbflash
mount: special device /dev/sdb does not exist
reality@reality-laptop:~$ 

```

---

### Post by NikTh on 2012-07-11
Copy - paste the command from here.. for accuracy 
```
sudo parted -l
``` Its not 1 (one) its l (list)

[B]Also:
[/B]give results of these commands 
```
mount
``` 
&
```
uname -r
```

---

### Post by MADinMelbourne on 2012-07-11
```

Model: ATA ST9160821AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  10.5GB  10.5GB  primary  ntfs            boot
 2      10.5GB  157GB   147GB   primary  ext3
 3      157GB   160GB   3052MB  primary  linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

No Implementation: Partition 1 isn't aligned to cylinder boundaries.  This is still unsupported.


```

---

### Post by MADinMelbourne on 2012-07-11
mount:

```

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro,user_xattr)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/reality/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=reality)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/mmcblk0p1 on /media/3AB0-13F3 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=reality)


```

---

### Post by MADinMelbourne on 2012-07-11
uname -r

```

2.6.32-41-generic


```

---

### Post by NikTh on 2012-07-11
Try 
```
cd /media/3AB0-13F3
``` 
and then 
```
 ls 
``` 
is this your usb-flash ? can you see your files in there ?

---

### Post by MADinMelbourne on 2012-07-11
this looks like my phone backup file

```

reality@reality-laptop:/media/3AB0-13F3$ ls
Android                    LunaPark
armscrossedTCM.png         MADartwork
Bambuser                   madinmelbournefat-webfont.ttf
clockworkmod               MattsMusic
copilot                    Meetup
data                       music
DCIM                       napster
download                   onhisheadTCMlogo4.png
DREAIMG.nbh                Pictures
Eclectico - Alansfile.xls  ringtones
Evernote                   tmp
factory.widgets.skins      UniversalAndroot-1.6.2-beta5.apk
GOLauncherEX               untitled folder
kindle                     update.zip
LazyList                   video
Little Photo               youlu
LOST.DIR                   zedge


```

The file I'm looking for is a 500G hard drive which is empty

---

### Post by NikTh on 2012-07-11
Do you want to try with a LiveUsb of Ubuntu 12.04 ? I see an old kernel here and i don't know if its responsible for this.

---

### Post by MADinMelbourne on 2012-07-11
if you're OK with stepping me thru it, sure. Thanks for your perserverance thus far.

---

### Post by NikTh on 2012-07-11
Download a Desktop iso image from here --> [http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)  and burn it to an empty usb(at least 2GB) with unetbootin . To install unetbootin ```
sudo apt-get install unetbootin
```. 
Then boot from usb and click "default" then plug your external hdd ( its ext.HDD i assume from size.. 500GB) and see if recognized.

**Edit: **
I just saw in your fist post that is NexStar CX . Is this a sata drive that you put it to a Usb case ? If yes then maybe something wrong with usb case ? ?

---

### Post by MADinMelbourne on 2012-07-11
I just saw in your fist post that is NexStar CX Is this a sata drive that you put it to a Usb case?

Took the casing apart, unscrewed everything and started again.. plugged the unit into somebody elses computer (Windows) and the HD was picked up.

Downloading Ubuntu 12.04 keeps getting interrupted @ .05mb, have tried six times. I've rebooted the laptop twice and same thing keeps happening.

Getting tired now, will look at it again tomorrow.

THANK YOU VERY MUCH FOR YOUR HELP.. really appreciated.

---

### Post by MADinMelbourne on 2012-07-12
ubuntu 12.04 now downloading on usb stick...after taking the hard case apart, and putting it back together again (I hadn't screwed it together properly) lsusb is now showing something different:
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 1784:0004 TopSeed Technology Corp. RF Combo Device
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. transcend storejet 25P
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b043 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

On my housemates laptop (Windows) the hard drive doesn't crop up immediately, I can only find it in the hard drive section.

Is this sounding like it's a faulty hard drive?

---

### Post by NikTh on 2012-07-12
> **MADinMelbourne said:**
> 
[/CODE]On my housemates laptop (Windows) the hard drive doesn't crop up immediately, I can only find it in the hard drive section.

Is this sounding like it's a faulty hard drive?

You can check your hard drive for errors with smart utility. Either from windows or Ubuntu. 
From Ubuntu you must frist install smartmontools```
sudo apt-get install smartmontools
```
then with disk plugged of course , you must give this command 
```
sudo smartctl -a /dev/sd?
``` where sd? = your hdd. 
I DON'T know if your HDD supports SMART data .. check it out and see. 

I continue to believe that usb case is responsible about this situation :P

---

### Post by MADinMelbourne on 2012-07-13
FYI didn't have any luck downloading ubuntu 12.04 onto usb stick, gave up after 2x 3hour attempts. That was all I did yesterday as far as this puzzle is concerned.

I'm also thinking ubuntu's not picking up because there's something wrong with the case. On Monday I'm buying an external harddrive, meanwhile, here is the result of your last instructions:

```


=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.3
Device Model:     ST9160821AS
Serial Number:    5MA5B0CF
Firmware Version: 3.ALD
User Capacity:    160,041,885,696 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Fri Jul 13 21:17:23 2012 EST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)	Offline data collection activity
					was completed without error.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 ( 426) seconds.
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
recommended polling time: 	 ( 111) minutes.
SCT capabilities: 	       (0x0001)	SCT Status supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   118   082   006    Pre-fail  Always       -       190397358
  3 Spin_Up_Time            0x0003   099   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   098   098   020    Old_age   Always       -       2618
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   084   060   030    Pre-fail  Always       -       273142748
  9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -       10269
 10 Spin_Retry_Count        0x0013   100   100   034    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   020    Old_age   Always       -       2311
187 Reported_Uncorrect      0x0032   040   040   000    Old_age   Always       -       60
189 High_Fly_Writes         0x003a   098   098   000    Old_age   Always       -       2
190 Airflow_Temperature_Cel 0x0022   061   049   045    Old_age   Always       -       39 (Lifetime Min/Max 16/39)
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       722
193 Load_Cycle_Count        0x0032   045   045   000    Old_age   Always       -       111094
194 Temperature_Celsius     0x0022   039   051   000    Old_age   Always       -       39 (0 11 0 0)
195 Hardware_ECC_Recovered  0x001a   066   058   000    Old_age   Always       -       124203801
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 TA_Increase_Count       0x0032   100   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 162 (device log contains only the most recent five errors)
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

Error 162 occurred at disk power-on lifetime: 9941 hours (414 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9e 8a b9 e9  Error: UNC at LBA = 0x09b98a9e = 163154590

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 05 9e 8a b9 e9 00      00:05:31.945  READ DMA
  27 00 00 00 00 00 e0 00      00:05:31.937  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:31.929  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:05:31.929  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:05:31.921  READ NATIVE MAX ADDRESS EXT

Error 161 occurred at disk power-on lifetime: 9941 hours (414 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9e 8a b9 e9  Error: UNC at LBA = 0x09b98a9e = 163154590

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 05 9e 8a b9 e9 00      00:05:27.533  READ DMA
  27 00 00 00 00 00 e0 00      00:05:27.528  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:25.346  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:05:25.346  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:05:25.337  READ NATIVE MAX ADDRESS EXT

Error 160 occurred at disk power-on lifetime: 9941 hours (414 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9e 8a b9 e9  Error: UNC at LBA = 0x09b98a9e = 163154590

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 05 9e 8a b9 e9 00      00:05:27.533  READ DMA
  27 00 00 00 00 00 e0 00      00:05:27.528  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:25.346  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:05:25.346  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:05:25.337  READ NATIVE MAX ADDRESS EXT

Error 159 occurred at disk power-on lifetime: 9941 hours (414 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9e 8a b9 e9  Error: UNC at LBA = 0x09b98a9e = 163154590

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 05 9e 8a b9 e9 00      00:05:20.943  READ DMA
  27 00 00 00 00 00 e0 00      00:05:20.922  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:25.346  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:05:25.346  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:05:25.337  READ NATIVE MAX ADDRESS EXT

Error 158 occurred at disk power-on lifetime: 9941 hours (414 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 9e 8a b9 e9  Error: UNC at LBA = 0x09b98a9e = 163154590

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 05 9e 8a b9 e9 00      00:05:20.943  READ DMA
  27 00 00 00 00 00 e0 00      00:05:20.922  READ NATIVE MAX ADDRESS EXT
  ec 00 00 00 00 00 a0 00      00:05:20.914  IDENTIFY DEVICE
  ef 03 46 00 00 00 a0 00      00:05:20.906  SET FEATURES [Set transfer mode]
  27 00 00 00 00 00 e0 00      00:05:20.906  READ NATIVE MAX ADDRESS EXT

SMART Self-test log structure revision number 1

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

reality@reality-laptop:~$ 

```

---

### Post by NikTh on 2012-07-13
> **MADinMelbourne said:**
> 
```

1 Raw_Read_Error_Rate     0x000f   118   082   006    Pre-fail  Always       -     190397358
9 Power_On_Hours          0x0032   089   089   000    Old_age   Always       -     10269
187 Reported_Uncorrect      0x0032   040   040   000    Old_age   Always       -     60
195 Hardware_ECC_Recovered  0x001a   066   058   000    Old_age   Always       -    124203801
```
Hi ,
Hmm.. i see some bad values here. And also see that hdd is old.. "Power_On_Hours" 
Take a look at here --> [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T). , about those values. 
I am not very sure but i think your hdd dying . Sorry . 
Thanks

---

### Post by MADinMelbourne on 2012-07-14
YES, I'm aware of the HDD dying, that's why I'm keen to transfer files onto an external harddrive and upgrade. Guy at the shop suggested I put a new harddrive into a case and copy what I need on to it. That's where the plan has gone down the tube, I hadn't planned on the usb not being detected.

What are the bad values? What action would you suggest I take?

---

### Post by MADinMelbourne on 2012-07-16
Matter is resolved, took the hard case back to the shop, new disc - it needed to be formatted.

---

