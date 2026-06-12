---
title: "Ubuntu 14.04 will not boot unless I go through recovery mode in grub"
date: 2015-03-07
forum: New to Ubuntu
---

### Post by Tyler_Roesler on 2015-03-07
So I just installed Ubuntu in a dual boot configuration with Windows 7 recently, and whenever I boot Ubuntu from grub, I just get a black screen forever. So after a hard reboot I tried going into recovery mode and booting it and it booted right up. I'm running off a pavilion dv6 (AMD A8 3500M processor, AMD Raedon HD 6620G graphics card, if that helps) I read elsewhere that it may be the AMD drivers causing the problem but I tried going to the additional drivers and using the proprietary drivers, but they won't switch over no matter how many times I've told it to apply the changes. So, I'm not really sure what to do here. Any help would be great.

---

### Post by Tyler_Roesler on 2015-03-08
***Update:***

I recieved an error from Ubuntu saying it experienced an interal error. Here is what it's telling me:

[ATTACH=CONFIG]260521[/ATTACH]

any thoughts?

---

### Post by Bashing-om on 2015-03-08
Tyler_Roesler; Hello;

Let's see what we can do.
1st is to address the error that says a prior shutdown was not proper. There may may file system corruption.
To check and repair the file system there are a few options. As you can not boot the system normally to your user account, I prefer to get hands on and direct with the terminal.
One can not operate on a file system while it is is use; in this instance we will work from the liveDVD(usb) to effect the check/repair.

Boot your liveDVD(USB) - the medium you used to install ubuntu - to a terminal:
issue terminal commands:
```

sudo fdisk -lu

```
In that output look for the partition marked with an asterisk :
for example in my case:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

```
my booting partition is 'sda1'

Now we know what partition to direct "e2fsck' to work over; do it like so:
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
where one changes the 'sda1' to the partition as indicated from the output of 'fdisk' ( that little asterisk).
IF there are errors reported, we need to fix them, this command will do that with no intervention on your part (believe me, the system is smarter about fixing the errors than we are, though we can, at this stage we do not want to intervene)
```

sudo e2fsck -f -y -v /dev/sda1

```
OK, file system is all good now;
Let's see what is going on with accessing your account on the install.

Reboot, set bios to boot the hard drive and boot the install .
Let us go with your premise that there is a graphics driver issue. Try this to boot to the GUI:
When booted to the grub menu hit the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line similar to "linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" and arrow across to the terms "quiet splash" and add the term "nomodeset".
key combo ctl+x to continue the boot process.
Do you now boot to the desktop ?
Here we need to look at what hardware we are working with, and then see about the graphics driver.
IF you get this far, what returns from terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
place that output - Between Code Tags - !
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

These will give a good place to start the troubleshooting procedures .

Keep in mind,
This is 'buntu ->
[INDENT][INDENT][INDENT]given the time and effort, and a liveDVD - it is always fixable 
[/INDENT][/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-08
So, I did as you said and got to the ```
sudo e2fsck -f -y -v /dev/sda1
```, and got even more errors. Here is what was ouputed:
```


:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1: 
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>

:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
ext2fs_open2: Bad magic number in super-block
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



```

on the plus side, this did somehow cause the light around my touchpad to light back up which it hasn't done in a while, so there's that.

---

### Post by Bashing-om on 2015-03-08
Tyler_Roesler; Hey !

Not good, but not hopeless.

Show me the output:
```

sudo fdisk -lu

```
to verify we are working the correct disk/partition.
Then perhaps we look at sparing off that superblock.
Might  be a good idea to run a SMART test on the drive to see the health status .

[INDENT][INDENT]cross that bridge when we get to it
[/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-08
```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd08a832e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   650485555   325139354    7  HPFS/NTFS/exFAT
/dev/sda3      1145815040  1250260991    52222976    7  HPFS/NTFS/exFAT
/dev/sda4       650485758  1145815039   247664641    5  Extended
/dev/sda5       650485760  1130129407   239821824   83  Linux
/dev/sda6      1130131456  1145815039     7841792   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by sandyd on 2015-03-08
Run this```

sudo apt-get -y install smartmontools
smartctl --test=long /dev/sda
```

Go out for a walk

Come back in an hour or so and post the output of```

smartctl --all /dev/sda
```

---

### Post by Bashing-om on 2015-03-08
Tyler_Roesler; Haste makes waste.

@sandyd Pleased to see ya pop up here ...Good to read ya !

+1 for the SMART test.

I must admit an error in my instruction:
> 
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT

My directive was to the partition containing the asterisk ... good advise but wrongly thought out.
That partition is a Windows partition ! - with the boot flag....

