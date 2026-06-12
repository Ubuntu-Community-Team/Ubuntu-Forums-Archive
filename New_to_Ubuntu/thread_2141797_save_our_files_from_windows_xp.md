---
title: "save our files from windows xp"
date: 2013-05-03
forum: New to Ubuntu
---

### Post by momodiouf on 2013-05-03
Hi Ubuntu community,
We have a emachine em250 netbook but it happened that the windows XP OS is dammaged it cannot start up. it always ask to start it using safe mode... if you use other modes such as start windows using a prompt it says erro 32 system missing or corrupt....

As a consequence I found out about Ubuntu, I created a bootable usb drive but Ubuntu cannot still open my internal hard drive where all my files are. In all attempts it says this:

```

Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to calculate free MFT records: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

```


Please can you guys help us save our files?
Thanks

---

### Post by tripp98 on 2013-05-03
It wasnt shutdown clean.  if you can start it in XP safe mode.  shut it down clean.  then boot from usb.
then see if you can mount it.

if not boot into safe mode open my computer. right click on your c drive.
go to properties.
on tools tab select scan disk
check both options.
it will ask to restart.  let it restart and do a scan disk.
once it has finished.  then try booting from usb(ubuntu)
then see if you can mount drive.

---

### Post by momodiouf on 2013-05-03
Thank you so much for replying, let me try that then I let you know.

---

### Post by momodiouf on 2013-05-03
> **tripp98 said:**
> It wasnt shutdown clean.  if you can start it in XP safe mode.  shut it down clean.  then boot from usb.
then see if you can mount it.

if not boot into safe mode open my computer. right click on your c drive.
go to properties.
on tools tab select scan disk
check both options.
it will ask to restart.  let it restart and do a scan disk.
once it has finished.  then try booting from usb(ubuntu)
then see if you can mount drive.

The only thing even in safe mode it sends me right on an error page (partition..., 32 system missing...something like that). I tried all that you said. It won't let me access to the hard drive. Do you have any other suggestions?

---

### Post by momodiouf on 2013-05-03
Hi Ubuntu community,
We have a emachine em250 netbook but it happened that the windows XP OS  is dammaged it cannot start up. it always ask to start it using safe  mode... if you use other modes such as start windows using a prompt it  says erro 32 system missing or corrupt....

As a consequence I found out about Ubuntu, I created a bootable usb  drive but Ubuntu cannot still open my internal hard drive where all my  files are. In all attempts it says this:

     Code:
     
Error mounting: mount exited with exit code 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to calculate free MFT records: Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details.[/QUOTE]

---

### Post by matt_symes on 2013-05-03
Hi

Boot into Ubuntu LiveCD/USB and post the output of

```
sudo fdisk -l
```

That's a small L.

I would also check the SMART status of the drive. From the LiveCD/USB, connect to the internet and, from the terminal, type

```
sudo apt-get install smartmontools
```

After it has installed type

```
sudo smartctl -t long /dev/sda
```

This assume your main hard drive is sda. 

Let it run, it will tell you when it's going to finish (expect it to take a couple of hours).

After it has finished, type

```
sudo smartctl -a /dev/sda
```

Post the results back here by copying and pasting from the terminal (highlight text->right click->copy).

That may give us some idea of what the hard drives thinks about its state.

If that looks all right then i wuld start looking at the filing system on the drive itself.

Kind regards

---

### Post by momodiouf on 2013-05-03
> **matt_symes said:**
> Hi

Boot into Ubuntu LiveCD/USB and post the output of

```
sudo fdisk -l
```

That's a small L.

I would also check the SMART status of the drive. From the LiveCD/USB, connect to the internet and, from the terminal, type

```
sudo apt-get install smartmontools
```

After it has installed type





 
```
sudo smartctl -t long /dev/sda
```

This assume your main hard drive is sda. 

Let it run, it will tell you when it's going to finish (expect it to take a couple of hours).

After it has finished, type

```
sudo smartctl -a /dev/sda
```

Post the results back here by copying and pasting from the terminal (highlight text->right click->copy).

That may give us some idea of what the hard drives thinks about its state.

If that looks all right then i wuld start looking at the filing system on the drive itself.

Kind regards



Hi, thank you so much for helping me out.
I did what you suggested but this is what I have.

