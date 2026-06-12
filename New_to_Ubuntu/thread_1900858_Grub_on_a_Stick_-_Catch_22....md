---
title: "Grub on a Stick - Catch 22..."
date: 2011-12-27
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-12-27
I followed the very clear instructions from Herman's Dual-Boot site to copy my Legacy Grub folder to a USB stick:
[http://members.iinet.net.au/~herman546/p15.html#How_to_add_Grub_to_your_USB_thumb_drive](http://members.iinet.net.au/~herman546/p15.html#How_to_add_Grub_to_your_USB_thumb_drive).

It works fine up to the point where I boot to the USB drive & see its Grub screen.
I know it is that grub screen because I changed the color & timeout.

But when I select any of my Ubuntu kernels, I get:
"Error 22 - no such partition."

I am familiar with error 22 as kernel updates frequently write incorrect addresses to menu.lst - typically (hd0,6) instead of (hd0,5) etc.
But in this case, nothing has changed in my menu.lst's.
My kernels are at (hd0,2) & (hd0,5) in the normal menu.lst & the USB menu.lst.

So what can be causing this problem?

Stabbing in the dark, I tried changing the line:
"root   (hd0,2)" to
"uuid   f5c....."
but then I get "error 15 - file not found"

Hours of Googling have not shed any light.

All clues gratefully accepted!

---

### Post by Paddy Landau on 2011-12-27
I don't know the answer, sorry. But, I'm curious: may I ask why you wish to use Grub legacy? Have you had problems with the Grub 2?

---

### Post by 2CV67 on 2011-12-27
> **Paddy Landau said:**
> I don't know the answer, sorry. But, I'm curious: may I ask why you wish to use Grub legacy? Have you had problems with the Grub 2?

The Devil you know...

I still have Legacy Grub on my old multi-boot PC & don't want to risk changing now.
So when it came to copying Grub to a stick, I automatically copied Legacy.

I am playing with Grub2 on a netbook, but that is another (long) story...

---

### Post by Rhizoid on 2011-12-27
Won't HD0 be the USB stick if you're booting from it?  How about adding another title called Test and use HD1,2 and another HD1,5 - do they work when booting from the USB stick?

---

### Post by 2CV67 on 2011-12-27
Thanks very much, Rhizoid - that seems to work!

At least for my main Ubuntu kernels on (hd0,2) which I changed to (hd1,2) & booted just fine.

Next problem will be to try to boot Windows XP which is on (hd0,0) with a chainloader.
I tried changing menu.lst to (hd1,0) but that just brings me to a "grub> " invite.
I haven't actually started Googling this one yet, but if anybody can short-circuit that...

The actual menu.lst entry for XP, after changing to (hd1,0) looks like this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd1,0)
savedefault
makeactive
chainloader	+1
```

Thanks again for that previous suggestion!

---

### Post by 2CV67 on 2011-12-27
In trying to understand why it didn't work when I changed the line "root   (hd0,2)" to "uuid   f5c...", I went into a grub terminal & typed "uuid" expecting to see a list of UUIDs.
But I got "Error 27:  Unrecognized command".

Looking inside the grub folder, I found a file "installed version" which says "0.97-29ubuntu21".
That seems to be a 2006 version!
SynApt tells me the latest (Legacy) version is 0.97-29ubuntu61-1" and it also tells me I have that version installed...

What should I believe?

---

### Post by oldfred on 2011-12-27
With grub or grub2 the device you boot is hd0, so the drives get reordered when you use BIOS to boot from something other than the first drive. But in Ubuntu the drives will still be sda for first hard drive so hd1 becomes sda. I often had to experiment to see which worked depending on drive used to boot.

You can chainload like you have but if booting Windows from some other than the same drive you usually need the map commands so then the drive gets reordered.

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

```

---

### Post by 2CV67 on 2011-12-28
> map        (hd0) (hd1)
map        (hd1) (hd0)

That fixed it, thanks very much oldfred!
Eliminating "makeactive" in the process...
Just need to catch up on my reading now, to try to understand how/why...

Coming back to my earlier attempts to boot Ubuntu, surely the change from "root (hd0,2)" to "uuid f5c....." should also have worked?

