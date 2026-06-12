---
title: "dual boot grub error 21 nighmare"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by PierreRussellStraddler on 2008-11-26
Hello!

Another newbie install problem nighmare!:lolflag:

The whole sordid story can be found here:

[https://answers.launchpad.net/ubuntu/+source/grub/+question/52422](https://answers.launchpad.net/ubuntu/+source/grub/+question/52422)

here's the short version:

Two hard drives, internal and external.

Internal 40gb hard drive has windows XP.  
External 300gb USB hard drive had about 20gb of back up files from the internal winXP hard drive

the plan was to set up a "dual boot" where, ideally, I would be given the Windows or Linux choice upon start up (kind of like what Super Grub Disk apparently offers.)

After installing Ubuntu on the external hard-drive, I re-booted and got nothing...the black screen of confusion, GRUB ERROR 21 wondering where everything was.

I have tried to point the bios to that point on the hard drive where (apparently) Ubuntu lives.  Still nothing happens, and by nothing, I mean more black screen of confusion and silence. (not even a grub 21 error...just nothing)

Like a fool, I re-installed ubuntu to the hard drive.  Apparently I was successful at that also--two successful ubuntu downloads to the hard drive.

When the external hard drive is plugged in, regardless of how the bios is set, nothing happens.  when the hard drive is not plugged in, and the bios is set to "CDROM"as it's first place to check, the live CD boots fine.

When I am up and running in the liveCD/ubuntu setting, I can re-plug in my external hard drive and all of a sudden, the external hard drive partitions where ubuntu is installed (twice) appear on the desk top.

here are some numbers and figures:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks ID System
/dev/sda1 * 1 4862 39053983+ C w95 FAT 32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device     Boot   Start End    Blocks      ID  System
/dev/sdb1         1     5093   40949653+   C   w95 FAT32 (LBA)
/dev/sdb2         5099  38913  271618987+  5   Extended
/dev/sdb5 *       5099  23087  14496611    83  Linux
/dev/sdb6         38726 38913  1510078+    82  Linux swap / Solaris
/dev/sdb7         23088 38537  124102093+  83  Linux
/dev/sdb8         38538 38725  1510078+    82  Linux swap / Solaris

grub> find /boot/grub/stage1
  (hd1, 4)
  (hd1, 6)


this fix was tried

sudo grub
root (hd1,4)
setup (hd1)
exit

and this also did nothing.

Does the fact that the first part of the external hard drive (1 - 5093) are "w95FAT" have anything to do with the computers inability to find the grub on the external hard drive?

P L E A S E S O M E O N E H E L P!

Thank you,

PRS

---

### Post by newbuntuxx on 2008-11-26
When you get the black screen with error 21, press the letter (e) for edit, and edit the root (hdx,x) with the following:

root (hd1,4)

then hit enter, and then type "boot" and hit enter

see if that works, if not, try:

(hd1,6)

---

### Post by Keen101 on 2008-11-26
I'm inclined to think the default install put GRUB on your internal drive. If you need to restore the windows MBR, which you seem to have tried with the windows cd and failed. Then try the **Super Grub Disk**, i've used it to restore the MBR on at least two computers. [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Also, try isong the live-cd and trying "boot from first hard drive" and see what happens. If it boots windows then GRUB is not on the internal drive. if it fails, try unplugging the internal drive and try "boot from first hard drive" again, and see if it access the external drive and ubuntu. IF not, well... phooey.

I would recommend trying to update your BIOS, as some older computers claim to be able to boot from usb drives, but only boot from external fat32 drives, which is weird. How old is your computer? If you need to delete the ubuntu on external, and try again use the gparted live-cd. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

next time you install to an external drive i recommend unplugging the internal drive before you begin. That way GRUB only has one choice to install to. IF you system doesn't boot from external after that, it would be clearly a BIOS issue.

---

### Post by PierreRussellStraddler on 2008-11-26
Hiya

Please bear with me as I learn how to use the reply function in an internet forum!

newbuntuxx:  This didn't work.  Once the grub error 21 comes up, that's it...no nothing.  I pressed all the buttons, and many buttons in combination with "e" and nothing, and so I couldn't type anything after that.  

Keen101:  "I'm inclined to think the default install put GRUB on your internal drive."

Just now, I booted up the computer with the liveCD and the USB HD unplugged (because nothing happens at boot when the USB HD is plugged in...even if it is 3rd on the boot list in bios.)

Once Ubuntu was up and running, I plugged in the USB HD.  All three partitions appeared on the hard drive.  When the 41.9 GB partition came up, so did a screen saying

This medium contains software intended to be automatically started.  Would you like to run it?

I say YES!

then:  Error starting autorun program:  Permission denied.


later, when I double click on the folder icon for said 41.9GB partition, there is a message at the top of the folder screen that says

"the media contains software"


now...when I double click on the internal hard drive icon, I can see all my old files (and can access them using "open office") but I don't get any similar message about the internal hard drive containing any software.

how does that make you feel?

lastly, my computer is ancient...from 1998!  It got a new cpu some time in the 21 century... 1.3mhz?  Something like that.

Is there a way to update the bios?

speaking of bios, here is now mine is set right at this very moment:

first bood device:         CD ROM
2nd boot device:           IDE-O
3rd boot device            USB HDD
try other boot devices     Yes
S.M.A.R.T. for Hard Disks  Disabled
Boot Up Num-Lock           ON
Floppy drive swap          Disabled
floppy drive seek          disabled
boot to os/2>64mb          NO
L1 cache                   enabled
L2 cache                   enabled
system bios cacheable      enabled
CLK GEN spread spectrum    disabled
DOS flat mode              disabled
Dram Driver Slew Rating    normal
S2K 1/0 compensation       disabled
memory termination         disabled

so that is that...maybe it is a BIOS thing afterall...

thank you both for you help.

PRS

---

### Post by caljohnsmith on 2008-11-26
How about changing your BIOS to boot the USB drive first, and then you can install Grub to the USB drive to make it bootable. Then you can add an entry for Windows in your Grub menu and boot both Ubuntu and Windows from Grub. If that sounds good to you, then first do these steps from the Live CD in a terminal (Applications > Accessories > Terminal):
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then you should be able to boot the USB drive and at least get the Grub menu on start up. See if you can get that far and we can work from there, or let me know if you run into problems. :)

---

### Post by PierreRussellStraddler on 2008-11-26
Hello caljohnsmith

Your fix idea wherein I could to boot windows or linux via the linux grub on my external hard drive is a fine idea.

The problem seems to be getting the USB to be the boot drive.

I did this

grub> find /boot/grub/stage1
(hd1, 4)
(hd1, 6)


and then this was tried

sudo grub
root (hd1,4)
setup (hd1)
exit

as was this

root (hd1,6)
setup (hd1)
exit

and neither worked.

If I turn the computer on with the USB HD plugged in, nothing happens at all...I can't even access the liveCD--regardless of where CDROM is in the boot order (said another way, the CD Rom can be first in the bios boot order, but if the USB HD is plugged in, it won't boot from the live CD)

