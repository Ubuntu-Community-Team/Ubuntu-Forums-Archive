---
title: "Desktop freeze"
date: 2012-10-01
forum: New to Ubuntu
---

### Post by KaizerLinux on 2012-10-01
Ubuntu 12.04 64-bit
ATI Radeon HD 5700

Hey guys. The past few days my desktop has been freezing up. First it happened while watching videos on youtube. Then it happened when installing Humble Indie Bundle games from the Software Center (not sure if it happens with software other than games), and it happened consistently EVERY time I installed something. Now it just happened while playing Rochard.

The desktop freezes up, I can sometime move the mouse but clicking it does nothing. Sometimes keyboard input works for a little while, but only to get to command line. The video continues playing with sound and everything, the game kept going, and the software center kept installing the software even if the screen was frozen. I can also ssh into the computer without any problems. 

I've tried to restart lightdm after ssh-ing into it, this does have an effect (IE the screen goes black, than the desktop returns), but it still won't accept any keyboard or mouse input, and the desktop is still frozen (you can see the Unity toolbar in the left having frozen while hiding.) The only thing that works is either the reboot command after ssh-ing in, or a hard reboot.

Any help would be appreciated, because this is getting rather annoying. Never had any problems like this before, and it seems to just have come by itself O_o Could have something to do with an update, not sure.

---

### Post by NikTh on 2012-10-01
Hi , 
please open a terminal and give the results of bellow commands. 

```
cat /var/log/Xorg.0.log | grep -e WW -e EE
``````
dpkg -l | grep -i fglrx
``````
lspci -nnk | grep -iA2 vga
``````
cat /etc/lsb-release && uname -r
``````
sudo parted -l
``````
sudo apt-get install  smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
```
_Put the results between the brackets so can be readable._ **[noparse]```
Here
```[/noparse]**

Thanks

---

### Post by KaizerLinux on 2012-10-01
That was quick!

```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.165] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.165] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.165] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.165] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.165] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.191] (II) Loading extension MIT-SCREEN-SAVER
[    28.206] (WW) Falling back to old probe method for fglrx
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[    28.212] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[    28.388] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    28.836] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.

```

```
michael@Desktop:~$ dpkg -l | grep -i fglrx
ii  fglrx                                       2:8.960-0ubuntu1.1                      Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                              2:8.960-0ubuntu1.1                      Catalyst Control Center for the AMD graphics accelerators
rc  fglrx-updates                               2:8.960-0ubuntu1.1                      Video driver for the AMD graphics accelerators

```

```
michael@Desktop:~$ dpkg -l | grep -i fglrx
ii  fglrx                                       2:8.960-0ubuntu1.1                      Video driver for the AMD graphics accelerators
ii  fglrx-amdcccle                              2:8.960-0ubuntu1.1                      Catalyst Control Center for the AMD graphics accelerators
rc  fglrx-updates                               2:8.960-0ubuntu1.1                      Video driver for the AMD graphics accelerators
michael@Desktop:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Juniper [Radeon HD 5700 Series] [1002:68b8]
	Subsystem: PC Partner Limited Device [174b:e147]
	Kernel driver in use: fglrx_pci

```

```
michael@Desktop:~$ cat /etc/lsb-release && uname -r
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
3.2.0-31-generic

```

```
michael@Desktop:~$ sudo parted -l
[sudo] password for michael: 
Model: ATA SAMSUNG HD154UI (scsi)
Disk /dev/sda: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs            boot
 2      106MB   1001GB  1001GB  primary   ntfs
 3      1001GB  1500GB  499GB   extended
 5      1001GB  1496GB  495GB   logical   ext4
 6      1496GB  1500GB  4293MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label 
```