And "uuid" in a grub terminal should produce a list of UUIDs, rather than error 27, shouldn't it?

And if I look inside the grub folder, the files (other than menu.lst) should have dates more recent than 16 Aug 2006 (date I installed 8.04...) shouldn't they?

Does it not look as though grub has never been updated, even though SynApt tells me I have 0.97-29ubuntu61-1?

How can I get (my main PC) LEGACY Grub up-to-date without risking losing all my bootability?
I imagine that might be something like:
- Copy menu.lst to safe place,
- Use SynApt to remove & reinstall Grub.
- Replace new menu.lst by old menu.lst
But I have had so many nasty surprises with booting that I prefer to ask first!

Thanks for your patience & for any further tips!

---

### Post by oldfred on 2011-12-28
Are you not past support so Synaptic will not work anymore?

There are some links to legacy Ubuntu that let you download the last versions, but they are not updated once support stops.

Versions and release & support until dates:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

You could just create a 20GB partition if you have room and do a full install of 10.04. That has grub2 so you can start to learn it. Ubuntu's grub legacy had an update with 9.04 to allow booting from ext4 partitions.

---

### Post by 2CV67 on 2011-12-28
> **oldfred said:**
> Are you not past support so Synaptic will not work anymore?

No - I don't think so.
I am talking about Ubuntu 11.04 on my main PC, which has been regularly upgraded from an 8.04 installation in 2008 & which has had all the updates proposed by Update Manager since then.
I naturally (?) assumed that Legacy Grub was also being updated regularly by update manager (in fact SynApt says it is) though I never thought to check that.
I have refused the upgrade to Grub2 at several recent upgrades but that shouldn't affect keeping legacy grub at its latest/last level, should it?
I see it was updated to version 60 in 2009, whereas I seem to have version 21 from 2006! (or do I? - how to check?).

I am getting some practice with Grub2 on a newer PC as mentioned in this thread - [http://ubuntuforums.org/showthread.php?t=1897616](http://ubuntuforums.org/showthread.php?t=1897616)
but will stick with legacy for the remaining (probably short) life of the old PC.

---

### Post by 2CV67 on 2011-12-28
I am ploughing through all I can find on booting - especially Herman's Dual-Boot site & Dedoimedo's tutorials) in the hope I may find some clues or even learn a little...

I notice that I have another "grub" folder at /usr/lib.
In that folder is a folder "i386-pc" which contains 9 of the files also present in /boot/grub ("stage 1"; "stage 2" etc) but they are dated 26 Sep 2011 instead of 2008, presumable after some update.
Is that normal?
Should the files in /boot/grub be at the same level as those in i386-pc?
Or is this just a red herring?

Back to ploughing...

---

### Post by oldfred on 2011-12-28
You can force a clean reinstall if you want. Just follow the instructions for converting from grub to grub2 or vice versa and just reinstall the same version.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by 2CV67 on 2012-01-05
Well - I also managed to get Grub-on-a-stick to boot my LTS Ubuntu, by copying the entry from its menu.lst & "correcting" (hd0,5) to (hd1,5).
This is getting easier with practice!

So now I think I should mark this thread [SOLVED].

I don't really want to take any chances with uninstalling/reinstalling Legacy Grub on my old PC, nor replace with Grub2, so will just live with what I have there.

Thanks for all your help!

---

### Post by oldfred on 2012-01-05
Glad you got it working.:)

Once I learned how to edit grub.cfg with either 40_custom in my full Ubuntu installs or just edit grub.cfg when on my flash drives, I now use grub2 for everything. (When you only have a hammer does not everything look like a nail?:)).  I even managed to get it to boot my Windows 7 repair flash, so I could have a few other repair ISO loopmounted on the same flash drive.

---

### Post by Grenage on 2012-01-05
> **oldfred said:**
> Glad you got it working.:)

Once I learned how to edit grub.cfg with either 40_custom in my full Ubuntu installs or just edit grub.cfg when on my flash drives, I now use grub2 for everything. (When you only have a hammer does not everything look like a nail?:)).  I even managed to get it to boot my Windows 7 repair flash, so I could have a few other repair ISO loopmounted on the same flash drive.