I would be "totally stoked" if upon turning on the computer, the USB HD was accessed and from there the choice to boot Ubuntu or Windows would appear.  Not that I have any real interest or desire to run windows all that often...quite the opposite infact.  Once I really understand linux and hard drive partitions and what not, I intend to remove every single zero and one speck of windows nonsense from my life forever, but in the meantime, I might have to run photo shop or windows media player one last time.

There has been some speculation that because my computer is from the 20th century (1998-9) the Bios might be the problem in that it (the bios) won't let me boot from my hard drive (a new western digital "book" model USB hard drive.  Can a bios be replaced, or set differently so that the USB HD can be read as the boot drive?



Thanks for your thoughts on this,

PRS

---

### Post by caljohnsmith on 2008-11-26
It sounds like your BIOS might not support booting from a USB drive; if you go to the manufacturer's website of your motherboard, there is probably a newer BIOS version available (since your computer is older), but whether the newer BIOS supports booting USB devices you will have to check their notes/documentation first. There is a boot manager called "PLoP" that is supposed to be able to boot USB drives even if the BIOS does not support it, and I've heard some people having success with it. Or another option is to shrink your Windows partition by only 200 MB, and create an ext3 partition with that space to use for Ubuntu's /boot directory; that way you can boot Ubuntu from your Windows drive. 