Postfix Configuration &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;   
  &#9474;                                                                          &#9474;   
  &#9474;                                                                             
  &#9474;  No configuration:                                                          
  &#9474;   Should be chosen to leave the current configuration unchanged.            
  &#9474;  Internet site:                                                             
  &#9474;   Mail is sent and received directly using SMTP.                            
  &#9474;  Internet with smarthost:                                                   
  &#9474;   Mail is received directly using SMTP or by running a utility such         
  &#9474;   as fetchmail. Outgoing mail is sent using a smarthost.                    
  &#9474;  Satellite system:                                                          
  &#9474;   All mail is sent to another machine, called a 'smarthost', for            
  &#9474; delivery.                                                                   
  &#9474;  Local only:                                                                
  &#9474;   The only delivered mail is the mail for local users. There is no          
  &#9474; network.                                                                    
  &#9474;                                                                             
  &#9474;                                 <Ok>


and then this 

ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
sudo: smartctl: command not found
ubuntu@ubuntu:~$

---

### Post by matt_symes on 2013-05-03
Hi

It looks like you did not install it correctly. 

What option did you select on the e-mail selection screen ? Did you cancel it using ctrl + c ?

You need to use the TAB key to navigate that screen. Navigate to the <OK> button and hit ENTER.

Select the **No configuration:** option on that screen.

It's in the smartmontools package and installs to
```

matthew-S206:/lib/plymouth/themes % which smartctl
/usr/sbin/smartctl
matthew-S206:/lib/plymouth/themes %
```

Try to install it again.

Kind regards

---

### Post by momodiouf on 2013-05-03
> **matt_symes said:**
> Hi

It looks like you did not install it correctly. 

What option did you select on the e-mail selection screen ? Did you cancel it using ctrl + c ?

You need to use the TAB key to navigate that screen. Navigate to the <OK> button and hit ENTER.

Select the **No configuration:** option on that screen.

It's in the smartmontools package and installs to
```

matthew-S206:/lib/plymouth/themes % which smartctl
/usr/sbin/smartctl
matthew-S206:/lib/plymouth/themes %
```



Hi thank you once again this is what I have so far, apparently it did not install right!

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5fc1e980

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    17214366     8607152   12  Compaq diagnostics
/dev/sda2   *    20981760   312578047   145798144    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders, total 7741440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7741439     3866624    b  W95 FAT32