It's immensely handy having a USB drive with various Linux and Windows images on it (not that we can post about them here).  Grub 2 is definitely worth a look if you get more into it.

---

### Post by 2CV67 on 2012-01-07
**EDIT: I reformatted the USB stick & started again & now it works OK.**

One step backwards...

Partly as practice & partly to put Grub on a smaller USB stick, I tried to run through the original procedure again, maybe with some short-cuts.
I created an empty folder "boot" in the new empty USB stick & copied the "grub" folder from my main Ubuntu into it.
Then I ran "sudo grub" & "grub> find /boot/grub/stage1" expecting to see the USB as (hd1,0) or something.
But it only lists my 2 Ubuntu's on the main HD - (hd0,2) & (hd0,5).

In Nautilus, I can clearly see the file boot/grub/stage1 in the USB stick.

I then reinserted the original USB stick with Grub, which still works & which still has a file boot/grub/stage1.
But "grub> find /boot/grub/stage1" doesn't see that one now either...

Lost again...

EDIT: I reformatted the USB stick & started again & now it works OK.

---

### Post by 2CV67 on 2012-01-07
> **oldfred said:**
> You can force a clean reinstall if you want. Just follow the instructions for converting from grub to grub2 or vice versa and just reinstall the same version.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I still don't want to risk reinstalling grub on my main Ubuntu 11.04 (but may edge towards it...).
But I decided to risk it with my LTS 10.04 version, which I can always reinstall completely if the worst comes to the worst.

11.04 is on (hd0,2)
10.04 on (hd0,5)
XP on (hd0,0)

Prior to reinstalling grub in LTS, my primary grub stage2 was (& still is) on (hd0,2).
Menu.lst in 11.04 calls 11.04 as follows:
```
title		Ubuntu 11.04, kernel 2.6.38-13-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-13-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.38-13-generic
quiet
```

and calls 10.04 by:
```
title Ubuntu LTS on sda6
configfile (hd0,5)/boot/grub/menu.lst
```

Selecting "Ubuntu LTS on sda6" brought me straight to a second grub screen run by grub in 10.04, which called LTS as follows:
```
title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash 
initrd		/boot/initrd.img-2.6.32-37-generic
quiet
```

All that worked OK but meant I had difficulties with emergency boot managers due to "root (hd0,5)" etc getting confused.
I had previously tried replacing the root... line with a uuid... line, thinking that would be unambiguous, but ran into "Error 15: file not found".
When trying "grub> uuid" in either 11.04 or 10.04, I got "Error 27: Unrecognized command" instead of the expected list of uuid's.
SynApt said I had grub 0.97-29ubuntu60.10.04.2 but inside grub the installed version said "0.97-29ubuntu21"...

So I have just tried reinstalling grub in 10.04 following kansasnoob's method very carefully & with no apparent hitches.
The only change I made was right at the end, where I used "setup (hd0,5)" instead of (hd0).
**I think that is what I needed there, isn't it?**

Looking inside the new menu.lst, I was encouraged to see the root... line replaced by a uuid... line.
The total entry is now:
```
title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic
uuid		5998da7e-4123-4481-80f0-99a6f3c5e244
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-37-generic
```

But it doesn't work.

After my first grub screen, when I select "Ubuntu LTS on sda6", I get (shortened) "Error 15 - press ESC to enter menu - Error 15 - press any key to continue" before finally getting to the second grub screen.

When I select the "Ubuntu 10.04.3 LTS..." option on the second screen, I get Error 15 again & can only get out by CLI.
Editing that option in the grub screen shows only 2 lines, kernel /... & initrd /..., with no uuid or root line at all.

I manually copied the entries for XP & LTS from the old LTS menu.lst to the new one & after that:
I still get the Error 15's before the second screen.
XP & LTS boot OK from those new (old) entries.

The "Installed version" file inside grub now says "0.97-29ubuntu60.10.04.2" OK, "but grub> uuid" still gives Error 27...

Hmmm...

---

### Post by oldfred on 2012-01-08
When you use drive and partition in the grub setup, you are installing to a partition -PBR not the drive - MBR.

I used to use grub legacy to chain load everything as I created a grub only partition to boot to and manually updated all the entries in the grub menu.lst. But I have forgotten most of that as I have used grub2 since 9.10.