If I were in your shoes, I would first check on whether there are any BIOS updates available for you motherboard that will give you USB booting capability. If that doesn't work, then how about downloading the [Super Grub Disk]("http://www.supergrubdisk.org"), and you can use that to try and boot the USB drive just to see if it will work. But first, after you burn the Super Grub Disk to CD, boot it up, and at the first main menu press "c" to get the command line, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
And please let me know what the results are; the second command should hopefully show the partitions on your USB drive. Anyway, let me know how it goes. :)

---

### Post by PierreRussellStraddler on 2008-11-27
*It sounds like your BIOS might not support booting from a USB drive; if you go to the manufacturer's website of your motherboard, there is probably a newer BIOS version available (since your computer is older), but whether the newer BIOS supports booting USB devices you will have to check their notes/documentation first.*

Yes.  the manufacturer is PCCHIPS.com.tw.  the site wasn't particularly helpful--i didn't down load a new bios out of it.  I did get my bios number.  In so doing I also saw that the bios is from 2000.  I did not find any notes/documentation about anything relevant there. 

other sites that did deal with replacement bios also came with a lot of warnings and caveats, and that frightened me away.


[I]If I were in your shoes, I would first check on whether there are any BIOS updates available for you motherboard that will give you USB booting capability.
[/I]

have not found any thus far...

 *If that doesn't work, then how about downloading the Super Grub Disk, and you can use that to try and boot the USB drive just to see if it will work. But first, after you burn the Super Grub Disk to CD, boot it up, and at the first main menu press "c" to get the command line, and then do:[*

the super grub disk application...what should I save that to?  to a pen drive

[http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB).

or to a floppy?  (a what?)

ok...I'll try the former.  and I'll look more at plop  [http://www.plop.at/](http://www.plop.at/) and try and make some sense out of that


even though I don't have super disk grub yet, I ran this

grub> geometry (hd0)

drive 0x80: C/H/s = 4865/255/63, the number of sectors = 78165360, /dev/sda
  partition num: 0, Fileystem type is fat, partition type 0xc

grub> geometry (hd1)

drive 0x81: C/H/S = 38913/255/63, The number of sectors = 6251142448, /dev/sdb
  Partition num:  0, Filesystem type is fat, partition type 0xc
  Partition num:  4, Filesystem type is ext2fs, partition type 0x83
  Partition num:  5, Filesystem type unknown, partition type 0x82
  Partition num:  6, Filesystem type is ext2fs, partition type 0x83
  Partition num:  7, Filesystem type unknown, partition type 0x82


how does that make you feel?




thanks

prs

---

### Post by gn2 on 2008-11-27
Have you entered the BIOS screen to see if USB is listed as a boot device?

If it's not listed you'll need to use a [USB Boot CD]("http://www.pendrivelinux.com/2008/11/15/usb-boot-cd-for-ubuntu-810/") to boot from the USB drive.

---

### Post by caljohnsmith on 2008-11-27
You can download and burn that Super Grub Disk to CD; you don't have to install it to a USB or floppy if you don't want to. Also, it is important that you run those Grub "geometry" commands from the Super Grub Disk on start up, because Grub sees the order of drives differently on start up than when you run the Grub commands in Ubuntu.

---

### Post by PierreRussellStraddler on 2008-11-27
Hiya!

Gn2:  I have spent all kinds of quality time on the BIOS screen.  There is the option for USB HDD, as well as USB FDD and IDE 1.  I *assume* that I want the USB HDD.  When I put that first in the boot order (and IDE1 second, and cdrom third) the USB HD in question lights up (as if to say "i'm here!") and then goes dark (as if to say "ha ha ha ha!") and then *nothing happens*.  When the USB HD is plugged in at boot time, there is nothing.  Once the system is booted with the liveCD (which is the only way I can boot the computer) I can then plug in the USB HD and see all my files, etc...

caljohnsmith:

when I go to the super grub disk webpage and click on "download CD Rom"  I'm given a choice between download CDROM Mirror #0, CDROM Mirror #1, CDROM Mirror #2.  

Is one better than another?  Do I need to download all three?

Can I download these to a CDROM while I am running Ubuntu from a CDROM?

Would it be easier to download this to my little keychain 1GB stick? 

sooo many questions, I know I know.

Thanks for your help.  Happy thanksgiving if you go that way.

PRS

---

### Post by caljohnsmith on 2008-11-27
One thing I would try before you download the Super Grub Disk would be to change the boot flag on your sdb USB drive, because right now sdb5 (a logical partition) has the boot flag. Some BIOSes will refuse to boot a drive that doesn't have the boot flag set on a primary/extended partition, or more precisely, a partition that's listed in the MBR (Master Boot Record). So how about trying the following first:
```
sudo fdisk /dev/sdb
```
"a" to change the boot flag, "5" for the partition, then again "a" to change the boot flag, "1" for the partition, and finally "w" to write the changes. Then do:
```
sudo fdisk -l
```
And sdb1 should have the boot flag (the asterisk). Then try and boot your USB drive again. If that doesn't work, go ahead and download the Super Grub Disk, and here is a direct link to the [ISO file]("http://forjamari.linex.org/frs/download.php/1119/super_grub_disk_0.9766.iso"). You can burn that ISO file from your Live CD if you first install a CD burning program. I've had best luck with "K3B", so you could try that first:
```
sudo apt-get install k3b
k3b &
```
And be sure to use the "Burn CD image" option and not "New Data CD Project" or anything else. Let me know how it goes or if you run into problems.

---

### Post by tomtom1982 on 2008-11-27
You have to choose ONE of the mirrors.

They are three mirrors because you also can download the file if one of the other isn´t working or overburden.

You can download it to your harddrive and you can burn it on a CD-R or CD-RW (because ROM means ReadOnlyMemory)out of the LiveSystem if you´ve a second drive).