The partition we are interested in is the linux - sda5 - partition.

When the health check is completed we look at the file system properly as 'sda5' rather than 'sda1' .

[INDENT][INDENT][INDENT]we make things write
[INDENT][INDENT][INDENT]when possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-09
Here is the result of the ```
 smartctl --all /dev/sda 
```:

```

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  120) seconds.
Offline data collection
capabilities:              (0x51) SMART execute Offline immediate.
                    No Auto Offline data collection support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
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
recommended polling time:      ( 185) minutes.
SCT capabilities:            (0x003f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0027   100   100   050    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0023   100   100   002    Pre-fail  Always       -       1686
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1157
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x002f   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Minutes        0x0032   098   098   000    Old_age   Always       -       15h+49m
 10 Spin_Retry_Count        0x0033   123   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       1153
183 Runtime_Bad_Block       0x0032   100   100   001    Old_age   Always       -       0
184 End-to-End_Error        0x0033   100   100   097    Pre-fail  Always       -       0
185 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       65535
187 Reported_Uncorrect      0x0032   097   097   000    Old_age   Always       -       3
188 Command_Timeout         0x0032   100   098   000    Old_age   Always       -       5
189 High_Fly_Writes         0x003a   100   100   001    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   062   048   040    Old_age   Always       -       38 (Min/Max 37/51)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       773
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       1441814
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       7329
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 3
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

Error 3 occurred at disk power-on lifetime: 462 hours (19 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 33 e5 fe 91 e2  Error: UNC 51 sectors at LBA = 0x0291fee5 = 43122405
Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 78 a0 fe 91 e0 00      00:00:18.781  READ DMA EXT
  25 00 78 28 fe 91 e0 00      00:00:18.779  READ DMA EXT
  25 00 78 b0 fd 91 e0 00      00:00:18.777  READ DMA EXT
  25 00 78 38 fd 91 e0 00      00:00:18.775  READ DMA EXT
  25 00 78 c0 fc 91 e0 00      00:00:18.774  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%       942         -
# 2  Extended offline    Interrupted (host reset)      90%       938         -

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

### Post by ck170 on 2015-03-09
yeah i had this problem after an update. it is the AMD catalyst (fglrx) drivers causing black screen. solution is to uninstall fglrx from the command line. good luck. it should reboot with normal display. then reinstall AMD Catalyst (fglrx).

---

### Post by Bashing-om on 2015-03-09
Tyler_Roesler; Well ..

see ck170's contribution ( thanks ck170 ) It is a likely happenstance.

Over all the SMART test looks good , a fairly new hard drive.
But, these I do not understand:
```

185 Unknown_Attribute       0x0032   100   100   001    Old_age   Always       -       65535
192 Power-Off_Retract_Count 0x0022   100   100   000    Old_age   Always       -       1441814

```

Let's now run the file system checks on the correct partition !
From the liveDVD:
```

sudo e2fsck -C0 -p -f -v /dev/sda5
sudo e2fsck -f -y -v /dev/sda5

```
Run Windows' chkdisk utility on the Windows' file system.

What results now when you try and boot into the ubuntu install ?
When we get the system(s) stable will be interesting to see the result of a updated SMART test ; and compare those questionable numbers .

[INDENT][INDENT]see what we can do
[/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-10
[URL="http://ubuntuforums.org/member.php?u=1973444"][B][COLOR=#000000]ck170:

[/COLOR][/B][COLOR=#000000][/COLOR][/URL] I tried doing as you suggested, but it appears that fglrx isn't even installed on my system, and the ```
sudo apt-get fglrx
``` didn't do anything. When I tried going through the GUI, I found it but when I tried installing it I got this as an error:

"The following packages have unmet dependencies:

fglrx: Depends: libqtcore4 (>= 4:4.8.4) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
       Depends: xorg-video-abi-15 but it is a virtual package"

not sure where to go from here... I'm pretty green to linux here...

Bashing-om:

I've been a little busy lately and haven't had time to run from the live dvd, but when I do (probably tonight) I will post! 

Thank you everyone for the help!

---

### Post by Tyler_Roesler on 2015-03-10
So I think I found out why I can't download fglrx. It appears that it's a bug with apt-get and ubuntu 14.04 that hasn't been fixed yet (to my knowledge): [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)

---

### Post by Bashing-om on 2015-03-10
Tyler_Roesler; Welp :

Possible that it is a graphics driver issue, but let's cross that bridge when we get to it. Let us not loose site of the tree for all the forest.
In small steps - all my liltle mind can cope with - to insure a firm foundation from which to work from;
a) file system checks are good in both Windows and ubuntu (sda5)
b) We try and boot to terminal and then see if we can isolate the failure to start the GUI.

When file system checks are complete then we proceed to a next step.

[INDENT][INDENT]a process
[INDENT][INDENT][INDENT]fault isolation to resolution
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-10
Ok so here is the output of the first code:
```

 244503 inodes used (1.63%, out of 14991360)
         117 non-contiguous files (0.0%)
         218 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 198095/33
     2152012 blocks used (3.59%, out of 59955456)
           0 bad blocks
           1 large file

      155549 regular files
       26248 directories
          57 character device files
          25 block device files
           0 fifos
           6 links
       62613 symbolic links (46283 fast symbolic links)
           2 sockets
