---
title: "[SOLVED] System won't boot xp or Hardy"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Ubuntscrewed on 2008-09-05
I installed Hardy Heron on my 250 Gb Sata HDD concurrently (dual boot) with existing Windows XP Home OS, allowing Ubuntu to partition my HDD.  Since install, I have been unable to boot into XP.  

I just ran Super Grub Disc, and now neither OS will boot unassisted.  I think I messed something up, bad.  Ubuntu will load using SGD, but XP won't.  I'm a total noob - can anyone help please?  Output from sudo fdisk -lu is:

john@john-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbcebde02

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   156280319    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x68fc68fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   367663589   183831763+   7  HPFS/NTFS
/dev/sdb2       367663590   488392064    60364237+   5  Extended
/dev/sdb5       367663653   483363719    57850033+  83  Linux
/dev/sdb6       483363783   488392064     2514141   82  Linux swap / Solaris

Disk /dev/sdc: 1021 MB, 1021125120 bytes
32 heads, 63 sectors/track, 989 cylinders, total 1994385 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe0af874b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1             247     1993823      996788+   6  FAT16
john@john-desktop:~$ 


Thank you.  EDIT The 80 Gb HDD is a non-issue - hoping to re-format to use for storage, after I learn how.  Cheers.

---

### Post by Pro-reason on 2008-09-05
When you boot from your hard drive, does it get as far as GRUB?  What error appears?

Post the contents of */boot/grub/menu.lst*.

---

### Post by MegaJim on 2008-09-05
The problem there is that you have two partitions marked as active (the asterisk) - only one per system should be marked as active at any time for windows.  Wherever you have windows installed (most likely sdb1) should be left as active, and the other drive unmarked.

In order to help you get your dual-boot setup without the need for super grub disk, can you post the output of the following commands:

```
 df /boot
```
```
 cat /boot/grub/menu.lst
```
```
 cat /boot/grub/device.map
```

---

### Post by Ubuntscrewed on 2008-09-05
Strange... The Grub loader has started working - it didn't on two previous attempts but will now load Ubuntu but still no joy on XP.  I get a black screen with  the error message "A disc read error occurred - Press Ctrl+Alt+Del to restart"

Quoting MegaJim "Wherever you have grub installed (most likely sdb1) should be left as active, and the other drive unmarked. "

Ooookaaayy, ah what? and how?  Please and thank you.

---

### Post by Pro-reason on 2008-09-05
> **Ubuntscrewed said:**
> 
Quoting MegaJim "Wherever you have grub installed (most likely sdb1) should be left as active, and the other drive unmarked. "

Ooookaaayy, ah what? and how?  Please and thank you.

I believe you can alter that in the *GParted* application.

---

### Post by Ubuntscrewed on 2008-09-05
john@john-desktop:~$  df /boot
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb5             57393628  28438132  26062996  53% /


john@john-desktop:~$  cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f52a099b-d054-42d0-ac79-fd05715a6950 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f52a099b-d054-42d0-ac79-fd05715a6950 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f52a099b-d054-42d0-ac79-fd05715a6950 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


john@john-desktop:~$  cat /boot/grub/device.map
(hd0)	/dev/sda
john@john-desktop:~$ 


Sorry all the output is strung together like that - I'm a noob to forums too.  Thanks  EDIT I didn't put those smilies there, they are all 8's

---

### Post by Ubuntscrewed on 2008-09-05
> **Pro-reason said:**
> I believe you can alter that in the *GParted* application.

I can't figure out Gparted - I tried to use it to reformat the 80 Gb HDD and I came up wanting, I may be a little "re-gparted in the head" if you know what I mean.  Sorry to be so useless.  Cheers.

---

### Post by MegaJim on 2008-09-05
Grub doesnt' know about your other disk it seems, you should add the line
```
(hd1) /dev/sdb
``` to the bottom of your devices.map

then change the entry for windows to read

```
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
chainloader +1

```

---

### Post by Ubuntscrewed on 2008-09-05
> **MegaJim said:**
> Grub doesnt' know about your other disk it seems, you should add the line
```
(hd1) /dev/sdb
``` to the bottom of your devices.map