---

### Post by tomtom1982 on 2008-11-27
There´s a burning program at the Ubuntu LiveCD. It should be brasero.

---

### Post by PierreRussellStraddler on 2008-11-27
Caljohnsmith:

> One thing I would try before you download the Super Grub Disk would be to change the boot flag on your sdb USB drive, because right now sdb5 (a logical partition) has the boot flag. Some BIOSes will refuse to boot a drive that doesn't have the boot flag set on a primary/extended partition, or more precisely, a partition that's listed in the MBR (Master Boot Record). So how about trying the following first:
>
> Code:
> ---------
> sudo fdisk /dev/sdb


OK!

I did the above, and this is what I got

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024, and could in certain setups cause problems with:
1) SOFTWARE THAT RUNS AT BOOT TIME (e.g., older versions of LILO)
2) BOOTING AND PARTITIONING SOFTWARE FROM OTHER OSs (e.g., DOS FDISK, OS/2 FDISK)> One thing I would try before you download the Super Grub Disk would be to change the boot flag on your sdb USB drive, because right now sdb5 (a logical partition) has the boot flag. Some BIOSes will refuse to boot a drive that doesn't have the boot flag set on a primary/extended partition, or more precisely, a partition that's listed in the MBR (Master Boot Record). So how about trying the following first:
>
> Code:
> ---------
> sudo fdisk /dev/sdb


OK!

I did the above, and this is what I got

The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024, and could in certain setups cause problems with:
1) Software that runs at boot time (e.g., older versions of LILO)
2) Booting and partitioning software from other OSs (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help)


and then I backed away from the terminal.

does that news change anything?

---

### Post by PierreRussellStraddler on 2008-11-27
sorry to have posted that twice, but you get the picture

tomtom1982:  what's a mirror?  I will look for brasero now.

thanks again to all!

prs

---