------------
      244500 files


```

and here's the second:
```

e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      244503 inodes used (1.63%, out of 14991360)
         117 non-contiguous files (0.0%)
         218 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 198095/33
     2152012 blocks used (3.59%, out of 59955456)
           0 bad blocks
           1 large file

      155549 regular files
       26248 directories
          57 character device files
          25 block device files
           0 fifos
           6 links
       62613 symbolic links (46283 fast symbolic links)
           2 sockets
------------
      244500 files


```

---

### Post by Bashing-om on 2015-03-10
Tyler_Roesler; Hey hey !

That looks good for the file system check !
OK, let's see if we can boot to terminal.

Boot the install, at the grub boot menu with 'ubuntu' selected to boot, press the 'e' key for edit mode -> boot parameters screen;
arrow down to the line similar " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff " and across to the terms "quiet splash" replace these terms with 'text' - with out the quotes ;
key combo ctl+x to continue the boot process to TTY1.
Log in here with username and pass word - there will be no response to the screen when pass word is entered.

Can do , so far so good ? 
IF you get here we look at what is going on with the GUI .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-10
No dice getting to the terminal after the edit. It still just goes to a black screen. My keyboard is lit up but that's it. No flicker, no anything.

---

### Post by Bashing-om on 2015-03-10
Tyler_Roesler; Humm ..

Hunting for a symptom of causation:
Booting to terminal and still get A totally back screen ?
no blinking cursor in the upper left ( boot code not found}
no grub advisories ending in a grub > prompt (grub config not found)
no initramfs ending in grub rescue > prompt (kernel not found)

Anyway, I can not see the harm in (re)installing grub, at the least will get some additional info;
We do this from the liveDVD ;
boot the liveDVD to terminal:
```

sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
Reboot into the install on the hard drive ... and if able to boot to the GUI :
now run terminal command:
```

sudo update-grub

```
to pick up and chainload Windows onto grub's boot menu

and hey
[INDENT][INDENT]all could come out rosy
[/INDENT][/INDENT]

---

### Post by ck170 on 2015-03-11
[I]This doesn't appear lto be the AMD/ATI video card problem that I experienced. But maybe remove the X-org (video driver).