then change the entry for windows to read

```
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
chainloader +1

```

I would love to.  Could you tell me how, sorta step-by-step.  I'm real green down here.  Thanks.

---

### Post by MegaJim on 2008-09-05
Sure, open up a terminal then type
```
gksu gedit /boot/grub/device.map
``` make changes [paste in "(hd1) /dev/sdb" without quotes on a new line], save, then type
```
gksu gedit /boot/grub/menu.lst
``` find the section at the bottom for your windows OS and change hd0 to hd1, save and close, then reboot and see if windows works

---

### Post by Ubuntscrewed on 2008-09-05
Made change to Windows entry, rebooted, same error.  I confirmed that the change held, both alterations are there as per your instructions.  Thanks.  Is there anything else we could try?

---

### Post by MegaJim on 2008-09-05
It sounds like your windows filesystem is damaged, if you still have your windows CD, boot into it, go to the recovery console and run chkdsk

---

### Post by Ubuntscrewed on 2008-09-05
Ran chkdsk and was told "volume appears to be in good condition chdkdsk not run.  Use /p to run chkdsk anyway."  Stupidly, I typed "/p" and was informed that "/p" is not a valid command.  Any ideas on what command I should type in order to force chkdsk.

---

### Post by MegaJim on 2008-09-05
[http://technet.microsoft.com/en-us/library/bb491051.aspx](http://technet.microsoft.com/en-us/library/bb491051.aspx)

---

### Post by Pro-reason on 2008-09-05
```

CHKDSK /p

```

---

### Post by Ubuntscrewed on 2008-09-05
Thanks for the info.  I managed to run chkdsk and it discovered one or more errors.  It, of course, didn't advise what these errors are nor how to go about repairing them.  I'm wading through the MStechnet pages but am finding them verbose yet bereft of practical information.  Does anyone know where I should go from here?  

I'm willing to reinstall the Windows OS to it's existing (Ubuntu created) partition but don't want to lose Ubuntu in the process, as my wife will kill me if I knock us offline again.  I'm already sleeping on the couch.  Please help if you can.  Thanks.

---

### Post by MegaJim on 2008-09-05
run chkdsk /r

---

### Post by Pro-reason on 2008-09-05
Run it with **/r** to repair.

---

### Post by Ubuntscrewed on 2008-09-05
chkdsk /r finished.  No change, I still get the same error.  I have to sleep now but look forward to a solution tomorrow.  Thank you for all the help thus far.  See you in about 8 hours.  Cheers

---

### Post by plucky on 2008-09-05
> Please help if you can. Thanks. 

Unplug the 80Gb drive and then change the BIOS to boot from HD0 and see if XP and Ubuntu will boot.

If it does,then I think you will have to fool XP into thinking it is on HD0 instead of HD1,as windows doesn't play well on drives that aren't HD0.

I am assuming that the 80Gb drive is IDE and not sata.


Good Luck

p.s Hope you slept well!

---

### Post by Ubuntscrewed on 2008-09-05
Progress I think...  Unplugged 80 Gb (IDE or ATA) HDD.  Windows still won't boot but I get a new error message...ERROR 21: Selected Drive Does Not Exist - press any key to continue.

I also poked around my bios and I don't see any way to make suggested change, it only shows my 250 Gb Sata drive, which is now moved to IDE Channel 0 master, it used to be on IDE channel 2 master.  

I feel like we're moving forward.  Please don't give up.  And thank you.

---

### Post by plucky on 2008-09-06
> Progress I think... Unplugged 80 Gb (IDE or ATA) HDD. Windows still won't boot but I get a new error message...ERROR 21: Selected Drive Does Not Exist - press any key to continue.


Can you boot Ubuntu? Probably not as > cat /boot/grub/device.map
(hd0) /dev/sda

So plug the 80Gb drive back in and boot Ubuntu and change the entry to boot windows.See this [link](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands) for how to make windows think it is on the first hard drive.


Good Luck

---

### Post by roscal on 2008-09-06
Unplug all your hd except the 250 sata.
ReInstall windows on a partition of your choosing.
Install Linux/Kubuntu/ on the remaining space. 
Easiest way, I believe.
:popcorn:

---

### Post by Ubuntscrewed on 2008-09-06
Sorry I'm a wee bit confused...Just to re-cap, only the 250 Gb Sata hdd is currently plugged in.  Windows has the lion's share of the hdd (about 188 Gb) and Ubuntu has the remaining 57 GB.  Windows refuses to boot under any circumstance.  Ubuntu, god bless, will boot happily from grub loader or Super Grub Disc.

I'd be happy to reinstall Windows on its partition.  Is that possible to do without interfering with the Ubuntu side of the partition?  If so, how?  I only ask because my wife and daughter will disown me if I stuff up the internet.  And until I get Windows operational, I'm relegated to the couch.  I miss my bed, please help.  Cheers.

Edit:  I also did some tinkering with SGD and now I get a new error when trying to boot XP  "Error 12:  Invalid device requested - Press any key to continue."

---

### Post by caljohnsmith on 2008-09-06
Ubuntscrewed, in your original post you said:
[QUOTE=Ubuntuscrewed]I installed Hardy Heron on my 250 Gb Sata HDD concurrently (dual boot) with existing Windows XP Home OS, allowing Ubuntu to partition my HDD. Since install, I have been unable to boot into XP.[/QUOTE]
So just to clarify, the Windows you are trying to boot is on the same HDD as Ubuntu, correct? Because if that is true, I think MegaJim misunderstood your problem and gave you advice trying to help you boot Windows from your other HDD. Now that chkdsk helped you repair some of your Windows problems, your Windows might be fine, but unfortunately your menu.lst needs to be corrected. Try the following:
```
gksudo gedit /boot/grub/menu.lst &
```
That will open up your Grub's menu.lst, so scroll to the bottom and change your Windows entry to:
```
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1
```
Save, and reboot. If you get any errors now, they should all be Windows related, and not a problem with Grub. But let us know what happens and we can go from there. :)