### Post by caljohnsmith on 2008-11-27
After doing the fdisk command and getting that prompt:
```
The number of cylinders for this disk is set to 38913.
There is nothing wrong with that, but this is larger than 1024, and could in certain setups cause problems with:
1) Software that runs at boot time (e.g., older versions of LILO)
2) Booting and partitioning software from other OSs (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help):
```
At that prompt type "a" to change the boot flag, "5" for the partition, then again "a" to change the boot flag, "1" for the partition, and finally "w" to write the changes. Try that and let me know how it goes.

---

### Post by PierreRussellStraddler on 2008-11-27
Command (m for help): w
The Partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: devise or resource busy.
The kernel still used the old table.
The new table will be used at the next reboot.
Syncing disks.

THEN I typed in sudo fdisk -l and I got this:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device     Boot      Start    End     Blocks       ID    System
/dev/sda1    *           1      4862   39053983+   C     W95 FAT32 (LBA)

Disk /dev/sdb: 320.GB, 320072933376 bytes

255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


Device     Boot     Start     End      Blocks      ID     SYSTEM
/dev/sdb1   *        1        5098     40949653+    C     W95 FAT32 (LBA)
/dev/sdb2            5099     38913    271618987+   5     Extended
/dev/sdb5            3099     23087    144496611    83    Linux
/dev/sdb6           38726     38913    1510078+     82    Linux swap / solaris
/dev/sdb7           23088     38537    124102093+   83    Linux
/dev/sdb8           38538     38725    1510078+     82    Linux swap / Solaris

Partition table entries are not in disk order





now I am going to try and re-boot.  I'll let you know how it goes.

Thanks

PRS

---

### Post by PierreRussellStraddler on 2008-11-27
re-booted and........

nothing!

if the hd is plugged in, we get to the 'black screen' (the one that usually comes before the other black screen that says "grub error 21") and we freeze there.  The hard drive indicates it is on, it indicates it is being accessed, then it goes dark and nothing happens.

USB HDD #1 in bios
IDE 1 #2 in bios
CD ROM #3 in bios

I am typing to you from the liveCD reality.

