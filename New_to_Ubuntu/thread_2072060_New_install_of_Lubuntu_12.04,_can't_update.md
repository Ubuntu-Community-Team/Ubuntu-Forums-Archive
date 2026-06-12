---
title: "New install of Lubuntu 12.04, can't update"
date: 2012-10-17
forum: New to Ubuntu
---

### Post by AnarisBell on 2012-10-17
Hi all,

Complete newbie to Linux here, just went through a bunch of crap to install EasyPeasy, had some issues and decided to go with a more recent distribution. I managed to get Lubuntu 12.04 installed with relative ease, however...

There is a red icon on my "toolbar" (not sure what the terms are for everything, haha) for updates, with a big grayed out error message on it. It reads:

"An error occurred, please run Package Manager from the right-click menu or apt- get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E:Read error - read (5: Input/output error), E:Problem opening /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.)'. This usually means that your installed packages have unmet dependencies."

So I have no idea what that means :confused: So I go and open Synaptic Package Manager" since that seems to be the only package managing thing I can find. It initially shows nothing, and then it errors with: 

"E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report."

Can someone give me a hand? I have absolutely no clue where to go from here.

---

### Post by NikTh on 2012-10-17
Hi , 

you can debug the problem from terminal . (In Lubuntu , lxterminal). Open it and paste these commands inside ```
sudo apt-get update 
sudo apt-get upgrade
``` 
it will ask for your password , write it carefully cuz nothing will appears (like not write something). 

Post the results back here and put the results between these brackets **[noparse]```
here
```[/noparse]** so can be readable by others. 

Thanks

---

### Post by AnarisBell on 2012-10-17
Thanks so much for the fast reply :)

Here's what I got from the first one (get update):

```
brianna@brianna-netbook:~$ sudo apt-get update
Ign http://extras.ubuntu.com precise InRelease
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://extras.ubuntu.com precise Release   
Hit http://extras.ubuntu.com precise/main Sources                     
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Ign http://ca.archive.ubuntu.com precise InRelease                   
Ign http://security.ubuntu.com precise-security InRelease            
Ign http://extras.ubuntu.com precise/main Translation-en_CA          
Ign http://extras.ubuntu.com precise/main Translation-en
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://security.ubuntu.com precise-security Release
Ign http://ca.archive.ubuntu.com precise-updates InRelease
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources
Ign http://ca.archive.ubuntu.com precise-backports InRelease
Hit http://security.ubuntu.com precise-security/multiverse Sources
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://ca.archive.ubuntu.com precise Release.gpg
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates Release.gpg
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports Release.gpg
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise Release
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-updates Release
Hit http://ca.archive.ubuntu.com precise-backports Release
Hit http://ca.archive.ubuntu.com precise/main Sources
Hit http://ca.archive.ubuntu.com precise/restricted Sources
Hit http://ca.archive.ubuntu.com precise/universe Sources
Hit http://ca.archive.ubuntu.com precise/multiverse Sources
Hit http://ca.archive.ubuntu.com precise/main i386 Packages
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates/main Sources
Hit http://ca.archive.ubuntu.com precise-updates/restricted Sources
Hit http://ca.archive.ubuntu.com precise-updates/universe Sources
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://ca.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/main Sources
Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources
Hit http://ca.archive.ubuntu.com precise-backports/universe Sources
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/main Translation-en
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
```

And the second one (upgrade):

```
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
```

---

### Post by NikTh on 2012-10-17
This error ```
E: Read error - read (5: Input/output error)
``` is odd ! 

Usually this error caused by a fault of file-system of HDD (hardware) , but I am not sure in your situation if the error caused by this , or by sources.list 

So give the results of this command to see what happen in your sources.list file and /sources.list.d/ folder. 

```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
``` 

copy-paste the command from here to your terminal if you want. 

Thanks

---

### Post by AnarisBell on 2012-10-17
Alright, here goes!

```
brianna@brianna-netbook:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	#deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423)]/ precise main multiverse restricted universe
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
     6	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    11	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://ca.archive.ubuntu.com/ubuntu/ precise universe
    17	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise universe
    18	deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
    19	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
    27	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise multiverse
    28	deb http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    29	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    37	deb-src http://ca.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu precise-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    41	deb http://security.ubuntu.com/ubuntu precise-security universe
    42	deb-src http://security.ubuntu.com/ubuntu precise-security universe
    43	deb http://security.ubuntu.com/ubuntu precise-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu precise partner
    51	# deb-src http://archive.canonical.com/ubuntu precise partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb http://extras.ubuntu.com/ubuntu precise main
    56	deb-src http://extras.ubuntu.com/ubuntu precise main

```