---

### Post by Ubuntscrewed on 2008-09-07
Caljohnsmith, you are correct, Windows and Ubuntu share the same HDD.  I made the change you suggested, and I'm back to the original error of "A disk read error occurred. Press blah, etc., blah to restart"  Sorry I've been slow to respond, it's Father's day here in Australia (silly huh?) and I've just gotten the last of the family off to bed.

So where to now people?  Do we have any other options?  Since Windows worked fine before the Ubuntu install, I'm concerned that the same problem will happen again if I wipe the entire HDD and start anew.  My preference, barring a miraculous Windows recovery, is to just re-install XP in its existing partition, but I can ill afford to lose both OS's.  We tried using Windows to partition another HDD (prior to a clean install) on different a computer and Ubuntu refused to install in the Windows made partition.  So, I leave my dilemma in your capable hands.  Thank you.

To reiterate for the sake of clarity, my questions are...

Is there anything left to try?

Can XP be re-installed into its existing (Ubuntu created) partition?  If so, would this be harder (riskier) than wiping the entire drive and starting over?  

If anyone lives near the Gold Coast, Queensland, would you like to come over and show me how?  I've got beer!  Cheers.

---

### Post by caljohnsmith on 2008-09-07
That "disk read error" you are getting definitely sounds like a Windows error, so I don't think your problem is with Grub any more. But if "chkdsk" didn't help, you might not be able to recover your Windows. But since you all ready said you don't mind reinstalling Windows, that is probably your best option at this point. But before doing so, I would run some tests to make sure your HDD's partition table is OK and your HDD's overall health is OK. From within Ubuntu, try the following:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen.

Also, to check your HDD's health:
```
sudo apt-get install smartmontools
sudo smartctl -H /dev/sdb
```
The second command will give your HDDs current health as pass/fail based on the last self-tests it ran. Next tell your HDD to run a self-test to check its current health:
```
sudo smartctl -t long /dev/sdb
```
That command will immediately terminate while your HDD starts its self-testing. You can monitor the progress of the test with:
```
sudo smartctl -a /dev/sdb
```
Let us know how that goes, and if the results are good, then I would go ahead and reinstall Windows.
[QUOTE=Ubuntscrewed]Can XP be re-installed into its existing (Ubuntu created) partition? If so, would this be harder (riskier) than wiping the entire drive and starting over?[/QUOTE]
Yes, Win XP should be able to reinstall into that partition you all ready have for it. You should not need to wipe your HDD clean if the above tests show your HDD to be in good health. :)