When you have multiple installs and different boot loaders in MBR & PBR, you need to run this to know what is booting to where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

There is a new test version also:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

---

### Post by 2CV67 on 2012-01-08
EDIT: see next post for current status.

> **oldfred said:**
> Paste contents of results.txt in a New Reply
This is V60.
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 221821473 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #3 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda6 and looks at sector 118110001 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #6 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   114,816,554   114,816,492   c W95 FAT32 (LBA)
/dev/sda2         232,396,290   234,436,544     2,040,255  82 Linux swap / Solaris
/dev/sda3         211,302,945   232,396,289    21,093,345  83 Linux
/dev/sda4         114,816,555   211,302,944    96,486,390   5 Extended
/dev/sda5         129,194,730   211,302,944    82,108,215  83 Linux
/dev/sda6         114,816,681   129,194,729    14,378,049  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/ramzswap0                                          swap       
/dev/sda1        2B1B-1302                              vfat       XP
/dev/sda2        5a626c9d-6484-489b-9a9a-c215110b5952   swap       
/dev/sda3        f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c   ext3       
/dev/sda5        e3bbb061-9a3d-4c6e-960a-03d42b490670   ext3       
/dev/sda6        5998da7e-4123-4481-80f0-99a6f3c5e244   ext3       LTS Ubuntu Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext3       (rw,relatime,commit=0)
/dev/sda6        /media/LTS Ubuntu Drive  ext3       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

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
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash

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
# howmany=3

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 11.04, kernel 2.6.38-13-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-13-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.38-13-generic
quiet

title		Ubuntu 11.04, kernel 2.6.38-13-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-13-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.38-13-generic

title		Ubuntu 11.04, kernel 2.6.38-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-12-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.38-12-generic
quiet

title		Ubuntu 11.04, kernel 2.6.38-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-12-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.38-12-generic

title		Ubuntu 11.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#Put in by Chris to chainload Ubuntu LTS
title Ubuntu LTS on sda6
#root (hd0,5)
#chainloader +1
configfile (hd0,5)/boot/grub/menu.lst

#just the end.



--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670	/home	ext3	relatime	0	2
#Entry for /dev/sdg3 :
#UUID=3531BCE07326F070	/media/Iomega_Asus	ntfs-3g	defaults,nosuid,nodev,locale=en_IE.utf8	0	0
#Entry for /dev/sda2 :
UUID=5a626c9d-6484-489b-9a9a-c215110b5952	none	swap	sw	0	0
/dev/scd1	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd0	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0

#UUID=48A5-D628	/media/SHARE	vfat	utf8,umask=007,gid=46	0	2

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.972496510 = 112.713359872  boot/grub/menu.lst                             1
 105.772827625 = 113.572708864  boot/grub/stage2                               2
 107.330944538 = 115.245724160  boot/initrd.img-2.6.38-12-generic             184
 105.899994373 = 113.709253120  boot/initrd.img-2.6.38-13-generic             41
 110.730255604 = 118.895706624  boot/vmlinuz-2.6.38-12-generic                31
 105.868282795 = 113.675203072  boot/vmlinuz-2.6.38-13-generic                18
 105.899994373 = 113.709253120  initrd.img                                    41
 107.330944538 = 115.245724160  initrd.img.old                                184
 105.868282795 = 113.675203072  vmlinuz                                       18
 110.730255604 = 118.895706624  vmlinuz.old                                   31

=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

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
# defoptions=splash

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
# howmany=4

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash 
initrd		/boot/initrd.img-2.6.32-37-generic
quiet

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro  single
initrd		/boot/initrd.img-2.6.32-37-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-33-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash 
initrd		/boot/initrd.img-2.6.32-33-generic
quiet

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-33-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro  single
initrd		/boot/initrd.img-2.6.32-33-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-30-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash 
initrd		/boot/initrd.img-2.6.32-30-generic
quiet

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-30-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-30-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro  single
initrd		/boot/initrd.img-2.6.32-30-generic

title		Ubuntu 10.04.3 LTS, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1




