---
title: "Google Chrome fails to start after crash"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by zinkwazi on 2014-07-29
Ubuntu 12.04 - Chrome was running beautifully, suddenly crashed. Did not start again from launcher nor dash. The icon only pulses and nothing happens. Removed hidden .config google-chrome files. Re-installed from software centre. Removed and re-installed. Downloaded google-chrome-stable-current-i386.deb from Google website and installed. All installations appear fine. Did a 'complete remove' in Synaptic Package manager and re-installed. Nothing works.

---

### Post by uRock on 2014-07-29
To help others help you, could you open a terminal, then type **google-chrome**, then copy and paste any information given in the terminal here?

---

### Post by tgalati4 on 2014-07-29
Perhaps your drive is having problems.

What are the SMART parameters for the drive:

Open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

If you can't install and run these tools, then I would be worried.  Back up any files to a USB stick as fast as you can.

---

### Post by zinkwazi on 2014-07-30
terminal response  = 'Aborted (core dumped)'

---

### Post by zinkwazi on 2014-07-30
> **tgalati4 said:**
> Perhaps your drive is having problems.

What are the SMART parameters for the drive:

Open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

If you can't install and run these tools, then I would be worried.  Back up any files to a USB stick as fast as you can.

The terminal response to your first command =
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-ubuntuoneui-3.0 liblualib50 libubuntuoneui-3.0-1 kdelibs5-data
  libqt3-mt liblua50 openjdk-7-jre-lib
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  heirloom-mailx
Suggested packages:
  exim4 mail-transport-agent gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  heirloom-mailx smartmontools
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 694 kB of archives.
After this operation, 1 864 kB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by tgalati4 on 2014-07-30
Respond "yes" and finish the installation then run the second command posted above.

---

### Post by zinkwazi on 2014-07-30
> **tgalati4 said:**
> Respond "yes" and finish the installation then run the second command posted above.

Thanks! This is the result:

```
Get:1 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise/universe heirloom-mailx i386 12.5-1build1 [238 kB]
Get:2 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) precise/main smartmontools i386 5.41+svn3365-1 [455 kB]
Fetched 694 kB in 5s (119 kB/s)         
Selecting previously unselected package heirloom-mailx.
(Reading database ... 172805 files and directories currently installed.)
Unpacking heirloom-mailx (from .../heirloom-mailx_12.5-1build1_i386.deb) ...
Selecting previously unselected package smartmontools.
Unpacking smartmontools (from .../smartmontools_5.41+svn3365-1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up heirloom-mailx (12.5-1build1) ...
update-alternatives: using /usr/bin/heirloom-mailx to provide /usr/bin/mailx (mailx) in auto mode.
Setting up smartmontools (5.41+svn3365-1) ...
klaus@klaus-laptop:~$ sudo smartctl -a /dev/sda
[sudo] password for klaus: 
smartctl 5.41 2011-06-09 r3365 [i686-linux-2.6.32-51-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD3200BEVS-16VAT0
Serial Number:    WD-WXH1E30ASD62
LU WWN Device Id: 5 0014ee 204aa87d3
Firmware Version: 11.01A11
User Capacity:    320 072 933 376 bytes [320 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Wed Jul 30 16:51:59 2014 SAST
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         ( 9600) seconds.
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
recommended polling time:      (   2) minutes.
Extended self-test routine
recommended polling time:      ( 113) minutes.
Conveyance self-test routine
recommended polling time:      (   5) minutes.
SCT capabilities:            (0x303f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0027   184   183   021    Pre-fail  Always       -       1766
  4 Start_Stop_Count        0x0032   098   098   000    Old_age   Always       -       2771
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   253   051    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   093   093   000    Old_age   Always       -       5341
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0032   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   098   098   000    Old_age   Always       -       2764
192 Power-Off_Retract_Count 0x0032   200   200   000    Old_age   Always       -       120
193 Load_Cycle_Count        0x0032   199   199   000    Old_age   Always       -       3545
194 Temperature_Celsius     0x0022   106   097   000    Old_age   Always       -       41
196 Reallocated_Event_Count 0x0032   200   200   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   200   200   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   253   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0009   100   253   051    Pre-fail  Offline      -       0

SMART Error Log Version: 1
No Errors Logged

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

### Post by tgalati4 on 2014-07-30
So you have 5300 hours on your drive and it seems OK.  When you have some down time, run a short and long test--at different times.  The long test could take several minutes.

```
sudo smartctl -t short /dev/sda
sudo smartctl -t long /dev/sda
```

To view the results:

```
sudo smartctl -a /dev/sda
```

Back up your personal data regardless, because SMART doesn't catch everything that fails in a drive--like controller circuitry.

Install and run firefox instead of chrome.  For some reason chrome is damaged beyond repair.  I don't know if chrome has debug mode:

```
google-chrome --debug
```

See if you get any messages before the segmentation fault/core dump.

If you are running 64-bit Ubuntu, then you need 64-bit google-chrome.  The *i386.deb that you downloaded is for 32-bit machines.

```
uname -a
```

---

### Post by zinkwazi on 2014-07-31
Thanks for your advice & help. So chrome won't run anymore. I tried the #debug - but didn't show anything new. Am running 32bit not 64. Will run the tests.

---

### Post by tgalati4 on 2014-07-31
Try installing a slightly older version of Chrome.  It's possible that the latest version breaks in 32-bit and you were the lucky one to find the bug.

---

### Post by Votlon on 2014-07-31
In case you didn't know there is a browser called Chromium which almost look exactly like chrome but is open source. Due to my past experiences with chrome on linux, I would say chromium is a little most stable than chrome;) plus it dosn't have all the fun tracking code built in.

---