---

### Post by Ubuntscrewed on 2008-09-07
Hey Caljohn thank you...ummm before I hit proceed from analyze I happened to see this:
Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)
 1 * HPFS - NTFS              0   1  1 22885 254 63  367663527
 2 E extended             22886   0  1 30400 254 63  120728475
 5 L Linux                22886   1  1 30087 254 63  115700067
   X extended             30088   0  1 30400 254 63    5028345
 6 L Linux Swap           30088   1  1 30400 254 63    5028282

Is that warning par for the course???  Should I do a back-up before I let this thing rip?

---

### Post by caljohnsmith on 2008-09-07
About that warning, I don't think it is anything serious as I get the exact same warning for my Windows on my HDD (I don't know the technical details about it). Your partition structure looks fine, so you can just quit testdisk (hit "q" multiple times), and proceed with the HDD tests. Let me know how it goes.

---

### Post by Ubuntscrewed on 2008-09-07
Woops.  I had quickly ripped my bookmarks over to my USB chip and didn't unmount it prior to running the first HDD test.  I got an error that mentioned my chip, so I closed the terminal window, unmounted the chip and re-ran the command. Now I get the following:

john@john-desktop:~$ sudo smartctl -H /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory

john@john-desktop:~$ sudo smartctl -t long /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory

john@john-desktop:~$ sudo smartctl -a /dev/sdb
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl open device: /dev/sdb failed: No such file or directory

Yikes.  Is that bad?

---

### Post by caljohnsmith on 2008-09-07
Yes, of course, my mistake; I was going by your original post that showed your 250 GB drive to be "sdb", but you later unplugged your 80 GB drive, so now the 250 GB drive is "sda". Just replace sdb with sda in all those commands and you should be fine.

---

### Post by Ubuntscrewed on 2008-09-07
Ok that worked here's the output:

john@john-desktop:~$ sudo smartctl -H /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
Please note the following marginal Attributes:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
255 Unknown_Attribute       0x373f   200   016   063    Pre-fail  Always   In_the_past 69278536062464
 81 Unknown_Attribute       0x3057   052   056   087    Pre-fail  Always   FAILING_NOW 35322351334705
 32 Unknown_Attribute       0x0320   000   000   032    Old_age   Offline  FAILING_NOW 53078413804608
 68 Unknown_Attribute       0x3548   050   072   072    Old_age   Offline  FAILING_NOW 35322352771120
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 35322350018592
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 550026354720
255 Unknown_Attribute       0x000f   000   007   015    Pre-fail  Always   FAILING_NOW 131943408599808
120 Unknown_Attribute       0x7800   000   000   000    Old_age   Offline  FAILING_NOW 0
104 Unknown_Attribute       0x0174   188   035   116    Old_age   Offline  In_the_past 27488214384449

john@john-desktop:~$ sudo smartctl -t long /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF OFFLINE IMMEDIATE AND SELF-TEST SECTION ===
Warning: device does not support Self-Test functions.

Sending command: "Execute SMART Extended self-test routine immediately in off-line mode".
Drive command "Execute SMART Extended self-test routine immediately in off-line mode" successful.
Testing has begun.
john@john-desktop:~$ sudo smartctl -a /dev/sda
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD250HJ
Serial Number:    S0URJDWQ401845
Firmware Version: FH100-06
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Sun Sep  7 23:38:19 2008 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Disabled

Warning! SMART Attribute Data Structure error: invalid SMART checksum.
Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x0e)	Offline data collection activity
					is in a Reserved state
.
					Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection: 		 (15104) seconds.
Offline data collection
capabilities: 			 (0x02) No SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					No Offline surface scan supported.
					No Self-test supported.
					No Conveyance Self-test supported.
					No Selective Self-test supported.