```
michael@Desktop:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-31-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Model Family:     SAMSUNG SpinPoint F2 EG
Device Model:     SAMSUNG HD154UI
Serial Number:    S1XWJ1LZ201865
LU WWN Device Id: 5 0024e9 002fc4bbc
Firmware Version: 1AG01118
User Capacity:    1,500,301,910,016 bytes [1.50 TB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Mon Oct  1 14:46:15 2012 CEST
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
data collection: 		(19493) seconds.
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
recommended polling time: 	 ( 255) minutes.
Conveyance self-test routine
recommended polling time: 	 (  34) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   085   085   011    Pre-fail  Always       -       5530
  4 Start_Stop_Count        0x0032   099   099   000    Old_age   Always       -       809
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       6871
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       806
 13 Read_Soft_Error_Rate    0x000e   100   100   000    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   000    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   074   063   000    Old_age   Always       -       26 (Min/Max 24/26)
194 Temperature_Celsius     0x0022   071   062   000    Old_age   Always       -       29 (Min/Max 24/29)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       1062025
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   100   000    Old_age   Always       -       5
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 5
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

Error 5 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 00 00 00 e0 00      08:40:19.460  READ DMA
  ef 03 42 00 00 00 a0 00      08:40:19.450  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      08:40:19.440  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      08:40:19.270  NOP [Abort queued commands]
  00 00 01 01 00 00 a0 ff      08:40:14.300  NOP [Abort queued commands]

Error 4 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 00 00 00 e0 00      00:00:12.130  READ DMA
  00 00 01 01 00 00 a0 00      00:00:11.900  NOP [Abort queued commands]

Error 3 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 00 00 00 e0 00      00:00:08.850  READ DMA
  ef 03 42 00 00 00 a0 00      00:00:08.850  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      00:00:08.840  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      00:00:08.610  NOP [Abort queued commands]

Error 2 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 00 00 00 e0 00      16:58:28.790  READ DMA
  ef 03 42 00 00 00 a0 00      16:58:28.780  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00      16:58:28.770  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00      16:58:28.600  NOP [Abort queued commands]
  00 00 01 01 00 00 a0 ff      16:58:23.640  NOP [Abort queued commands]

Error 1 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  84 51 00 00 00 00 e0  Error: ICRC, ABRT at LBA = 0x00000000 = 0

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 00 01 00 00 00 e0 00   1d+15:43:37.550  READ DMA
  ef 03 42 00 00 00 a0 00   1d+15:43:37.540  SET FEATURES [Set transfer mode]
  ec 00 00 00 00 00 a0 00   1d+15:43:37.530  IDENTIFY DEVICE
  00 00 01 01 00 00 a0 00   1d+15:43:37.360  NOP [Abort queued commands]
  00 00 01 01 00 00 a0 ff   1d+15:43:32.390  NOP [Abort queued commands]

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

### Post by NikTh on 2012-10-01
Hi , 

you card seems to supported from open source radeon driver : [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) , take a look at the list. 

If you want to try to remove completely the fglrx 

```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
``````
sudo apt-get install --reinstall libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
``````
sudo dpkg-reconfigure xserver-xorg xserver-xorg-core xserver-xorg-video-ati
```and reboot your system. 

Thanks

---

### Post by KaizerLinux on 2012-10-02
Got it installed I think, though the "Details" menu in "System Settings" show unknown device and driver. Had a quick try of Torchlight, that seemed to work better now than it did before. Going to give it a day or two of use before I close this, to see of there are any more freezes. Thanks so far!

---

### Post by KaizerLinux on 2012-10-02
Hasn't frozen yet, but now Rochard (a Unity-engine game) is pretty much unplayable due to lag. The Unity (desktop) toolbar on the left also seems like it's lagging when unhiding.

---

### Post by NikTh on 2012-10-02
> **KaizerLinux said:**
> Hasn't frozen yet, but now Rochard (a Unity-engine game) is pretty much unplayable due to lag. The Unity (desktop) toolbar on the left also seems like it's lagging when unhiding.

Give the result of this command 

```
sudo cat /sys/class/drm/card0/device/power_profile
```

OR 

```
ls /sys/class/drm/
```
Thanks

---

### Post by KaizerLinux on 2012-10-04
Here's both:

```
michael@Desktop:~$ sudo cat /sys/class/drm/card0/device/power_profile
[sudo] password for michael: 
default
michael@Desktop:~$ ls /sys/class/drm/
card0       card0-DVI-I-1  card0-HDMI-A-1  ttm
card0-DP-1  card0-DVI-I-2  controlD64      version
```

---

### Post by KaizerLinux on 2012-10-04
And it just froze again. It had been standing idle for a while, and the monitor had shut down. When I moved the mouse to get the monitor back on, it took longer than usual, and when it came on I could only move the cursor. No other input worked.

---

### Post by NikTh on 2012-10-04
Then maybe is a hardware problem ? 

Can you check the RAMs ? Grub menu > memtest. Leave it for 1 hour and see for errors. 

Also you can try this command 

```
echo "low" | sudo tee -a /sys/class/drm/card0/device/power_profile
```Above command is for ONE session Only. When you reboot is gone. Test if system frozen with this command enabled.

OR 

you can install again the fglrx driver. 
```
sudo apt-get install fglrx fglrx-amdcccle
```Reboot and check. 

Thanks

---

### Post by KaizerLinux on 2012-10-04
> **NikTh said:**
> Then maybe is a hardware problem ? 

Can you check the RAMs ? Grub menu > memtest. Leave it for 1 hour and see for errors. 

Also you can try this command 

```
echo "low" | sudo tee -a /sys/class/drm/card0/device/power_profile
```Above command is for ONE session Only. When you reboot is gone. Test if system frozen with this command enabled.

OR 

you can install again the fglrx driver. 
```
sudo apt-get install fglrx fglrx-amdcccle
```Reboot and check. 

Thanks

This is the stats when running on low:
```
michael@Desktop:~$ sudo sh -c "cat /sys/kernel/debug/dri/0/radeon_pm_info"
default engine clock: 850000 kHz
current engine clock: 156990 kHz
default memory clock: 1200000 kHz
current memory clock: 300000 kHz
voltage: 1000 mV
PCIE lanes: 2

