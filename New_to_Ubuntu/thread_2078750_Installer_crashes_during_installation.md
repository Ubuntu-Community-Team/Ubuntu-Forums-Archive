---
title: "Installer crashes during installation"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Noor1101 on 2012-10-31
Hi,

My hdd broke down and I just bought a new one and put it in my notebook. The new hdd is a Toshiba 500GB 2.5" SATA300 540, my notebook Packard Bell Easynote MH35.

I made a bootable live USB with ubuntu-12.04.1-desktop-i386.iso. I used winMD5Sum to check the hash/checksum of my .iso-file (on someone else's WinXP PC) and it is correct.

However, the installer keeps crashing:
(With help from a youtube video) I tried three times to make three partitions (root (/) (10,000MB), swap (6000MB) and /home (all the rest of the MB's) but when the installer starts installing the system (after I've given my location, name, computer's name, password etc.), it crashes.

Then I thought I might have done something wrong in the partitioning (though I really paid attention to the video, so really it's not likely) - and I decided to try another way: 
choosing to install Ubuntu without partitioning my disk. Didn't work, same thing:
Two messages come up: 
1. "System program problem detected" (the installer keeps going while this message is up)
2. (A minute or so later) "The installer has crashed"

Every time I try again, the installer seems to think Ubuntu 12.04 is already installed (it isn't though, I tried booting from hdd and all I get is a blinking cursor): it gives me the option to "Erase Ubuntu 12.04LTS and reinstall".

What can I do? 

Apart from getting frustrated, I'm also surprised: when I installed Ubuntu12.04 for the first time (last August), everything was fine.

Has it something to do with my hdd being new, non-compatible, or ...?
Could it be the USB is not good, despite the hash/checksum being correct?


I'm on a Live Session now, that seems to work fine (internet and all).

Please help!
Thanks a lot

Noor

---

### Post by Noor1101 on 2012-10-31
Please, anyone? 

The installer keeps crashing when it gets to 'creating user' within 'installing system'.
I've just tried the Xubuntu-desktop-iso - the same thing happens.

I'll go an try Ubuntu-alternate iso now, but if anyone has any other ideas, I would really appreciate it if you let me know..

Thanks

---

### Post by Pilot6 on 2012-10-31
Altenate must work. 

But you can use normal installer too. Boot from the installer CD or flash, choose 'Try Ubuntu'. Then open terminal and run command
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```
After that just click 'Install Ubuntu' icon. It should work.

---

### Post by NikTh on 2012-10-31
> **Pilot6 said:**
> 
But you can use normal installer too. Boot from the installer CD or  flash, choose 'Try Ubuntu'. Then open terminal and run command
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```After that just click 'Install Ubuntu' icon. It should work.

Yes , this is almost the same as the alternate installation media. Probably the sideshow did the crash. 


> **Noor1101 said:**
> 

I'll go an try Ubuntu-alternate iso now, 


This would be my advice , to try with the alternate CD iso. 

Keep us informed about the progress. 

Thanks

---

### Post by Noor1101 on 2012-10-31
Thanks very much for your replies!

My CDROM drive doesn't work, so I'm using a live USB for this installation.

At the beginning of the (Ubuntu 12.04.1 alternate) installation I get an error message saying (something like)
> There was a problem reading data from the CD-ROM. Please make sure it is  in the drive. If retrying does not work, you should check the integrity  of your CD-ROM.

I have found [this page]("http://www.dotkam.com/2010/11/29/install-alternate-ubuntu-image-from-usb/?cfemail=posted#cformsform") which seems to have helped many people, but I don't know how to do it. I don't know what a "target host" is and I don't see the menu item "Default".

Someone replied on that site:
> It worked, I created the boot disk with the Universal Usb Installer, Used alternate for Ubuntu 10.04.4, then edited syslinux.cfg
 From
append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet  –
 To
append  file=/cdrom/preseed/ubuntu.seed initrd=/install/initrd.gz quiet cdrom-detect/try-usb=true –


but in my syslinux.cfg file it says
> # D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo


so it seems that has been changed.

Any ideas on how to make my pc look in the USB instead of CDROM??

---

### Post by Noor1101 on 2012-10-31
I might have found something, it might be that where it used to say "default", it now says "install on hdd" (or something like that (can't go back now)).

Will let you know how it goes

---

### Post by Noor1101 on 2012-10-31
It doesn't work :(

I booted from the USB, selected the option "Install Ubuntu" (there is nothing that says 'default') and pressed TAB (to change the menu entry - this worked for many people on the site I mentioned ([here]("http://www.dotkam.com/2010/11/29/install-alternate-ubuntu-image-from-usb/?cfemail=posted#cformsform") - I'll copy-paste the steps of the website at the end of this post)
The menu entry was: 
```
/install/vmlinuz cdrom-detect/try-usb=true file=cdrom/preseed/ubuntu.seed vga=788 initrd=/install/initrd.gz quiet --
```
and I changed it to
```
/install/vmlinuz cdrom-detect/try-usb=true  file=cdrom/preseed/ubuntu.seed vga=788 initrd=/install/initrd.gz quiet cdrom-detect/try-usb=true  --
```

I went on to install Ubuntu but the same error message came up:
> There was a problem reading data from the CD-ROM. (...)

Does anyone have any ideas?


--------

from [http://www.dotkam.com/2010/11/29/install-alternate-ubuntu-image-from-usb/?cfemail=posted#cformsform](http://www.dotkam.com/2010/11/29/install-alternate-ubuntu-image-from-usb/?cfemail=posted#cformsform)

> 1. download an alternate image: [Ubuntu Alternative Downloads]("http://www.ubuntu.com/desktop/get-ubuntu/alternative-download")
2. write an image to USB drive using [UNetbootin]("http://unetbootin.sourceforge.net/")
3. boot from this new USB on the target host
4. select the menu item “Default”
5. DON’T press ENTER
6. press TAB
7. add the “**cdrom-detect/try-usb=true**” before the “- -”
8. press ENTER
 Now it will actually look into USB to install the system rather than looking for CD-ROM or trying the whole OS from the network.


---

### Post by Noor1101 on 2012-10-31
Well, this alternate version really isn't working..

I guess I'll try the desktop version again and follow this advise:

> But you can use normal installer too. Boot from the installer CD or  flash, choose 'Try Ubuntu'. Then open terminal and run command
     Code:
     sudo apt-get remove ubiquity-slideshow-ubuntu 
After that just click 'Install Ubuntu' icon. It should work.will let you know how it goes

---

### Post by Noor1101 on 2012-10-31
I have been trying for 8 hours now to install Ubuntu 12.04 after I put in a  new internal harddisk in my notebook. 

I can't get (x)ubuntu-alternate to work - it keeps saying it can't find the CDROM. I'm using USB.

I  tried Ubuntu 12.04 desktop and Xubuntu 12.04 desktop iso files (on a  bootable-made USB): I can run a Live  Session (no problems - internet works and all) but installing to my HDD  fails every time.

The first few times it simply said "We're sorry, but the installer has crashed"

Then I tried Alternate - didn't work.
Then I went back to Desktop-iso-USB's, and removed "ubiquity-slideshow-xubuntu" (or -ubuntu, whichever I was using), because I was advised to do so in this thread. Since then the error message is 
> Apt Configuration Problem
An attempt to configure apt to install additional packages from the CD failedThis happens after I have given my name, username etc, when the installer starts to install the system.

Please help me, I'm really getting desperate.

:-/


edit: I googled the error message I'm getting now (about the apt configuration) but all I find is either quite old (2009) or too advanced (hocus-pocus) for me.

:-\


editedit: It seems like the installer is still looking for a CD.. Or at least it sounds like it: "An attempt to configure apt to install additional packages from the _CD_ failed"
Or is "CD" synonymous with "USB" within the installation?

Pleasepleaseplease, help me

---

### Post by Noor1101 on 2012-10-31
Pretty please ... ?:???:

---

### Post by NikTh on 2012-11-01
Please check your HDD for errors. 
Boot from Live and open a terminal and then do 
```
sudo apt-get install smartmontools --no-install-recommends
sudo smartctl -a /dev/sda
``` 

Compare the results with these values => [http://en.wikipedia.org/wiki/S.M.A.R.T](http://en.wikipedia.org/wiki/S.M.A.R.T).
and see if your HDD is failing or something.

Thanks

---

### Post by Noor1101 on 2012-11-01
Hi NikTh,

here are the results. I've compared them to the wikipedia values (results below)

```
xubuntu@xubuntu:~$ sudo smartctl -a /dev/sda
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF INFORMATION SECTION ===
Device Model:     TOSHIBA MQ01ABD050
Serial Number:    82ACC1OUT
LU WWN Device Id: 5 000039 43388224f
Firmware Version: AX001A
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   8
ATA Standard is:  Exact ATA specification draft version not indicated
Local Time is:    Thu Nov  1 12:12:15 2012 CET
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
recommended polling time:      ( 131) minutes.
SCT capabilities:            (0x003d)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000b   100   100   050    Pre-fail  Always       -       0
  2 Throughput_Performance  0x0005   100   100   050    Pre-fail  Offline      -       0
  3 Spin_Up_Time            0x0027   100   100   001    Pre-fail  Always       -       1056
  4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       37
  5 Reallocated_Sector_Ct   0x0033   100   100   050    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000b   100   100   050    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0005   100   100   050    Pre-fail  Offline      -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       8
 10 Spin_Retry_Count        0x0033   100   100   030    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   000    Old_age   Always       -       27
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       0
192 Power-Off_Retract_Count 0x0032   100   100   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   100   100   000    Old_age   Always       -       138
194 Temperature_Celsius     0x0022   100   100   000    Old_age   Always       -       18 (Min/Max 16/32)
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   200   200   000    Old_age   Always       -       0
220 Disk_Shift              0x0002   100   100   000    Old_age   Always       -       0
222 Loaded_Hours            0x0032   100   100   000    Old_age   Always       -       3
223 Load_Retry_Count        0x0032   100   100   000    Old_age   Always       -       0
224 Load_Friction           0x0022   100   100   000    Old_age   Always       -       0
226 Load-in_Time            0x0026   100   100   000    Old_age   Always       -       265
240 Head_Flying_Hours       0x0001   100   100   001    Pre-fail  Offline      -       0

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


```This is what is different from the wikipedia-info:

#2 Throughput performance: raw value = 0 (Updated = 'offline') 
(wiki says: Overall (general) throughput performance of a hard disk drive. If the value is decreasing there is a high probability that there is a problem with the disk --- higher raw value = better.)

#8 Seek time Performance: raw value = 0 (Updated = 'offline')
(wiki says: Average performance of seek operations of the magnetic heads. If this attribute is decreasing, it is a sign of problems in the mechanical subsystem --- higher raw value = better)

they are both 'offline', so what does that mean?

#3 Spin-Up Time = 1056ms  ------ that's OK, right? 

It seems alright to me. There are a lot of # missing (#6,11,13,184 etc), is that a problem?

 With this info, can you see whether my hdd is functioning correct? 

------
edit: of the "**Critical: pink colored row** Potential indicators of imminent electromechanical failure", the following are GOOD:
#1 Read Error Rate (value=0)
#5 Reallocated Sectors Count (0)
#10 Spin Retry Count (0)
#196 Reallocation Event Count (0)
#197 Current Pendng Sector Count (0)
#198 Offline Uncorrectable (0)

The following critical # are missing:
#184 End-toEnd error /IOEDC
#188 Command Timeout
#201 Count of off-track errors
#230 Current state of drive operation based upon life curve

None of the 'critical' have a negative test result.
--------

Thanks a lot

---

### Post by Noor1101 on 2012-11-01
After reading the thread [12.04 Installation Crashes]("http://ubuntuforums.org/showthread.php?t=1965802&highlight=installer+crashed") I'm now creating a USB with Xubuntu _11.10_ desktop -iso on it, to see if that will install.. Some people in the thread said that worked OK for them.

I'll be back to let you know how that went.

---

### Post by Noor1101 on 2012-11-01
11.10 desktop did not work either :(

Same error as before: 
> 
Apt Configuration Problem
An attempt to configure apt to install additional packages from the CD failed 			 		

(while installing the system - "scanning the CD-ROM".) 

 Does this mean the installer is checking my CD-ROM drive, or does it _always_ say CD-ROM, even if you're installing from USB?

---

### Post by NikTh on 2012-11-01
Your HDD is perfect . Has nothing to do with the crash. All values are ideal.  

I really cannot understand what happens here.

With what programm you create the LiveUSB ?

---

### Post by Noor1101 on 2012-11-01
Universal USB Installer 1.9.1.5, from pendrivelinux, on a Windows XP PC.

(I used the same program and PC last August and that worked)

Thanks for your time NikTh. Greatly appreciated.

--edit--
The live session works perfectly.. I thought that must mean the USB is fine..

---

### Post by teward on 2012-11-01
PUrely curious, but did you double check the md5 or sha256 sums on the ISOs to make sure they're complete?

And you mentioned Ubuntu and Xubuntu.  You should test Lubuntu, its lighter than both of those.

---

### Post by Noor1101 on 2012-11-01
Yes I did check the checksums. Double check. Made new USB's, checked again, double check.. etc. It's not that. 
Thanks anyway

---

### Post by Noor1101 on 2012-11-01
Theoretically, 
if Ubuntu, Kubuntu and Xubuntu worked fine on my pc, then my HDD crashes and I put in a new one, could it then be that my system can't handle Ubuntu, Kubuntu or Xubuntu anymore?

I don't know much about computers, but it sounds weird to me..

---

### Post by teward on 2012-11-01
It could mean your hardware's too old to support the OS, yes.  5 year old systems are still well within the range of supported equipment though.  It could be a bad USB drive, or that the Pendrive LInux installer is crap.  Did you try using unetbootin to write the Ubuntu ISO to the USB?

---

### Post by Noor1101 on 2012-11-01
No I didn't try that yet. I'll have a look. I need to create the usb in WinXP.

Will be back.

---

### Post by flint5 on 2012-11-01
I'm not sure if this will help you, but before two months i had the same problem as you.
I bought to a new HDD WD 500GB, because  my old HDD got a bad sectors.
I tried twice, like you on new HDD to install Ubuntu 12.04 booting from USB, and the installation every time crashed after this screen where i entered my user name, password and managed the home folder.
Then i tried to install Ubuntu 12.04 from a live CD, and all went well, except the installation took a little bit longer, but after installation my Ubuntu 12.04 worked fine.
I'm not sure, but i think that this problem got something to do with your (and my) older laptop, new HDD and SATA driver (i bought my Acer laptop about four years ago).

---

### Post by Noor1101 on 2012-11-01
Thanks, flint5, for your thoughts.
I might have to risk it (the money) and buy a new CD-ROM drive though I don't really know how I'm going to pay for that :-S

--

Since my last post I've been looking for (and I've found) Linux-support in the city I live in. That might be a better way of doing this, because my head is really spinning now and I haven't got anything working after 20 hours of trying - not non-stop, I _did_ sleep ;)

--

If I ever find out anything about the cause of my problems, I'll post it here.

So, for now, thanks to everyone, especially NikTh! 
This community is great :)

All the best
Noor

---

### Post by flint5 on 2012-11-01
Just a another thought!! (You do not need to answer me)

Maybe one of your friends might have an extern DVD/CD-ROM??

or

if you want to tray, here is a link, perhaps this could help:

[http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r](http://askubuntu.com/questions/127398/usb-drive-install-of-ubuntu-12-04-server-fails-cant-find-components-from-cd-r)

Install Ubuntu as described in the "ajay" answer (befor the last answer) with Universal-USB-Installer (USB works as a CD-ROM).

---

### Post by Noor1101 on 2012-11-02
Well, I tried installing Debian with lxde, just to see if it was an Ubuntu-installer issue. That seemed to work fine, "installation complete", but rebooting resulted in many,many errors that I couldn't understand, and the OS couldn't be started up.. 

I've agreed to get help on a no-cure-no-pay base. If I find out what the problem was, I'll post it here.


flint5, thanks for your advice. I've tried using a USB-CD/DVD-ROM drive, but it didn't work (no drivers, drive not detected).
I came by the url you mentioned before and tried to follow the directions but it's all getting too confusing for me. I'm happy now to let someone else try, to be honest. 

On a side note, I've also been told about a linux users' get-together group, once a month in the city I live in. I'll definitely go there, to learn new things. This forum is great, but sometimes it's nice to have someone sitting right next to you to explain what to do, how and why.

Thanks, flint5 and everyone else.

---

### Post by NikTh on 2012-11-02
Have you tried with Unetbootin ? 
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Try to create a bootable usb with unetbootin (from within XP). 
Also (if you have) try with another USB-Flash. 

Thanks

---

### Post by Noor1101 on 2012-11-02
Yes, I tried multiple times with pendrivelinux's Universal USB Installer, and then (also multiple times, and versions) with Unetbootin, on 3 different flashUSB's. All of them (versions, flashUSB's, UUI/Unetbootin) worked just fine in a live session. But the installation failed every time.

No luck. I hope the guy who's - hopefully - going to fix it for me, will be able to tell me what went wrong, so that I can in turn tell you here.

That won't be until sometime next week though.

---

### Post by NikTh on 2012-11-02
> **Noor1101 said:**
> 
I hope the guy who's - hopefully - going to fix it for me, will be able to tell me what went wrong, so that I can in turn tell you here.

That won't be until sometime next week though.

I will wait even until next month. I'm very curious what causes this weird problem.

Hope you solved it.

Thread bookmarked.

---

### Post by warjowuch on 2012-11-03
THat's familiar to me... Maybe you can try to format the usb-drive to FAT32? I believe that's what solved my problem.

It should (IMO) not be a problem, but it seems to be.

Good luck!

---

### Post by Noor1101 on 2012-11-03
Dankjewel voor je reactie warjowuch -- thanks for your reply warjowuch :)

...I haven't mentioned it before, but I have all my flash USB's formatted as FAT32.

---

### Post by LukeMorrison on 2012-11-03
Have you tried using the mini.iso to install?  This will pull the latest packages from the internet instead of the install media.  This is how I do the majority of my installs.

I tried to input the links, but they were getting truncated.  Search for ubuntu precise mini.iso and your architecture (32-bit or 64-bit)

You will need to download the mini.iso for your architecture and "burn" the .iso image to your USB stick.

---

### Post by warjowuch on 2012-11-03
:) Gaarne gedaan - You're welcome!

And what happens if at first you prepare the drives, run fsck (GUI via gparted and disk-utility) and then run the installer?

---

### Post by Noor1101 on 2012-11-07
UPDATE

I just got my notebook back, with Debian7+Gnome3 installed. 
It works! Hurrah! :guitar:

The (Debian) expert found out that the problem was related to **DMA**, Direct Memory Access (or at least, it was solved by configuring the DMA settings). It did puzzle him though, and he's still **not completely sure** why the problems occurred. It might also have something to do with the **combination** of a not-so-new motherboard/SiSchipset and a new SATA300 hard-disk. 

I don't know how to check it (and I don't know whether it is possible to check it on a broken disk), but the original hard-disk may have been a SATA150-disk, and it may be that the rest of the components in my notebook have problems connecting with a (newer) SATA_300_-disk.

I'll translate the e-mail the expert sent me, with information on what he found and how he fixed it. Please note I don't understand all it says - I'm just translating.

> Like I told you, the file system becomes corrupt when DMA is enabled. DMA makes the hard-disk much faster, but apparently the Linux driver for the sis5513 chip has problems with this. I tested this, from a Live boot CD(/USB) with
```
e2fsck -f /dev/sda1 
```When DMA is enabled and there is a file system on it, I always got errors. If you press ctrl-c with the first error, nothing will be changed.

I disabled DMA with the kernel option 
```
libata.dma=0
```In Debian, you can do that -after booting- by going to your choice (of installation), pressing TAB, and then adding "libata.dma=0" after "-- quiet". Then return to the menu.
I noticed that after reboot this setting is not automatically put into GRUB, so first GRUB needs to be configured with "e" (edit), and putting "libata.dma=0" after "quiet". Once that has been done it's possible to boot with F10.
After booting it also needs to be changed in GRUB, so that it doesn't need to be configured again the next time you boot. You can do that in the file /etc/default/grub.

Remember this also needs to be done with live-CD's of live-USB's if you want to access the disk.The consequence of disabling DMA is that the starting of applications is slower than it used to be. Once applications are running there is no (noticeable) difference. (When I want to start Iceweasel, my current internet browser, it takes about 10-15 seconds; a bit slow but not insurmountable.)


Right now I have my notebook back (and I'm very happy about it!), but it might be that the expert will think of something else, and will contact me to have another look and try some things.

Anyway, it was quite a struggle and it has got me to join a local Linux users' group and be even more eager to learn than I was before. (Especially having an expert not quite knowing why his solution worked, intrigues me! Plus he hasn't got a degree, but learnt it all by himself over the last 12 years by trying, reading and talking to other people.)

Thanks to everyone here! 
Especially NikTh, who helped me on multiple threads. &#963;&#945;&#962; &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; !!

I guess it's 'bye-bye', or am I, as a Debian user, still welcome? ;)

A very helpful forum, and a nice community. I'm sorry to leave you (especially as I've  just reached the number of posts that allows me to edit my profile :) )

All the best,
Noor

---

### Post by NikTh on 2012-11-07
> **Noor1101 said:**
> &#963;&#945;&#962; &#949;&#965;&#967;&#945;&#961;&#953;&#963;&#964;&#974; !!
You're welcome ! 

> **Noor1101 said:**
> I guess it's 'bye-bye', or am I, as a Debian user, still welcome? ;) 

Everyone is welcome here . Do not forget that Ubuntu is based in some way to Debian distro. 

About the problem , I bet more in sis chip. Those chips either graphic cards or motherborads were always problematic with a lot of Linux distributions.

---

### Post by Noor1101 on 2012-11-09
It seems the primary problem is that my chipset ([FONT=Tahoma][SIZE=2][SiS] 671MX) cannot "communicate" properly with a SATA300 (=3Gb/s) hdd.

On this site Western Digital gives a description of the problem and a solution (setting the hdd to 1,5Gb/s): [http://wdc.custhelp.com/app/answers/detail/search/1/a_id/1337/c/130/p/227,194](http://wdc.custhelp.com/app/answers/detail/search/1/a_id/1337/c/130/p/227,194)

After the weekend I will go to the store where I bought my hdd and ask what to do. I may be able to bring my current hdd back and get a WD 500Gb in return.
This phrase worries me though: [/SIZE][/FONT]

[LIST]
[*]To lock the drive at 150 MB/s data transfer rate install a jumper shunt on pins 5-6 (**OPT1**), shown in the picture below. (_Only available on 3.5 inch (Desktop) size drives_)
[/LIST]
[FONT=Tahoma][SIZE=2]I have a 2,5 inch drive...


I'll let you know if and how it can be solved.


[/SIZE][/FONT]

---

### Post by Noor1101 on 2012-11-22
I returned the first new hdd and got a Western Digital SATA300 500Gb. Didn't solve much. DMA did not need to be disabled, Debian&Gnome sometimes worked, but it crashed (or wouldn't start up) regularly giving errors like
```
fsck died with exit code 4 (or 8)
ata3.00 revalidation failed
/dev/sda1 contains a file system with errors, check forced
Inodes that were part of a corrupted orphan linked list found
end_request: I/O errors, dev sda sector #
```Also, the system kept configuring (changing) the udma speed: ranging from 33 (= very slow) to 133 (= (too) fast) (I'm not quite sure what it means, but I've been told it's strange)

The I/O errors and dev/sda errors could be fixed temporarily by running```
 fsck /dev/sda1
```  (and typing y (yes) many times), but the problem kept coming back. I couldn't rely on my computer, couldn't be sure my work was saved.
 

**I'm not completely sure, but I think I've found out what the cause of the problem is.**

In my despair I decided to try to install Ubuntu onto an (eight-year-) old internal hdd with a capacity of only 60Gb. Someone told me it is possible that the _BIOS has a maximum in terms of supported hdd-capacity_. The 2 new hdd's I tried were 500Gb, and the (original) broken one 250Gb.

And it seems to work - or at least it has now been working perfectly for three hours. I successfully installed Ubuntu 12.04.1 from USB, the xfce desktop, and 227 updates, and copied my documents, pictures, and audio books onto the 60Gb disk.
[SIZE=1]I only have 18Gb left[/SIZE] :)

I'm surprised the system didn't "tell" me the capacity of the hdd was problematic in an (even to the experts) understandable way, and I'm also surprised the guys at the computer store didn't mention it being possible that the disk was too big for my BIOS. I never knew that was possible, and I spent quite some time there, talking to them and asking for advice. But well.. it works now (fingers crossed) and for 10 euros extra I bought a casing for the new 500Gb disk.


Does anybody know how to find out the maximum supported disk capacity of BIOS? 


Thank you very much

Regards,
Noor

---

### Post by NikTh on 2012-11-23
Hi , 
well first of all I'm glad you have installed Ubuntu successfully . Have a joy :) 

Yes, the capacity of HDD sometimes is important combined with BIOS. Take a look if BIOS has an update (update BIOS through Linux is quite difficult) .
 Open a terminal and give this command for more info 
```
sudo dmidecode -t  0,1,2,3
``` 
or 
give a link where your PC listed (specifications ..etc).
Thanks

---

### Post by Noor1101 on 2012-11-24
Hi NikTh,

Thanks for your continued support :)

I have already looked into updating BIOS - there are updates available, and my BIOS (PE14A04) is upgradeable. But to be honest, I dare not try it. At least not now.

I need this -only- pc of mine for my studies, and I've had to go without it for three weeks. It was very annoying and cost me a lot of time; having to use shared (uni) computers that are not available most of the time.

So right now I won't try to update BIOS, I'm too scared something will go wrong. The 60Gb hd works well right now -- I just have to copy some stuff to and from the currently-external 500Gb hd every now and then. That's OK. 
I might try upgrading the BIOS in the (Christmas) holidays or the end of January, when I'm a little less busy with my studies (I hope).

So thank you very much for your help! Have a nice evening.

Regards
Noor

---