SMART capabilities:            (0x5f00)	Does not save SMART data before
					entering power-saving mode.
Error logging capability:        (0x0d)	Error logging supported.
					General Purpose Logging supported.

SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       1060314912768
180 Unknown_Attribute       0x00df   000   000   223    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
254 Unknown_Attribute       0xc0f6   163   246   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x9800   180   229   000    Old_age   Offline      -       1030653280502
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       1060516730880
250 Read_Error_Retry_Rate   0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
237 Unknown_Attribute       0x80f6   106   251   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x1800   224   238   000    Old_age   Offline      -       1062379094262
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       71429283682304
245 Unknown_Attribute       0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
240 Head_Flying_Hours       0x00f6   153   070   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x9800   010   242   000    Old_age   Offline      -       960029098230
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       1060680603648
 14 Unknown_Attribute       0x0000   170   153   000    Old_age   Offline      -       11160715266
153 Unknown_Attribute       0x0002   003   014   002    Old_age   Always       -       11160715264
 13 Read_Soft_Error_Rate    0x0000   048   154   000    Old_age   Offline      -       235077634
153 Unknown_Attribute       0x0002   195   013   002    Old_age   Always       -       11167989760
153 Unknown_Attribute       0x0002   147   153   002    Old_age   Always       -       234881026
152 Unknown_Attribute       0x0002   195   013   002    Old_age   Always       -       11167989760

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 0
No Errors Logged

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging
john@john-desktop:~$ 

Seems to be a lot of failing going on.  Glad to see it's also able to "pre-fail".  I noticed the SMART capability in the bios, which came disabled.  I have the power to enable it I think, I just don't know what that means.  Anyway, does any of this help???  Thanks again mate.

---

### Post by caljohnsmith on 2008-09-07
OK, looks like you've got a Samsung HDD, and because they don't adhere to the exact S.M.A.R.T. standard that all other HDDs do, you have to use one of the following instead of what we tried previously:
```
sudo smartctl -a -F samsung /dev/sda
sudo smartctl -a -F samsung2 /dev/sda
sudo smartctl -a -F samsung3 /dev/sda
```
That's going to be alot of output, so when you post it, highlight it all and then click the pound sign graphic "#" in your message box to put "code" tags around it and make it more viewable.

---

### Post by Ubuntscrewed on 2008-09-07
Cheers for the "code" tip and all the research you must be doing on your end on my behalf.  You people amaze me.  Thank you so much.

```
=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD250HJ
Serial Number:    S0URJDWQ401845
Firmware Version: FH100-06
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Mon Sep  8 00:08:33 2008 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Disabled

Warning! SMART Attribute Data Structure error: invalid SMART checksum.
Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0xf5)	Offline data collection activity
					is in a Vendor Specific state
.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 117)	The previous self-test completed having
					the read element of the test failed.
Total time to complete Offline 
data collection: 		 (27178) seconds.
Offline data collection
capabilities: 			 (0xff) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Abort Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0000)	Automatic saving of SMART data					is not implemented.
Error logging capability:        (0x00)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   1) minutes.
Extended self-test routine
recommended polling time: 	 (   0) minutes.
Conveyance self-test routine
recommended polling time: 	 ( 223) minutes.

SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       212166547445760
 80 Unknown_Attribute       0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 167126304423936
 20 Unknown_Attribute       0xc0ef   163   246   239    Pre-fail  Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x9800   180   229   000    Old_age   Offline      -       1030653280502
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       1060516730880
250 Read_Error_Retry_Rate   0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
237 Unknown_Attribute       0x80f6   106   251   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x1800   224   238   000    Old_age   Offline      -       1062379094262
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       71429283682304
245 Unknown_Attribute       0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
240 Head_Flying_Hours       0x00f6   153   070   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x9800   010   242   000    Old_age   Offline      -       960029098230
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       2160192231424
 39 Unknown_Attribute       0x1c03   033   039   003    Pre-fail  Always       -       28587302322179
 39 Unknown_Attribute       0x0003   000   000   003    Pre-fail  Always   FAILING_NOW 1099511627776
 39 Unknown_Attribute       0x3603   007   002   003    Pre-fail  Always   In_the_past 170437843688192
  9 Power_On_Hours          0x0300   033   039   000    Old_age   Offline      -       212219285543427

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 0
No Errors Logged

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 0
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Warning! SMART Selective Self-Test Log Structure error: invalid SMART checksum.
SMART Selective Self-Test Log Data Structure Revision Number (0) should be 1
SMART Selective self-test log data structure revision number 0
Warning: ATA Specification requires selective self-test log data structure revision number = 1
 SPAN              MIN_LBA               MAX_LBA  CURRENT_TEST_STATUS
    1  6971833706434527232   7331860193359228898  Not_testing
    2    72268779175868162  12796978478645772304  Not_testing
    3      263130479392479   6854750222526971904  Not_testing
    4   144115256812158994  11799693895801503776  Not_testing
    5  7331860193359228918     72268779175868162  Not_testing
 7039   227186718939480648    227186718939546183  Read_scanning is in a Vendor Specific state

Selective self-test flags (0x327):
  After scanning selected spans, read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

john@john-desktop:~$ 
```