--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  56.375870228 = 60.533129728   boot/grub/menu.lst                             1
  56.466690540 = 60.630647296   boot/grub/stage2                               2
  55.837074757 = 59.954602496   boot/initrd.img-2.6.32-30-generic             98
  57.505543232 = 61.746106880   boot/initrd.img-2.6.32-33-generic             124
  56.342285633 = 60.497068544   boot/initrd.img-2.6.32-37-generic              3
  57.261318684 = 61.483872768   boot/vmlinuz-2.6.32-30-generic                28
  57.313045979 = 61.539414528   boot/vmlinuz-2.6.32-33-generic                37
  56.307892323 = 60.460139008   boot/vmlinuz-2.6.32-37-generic                 2
  56.342285633 = 60.497068544   initrd.img                                     3
  57.505543232 = 61.746106880   initrd.img.old                                124
  56.307892323 = 60.460139008   vmlinuz                                        2
  57.313045979 = 61.539414528   vmlinuz.old                                   37

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```

Many thanks for your continued interest oldfred!

---

### Post by 2CV67 on 2012-01-08
Sorry - the previous post was for my earlier grub version in LTS.

This is the latest version, with uuids & with error 15s...

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda3 and looks at sector 221821473 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #3 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub Legacy
    Boot sector info:   Grub Legacy (v0.97) is installed in the boot sector 
                       of sda6 and looks at sector 118110001 of the same hard 
                       drive for the stage2 file.  A stage2 file is at this 
                       location on /dev/sda.  Stage2 looks on partition #6 
                       for /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   114,816,554   114,816,492   c W95 FAT32 (LBA)
/dev/sda2         232,396,290   234,436,544     2,040,255  82 Linux swap / Solaris
/dev/sda3         211,302,945   232,396,289    21,093,345  83 Linux
/dev/sda4         114,816,555   211,302,944    96,486,390   5 Extended
/dev/sda5         129,194,730   211,302,944    82,108,215  83 Linux
/dev/sda6         114,816,681   129,194,729    14,378,049  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/ramzswap0                                          swap       
/dev/sda1        2B1B-1302                              vfat       XP
/dev/sda2        5a626c9d-6484-489b-9a9a-c215110b5952   swap       
/dev/sda3        f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c   ext3       
/dev/sda5        e3bbb061-9a3d-4c6e-960a-03d42b490670   ext3       
/dev/sda6        5998da7e-4123-4481-80f0-99a6f3c5e244   ext3       LTS Ubuntu Drive

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext3       (rw,relatime,errors=remount-ro,commit=0)
/dev/sda5        /home                    ext3       (rw,relatime,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP dition familiale" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

=========================== sda3/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP dition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

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
# kopt=root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
# defoptions=splash

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
# howmany=3

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 11.04, kernel 2.6.38-13-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-13-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.38-13-generic
quiet

title		Ubuntu 11.04, kernel 2.6.38-13-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-13-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.38-13-generic

title		Ubuntu 11.04, kernel 2.6.38-12-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-12-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro splash 
initrd		/boot/initrd.img-2.6.38-12-generic
quiet

title		Ubuntu 11.04, kernel 2.6.38-12-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.38-12-generic root=UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c ro  single
initrd		/boot/initrd.img-2.6.38-12-generic

title		Ubuntu 11.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

#Put in by Chris to chainload Ubuntu LTS
title Ubuntu LTS on sda6
#root (hd0,5)
#chainloader +1
configfile (hd0,5)/boot/grub/menu.lst

#just the end.



--------------------------------------------------------------------------------

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda3 :
UUID=f5c122c7-090a-4c0b-a5e4-82a6ca0fa56c	/	ext3	relatime,errors=remount-ro	0	1
#Entry for /dev/sda5 :
UUID=e3bbb061-9a3d-4c6e-960a-03d42b490670	/home	ext3	relatime	0	2
#Entry for /dev/sdg3 :
#UUID=3531BCE07326F070	/media/Iomega_Asus	ntfs-3g	defaults,nosuid,nodev,locale=en_IE.utf8	0	0
#Entry for /dev/sda2 :
UUID=5a626c9d-6484-489b-9a9a-c215110b5952	none	swap	sw	0	0
/dev/scd1	/media/cdrom0	udf,iso9660	user,noauto,exec,utf8	0	0
/dev/scd0	/media/cdrom1	udf,iso9660	user,noauto,exec,utf8	0	0

#UUID=48A5-D628	/media/SHARE	vfat	utf8,umask=007,gid=46	0	2

--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 104.972496510 = 112.713359872  boot/grub/menu.lst                             1
 105.772827625 = 113.572708864  boot/grub/stage2                               2
 107.330944538 = 115.245724160  boot/initrd.img-2.6.38-12-generic             184
 105.899994373 = 113.709253120  boot/initrd.img-2.6.38-13-generic             41
 110.730255604 = 118.895706624  boot/vmlinuz-2.6.38-12-generic                31
 105.868282795 = 113.675203072  boot/vmlinuz-2.6.38-13-generic                18
 105.899994373 = 113.709253120  initrd.img                                    41
 107.330944538 = 115.245724160  initrd.img.old                                184
 105.868282795 = 113.675203072  vmlinuz                                       18
 110.730255604 = 118.895706624  vmlinuz.old                                   31

=========================== sda6/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

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
hiddenmenu

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
# kopt=root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=5998da7e-4123-4481-80f0-99a6f3c5e244

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic
uuid		5998da7e-4123-4481-80f0-99a6f3c5e244
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-37-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic (recovery mode)
uuid		5998da7e-4123-4481-80f0-99a6f3c5e244
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro  single
initrd		/boot/initrd.img-2.6.32-37-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic
uuid		5998da7e-4123-4481-80f0-99a6f3c5e244
kernel		/boot/vmlinuz-2.6.32-33-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-33-generic

title		Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic (recovery mode)
uuid		5998da7e-4123-4481-80f0-99a6f3c5e244
kernel		/boot/vmlinuz-2.6.32-33-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro  single
initrd		/boot/initrd.img-2.6.32-33-generic

title		Ubuntu 10.04.3 LTS, memtest86+
uuid		5998da7e-4123-4481-80f0-99a6f3c5e244
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Edition familiale
root		(hd0,0)
savedefault
makeactive
chainloader	+1

# Manually copied from old menu.lst
title		Ubuntu 10.04.3 LTS, kernel 2.6.32-37-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.32-37-generic root=UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 ro splash 
initrd		/boot/initrd.img-2.6.32-37-generic
quiet
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=5998da7e-4123-4481-80f0-99a6f3c5e244 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=5a626c9d-6484-489b-9a9a-c215110b5952 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  56.350452900 = 60.505838080   boot/grub/menu.lst                             1
  56.319355488 = 60.472447488   boot/grub/stage2                               2
  55.837074757 = 59.954602496   boot/initrd.img-2.6.32-30-generic             98
  57.505543232 = 61.746106880   boot/initrd.img-2.6.32-33-generic             124
  56.342285633 = 60.497068544   boot/initrd.img-2.6.32-37-generic              3
  57.261318684 = 61.483872768   boot/vmlinuz-2.6.32-30-generic                28
  57.313045979 = 61.539414528   boot/vmlinuz-2.6.32-33-generic                37
  56.307892323 = 60.460139008   boot/vmlinuz-2.6.32-37-generic                 2
  56.342285633 = 60.497068544   initrd.img                                     3
  57.505543232 = 61.746106880   initrd.img.old                                124
  56.307892323 = 60.460139008   vmlinuz                                        2
  57.313045979 = 61.539414528   vmlinuz.old                                   37

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```