```

I tried running it at "high", but that only gave me the same as "default", and didn't fix my low fps issue. Might be an issue with the Unity engine and the open driver? Since it worked well with the proprietary ones?

I'm thinking it's not hardware. I'm running a dual boot with Ubuntu 12.04 and Win7. This has never happened in Win7. And it only started happening recently in Ubuntu, which is why I'm puzzled. But I'll run a memtest anyway, just to rule it out.

Could it be a problem with X? Since it happened after the monitor had gone to standby? Or might that just be a coincidence? Where can I find the logfile for X?

---

### Post by NikTh on 2012-10-04
> **KaizerLinux said:**
>  Might be an issue with the Unity engine and the open driver? 
Maybe yes , maybe no. You can try Unity-2d session (ubuntu-2d from login screen) and test it there. The big difference is that 2d session uses metacity instead of compiz. 

> **KaizerLinux said:**
> I'm thinking it's not hardware. I'm running a dual boot with Ubuntu 12.04 and Win7. This has never happened in Win7. 
I accept that. 

> **KaizerLinux said:**
> Could it be a problem with X? Since it happened after the monitor had gone to standby? Or might that just be a coincidence? Where can I find the logfile for X?

The log files can be located in /var/log/ 

For X , ```
cat /var/log/Xorg.0.log
```> **KaizerLinux said:**
> Since it worked well with the proprietary ones? 
You can try to re-install proprietary drivers (I prefer with commands I gave in previous post) and see if fixed.

Thanks

---

### Post by KaizerLinux on 2012-10-04
Not sure if this tells you anything:

```
michael@Desktop:~$ cat /var/log/Xorg.0.log | grep -e WW -e WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.399] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.399] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.399] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.399] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.399] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.443] (WW) Warning, couldn't open module fglrx
[    28.443] (WW) Warning, couldn't open module fglrx
[    28.446] (WW) Falling back to old probe method for vesa
[    28.446] (WW) Falling back to old probe method for fbdev
[    28.805] (WW) RADEON(0): Option "Monitor-DFP2" is not used
[    28.833] (WW) evdev: Logitech USB Receiver: ignoring absolute axes.
```

But this log "resets" each time I reboot it seems? Would it help if next time I get e freezeup, I ssh into the computer and run that command?

---

### Post by NikTh on 2012-10-04
> **KaizerLinux said:**
> But this log "resets" each time I reboot it seems? Yes. You can find and see older logs of X in /var/log eg: Xorg.0.log.old 
> **KaizerLinux said:**
> Would it help if next time I get e freezeup, I ssh into the computer and run that command?> **KaizerLinux said:**
> ```
michael@Desktop:~$ cat /var/log/Xorg.0.log | grep -e WW -e WW
```

Better is ```
cat /var/log/Xorg.0.log
``` without the restriction of grep . So we can see Full log file. 

Thanks

---