You weren't kidding about the volume of output, hope that's got it. Ta (Aussie for thanks)

---

### Post by caljohnsmith on 2008-09-07
> **Ubuntscrewed said:**
> Cheers for the "code" tip and all the research you must be doing on your end on my behalf.  You people amaze me.  Thank you so much.
You're welcome, hope we can get you to the point where you can use either Windows or Ubuntu. :)
[QUOTE=Ubuntscrewed]
```
...
General SMART Values:
Offline data collection status:  (0xf5)	Offline data collection activity
					is in a Vendor Specific state
.
					Auto Offline Data Collection: Enabled.
Self-test execution status:      ( 117)	[COLOR="Red"]The previous self-test completed having
					the read element of the test failed.[/COLOR]

```
[/QUOTE]
So did you try all three commands and they all gave the above result? Or which command gave the above result? I'm concerned it says the "read element of the test failed", but it still lists your HDD's health as "passed"; that error may not be related to your HDD's integrity but rather a limitation of your Samsung drive's SMART capabilities. Do you have a HDD diagnostics CD that came with your HDD? If you do and it is bootable, run that and let me know the results. Otherwise, I would go ahead and reinstall Windows. If Windows installs successfully, it will overwrite Grub in the master boot record (MBR) of your HDD, and you won't be able to boot Ubuntu any more. The fix is easy though; just boot up your Ubuntu Live CD and do the following:
```
sudo grub
grub> find /boot/grub/stage1
[COLOR="Blue"][should return your Ubuntu partition in the form (hdX,Y), use that:][/COLOR]
grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That will reinstall Grub to the MBR, and you should be able to boot Ubuntu or Windows fine. If not, we can help you tweak your Grub's menu.lst if it needs it. Let us know how it goes. :)

---

### Post by Ubuntscrewed on 2008-09-07
I ran all three commands last night and only one seemed to have any real output, however, when I re-ran the commands this morning I seemed to get a different result.  So The following is the result of all three:

sudo smartctl -a -F samsung /dev/sda

```
john@john-desktop:~$ sudo smartctl -a -F samsung /dev/sda
[sudo] password for john: 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD250HJ
Serial Number:    S0URJDWQ401845
Firmware Version: FH100-06
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Mon Sep  8 10:27:17 2008 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Disabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection: 		 (   0) seconds.
Offline data collection
capabilities: 			 (0x00) 	Offline data collection not supported.
SMART capabilities:            (0x0000)	Automatic saving of SMART data					is not implemented.
Error logging capability:        (0x00)	Error logging supported.
					General Purpose Logging supported.