:(

does the fact that 1 - 5098 on the USB hard drive is W95 FAT32 make any difference with regards to not being able to boot from the HD?

---

### Post by PierreRussellStraddler on 2008-11-27
> **caljohnsmith said:**
>  If that doesn't work, go ahead and download the Super Grub Disk, and here is a direct link to the [ISO file]("http://forjamari.linex.org/frs/download.php/1119/super_grub_disk_0.9766.iso"). You can burn that ISO file from your Live CD if you first install a CD burning program. I've had best luck with "K3B", so you could try that first:
```
sudo apt-get install k3b
k3b &
```
And be sure to use the "Burn CD image" option and not "New Data CD Project" or anything else. Let me know how it goes or if you run into problems.


I have the ISO on my desk top...but the LiveCD is in the drive where I burn CD's, and when I try to eject it so as to make room for a blank CD, I get an error message.

:confused:

---

### Post by Jesan Fafon on 2008-11-27
Grub 21 and 22 errors are related to the inability of USB hard drives to spin up before the BIOS detects them and begins to boot. Hence, its available in the OS but the BIOS didn't see it to begin with.

I have a similar set-up on my machine and everytime I turn on the computer I get error 21. The easiest solution is to press the power button and turn off the machine, then immediately turn it back on. This should leave your external disk in the "on" state and allow GRUB to load correctly. However, enough changes have been suggested that this may no longer work.:(

-Jesan Fafon

---

### Post by PierreRussellStraddler on 2008-11-28
Hi again.

I downloaded the ISO file for super grub disc.  It's 4.5 meg (is that the right abbreviation?), which is (obviously) too big for a floppy--but I tried anyway, and was unable to get SGD from the desk top to the drive (the floppy wasn't found.)

I put in my 1 GB USB stick (which has 450 meg of free space.)  The folder appeared on the desk top, I could browse the contents, but when it came time to burn the image using brasero (thank you tomtom1982!) I got the message that there was no available medium.

as mentioned, I can't eject the liveCD to make room for a blank CD...

How was thanksgiving?

I am thankful for everyone's help.  Thank you!

PRS

---

### Post by caljohnsmith on 2008-11-28
OK, how about downloading the Super Grub Disk floppy version to your Ubuntu desktop from [here]("http://forjamari.linex.org/frs/download.php/1121/super_grub_disk_english_floppy_0.9766.img"), and then do:
```
sudo dd if=~/Desktop/super_grub_disk_english_floppy_0.9766.img of=/dev/fd0
```
Reboot, and see if you can boot the SGD floppy.

---

### Post by PierreRussellStraddler on 2008-11-28
sudo dd if=~/Desktop/super_grub_disk_english_floppy_0.9766.img of=/dev/fdo
2880+0 records in
2880+0 records out
1474560 bytes (1.5 MB) copied, 0.0336043 s, 43.9 MB/s
ubuntu@ubuntu:~$

so far so good,

rebooted, nothing.

changed bios so IDE0 (internal hard drive) was first in line.  Grub error 21 came up that much faster.

changed bios back to cdrom first in line so I could write this.

sad faced emoticon.

in happier news, I do see there is all kinds of linux software to notate music, sequence midi and do CAD.  Very exciting!  I haven't given up.  

would it be easier to try and get an actual cd of super grub disk?

thank you for your continued help

PRS

---

### Post by PierreRussellStraddler on 2008-12-03
Hello 

Just dropping by to let everyone know this dual boot problem hasn't been resolved and I am still running on the live CD.  I'm not *blaming* anyone, I'm just saying...

It was suggested at some point that Super Grub Disk might be the answer.  That hasn't yet panned out, as I am unable to copy Super Grub Disk on to my pen drive.  If you are interested, the parallel thread is [here]("http://www.supergrubdisk.org/forum/index.php?topic=220").

Maybe the Super Grub Disk scenario will work out, maybe it won't.

In the mean time, here is a question (which may belong under another heading)

To those of you who have been reading this far, does there seem to be a solution in the offing to my dual disk problems, or would it be easier to unplug the USB HDD, return to the original BIOS configuration and try and install Ubuntu on the internal hard drive and take my chances that way?  

It would be nice if Ubuntu would recognize the 13GB of space I made for it and peacefully co-exist with windows XP (for the time being) and not erase the files and other software in the installation process.

I am not deterred yet.

Thank you for your input,

PRS

---

### Post by PierreRussellStraddler on 2008-12-07
Hi again

great news, SGD "worked" in that it fixed my Windows XP MBR, and now I'm writing this from the wonderful Windows XP operating system.  :|

This is comforting and all, but I'd really like to get to that special place where upon booting, I'm given an option of windows (which lives on the internal hard drive) and Ubuntu (which lives in the USB hard drive.)

One thing that still has me troubled is the fact that the computer doesn't boot with the USB hard drive plugged in.  It used to, now it doesn't.  

Anyhow, any suggestions as to how to proceed would be much appreciated.

thanks

p. russell straddler

---

### Post by samsung72 on 2008-12-09
Hi Pierre, having read about your dual boot nightmare I wonder why you did not take the simple way out and install Ubuntu on your main drive alongside Windows. When you select "Install" from the desk top Ubuntu will create a new partition and install itself on that and install the grub boot loader giving you a choice of Windows or Ubuntu at startup which is what you are asking for. Then use your usb hard drive as storage and backup.

 This is what I have been doing for the last year or so. My hard drive is only 20GB but I have Windows XP and Ububtu Hardy Heron installed on it and if either partition gets too full I move the larger files such as videos or music files to the usb hard drive, simple!

If you do decide to install Ubuntu from the live disk it is most important that you first copy or backup any important files to the usb hard drive. Wishing you the best of luck samsung72 :-)

---

### Post by PierreRussellStraddler on 2008-12-09
Hiya

Thank you sumsung72!

That's exacty what I did, and now I'm writing to you from the Ubuntu!

Yaaay!

the installation went totally smooth without error or glitch.  totally excellent.  Linux is blowing my mind and I feel as if life has begun anew!  TRUE!

Thank you to everyone for all their help with this issue.  Yaay Ubuntu Forum, yaay Ubuntu!

PRS

---