---

### Post by oldfred on 2012-01-08
You have grub in both MBR and the PBR for each partition. 

Which does not work, the configfile entry? I thought the configfile was a grub2 command?

I used to use a chainload entry when I had grub in the PBR. this should work in the menu.lst on sda3.

title       Ubuntu 10.04  @ sda6
root        (hd0,5)
chainloader +1

---

### Post by 2CV67 on 2012-01-09
> Which does not work, the configfile entry? I thought the configfile was a grub2 command?
Yes & No, respectively.
I originally used the chainloader method (it is still in menu.lst - commented out) but changed to configfile some years back (I don't remember why) & it worked OK till this week.
Since I updated grub version in sda6 this week, I started having problems which I thought were related to the use of "uuid..." instead of "root..." in menu.lst, but apparently not.
Checking the Dual-Boot site confirms configfile is valid for Legacy Grub, but is now only 3rd choice & may not work if different versions of grub are present, which is my case since I updated grub in sda6 LTS.
> I used to use a chainload entry
So I switched back to chainloader & that now works OK.
Thanks!

> You have grub in both MBR and the PBR for each partition. 
Looking back through the extensive notes from my well-named "crash" course in booting over the last few weeks, I see I did "grub> setup (hd0,2)" when I was playing about with GAG...
Presumably that has put grub stage1 in the MBR of sda3 where it should not really be?
I assume the other grubs in MBR of sda & sda6 are OK?
Should I remove grub from MBR of sda3?
I am now Googling to see how.
Maybe I need to uninstall & reinstall grub in sda3 with SynApt, then setup (hd0) but not (hd0,3)??

In my own defence, "install grub" is not exactly clear!
I might imagine that meant generating the folder /boot/grub.
But copying stage1 (& 1.5?) to or near MBR is something else.
Not to mention "update grub" which doesn't actually update grub at all, but updates menu.lst, doesn't it?

Anyway - back to maybe removing grub from MBR of sda3.
And maybe updating grub version in sda3 to be same level as in sda6, with uuid addresses instead of root addresses?
Then rechecking all my USB rescue devices again after that change...

---

### Post by 2CV67 on 2012-01-09
I suppose:
```
# dd if=/dev/null of=/dev/sda3 bs=446 count=1
```
would clear out the MBR on sda3 wouldn't it?

On the other hand, is that extra grub actually doing any harm?
Or just looking untidy?

---

### Post by oldfred on 2012-01-09
In both grub & grub2 sudo update-grub just updates menu.

the setup with a partition installs to that partition not the MBR.

to install to sda1 for example:
6. Type "setup (hd0,1)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition - PBR, then you want the number after the comma, such as "(hd0,3)".

The PBR is not used unless you chainload to it, so having an old grub installed to the PBR that is not used does not matter. And then if you later want to use it, just reinstall the update or new version.

I was upset when they said not to install grub2 to the PBR as I was chainloading everything. But grub2's os-prober is so good at finding other installs, it is worth converting to grub2 just for that. And you can still add manual entries, chainload to grub legacy in PBRs, or easily boot ISO directly with grub2. So now I like grub2, but it was a big change.

---

### Post by 2CV67 on 2012-01-09
> **oldfred said:**
> ...having an old grub installed to the PBR that is not used does not matter.
OK - I will just let sleeping grubs lie then.

I have just updated my main (hd0,2) grub to latest legacy version, same as (hd0,5) & "installed" it to (hd0) MBR.

Surprisingly (??) even that was not quite plain sailing...
Firstly, it did not autodetect either XP or LTS but just booted 11.04 straight away.
I added XP via chainloader in the new menu.lst & put it at the top, as previously.
Rebooting now went straight to XP, with no grub screen...
After a short panic & several reboots, I noticed the invite to press ESC for main menu & that did get me to the grub screen.
Back in 11.04 I could dig into menu.lst again & comment out hiddenmenu.
Really, I would have expected that to be the default setting...
And I reset the default OS from 0 to 2. (1. being a dummy spacer).

With XP & 11.04 booting OK, I copied in my chainloader for LTS but getting to it also needed some fiddling, until I realized I needed to comment out hiddenmenu in that menu.lst too...

Now it all seems OK. :)
All using uuid's instead of (hd0,x)'s - except chainloaders, that is.

Just need to check & maybe update all my GAG, Grub & Super Grub USB sticks now...

By the way, from what you say about Grub2, do I take it that it doesn't handle kernel updates of several Ubuntus as tidily as old Grub with chainloading?

---

### Post by oldfred on 2012-01-09
There is a work around in grub where you add a boot stanza that directly boots a partition. Ubuntu puts a link to the newest kernel in / (root).

Similar as this for grub legacy:
title    Most Current Ubuntu on sdc5
root    (hd2,4)
kernel   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

The /vmlinuz & /initrd.img are just links in root. Other distributions may not have links, so then you are correct that it becomes a bit of double work to update both grub.cfg (or whatever menu file they have)  menu files to have the newest entry.

---