SMART Attributes Data Structure revision number: 64
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
255 Unknown_Attribute       0x373f   200   016   063    Pre-fail  Always   In_the_past 69278536062464
 81 Unknown_Attribute       0x3057   052   056   087    Pre-fail  Always   FAILING_NOW 35322351334705
 32 Unknown_Attribute       0x0320   000   000   032    Old_age   Offline  FAILING_NOW 53078413804608
 45 Unknown_Attribute       0x3630   048   065   048    Old_age   Offline  FAILING_NOW 35550757999443
 68 Unknown_Attribute       0x3548   050   072   072    Old_age   Offline  FAILING_NOW 35322352771120
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 35322350018592
 32 Unknown_Attribute       0x2020   032   032   032    Old_age   Offline  FAILING_NOW 550026354720
 16 Unknown_Attribute       0x3f00   000   016   000    Old_age   Offline  FAILING_NOW 280380028550140
255 Unknown_Attribute       0x000f   000   007   015    Pre-fail  Always   FAILING_NOW 131943408599808
120 Unknown_Attribute       0x7800   000   000   000    Old_age   Offline  FAILING_NOW 0
 64 Unknown_Attribute       0xf800   000   082   000    Old_age   Offline  FAILING_NOW 39028526443264
104 Unknown_Attribute       0x0174   188   035   116    Old_age   Offline  In_the_past 27488214384449

SMART Error Log Version: 64
No Errors Logged

SMART Self-test log structure revision number 64
No self-tests have been logged.  [To run self-tests, use: smartctl -t]


Device does not support Selective Self Tests/Logging
```

Output for  sudo smartctl -a -F samsung2 /dev/sda:
```

john@john-desktop:~$ sudo smartctl -a -F samsung2 /dev/sda
[sudo] password for john: 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD250HJ
Serial Number:    S0URJDWQ401845
Firmware Version: FH100-06
User Capacity:    250,059,350,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   7
ATA Standard is:  Not recognized. Minor revision code: 0x52
Local Time is:    Mon Sep  8 10:25:41 2008 EST

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Disabled

Warning! SMART Attribute Data Structure error: invalid SMART checksum.
Warning! SMART Attribute Thresholds Structure error: invalid SMART checksum.
=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
See vendor-specific Attribute list for marginal Attributes.

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Total time to complete Offline 
data collection: 		 (2203) seconds.
Offline data collection
capabilities: 			 (0x00) 	Offline data collection not supported.
SMART capabilities:            (0xe503)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x29)	Error logging supported.
					General Purpose Logging supported.

SMART Attributes Data Structure revision number: 0
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       1060314912768
 78 Unknown_Attribute       0x00f7   000   000   247    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
148 Unknown_Attribute       0xc0ee   163   246   238    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x9800   180   229   000    Old_age   Offline      -       1030653280502
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       1060516730880
250 Read_Error_Retry_Rate   0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
237 Unknown_Attribute       0x80f6   106   251   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x1800   224   238   000    Old_age   Offline      -       1062379094262
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       71429283682304
245 Unknown_Attribute       0x00ef   000   000   239    Pre-fail  Always   FAILING_NOW 36245269233664
 18 Unknown_Attribute       0x00c0   001   016   192    Old_age   Offline  FAILING_NOW 26388816068608
240 Head_Flying_Hours       0x00f6   153   070   246    Old_age   Always   FAILING_NOW 211106232533231
  2 Throughput_Performance  0x20f7   095   018   247    Pre-fail  Always   FAILING_NOW 268501184
 32 Unknown_Attribute       0x9800   010   242   000    Old_age   Offline      -       960029098230
 16 Unknown_Attribute       0x0000   002   032   000    Old_age   Offline      -       98917215475712
 41 Unknown_Attribute       0x8103   189   041   003    Pre-fail  Always       -       16778243
201 Soft_Read_Error_Rate    0xb7ff   193   203   255    Pre-fail  Always   FAILING_NOW 171522937436159
  6 Read_Channel_Margin     0x5a00   229   041   000    Old_age   Offline      -       59387215698179
  4 Start_Stop_Count        0x5a00   229   041   000    Old_age   Offline      -       1099511628035

Warning! SMART ATA Error Log Structure error: invalid SMART checksum.
SMART Error Log Version: 0
No Errors Logged