Thanks again for taking the time to help :D

---

### Post by NikTh on 2012-10-17
OK , I don't see anything wrong inside sources.list (and this is not good). 

Boot from the LiveCD-or-USB and open a terminal (cuz we want the partition unmounted) and then give the results of this command 
```
sudo fdisk -l
```We will do some tests to your HDD and to the filesystem. 

Thanks

---

### Post by AnarisBell on 2012-10-17
I'm sorry, this is all so strange. I think I did something wrong. Booted from my Lubuntu on SD (its way faster on this netbook than the USB) and opened LXTerminal, typed your command. Here's what I got:

```
lubuntu@lubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

```

---

### Post by NikTh on 2012-10-17
Yes its ok.. its not 1 (one) but lowercase L 

Copy-paste the command from here to terminal.

Thanks

---

### Post by AnarisBell on 2012-10-17
Bahahaha, whoops!! It was so short I didn't bother copying it, that'll teach me :)

```


lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e466e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   486322175   243160064   83  Linux
/dev/sda2       486324222   488396799     1036289    5  Extended
/dev/sda5       486324224   488396799     1036288   82  Linux swap / Solaris

Disk /dev/sdb: 4093 MB, 4093640704 bytes
63 heads, 62 sectors/track, 2046 cylinders, total 7995392 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7995391     3993600    b  W95 FAT32

```

If I don't end up replying to this thread after this post, I'll be checking it tomorrow. It's getting pretty late here :)

---

### Post by NikTh on 2012-10-17
From the LiveSD , give the results of these commands 

```
sudo e2fsck -f -v /dev/sda1
``` 

```
sudo apt-get install --no-install-recommends smartmontools
sudo smartctl -a /dev/sda
``` 

Thanks

---

### Post by AnarisBell on 2012-10-17
Back again :) First bit's results:

```
lubuntu@lubuntu:~$ sudo e2fsck -f -v /dev/sda1
e2fsck 1.42 (29-Nov-2011)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  106544 inodes used (0.70%)
      48 non-contiguous files (0.0%)
     102 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 83106/12
 1440818 blocks used (2.37%)
       0 bad blocks
       1 large file

   72089 regular files
   10180 directories
      57 character device files
      25 block device files
       0 fifos
       0 links
   24181 symbolic links (23333 fast symbolic links)
       3 sockets
--------
  106535 files

```

Second:

```
lubuntu@lubuntu:~$ sudo apt-get install --no-install-recommends smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  smartmontools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 455 kB of archives.
After this operation, 1,315 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main smartmontools i386 5.41+svn3365-1 [455 kB]
Fetched 455 kB in 3s (124 kB/s)        
Selecting previously unselected package smartmontools.
(Reading database ... 132720 files and directories currently installed.)
Unpacking smartmontools (from .../smartmontools_5.41+svn3365-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up smartmontools (5.41+svn3365-1) ...

```

Third:

```
lubuntu@lubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     Western Digital Scorpio Blue Serial ATA
Device Model:     WDC WD2500BEVT-75A23T0
Serial Number:    WD-WXH1AC0A8333
LU WWN Device Id: 5 0014ee 6ab90dc3b
Firmware Version: 01.01A01
User Capacity:    250,059,350,016 bytes [250 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Oct 17 15:52:52 2012 UTC
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
data collection: 		( 6780) seconds.
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
recommended polling time: 	 (  82) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x7037)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always       -       15804
  3 Spin_Up_Time            0x0027   154   148   021    Pre-fail  Always       -       1258
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       1751
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   200   200   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   097   097   000    Old_age   Always       -       2824
 10 Spin_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       1743
191 G-Sense_Error_Rate      0x0032   001   001   000    Old_age   Always       -       626
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       183
193 Load_Cycle_Count        0x0032   096   096   000    Old_age   Always       -       313257
194 Temperature_Celsius     0x0022   111   090   000    Old_age   Always       -       32
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   198   197   000    Old_age   Always       -       107
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0008   100   253   000    Old_age   Offline      -       0
240 Head_Flying_Hours       0x0032   097   097   000    Old_age   Always       -       2547
241 Total_LBAs_Written      0x0032   200   200   000    Old_age   Always       -       3785950397
242 Total_LBAs_Read         0x0032   200   200   000    Old_age   Always       -       7100809381
254 Free_Fall_Sensor        0x0032   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 7 (device log contains only the most recent five errors)
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

Error 7 occurred at disk power-on lifetime: 2822 hours (117 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 3f 37 2d 20 e0  Error: UNC 63 sectors at LBA = 0x00202d37 = 2108727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 3f 01 2d 20 e0 00      00:00:22.708  READ DMA
  20 ff 3f 01 2d 20 e0 00      00:00:20.244  READ SECTOR(S)
  c8 ff 3f 01 2d 20 e0 00      00:00:17.779  READ DMA
  20 ff 3f 01 2d 20 e0 00      00:00:15.471  READ SECTOR(S)
  c8 ff 3f 01 2d 20 e0 00      00:00:13.162  READ DMA

Error 6 occurred at disk power-on lifetime: 2822 hours (117 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 3f 37 2d 20 e0  Error: UNC at LBA = 0x00202d37 = 2108727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 ff 3f 01 2d 20 e0 00      00:00:20.244  READ SECTOR(S)
  c8 ff 3f 01 2d 20 e0 00      00:00:17.779  READ DMA
  20 ff 3f 01 2d 20 e0 00      00:00:15.471  READ SECTOR(S)
  c8 ff 3f 01 2d 20 e0 00      00:00:13.162  READ DMA

Error 5 occurred at disk power-on lifetime: 2822 hours (117 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 3f 37 2d 20 e0  Error: UNC 63 sectors at LBA = 0x00202d37 = 2108727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 3f 01 2d 20 e0 00      00:00:17.779  READ DMA
  20 ff 3f 01 2d 20 e0 00      00:00:15.471  READ SECTOR(S)
  c8 ff 3f 01 2d 20 e0 00      00:00:13.162  READ DMA

Error 4 occurred at disk power-on lifetime: 2822 hours (117 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 3f 37 2d 20 e0  Error: UNC at LBA = 0x00202d37 = 2108727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  20 ff 3f 01 2d 20 e0 00      00:00:15.471  READ SECTOR(S)
  c8 ff 3f 01 2d 20 e0 00      00:00:13.162  READ DMA

Error 3 occurred at disk power-on lifetime: 2822 hours (117 days + 14 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 3f 37 2d 20 e0  Error: UNC 63 sectors at LBA = 0x00202d37 = 2108727

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 ff 3f 01 2d 20 e0 00      00:00:13.162  READ DMA

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1947         -
# 2  Short offline       Completed without error       00%       493         -
# 3  Short offline       Completed without error       00%         0         -
# 4  Short offline       Aborted by host               90%         0         -
# 5  Extended offline    Aborted by host               70%         0         -

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

### Post by NikTh on 2012-10-17
File-system seems OK, but the HDD no. 

```
1 Raw_Read_Error_Rate     0x002f   199   199   051    Pre-fail  Always       -       15804
197 Current_Pending_Sector  0x0032   198   197   000    Old_age   Always       -       107
```

What above errors means ? Look here: [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).

So the I/O error (Input-Output) might be due to the poor state of the Disk. 

I don't know what else you can do , so wait for someone else with a better idea. 

Thanks

---

### Post by AnarisBell on 2012-10-17
Alright, well thanks for trying to help and bearing with me!

Is this something that could be avoided with a different distribution? I purposely haven't put anything important on it yet until I know it will work okay. 

I wanted to download Skype and that is in the package manager from what I've read online... So maybe I should just go back to EasyPeasy 1.6 and avoid updating? It does come with Skype, anyway. 

All I want to use this little netbook for is writing a book, Skype, and occasional web browsing. Is it bad to avoid updates in that case? My problems with EasyPeasy started when I updated, then the machine got stuck mid-boot and I made the mistake of hard-resetting it. :S

---

### Post by NikTh on 2012-10-17
If you have 32bit Lubuntu , then you can download skype from the Web page and install it. 
How to : [http://www.unixmen.com/howto-install-skype-in-ubuntu-12-04-precise-pangolin/](http://www.unixmen.com/howto-install-skype-in-ubuntu-12-04-precise-pangolin/)

In 64bit version this is not going to happen cuz you need dependencies to be installed, 32bit libs. 

Thanks

---

### Post by Rex Bouwense on 2012-10-18
>  Is it bad to avoid updates in that case? 
Generally updates are a good thing.  They introduce new versions of programs that you already have installed.  They provide patches to installed programs that correct errors.  They are not a thing to be feared or dreaded.  If you are going to use the computer on the Internet I would not avoid updates in any case especially if you value the work that you have created on your computer, but that is always up to the user.  Enjoy.

---