[/I][COLOR=#0A0200][FONT=Arial]Remove existing xorg using the following command[/FONT][/COLOR][INDENT][FONT=inherit]sudo apt-get remove --purge xserver-xorg[/FONT]
[/INDENT]
[COLOR=#0A0200][FONT=Arial]Install xorg using the following command[/FONT][/COLOR][INDENT][FONT=inherit]sudo apt-get install xserver-xorg[/FONT]
[/INDENT]
[COLOR=#0A0200][FONT=Arial]Reconfigure xorg using the following command[/FONT][/COLOR][INDENT][FONT=inherit]sudo dpkg-reconfigure xserver-xorg
[/FONT][COLOR=#000000][FONT=serif]
Also,

To uninstall the ATI/AMD driver, run [/FONT][/COLOR]*fglrx-uninstall.sh, which is located in /usr/share/ati directory.*[FONT=inherit]
[/FONT]
Again, good luck.[/INDENT]

---

### Post by Tyler_Roesler on 2015-03-12
So I reinstalled Grub as you said, and when I tried to boot to the installed system I got a black terminal-like screen that said something along the lines of welcome to grub, tell it what to do, and I tried inputting ```
sudo update grub
``` and it couldn't recognize that. 

So now I can only access Ubuntu (or my computer in general) through the liveDVD because I can't figure out how to get past this screen. When I tried to do the ```
sudo update-grub
``` from the liveDVD I get this error:
```

/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.

```
This is sort of a problem for me because I was using Windows still for school work and I can't open Windows, so where do we go from here?

---

### Post by Tyler_Roesler on 2015-03-12
ck170:

I tried to do as you said, here is what happened:
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
ubuntu@ubuntu:~$ sudo apt-get libcheese-gtk23
E: Invalid operation libcheese-gtk23
ubuntu@ubuntu:~$ sudo apt-get install libcheese-gtk23
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcheese-gtk23 is already the newest version.
libcheese-gtk23 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo apt-get install libcheese7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libcheese7 is already the newest version.
libcheese7 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ 


``` 
So i'm not really sure what is going on here. It says I have the libraries and they are up to date, so is it something going wrong with apt-get? I don't know.
Also I tried uninstalling the AMD drivers and all I got was an error saying your command wasn't recognized.

This is fun.

---

### Post by Bashing-om on 2015-03-12
Tyler_Roesler; UnGood ;

Totally not expected.
Show me again what we are working with - as there are conflicts with the info thus far provided.
What now returns -from the liveDVD:
```

sudo fdisk -lu

```
we still working with the file system on device 'sda5' ?
Then we try and boot the system from that grub > prompt .

[INDENT][INDENT]more than 1 way to an end
[/INDENT][/INDENT]

---

### Post by leunam12 on 2015-03-12
If you can boot to the live DVD try installing and running boot-repair[URL="https://help.ubuntu.com/community/Boot-Repair"]

https://help.ubuntu.com/community/Boot-Repair[/URL]

It has saved me from a lot of booting problems in the past.

---

### Post by Tyler_Roesler on 2015-03-12
Here's the result of the ```
sudo fdisk -lu
``` code:

```

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd08a832e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   650485555   325139354    7  HPFS/NTFS/exFAT
/dev/sda3      1145815040  1250260991    52222976    7  HPFS/NTFS/exFAT
/dev/sda4       650485758  1145815039   247664641    5  Extended
/dev/sda5       650485760  1130129407   239821824   83  Linux
/dev/sda6      1130131456  1145815039     7841792   82  Linux swap / Solaris

Partition table entries are not in disk order

```

should still be sda5 from what i can tell

---

### Post by Bashing-om on 2015-03-12
Tyler_Roesler; Yep;

It do show ubuntu installed to 'sda5' .
I do not know yet where the failure lies;
Let's try this:
boot the install to that grub menu.
At the grub menu with ubuntu selected to boot, press the 'c' key for a command line:
enter terminal commands:
```

linux (hd0,msdos5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,msdos5)/initrd.img
boot

```

see if now you boot and where we go from here.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-12
Update: The boot repair helped, thanks lauman12! Now I can get to the regular grub interface. Trying to boot straight to Ubuntu however still yields the same results.

---

### Post by leunam12 on 2015-03-12
It does sound like a graphics driver problem. Try to boot to Ubuntu and examine the screen with a strong light to see if you can see something on the screen, maybe your problem is that the laptop is booting with a dimmed screen where the backlight is completely off. It happened to me once, I don't remember how I solved it, though, it was something like adding acpi_backlight=vendor somewhere in grub configuration file. Do some research if you think that could be the problem

---

### Post by Tyler_Roesler on 2015-03-14
Hello all, 

sorry for the late reply, been travelling a lot lately not much time to jump on my computer!

Bashing-om, I was able to boot after inputting that code right to ubuntu, but after a restart and going straight to booting ubuntu I still got the black screen

leunsm12, the screen is totally black, no images behind it.

---

### Post by Bashing-om on 2015-03-14
Tyler_Roesler; Progress !

OK, that grub > commands was to see if we could boot, and will not persist a reboot.
Let's see if we can make it a fix with executing those grub > commands again:
```

linux (hd0,msdos5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,msdos5)/initrd.img
boot

```
Once booted to the GUI, let's try this to fix the issue;
Issue terminal commands - from within the install:
```

sudo grub-install /dev/sda
sudo update-grub

```
To confirm the installation had no error:
```

grub-install --recheck /dev/sda

```

Now reboot, see now if you boot normally to the GUI .

[INDENT][INDENT]Maybe YES
[INDENT][INDENT][INDENT]maybe have to get a bit more aggressive 
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tyler_Roesler on 2015-03-23
First let me apologize for the late reply, I had a death in the family recently and have been unable to find time to pop on my computer and try these things out.

Now, the good news! That solution worked! I logged right in from the grub menu and didn't have a problem. Thank you so very much Bashing-om for all of your help, would have been totally lost without you.
Now on to my next project.... learning the language so I'm not quite so green! Thank you again and thanks to everyone looking and posting to help my find this solution.

---

### Post by Bashing-om on 2015-03-23
Tyler_Roesler; Great !

Pleased to be of some small help. Glad ya up and running and just that much more comfortable with this our operating system of choice.
You have your feet wet now, go ahead,  jump in, the water is fine. There is an abundance of help. The trick is determining what is old and obsolete guidance; ubuntu is a fast moving ever evolving target.  It does not take long to learn how to differentiate .

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