Warning! SMART Self-Test Log Structure error: invalid SMART checksum.
SMART Self-test log structure revision number 0
Warning: ATA Specification requires self-test log structure revision number = 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Vendor offline      Self-test routine in progress 60%     27264         -
# 2  Vendor offline      Unknown/reserved test status  150%         0         -
# 3  Offline             Completed without error       00%     26048         -
# 4  Extended offline    Self-test routine in progress 70%     24352         -
# 5  Reserved offline    Unknown/reserved test status  00%       256         -
# 6  Reserved offline    Completed without error       00%       512         -
# 7  Offline             Completed without error       00%     45344         -
# 8  Reserved offline    Completed without error       00%     58715         -
# 9  Reserved offline    Completed without error       30%      1179         -
#10  Vendor offline      Self-test routine in progress 150%         0         -
#11  Extended offline    Completed without error       00%     58713         -
#12  Offline             Completed without error       00%         0         -
#13  Offline             Completed without error       00%      2203         -
#14  Offline             Completed without error       00%       256         -
#15  Vendor offline      Self-test routine in progress 150%     49591         -
#16  Reserved offline    Completed without error       30%     48513         -
#17  Offline             Completed without error       00%     26048         -
#18  Extended offline    Self-test routine in progress 70%     24352         -
#19  Reserved offline    Unknown/reserved test status  00%       256         -
#20  Reserved offline    Completed without error       00%       512         -
#21  Reserved offline    Completed without error       00%     57368         -

Device does not support Selective Self Tests/Logging

```

Output for sudo smartctl -a -F samsung3 /dev/sda:

```
john@john-desktop:~$ sudo smartctl -a -F samsung3 /dev/sda
[sudo] password for john: 
smartctl version 5.37 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=======> INVALID ARGUMENT TO -F: samsung3
=======> VALID ARGUMENTS ARE: none, samsung, samsung2 <=======

Use smartctl -h to get a usage summary

```

I could have sworn last night that it was only the first one that worked.  I must have done something wrong.  I hope this covers it.

After checking the discs that came with this computer, it appears that I only have the Gigabyte Mobo drivers discs.  They have a feature that appears during start up called "Xpress2 Recovery."  Could that be something of value?  I have a fear that it might strip my system back to default, mess up the Ubuntu install and possibly cause my wife to leave me.  Thanks.

---

### Post by caljohnsmith on 2008-09-07
From what I can tell from the output you posted, your HDD looks like it is OK. 
> **Ubuntscrewed said:**
> 
After checking the discs that came with this computer, it appears that I only have the Gigabyte Mobo drivers discs.  They have a feature that appears during start up called "Xpress2 Recovery."  Could that be something of value?  I have a fear that it might strip my system back to default, mess up the Ubuntu install and possibly cause my wife to leave me.  Thanks.
I definitely wouldn't run that "Xpress2 Recovery" as that doesn't sound like it will do any HDD diagnostics, and besides, we don't want to risk causing your wife to leave you. :)

I would go ahead and reinstall Windows. Just make sure you install it to the first partition since that is where you currently have Windows. Once you have it installed, go ahead and boot it just to make sure it works OK; once you are sure Windows is OK, you can reinstall Grub to the MBR using the directions from post #35. Let me know how it goes, or if you run into any problems or have further questions.

---

### Post by Ubuntscrewed on 2008-09-08
All systems go!  That did it.  Caljohnsmith you are a life saver.  I'll be able to sleep in my own bed tonight.

For any Noobs who are suffering the same problem and doing the XP re-install here's what I did...

1. Chose fresh install of XP.
2. Chose Repair existing install - and wasted 20 minutes - DON'T BOTHER!
3. Reformatted XP partition the slow "non-quick" option
4. Installed XP
5. Ran Ubuntu Live CD and followed steps in post #35.  Note: X,Y represents the numbers you get back after running the "find /boot/grub/stage1" command.  Probably obvious to anyone who isn't me.
6. Do a little dance when it all works perfectly!
7. Pray that Bill Gates' path to happiness is as easy as repairing a faulty Windows partition.


Thanks to all who helped, you people are fantastic.  Cheers.

---

### Post by caljohnsmith on 2008-09-08
Glad everything is working for you again! Cheers. :)

---

