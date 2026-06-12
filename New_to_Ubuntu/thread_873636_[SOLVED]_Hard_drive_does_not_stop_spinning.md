---
title: "[SOLVED] Hard drive does not stop spinning"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by abhiroopb on 2008-07-29
I recently bought a 320gb Western Digital Scorpio Blue (2.5") and stuck it into my laptop. I then installed ubuntu, created 4 partitions (swap, /, /home, and XP) and so on.

Recently I have noticed that no matter how long I leave the computer for the hard drive just does not stop spinning. What should I do?

Thanks

EDIT: Just a note, I also installed Ramlog which is supposed to write log files to RAM so as to stop the hard disk spinning unnecessarily. I mention this as I have no idea how it works, so it may be causing a problem.

---

### Post by Het Irv on 2008-07-29
Do you have anything else that is running alot?  Processes, network useage, or anything eles that would affect the hard drive, or is the hard drive just spinning?

Does this only happen in Ubuntu or Windows as well?

---

### Post by JoneYee on 2008-07-29
Do you have conky installed?
```
sudo apt-get install conky
```

See which processes/applications are using up the most system resources.

Also, when the hard drive is spinning (unnecessarily) can you post the output of top?

```
top - 08:46:34 up 49 min,  2 users,  load average: 0.18, 0.39, 0.44
Tasks: 103 total,   1 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.3%us,  7.0%sy,  0.0%ni, 79.1%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    515580k total,   498168k used,    17412k free,    22156k buffers
Swap:   489940k total,        0k used,   489940k free,   253580k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5289 root      20   0 46328  21m 8040 S 10.0  4.3   4:39.64 Xorg               
 5931 jaredozv  20   0  193m  76m  25m S  4.0 15.1   3:47.75 firefox            
 5984 jaredozv  20   0 82836  20m  10m S  2.7  4.0   0:01.94 gnome-terminal     
 5170 root      20   0  3420 1220 1068 S  0.7  0.2   0:01.34 hald-addon-stor    
 5585 jaredozv  20   0 11084 4856 2612 S  0.7  0.9   0:00.58 pulseaudio         
 6096 jaredozv  20   0  2308 1104  852 R  0.7  0.2   0:00.04 top                
    1 root      20   0  2844 1692  544 S  0.0  0.3   0:01.84 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.16 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.26 kblockd/0          
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
  106 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kseriod            

```

---

### Post by abhiroopb on 2008-07-29
Well when I put my ear to where the HD is I can hear it spin. I guess it is being used while I am there, but I am talking about when I leave my computer running (without any open processes, save for the basic wireless and background program) and come back after like an hour and if I put my ear to the HD I can hear a lot of noise.

haven't really used Windows all that much, but I just noticed it so I guess I could test it ot on windows.

top output:

```

top - 21:53:06 up  2:51,  2 users,  load average: 0.23, 0.31, 0.30
Tasks: 148 total,   2 running, 145 sleeping,   0 stopped,   1 zombie
Cpu(s): 10.8%us,  2.6%sy,  0.0%ni, 85.4%id,  0.0%wa,  0.2%hi,  1.0%si,  0.0%st
Mem:   2074216k total,  1973840k used,   100376k free,    63200k buffers
Swap:  2931820k total,        0k used,  2931820k free,  1093124k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
16586 abhiroop  20   0  371m 146m  28m S    6  7.2   2:20.36 miro.real          
 6693 abhiroop  20   0  166m  60m  26m R    5  3.0   8:13.37 amarokapp          
 6057 root      20   0 97080  84m  15m S    3  4.2   6:45.99 Xorg               
16595 abhiroop  20   0 88060  12m 7444 S    3  0.6   1:29.46 python             
19792 abhiroop  20   0 94300  23m  12m S    2  1.1   0:00.58 gnome-terminal     
 6393 abhiroop  20   0 38120  18m 9.9m S    1  0.9   0:37.11 python             
 6800 abhiroop  20   0  193m  71m  23m S    1  3.5   1:48.38 xulrunner-bin      
19813 abhiroop  20   0  2308 1140  856 R    1  0.1   0:00.06 top                
 6672 abhiroop  20   0  142m  46m  23m S    0  2.3   1:05.19 pidgin             
    1 root      20   0  2844 1688  544 S    0  0.1   0:02.26 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.96 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.26 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1      

```

How do I use conky?

---

### Post by Het Irv on 2008-07-29
I am not sure you need conky right now, thats more of a desktop customization program than a diagnostic,  are you running amarok on your laptop when you leave it, if so the hard drive is probably still spinning because it is accessing your songs.

---

### Post by JoneYee on 2008-07-29
> **Het Irv said:**
> I am not sure you need conky right now, thats more of a desktop customization program than a diagnostic,  are you running amarok on your laptop when you leave it, if so the hard drive is probably still spinning because it is accessing your songs.

That was my first thought as well.

The list provides applications that are running, so I would shut down applications (not system processes) sequentially to see which one stops drive access.

---

### Post by tjwoosta on 2008-07-29
to use conky press alt-f2 and type conky


but there is a set of hardisk monitoring tools (to monitor the usage and wear on your harddrive)

its called smartmontools but i actuall have never used it so i cant really begin to describe what to do

here is the official ubuntu help documentation
[https://help.ubuntu.com/community/Smartmontools]("https://help.ubuntu.com/community/Smartmontools")

---

### Post by abhiroopb on 2008-07-29
Thanks for the responses. Well amarok is running (I use sqlite) but no songs are playing, I turned it on but never turned on any music.

Any other thoughts? I mean it is a bit of a pain to try every app one at a time but if its the only way.

Just that the way I use it now and the way I used it when I had my old HD is practically the same. Well almost identical. So if it stopped then shouldn't it stop now?

Does it have anything to do with the fact that this is I believe SATA and that (I don't think) was not?

---

### Post by abhiroopb on 2008-07-29
From the site I ran the smartmontools command and got this:

```

abhiroop@vanimo:~$ sudo smartctl -a -d ata /dev/sda

smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200BEVT-22ZCT0
Serial Number:    WD-WXE608KT0538
Firmware Version: 11.01A11
User Capacity:    320,072,933,376 bytes
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Tue Jul 29 22:06:25 2008 SGT
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
data collection: 		 (10800) seconds.
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
recommended polling time: 	 ( 127) minutes.
Conveyance self-test routine
recommended polling time: 	 (   5) minutes.
SCT capabilities: 	       (0x303f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   189   184   021    Pre-fail  Always       -       1541
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       34
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002e   100   253   000    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       80
 10 Spin_Retry_Count        0x0033   100   253   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   253   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       28
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       11
193 Load_Cycle_Count        0x0032   200   200   000    Old_age   Always       -       1522
194 Temperature_Celsius     0x0022   101   091   000    Old_age   Always       -       46
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Aborted by host               90%         0         -

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

No idea what it means!

---

### Post by JoneYee on 2008-07-29
> **abhiroopb said:**
> Does it have anything to do with the fact that this is I believe SATA and that (I don't think) was not?

From a HW perspective I doubt it.  I run my primary client machine on a HP DV 1331se which has a SATA drive in it.

SATA spins at 7.2k RPMs max, and I would seriously doubt that the drive type is the problem.

---

### Post by abhiroopb on 2008-07-29
Well didn't think so.

I read that hdparm doesn't work with SATA, and that sdparm does. I remember both of those used to run in the backgroun but I never fiddled with it as such.

Any other thoughts?

---

### Post by Het Irv on 2008-07-29
I am gonna run it on mine and compare the two, I don't know if that middle section is an error log or not.

---

### Post by JoneYee on 2008-07-29
Instructions for running a HDD testo n your machine:

[quote="hp support"]	 Content starts here

Use the steps below to test the hard drive in a Notebook PC using the HP Hard Drive Self Test.

   1. Plug the AC adapter into the Notebook PC.
   2. Press and hold the Power button for 5 seconds to turn off the PC.
   3. Press and hold the F10 key. Then press the Power button to turn on the PC releasing the F10 key after text is displayed on the screen of the PC.
   4. After the BIOS Setup Utility is displayed, use the Right Arrow key to select the Tools menu.
   5. Select Hard Drive Self Test .
   6. Press the Enter key to start the test.[/quote]

source: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00439024&lc=en&cc=us&dlc=en&product=3223544&rule=2920&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00439024&lc=en&cc=us&dlc=en&product=3223544&rule=2920&lang=en)

That will at least help you determine HW/SW (config/app)

Drive Self Tests are generally about 90% accurate.

---

### Post by Het Irv on 2008-07-29
```
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   062    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   253   100   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   100   100   000    Old_age   Always       -       940
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   098   098   000    Old_age   Always       -       999
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       532
191 G-Sense_Error_Rate      0x000a   099   095   000    Old_age   Always       -       65538
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       21
193 Load_Cycle_Count        0x0012   085   085   000    Old_age   Always       -       156764
194 Temperature_Celsius     0x0002   144   100   000    Old_age   Always       -       38 (Lifetime Min/Max 5/45)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   253   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

```

Dunno what it means, but my Hard drive doesn't spin constantly, and it is SATA.

---

### Post by JoneYee on 2008-07-29
Hate double posting, but i checked both HP and WD's websites and you have the most current firmware for Scorpio Blue 2.5 Notebook drives. 

I work storage and RAID for a living, so I am naturally looking at the HW side to make sure bases are covered.

---

### Post by abhiroopb on 2008-07-29
Thanks for all the effort...

Am running the test... Will do it overnight as it appears it will take time.

Will get back to everyone...

Also what should I look out for in the test? I.e. I know the drive works (and ubuntu succesfully ran its check on startup as well).

---

### Post by JoneYee on 2008-07-29
[http://www.t13.org/Documents/UploadedDocuments/docs2005/e05148r0-ACS-SMARTAttributesAnnex.pdf](http://www.t13.org/Documents/UploadedDocuments/docs2005/e05148r0-ACS-SMARTAttributesAnnex.pdf)

Thats a good doc for understanding what some of the output of smartmontools means.

Seeing as how none of the flags start with 1x, there are no pre-fail notification (only advisories) coming from smartmon.

I think that info brings us full circle to there being an app causing the spinup.

---

### Post by JoneYee on 2008-07-29
> **abhiroopb said:**
> Thanks for all the effort...

Am running the test... Will do it overnight as it appears it will take time.

Will get back to everyone...

Also what should I look out for in the test? I.e. I know the drive works (and ubuntu succesfully ran its check on startup as well).

I would be looking for two things:

1. Any indication of Drive Self Test (DST) Failure
2. Any SMART error messaging including key-code-qualifiers provided by the diagnostic.

Still, I don't think its likely to be the HDD based on the smartmontools output.

---

### Post by abhiroopb on 2008-07-29
Right thanks...

Also I'm going to reboot (after the test) and keep all apps off and see what happens.

Thanks for the help.

---

### Post by abhiroopb on 2008-07-29
While restarting I noticed a command called enable SATA support (in the bios). It was set to "disabled" I "enabled" and now I can hear that the HD has stopped spinning.

HURRAY for human ingenuity :D...

Will keep updates here. But the HD has ALREADY stopped spinning (even while writing this post!)

---

### Post by Het Irv on 2008-07-29
This is one to mark as solved.  That is such a random fix.  Good catch abhiroopb!

---

### Post by abhiroopb on 2008-07-29
Ah slight problem...Booting into XP, BSOD...O dear!

I believe this is a driver issue though, so separate thing will look into later.

Marked as solved

Thanks

---

### Post by tigersan on 2008-07-29
I ran into this scenario after installing MythTV.  Suddenly, my hard drive was working all the time even though I was not using the programme.  So, I just uninstalled it and the problem went away.

---

### Post by abhiroopb on 2008-07-29
The difference is you had a specific app which obviously seemed to be causing problems

---

