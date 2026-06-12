---
title: "black screen"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by joks on 2012-12-29
hello,
sometimes when i start ubuntu the screen stays black, the pc starts but not the the gui.
 i have no idea how i can find a solution.
please help

---

### Post by NikTh on 2012-12-29
Hi ,
probably a graphics card - or - driver problem. 

Give more info please , open a terminal (CTRL+ALT+T) and apply the commands below (one at time)
```
lspci -nnk | grep -iA2 vga
sudo lshw -C display
lsb_release -rcd ; uname -r
```_Please click on **"New Reply"** and put the results inside [CODE] tags to be easier to read._ [See here how]("http://i.stack.imgur.com/zADbK.png")

**ps:** You can do all above from a Live Session (CD/DVD/USB) if you cannot login at all.

Thanks

---

### Post by joks on 2012-12-29
```
joks@x230:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09)
	Subsystem: Lenovo Device [17aa:21fa]
	Kernel driver in use: i915
joks@x230:~$ sudo lshw -C display
[sudo] password for joks: 
  *-display               
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:5000(size=64)
joks@x230:~$ lsb_release -rcd ; uname -r
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal
3.5.0-21-generic


```

---

### Post by NikTh on 2012-12-29
Hi ,
also these results please
```
free -m 
lscpu
``` 

Thanks

---

### Post by joks on 2012-12-29
```
joks@x230:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          7792       4767       3024          0         50       3703
-/+ buffers/cache:       1013       6778
Swap:         7885          0       7885
joks@x230:~$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                4
On-line CPU(s) list:   0-3
Thread(s) per core:    2
Core(s) per socket:    2
Socket(s):             1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 58
Stepping:              9
CPU MHz:               1200.000
BogoMIPS:              5188.72
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              3072K
```

---

### Post by NikTh on 2012-12-29
Hi ,

your system seems ideal. No graphics problem (Correct driver is loaded) .. strong cpu and a lot of physical memory.. what would it be ? 

Hmmm.. 

An HDD error ?
Lets preclude this possibility.. 
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
``` 

Also , do you remember if you installed something recently ? 
Lets take a look to you sources.list also 
```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \; 
```

And lets examine some other logs. 
```
cat /var/log/Xorg.0.log | grep -e WW -e EE
cat .xsession-errors
```

Thanks

---

### Post by joks on 2012-12-30
sry its a little long:
```
joks@x230:~$ sudo apt-get install smartmontools --no-install-recommends
[sudo] password for joks: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  smartmontools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 459 kB of archives.
After this operation, 1,235 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main smartmontools i386 5.43-0ubuntu1 [459 kB]
Fetched 459 kB in 0s (548 kB/s)        
Selecting previously unselected package smartmontools.
(Reading database ... 193289 files and directories currently installed.)
Unpacking smartmontools (from .../smartmontools_5.43-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up smartmontools (5.43-0ubuntu1) ...
Processing triggers for ureadahead ...
joks@x230:~$ sudo smartctl -a /dev/sda
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.5.0-21-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Device Model:     Samsung SSD 840 Series
Serial Number:    S14LNEACB07704E
LU WWN Device Id: 5 002538 550081473
Firmware Version: DXT06B0Q
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4c
Local Time is:    Sun Dec 30 20:56:01 2012 CET
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
data collection: 		(53956) seconds.
Offline data collection
capabilities: 			 (0x53) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					Self-test supported.
					No Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 (  70) minutes.
SCT capabilities: 	       (0x003d)	SCT Status supported.
					SCT Error Recovery Control supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 1
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  9 Power_On_Hours          0x0032   099   099   000    Old_age   Always       -       15
 12 Power_Cycle_Count       0x0032   099   099   000    Old_age   Always       -       55
177 Wear_Leveling_Count     0x0013   100   100   000    Pre-fail  Always       -       0
179 Used_Rsvd_Blk_Cnt_Tot   0x0013   100   100   010    Pre-fail  Always       -       0
181 Program_Fail_Cnt_Total  0x0032   100   100   010    Old_age   Always       -       0
182 Erase_Fail_Count_Total  0x0032   100   100   010    Old_age   Always       -       0
183 Runtime_Bad_Block       0x0013   100   100   010    Pre-fail  Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0032   076   060   000    Old_age   Always       -       24
195 Hardware_ECC_Recovered  0x001a   200   200   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x003e   099   099   000    Old_age   Always       -       247
235 Unknown_Attribute       0x0012   099   099   000    Old_age   Always       -       14
241 Total_LBAs_Written      0x0032   099   099   000    Old_age   Always       -       73022086

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
  255        0    65535  Read_scanning was never started
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

joks@x230:~$ find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list.d/jd-team-jdownloader-quantal.list

     1	deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) quantal main
     2	deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) quantal main

/etc/apt/sources.list.d/dropbox.list

     1	deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) precise main

/etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_defensezone_ubuntu.list

     1	deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/defensezone/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/defensezone/ubuntu) quantal main #Added by software-center; credentials stored in /etc/apt/auth.conf

/etc/apt/sources.list.d/gwibber-daily-ppa-quantal.list

     1	# deb [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) quantal main
     2	# deb-src [http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu](http://ppa.launchpad.net/gwibber-daily/ppa/ubuntu) quantal main

/etc/apt/sources.list.d/google-chrome.list

     1	### THIS FILE IS AUTOMATICALLY CONFIGURED ###
     2	# You may comment out this entry, but any other modifications may be lost.
     3	deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

/etc/apt/sources.list

     1	# deb cdrom:[Ubuntu 12.10 _Quantal Quetzal_ - Release i386 (20121017.2)]/ quantal main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted
     6	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted
    11	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal universe
    17	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal universe
    18	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates universe
    19	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal multiverse
    27	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal multiverse
    28	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates multiverse
    29	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse
    37	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-backports main restricted universe multiverse
    38	
    39	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted
    40	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security main restricted
    41	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security universe
    42	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security universe
    43	deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security multiverse
    44	deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) quantal-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    51	deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) quantal partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) quantal main
joks@x230:~$ cat /var/log/Xorg.0.log | grep -e WW -e EE
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.924] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.924] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.924] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.924] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.924] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.924] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     3.926] Initializing built-in extension MIT-SCREEN-SAVER
[     3.928] (WW) Falling back to old probe method for vesa
[     3.928] (WW) Falling back to old probe method for modesetting
[     3.928] (WW) Falling back to old probe method for fbdev
joks@x230:~$ cat .xsession-errors
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
compiz (core) - Info: Unity is fully supported by your hardware.
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
I/O warning : failed to load external entity "/home/joks/.compiz/session/10f0ebaa8afd2ac093135688492812342900000013450032"
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
** Message: applet now removed from the notification area
compiz (core) - Info: Starting plugin: unityshell
** Message: using fallback from indicator to GtkStatusIcon
** Message: moving back from GtkStatusIcon to indicator

** (zeitgeist-datahub:2350): WARNING **: zeitgeist-datahub.vala:227: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
[86:86:1230/173337:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173341:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173342:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173342:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173342:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173342:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173342:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173343:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173343:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173344:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173651:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/173655:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/174711:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/174721:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[86:86:1230/174721:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
Agent unregistration failed: GDBus.Error:org.freedesktop.DBus.Error.UnknownObject: Method "UnregisterAgent" with signature "o" on interface "org.bluez.Adapter" doesn't exist
 'g-io-error-quark'
[86:86:1230/205031:ERROR:render_widget_fullscreen_pepper.cc(275)] Not implemented reached in virtual void<unnamed>::PepperWidget::setFocus(bool)
[1811:1811:1230/205124:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[1811:1811:1230/205140:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
[1811:1811:1230/205210:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[1811:1811:1230/205250:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[1811:1811:1230/205403:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[1811:1811:1230/205512:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[1811:1811:1230/205522:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
[1811:1811:1230/205538:ERROR:layout.cc(160)] Not implemented reached in ui::ScaleFactor ui::GetScaleFactorForNativeView(GtkWidget*)
```

---

### Post by NikTh on 2012-12-31
Well ,  you know what ? I have not further ideas. You system (As I said before) seems ideal and I guess is brand new. You hard disk is brand new (15 Power_On_Hours).. 

Xorg.0.log seems clean to me . 

.xsession-errors have some Errors , but I don't think you will get black screen from these errors. 

The errors ```
ERROR:layout.cc(160)
ERROR:render_widget_fullscreen_pepper.cc(275)
``` 
are very likely from Chromium or Chrome (you have installed) , but I don't think that affects the desktop environment (black screen result). 

**This behavior (black screen) appears often ? **

Thanks

---

### Post by squakie on 2012-12-31
Is this a stand alone, dual boot, or wubi (installed within Windows) installation?

Also another thought:  since it is using the i915 driver, try putting i915.modeset=0 in the boot line.  If that doesn't work, change it to i915.modeset=1.

---

### Post by joks on 2013-01-01
at the moment stand alone, later i want to install windows...
how do chnage the modset?
now the black screen didnt appear 5 times...
another question, does ubuntu control the cpu speed on its own or should i do anything?

---

### Post by ivicks on 2013-01-01
The CPU speed should be handled by the bios then automatically adjusted by the OS. Also your video issue might be a "video out of range" problem, you could try changing the video setting at the boot screen to see if that help. But as you stated the issue might of resolved itself.

---

### Post by squakie on 2013-01-02
I haven't done it for a while, but if I remember correctly, you need to keep pushing F6 when the hardware is booting - if Ubuntu starts to boot you've gone to far.  From there you can follow the screen for how to edit the boot line.

---