```
```

ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common postfix-cdb gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,789 kB of archives.
After this operation, 4,662 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package postfix.
(Reading database ... 147580 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.9.1-4_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/postfix_2.9.1-4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Selecting previously unselected package bsd-mailx.
Unpacking bsd-mailx (from .../bsd-mailx_8.1.2-0.20111106cvs-1_i386.deb) ...
Selecting previously unselected package smartmontools.
Unpacking smartmontools (from .../smartmontools_5.41+svn3365-1_i386.deb) ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.9.1-4_i386.deb
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ sudo: smartctl: command not found
No command 'sudo:' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudo:: command not found
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$ sudo: smartctl: command not found
No command 'sudo:' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudo:: command not found
ubuntu@ubuntu:~$ ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$: command not found
ubuntu@ubuntu:~$
```

---

### Post by matt_symes on 2013-05-03
Hi

> /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable

Reboot into the LiveCD/USB again and try to install it again.

Kind regards

---

### Post by momodiouf on 2013-05-03
> **matt_symes said:**
> Hi



Reboot into the LiveCD/USB again and try to install it again.

Kind regards


Thank you! 
I did as you said, now i am waiting  for the test to complete and then I let you know.
thank you so much!

---

### Post by momodiouf on 2013-05-04
> **matt_symes said:**
> Hi



Reboot into the LiveCD/USB again and try to install it again.

Kind regards



Hi, this is what I have have now, I think an erro occuredduring the test.

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5fc1e980

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    17214366     8607152   12  Compaq diagnostics
/dev/sda2   *    20981760   312578047   145798144    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 3963 MB, 3963617280 bytes
128 heads, 63 sectors/track, 960 cylinders, total 7741440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8192     7741439     3866624    b  W95 FAT32
```

```

ubuntu@ubuntu:~$ sudo apt-get install smartmontools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bsd-mailx postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  dovecot-common postfix-cdb gsmartcontrol smart-notifier
Recommended packages:
  mailx mailutils
The following NEW packages will be installed:
  bsd-mailx postfix smartmontools
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,789 kB of archives.
After this operation, 4,662 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously unselected package postfix.
(Reading database ... 170007 files and directories currently installed.)
Unpacking postfix (from .../postfix_2.9.1-4_i386.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/postfix_2.9.1-4_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Selecting previously unselected package bsd-mailx.
Unpacking bsd-mailx (from .../bsd-mailx_8.1.2-0.20111106cvs-1_i386.deb) ...
Selecting previously unselected package smartmontools.
Unpacking smartmontools (from .../smartmontools_5.41+svn3365-1_i386.deb) ...
Processing triggers for man-db ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--unpack):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for ureadahead ...
Errors were encountered while processing:
 /var/cache/apt/archives/postfix_2.9.1-4_i386.deb
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ /usr/bin/dpkg
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
ubuntu@ubuntu:~$ more
Usage: more [options] file...

Options:
  -d        display help instead of ring bell
  -f        count logical, rather than screen lines
  -l        suppress pause after form feed
  -p        suppress scroll, clean screen and disblay text
  -c        suppress scroll, display text and clean line ends
  -u        suppress underlining
  -s        squeeze multiple blank lines into one
  -NUM      specify the number of lines per screenful
  +NUM      display file beginning from line number NUM
  +/STRING  display file beginning from search string match
  -V        output version information and exit

```
```

ubuntu@ubuntu:~$ sudo smartctl -t long /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
Please wait 65 minutes for test to complete.
Test will complete after Sat May  4 02:18:41 2013

Use smartctl -X to abort test.
ubuntu@ubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.5.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Hitachi Travelstar 5K500.B
Device Model:     Hitachi HTS545016B9A300
Serial Number:    091226PB5B06QCEAMREH
LU WWN Device Id: 5 000cca 5a2e104c2
Firmware Version: PBBOC60F
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 6
Local Time is:    Sat May  4 12:42:52 2013 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      ( 121)    The previous self-test completed having
                    the read element of the test failed.
Total time to complete Offline 
data collection:         (  645) seconds.
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
recommended polling time:      (  65) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   099   099   062    Pre-fail  Always       -       131072
  2 Throughput_Performance  0x0005   100   100   040    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0007   250   250   033    Pre-fail  Always       -       1
  4 Start_Stop_Count        0x0012   081   081   000    Old_age   Always       -       31418
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   067    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   040    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0012   090   090   000    Old_age   Always       -       4393
 10 Spin_Retry_Count        0x0013   100   100   060    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1507
191 G-Sense_Error_Rate      0x000a   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       31
193 Load_Cycle_Count        0x0012   087   087   000    Old_age   Always       -       135054
194 Temperature_Celsius     0x0002   152   152   000    Old_age   Always       -       36 (Min/Max 12/52)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       168
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       85
198 Offline_Uncorrectable   0x0008   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x000a   200   200   000    Old_age   Always       -       0
223 Load_Retry_Count        0x000a   100   100   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 155 (device log contains only the most recent five errors)
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

Error 155 occurred at disk power-on lifetime: 4354 hours (181 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 f3 52 2e ed  Error: UNC 3 sectors at LBA = 0x0d2e52f3 = 221139699

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 bb 36 c0 52 2e e0 08      00:20:54.000  READ DMA EXT
  25 bb 03 3d 51 2e e0 08      00:20:54.000  READ DMA EXT
  25 bb 3d 00 51 2e e0 08      00:20:53.900  READ DMA EXT
  25 bb 07 00 0d 2d e0 08      00:20:53.900  READ DMA EXT
  25 bb 1d e3 0c 2d e0 08      00:20:53.900  READ DMA EXT

Error 154 occurred at disk power-on lifetime: 4354 hours (181 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 03 f3 52 2e ed  Error: UNC 3 sectors at LBA = 0x0d2e52f3 = 221139699

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 bb 36 c0 52 2e e0 08      00:19:13.300  READ DMA EXT
  25 bb 03 3d 51 2e e0 08      00:19:13.300  READ DMA EXT
  25 bb 3d 00 51 2e e0 08      00:19:13.300  READ DMA EXT
  25 bb 07 00 0d 2d e0 08      00:19:13.300  READ DMA EXT
  25 bb 1d e3 0c 2d e0 08      00:19:13.300  READ DMA EXT

Error 153 occurred at disk power-on lifetime: 4354 hours (181 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 06 f0 52 2e ed  Error: UNC 6 sectors at LBA = 0x0d2e52f0 = 221139696

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 bb 36 c0 52 2e e0 08      00:17:34.000  READ DMA EXT
  25 bb 36 c0 52 2e e0 08      00:17:30.000  READ DMA EXT
  29 bb 36 c0 52 2e e0 08      00:17:20.600  READ MULTIPLE EXT
  25 bb 36 c0 52 2e e0 08      00:17:15.900  READ DMA EXT
  25 bb 03 3d 51 2e e0 08      00:17:15.900  READ DMA EXT

Error 152 occurred at disk power-on lifetime: 4354 hours (181 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 06 f0 52 2e ed  Error: UNC 6 sectors at LBA = 0x0d2e52f0 = 221139696

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 bb 36 c0 52 2e e0 08      00:17:30.000  READ DMA EXT
  29 bb 36 c0 52 2e e0 08      00:17:20.600  READ MULTIPLE EXT
  25 bb 36 c0 52 2e e0 08      00:17:15.900  READ DMA EXT
  25 bb 03 3d 51 2e e0 08      00:17:15.900  READ DMA EXT
  25 bb 3d 00 51 2e e0 08      00:17:15.900  READ DMA EXT

Error 151 occurred at disk power-on lifetime: 4354 hours (181 days + 10 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 06 f0 52 2e ed  Error: UNC at LBA = 0x0d2e52f0 = 221139696

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  29 bb 36 c0 52 2e e0 08      00:17:20.600  READ MULTIPLE EXT
  25 bb 36 c0 52 2e e0 08      00:17:15.900  READ DMA EXT
  25 bb 03 3d 51 2e e0 08      00:17:15.900  READ DMA EXT
  25 bb 3d 00 51 2e e0 08      00:17:15.900  READ DMA EXT
  25 bb 07 00 0d 2d e0 08      00:17:15.900  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      4382         21284993

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

Thank you so much!

---

### Post by matt_symes on 2013-05-04
Hi

> 196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       168 197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       85

You have some bad block on the drive and this may be the cause of your problems.

The first thing i would do is image the drive from a LiveCD/USB using ddrescue onto a spare hard drive.

```
sudo apt-get install gddrescue
```

ddrescue is a tool i have been using for a number of years and it will make a byte by byte copy of the drive. It will attempt to read the damaged block and will eventually skip of them if they are unreadable.

After you have done that you can attempt to recover the files from the drive.

I would start by running chksdk from an XP recovery disk. This is the general idea....

[http://www.schrockinnovations.com/how-to-run-a-chkdsk-to-repair-your-damaged-hard-drive-2/](http://www.schrockinnovations.com/how-to-run-a-chkdsk-to-repair-your-damaged-hard-drive-2/)

If that fails to work then you'll be looking at file recovery software.

Kind regards

---

### Post by momodiouf on 2013-05-04
> **matt_symes said:**
> Hi



You have some bad block on the drive and this may be the cause of your problems.

The first thing i would do is image the drive from a LiveCD/USB using ddrescue onto a spare hard drive.

```
sudo apt-get install gddrescue
```

ddrescue is a tool i have been using for a number of years and it will make a byte by byte copy of the drive. It will attempt to read the damaged block and will eventually skip of them if they are unreadable.

After you have done that you can attempt to recover the files from the drive.

I would start by running chksdk from an XP recovery disk. This is the general idea....

[http://www.schrockinnovations.com/how-to-run-a-chkdsk-to-repair-your-damaged-hard-drive-2/](http://www.schrockinnovations.com/how-to-run-a-chkdsk-to-repair-your-damaged-hard-drive-2/)

If that fails to work then you'll be looking at file recovery software.

Kind regards

Thank you so much, I am going to do what you said step by step.
Thank you for help and understanding.

---

### Post by Mark Phelps on 2013-05-04
If your hard drive has filesystem damage, then it's not going to start in XP, no matter what.  And, installing SMART tools is, at best, only going to confirm that -- as those can not fix filesystem damage.

If you really want to recover files from the hard drive, you will need two things: (1) the ability to connect the drive to a working PC running MS Windows, and (2) willingness to spend some money -- as the really good Windows data recovery apps are not free.

If these are both true for you, then read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

