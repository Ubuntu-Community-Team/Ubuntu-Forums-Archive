---
title: "[SOLVED] Dual boot SATA &amp;amp; IDE"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-01
OK, here is what I've done:  I have XP installed on an IDE drive; then I installed Ubuntu 8,04 on that drive using WUBI (kept windows bootloader); I just wanted to see if I could use it well enough to switch to it for most stuff; I can (and plan to), but must keep XP for some things.

So I bought a SATA hard drive and set the bios to boot it.  I installed Kubuntu (KDE4.1)on a partition of the new drive to test out the KDE desktop to see if I like it better than Gnome.  Grub does list Windows NT/2000/XP loader as a boot option.  When selected, the windows boot menu comes up, but pressing any key freezes the screen and you have to power off to reboot.

After searching other threads, I changed the GRUB entry to the following:

title            Windows XP [or whatever the exact title is]
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
chainloader     +1

No change in behavior.  I can change the BIOS back to boot from IDE and it works fine, but not through GRUB on the SATA.  Fix??

I also would like to install Ubuntu on another partition on the SATA and transfer entire configuration over from the wubi IDE XP installation.  The SATA currently has 4 partitions: swap, kubuntu root, future ubuntu root, kubuntu /home.  I was thinking of mounting /home as the /home for both linux installs.  Is this wise?  Advice??

Thanks a lot.

---

### Post by gregphil on 2008-09-01
I just did almost exactly the same thing, and it is working.

WinXp is on primary IDE disk
Ubuntu os on first SATA disk
Kubuntu is on second SATA disk

My BIOS are now set to boot from SCSI first (= SATA first), and was set that way during the ubuntu/kubuntu installs.

The GRUB menu does allow me to boot to the WinXp bootloader (in the mbr of the IDE disk) and then into Windows.

My /boot/grub/menu.lst looks like this:
## ## End Default Options ##

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=3196e3f5-d538-4a64-aad8-b3eda368d85b ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=3196e3f5-d538-4a64-aad8-b3eda368d85b ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+ (on /dev/sda1)
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Kubuntu 8.04.1, kernel 2.6.24-19-generic (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=8441227a-acd7-4bda-9aaa-d74251eee147 ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
savedefault
boot

title           Kubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode) (on /dev/sdb1)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=8441227a-acd7-4bda-9aaa-d74251eee147 ro single
initrd          /boot/initrd.img-2.6.24-19-generic
savedefault
boot

title           Microsoft Windows XP Professional
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

---

### Post by 44tr on 2008-09-01
The only difference appears to be the use of root vs. rootnoverify.  I tried both because I saw both as suggestions; I don't have a clue what the difference is between them.  Still, I don't know why the XP bootloader freezes after the menu loads and you press a key.  Frustrating since it seems like it should work.  I'm just trying out different distros until I settle on the best for me.  I like Ubuntu so much, though, I want to switch to it for my main work while I try out other options.

---

### Post by Paqman on 2008-09-01
> **44tr said:**
> 
I also would like to install Ubuntu on another partition on the SATA and transfer entire configuration over from the wubi IDE XP installation.  The SATA currently has 4 partitions: swap, kubuntu root, future ubuntu root, kubuntu /home.  I was thinking of mounting /home as the /home for both linux installs.  Is this wise?  Advice??


A shared /home between multiple Linux installs is no problem. Just make sure you use different user names on each system to prevent them corrupting each others' config files.

However, it's not really necessary to set up Kubuntu and Ubuntu separately. The only difference between the two is the desktop environment. You can install Kubuntu's KDE desktop onto Ubuntu and vice versa (Ubuntu's Gnome onto Kubuntu). You simply pick which one to use when you log in.

On the other hand, setting up two separate copies of Linux on one machine is a good thing to know how to do, since it lets you try out other distros without ditching your current setup.

---

### Post by caljohnsmith on 2008-09-01
> **44tr said:**
> 
title            Windows XP [or whatever the exact title is]
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
chainloader     +1

Change your Windows entry to the following and I think you will be all set:
```
title            Windows XP
root             (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```
"rootnoverify" is not really necessary in this case as Grub doesn't have any problems with NTFS partitions.

---

### Post by 44tr on 2008-09-01
Nope.  The XP loader menu comes up; the seconds count down do zero and then it just freezes until you turn it off; if you press a choice before that, it freezes too.  Why in the world would the bootloader start if the grub menu.lst was messed up?  Once it does start why wouldn't it continue like it does why IDE is set to boot first in BIOS?  It always seems to be the simple things that clog everything up.

BYW, KDE 4 seems crippled or something.  I can't find KControl, many apps don't show up in the menu unless you type a keyword in the KMenu search box; I'm having a difficult time right now understanding how this could be competition for Gnome, or even Windows.  Must be something wrong with that latest and greatest edition I got instead of the stable KDE 3 bundle?

Thanks for replies so far.

---

### Post by caljohnsmith on 2008-09-01
OK, how about posting your full menu.lst and also your HDDs partitions:
```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

---

### Post by erickghint on 2008-09-01
Stupid question, but did you reinstate the GRUB to the MBR?

---

### Post by egalvan on 2008-09-01
> **44tr said:**
> OK, here is what I've done:  I have XP installed on an IDE drive; 

Is XP still installed on the IDE drive?

> So I bought a SATA hard drive and set the bios to boot it. When selected, the windows boot menu comes up, but pressing any key freezes the screen and you have to power off to reboot.


Has the SATA drive become drive C:, making the IDE drive D: ?

(Windows is not happy if you change drive designations.)

Also, depending on the age of the motherboard and/or BIOS, it may have trouble booting Windows from SATA.

ErnestG

---

### Post by egalvan on 2008-09-01
> **44tr said:**
> 
BYW, KDE 4 seems crippled or something.  I can't find KControl, many apps don't show up in the menu unless you type a keyword in the KMenu search box; I'm having a difficult time right now understanding how this could be competition for Gnome, or even Windows.  Must be something wrong with that latest and greatest edition I got instead of the stable KDE 3 bundle?

Thanks for replies so far.

KDE4 is not 'crippled', it's just experiencing "growing pains". 
It's fairly new, give it time to mature.
Not really fair comparing it to KDE3, which is mature.
But I went back to KDE3 for that reason.
Ibex (8.10) may have better support for it.
Same for 64bit. Which I really want....

---

### Post by 44tr on 2008-09-02
OK, here is my output from "sudo fdisk -lu"
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd45e40ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     4000184     2000061   82  Linux swap / Solaris
/dev/sda2   *     4000185   199318454    97659135   83  Linux
/dev/sda3       199318455   394636724    97659135   83  Linux
/dev/sda4       394636725   625137344   115250310    5  Extended
/dev/sda5       394636788   625137344   115250278+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8da28da2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sdb2        52436160   234436544    91000192+   f  W95 Ext'd (LBA)
/dev/sdb5        52436223    73400984    10482381    7  HPFS/NTFS
/dev/sdb6        73401048   104856254    15727603+   7  HPFS/NTFS
/dev/sdb7       104856318   167766794    31455238+   7  HPFS/NTFS
/dev/sdb8       167766858   234436544    33334843+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31263125

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    31455269    15727603+   7  HPFS/NTFS
/dev/sdc2        31455270   156296384    62420557+   f  W95 Ext'd (LBA)
/dev/sdc5        31455333    94365809    31455238+   7  HPFS/NTFS
/dev/sdc6        94365873   156296384    30965256    7  HPFS/NTFS
```

And here is my output from boot/grub/menu.lst
```
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=42516125-ad3b-4097-887f-ec9e6eacb5ff ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=42516125-ad3b-4097-887f-ec9e6eacb5ff ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=42516125-ad3b-4097-887f-ec9e6eacb5ff ro single
initrd          /boot/initrd.img-2.6.24-19-generic

title           Ubuntu 8.04.1, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
chainloader     +1
```

Ideas?

BTW, I wasn't trying to be offensive about KDE4; I didn't know it was a alpha type release; Firefox 3 was a huge improvement over Firefox 2; I expected KDE4 to be a big improvement and I haven't tried KDE 3.  I want to give it a fair trial though.

As to the other inquiries, both Windows (IDE) and Kubuntu (SATA) boot fine when I designate their drives to boot first in BIOS, so I guess grub's MBR is OK, though "reinstate" may be a term I don't recognize.  I don't know if the IDE drive letter is getting redesignated, but I thought that was the point of the mappings in menu.lst.

Thanks.

---

### Post by gn2 on 2008-09-02
If you can access a "Boot Device Selection Menu" at boot by tapping F8, F2 (or whatever key) then use that to choose which drive to boot from.

You don't need separate partitions to install the various DE's, you can add them all with Synaptic and choose between them at the log-in screen in "Sessions"

---

### Post by caljohnsmith on 2008-09-02
> **44tr said:**
> OK, here is my output from "sudo fdisk -lu"
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd45e40ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     4000184     2000061   82  Linux swap / Solaris
/dev/sda2   *     4000185   199318454    97659135   83  Linux
/dev/sda3       199318455   394636724    97659135   83  Linux
/dev/sda4       394636725   625137344   115250310    5  Extended
/dev/sda5       394636788   625137344   115250278+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8da28da2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    52436159    26218048+   7  HPFS/NTFS
/dev/sdb2        52436160   234436544    91000192+   f  W95 Ext'd (LBA)
/dev/sdb5        52436223    73400984    10482381    7  HPFS/NTFS
/dev/sdb6        73401048   104856254    15727603+   7  HPFS/NTFS
/dev/sdb7       104856318   167766794    31455238+   7  HPFS/NTFS
/dev/sdb8       167766858   234436544    33334843+   7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31263125

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63    31455269    15727603+   7  HPFS/NTFS
/dev/sdc2        31455270   156296384    62420557+   f  W95 Ext'd (LBA)
/dev/sdc5        31455333    94365809    31455238+   7  HPFS/NTFS
/dev/sdc6        94365873   156296384    30965256    7  HPFS/NTFS
```

I don't remember reading in any of your posts that you have three HDDs and not the two you originally mentioned (IDE and SATA). Is the third HDD data only? 
> 
And here is my output from boot/grub/menu.lst
```

title           Windows NT/2000/XP (loader)
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
chainloader     +1
```

The above entry shows what you originally used which doesn't work; did you try my suggestion from post #5? And if you did, are you sure you got the mapping lines correct, using (hd0) and (hd1) instead of (hd0,0) and (hd1,0) like you do above?

Try adding both of the entries below, and let me know exactly what happens on start up (especially errors) when you try each one:
```
title            Windows XP (hd1)
root             (hd1)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

title            Windows XP (hd2)
root             (hd2)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1
```

---

### Post by 44tr on 2008-09-02
Yes, I have a third hard drive (IDE slave) that is almost data only:)  It also contains the Ubuntu directory that Wubi installed on one of the partitions.  It shows up as an option in the Windows bootloader.  I didn't think it was too important to this problem.  One of my goals is to get it installed normally on the SATA drive with the same config, apps, and modifications that I have already made to it.  Would like advice on best way to accomplish.  I could install Ubuntu where Kubuntu KDE4 is now, and just try out the different desktops as advised above.  I tried something similar on another computer of mine: had Ubuntu 8.04 installed and added the Xfce desktop.  When I booted into it, it didn't look or act very different; perhaps I just don't know what components change with different desktops.  

Anyway, yes I did try the (hd0) (hd1) mappings and same result (I actually did that first).  I will add those other entries and let you know what happens.  Sorry for time between posts; I have a long day job.

---

### Post by 44tr on 2008-09-02
OK, I tried caljohnsmith's suggestion and put both of those entries in (copy and paste exact) my menu.lst and rebooted.

both entries showed up in the grub boot menu.  Selecting either one gave the same result:

Error 12: Invalid device requested, press any key to continue.

Selecting the Ubuntu kernel booted Kubuntu like normal.

Is the title text important or is it just the text that goes in the menu?  It was a bit different before.

---

### Post by caljohnsmith on 2008-09-02
I made a mistake in my previous post, those entries should not include "makeactive" or "savedefault". Try the following:
```
title            Windows XP (hd1)
root             (hd1)
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

title            Windows XP (hd2)
root             (hd2)
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```
Reboot, and let me know what errors you get (if any) when you use the above entries. If you do get errors, hit "c" while you are in the Grub menu to get the grub CLI. Next type the following commands and post the output:
```
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
```
That will tell us if Grub is even seeing your other HDDs on start up, because a Grub error 12 could mean that Grub doesn't think your other HDDs exist.

---

### Post by kansasnoob on 2008-09-02
I know this is not helpful at this point, but I'm quite serious when I say, "It's much better to have all operating systems on one drive!

I've had as many as 3 Linux OS's inside one extended partition with one shared swap (it does require some uuid tweaking) but everything still works great!

IMHO it's much more sane to install additional drives for data and resize one existing "main" drive to house all of your OS"s.

---

### Post by 44tr on 2008-09-03
Kansasnoob, I suppose you are including XP as one of the operating systems that all go on one drive?  I didn't really want to overwrite the Windows MBR since I don't know if or how to get it back as it was.  I DID plan to keep all of the GNU/Linux OS's on the same drive.  That said, partition and setup advice is appreciated.

---

### Post by 44tr on 2008-09-03
caljohnsmith,

I did as directed.  picking the hd1 option gave me the windows boot menu but choosing an option just froze the screen as before.  Choosing hd2 didn't find anything to boot.  Typing the grub commands resulted in the following:

grub> geometry (hd0)
drive 0x80: C/H/S = 1023/255/63, The number of sectors = 625142448, LBA
Partition num: 0,  Filesystem type unknown, partition type 0x82
Partition num: 1,  Filesystem type is ext2fs, partition type 0x83
Partition num: 2,  Filesystem type is ext2fs, partition type 0x83
Partition num: 4,  Filesystem type is ext2fs, partition type 0x83

grub> geometry (hd1)
drive 0x81: C/H/S = 1024/255/63, The number of sectors = 234441648, LBA
Partition num: 0,  Filesystem type unknown, partition type 0x7
Partition num: 4,  Filesystem type unknown, partition type 0x7
Partition num: 5,  Filesystem type unknown, partition type 0x7
Partition num: 6,  Filesystem type unknown, partition type 0x7
Partition num: 7,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x82: C/H/S = 1024/255/63, The number of sectors = 156301488, LBA
Partition num: 0,  Filesystem type unknown, partition type 0x7
Partition num: 4,  Filesystem type unknown, partition type 0x7
Partition num: 5,  Filesystem type unknown, partition type 0x7

On hd1, the 0 partition is setup as swap. next partition is kubuntu.

Thanks.

---

### Post by caljohnsmith on 2008-09-03
> **44tr said:**
> caljohnsmith,
I did as directed.  picking the hd1 option gave me the windows boot menu but choosing an option just froze the screen as before.  Choosing hd2 didn't find anything to boot.

Ok, so when you get the Windows boot menu, does it give you the option to pick between Windows XP and Grub4DOS/Ubuntu (from your old Wubi install)? And when you pick Windows XP is when the screen hangs? Are you sure you're giving it enough time to boot? Because when I boot Win XP the screen goes blank for just a little while before it shows a low-res progress bar and then the Win splash screen. Also, if you set BIOS to boot your Windows XP HDD first, do you get the same Windows boot menu, and when you pick the Windows XP option it boots fine? Would you be willing to change your BIOS and confirm that this is still true? I ask because I'm doubtful that you can still boot that Windows HDD even if you change it to boot first on start up.

---

### Post by 44tr on 2008-09-03
> **caljohnsmith said:**
> Ok, so when you get the Windows boot menu, does it give you the option to pick between Windows XP and Grub4DOS/Ubuntu (from your old Wubi install)? And when you pick Windows XP is when the screen hangs? Are you sure you're giving it enough time to boot? Because when I boot Win XP the screen goes blank for just a little while before it shows a low-res progress bar and then the Win splash screen. Also, if you set BIOS to boot your Windows XP HDD first, do you get the same Windows boot menu, and when you pick the Windows XP option it boots fine? Would you be willing to change your BIOS and confirm that this is still true? I ask because I'm doubtful that you can still boot that Windows HDD even if you change it to boot first on start up.

When I get the Windows Boot menu, I get to choose from Windows XP (default), three Windows Tune-Up Utilities backup options, Windows XP recovery console and Ubuntu (installed by Wubi).

Since I have no other way to boot Windows, I change it back to boot from the IDE drive every day and it boots perfectly every time.  When I choose an option the screen immediately blanks and begins to load the chosen option.  On the other hand, when I boot to the SATA drive and choose Windows from grub, the same windows boot menu opens, except choosing an option makes it freeze for at least 5 minutes, the longest I've had the patience to wait when I am used to typing in my password after 30-40 seconds.

I suppose Tune-up utilties may have put its own bootloader in there that just looks the same, but shouldn't the thing boot no matter what bootloader is in there if it boots fine when designated to boot first by BIOS?

---

### Post by caljohnsmith on 2008-09-03
> **44tr said:**
> ...but shouldn't the thing boot no matter what bootloader is in there if it boots fine when designated to boot first by BIOS?
I agree, under normal circumstances it shouldn't matter which boot loader boots Windows, because all the Windows MBR does is chain load the PBR (partition boot loader) of whichever partition is active on the HDD (has its boot flag set), and Grub is perfectly capable of doing that. And the fact that you are successfully getting the Windows boot menu after booting it from Grub means that Grub can't be the culprit at this point.

I think the problem is that you probably have software on your Windows drive that accesses the SATA HDD or your 80 GB sdc HDD, and when you change the boot order to boot Ubuntu first, the Windows HDD doesn't see those HDDs in the same order, and the software hangs because it looks on the wrong HDD. In other words, do you have software like maybe "ext2fsd" that allows you to access your Ubuntu HDD? Or software that accesses that 80 GB HDD? I'm betting that has something to do with that. Can you think of anything on your Windows HDD that might be trying to access the other HDDs?

---

### Post by 44tr on 2008-09-04
I didn't install anything in Windows, yet, to access my Linux partitions.  The only thing I can think of is that I had Wubi install Ubuntu on a partition on that 3rd (80GB) drive.

I don't understand why that would be a problem; do I need to map that drive as hdl in grub the way we are remapping the Windows boot drive to hd0?  If so, how?  It still seems like that shouldn't matter until I chose the Ubuntu option in the Windows boot loader, but what do I know?:)

---

### Post by caljohnsmith on 2008-09-04
I have an idea that will hopefully help us narrow down your problem. There is a simple way to make Windows display messages of what is happening while you boot Windows, and it is a simply registry change. Just follow [Raymond's guide]("http://www.raymond.cc/blog/archives/2008/06/18/how-to-troubleshoot-windows-startup-logoff-login-and-shutdown-problems/") of how to do it, and then the next time you try and boot Windows from Grub, see what messages Windows reports while trying to boot. That will hopefully give us a better clue why Windows is hanging.

---

### Post by 44tr on 2008-09-04
> **caljohnsmith said:**
> I have an idea that will hopefully help us narrow down your problem. There is a simple way to make Windows display messages of what is happening while you boot Windows, and it is a simply registry change. Just follow [Raymond's guide]("http://www.raymond.cc/blog/archives/2008/06/18/how-to-troubleshoot-windows-startup-logoff-login-and-shutdown-problems/") of how to do it, and then the next time you try and boot Windows from Grub, see what messages Windows reports while trying to boot. That will hopefully give us a better clue why Windows is hanging.

OK, I edited the registry as directed and rebooted several times with the BIOS set both ways.  I don't see any messages until the logon screen appears when IDE windows drive is set to boot.  When SATA grub boots I choose the Windows hd1 option and get the windows bootup screen as before.  I can up arrow and down arrow and even press F8 and get another menu (start windows normally, recovery console, reboot, and other stuff.  If I choose start windows normally or return to menu it goes back to the Windows boot menu.  Anytime I actually choose one of the options in the Windows boot menu though, it instantly freezes and stays that way.  At the grub menu, I even selected the option to boot other operating systems, and got error 11, device string not recognized or something like that.  It does seem like Windows doesn't see the drive order the same way as when IDE is set to boot first doesn't it?  It would be nice if there was a boot log or something I could look at.  Even if we stipulate that is the problem, how do we fix it?

What would happen if we set the drive mappings like this:

map (hd0) (hd2)
map (hd1) (hd0)
map (hd2) (hd1)

??

---

### Post by 44tr on 2008-09-04
I tried it just for grins.  Screen still freezes the same way. :confused:

---

### Post by 44tr on 2008-09-04
Just brainstorming a bit: the labels in the drive mappings don't change from hd1 to sd1 or something because it is SATA do they?

---

### Post by caljohnsmith on 2008-09-04
> **44tr said:**
> OK, I edited the registry as directed and rebooted several times with the BIOS set both ways.  I don't see any messages until the logon screen appears when IDE windows drive is set to boot.  When SATA grub boots I choose the Windows hd1 option and get the windows bootup screen as before.  I can up arrow and down arrow and even press F8 and get another menu (start windows normally, recovery console, reboot, and other stuff.  If I choose start windows normally or return to menu it goes back to the Windows boot menu.  Anytime I actually choose one of the options in the Windows boot menu though, it instantly freezes and stays that way.  At the grub menu, I even selected the option to boot other operating systems, and got error 11, device string not recognized or something like that.  It does seem like Windows doesn't see the drive order the same way as when IDE is set to boot first doesn't it?  It would be nice if there was a boot log or something I could look at.  Even if we stipulate that is the problem, how do we fix it?

What would happen if we set the drive mappings like this:

map (hd0) (hd2)
map (hd1) (hd0)
map (hd2) (hd1)

??
Unfortunately, I think doing those drive mappings in Grub won't fix the problem; Windows successfully boots to its boot screen, meaning that Grub successfully chain loaded Windows' partition boot record (PBR). I could be wrong, but once Grub successfully chain loads Windows, i.e. hands off the boot process to Windows, then I think no amount of remapping with Grub will further affect the boot process. 

I have an idea though: can you set BIOS to boot your Windows HDD, but disconnect your Ubuntu and storage HDDs first? That will tell us if the problem is related to the other HDDs changing order, because if you have no problem booting Windows with both those HDDs disconnected, then reordering them should probably not make any difference (which is what we think is happening when you boot the Ubuntu HDD first).

---

### Post by 44tr on 2008-09-04
> **caljohnsmith said:**
> Unfortunately, I think doing those drive mappings in Grub won't fix the problem; Windows successfully boots to its boot screen, meaning that Grub successfully chain loaded Windows' partition boot record (PBR). I could be wrong, but once Grub successfully chain loads Windows, i.e. hands off the boot process to Windows, then I think no amount of remapping with Grub will further affect the boot process. 

I have an idea though: can you set BIOS to boot your Windows HDD, but disconnect your Ubuntu and storage HDDs first? That will tell us if the problem is related to the other HDDs changing order, because if you have no problem booting Windows with both those HDDs disconnected, then reordering them should probably not make any difference (which is what we think is happening when you boot the Ubuntu HDD first).

I guess I could try, but it boots fine with the BIOS set to HDD-0 and it did also before I ever connected the SATA, which is a new edition.  It is only when I change the BIOS to boot SCSI first that there is a problem.  If it still boots fine with the slave IDE drive disconnected, exactly what does that tell us?

---

### Post by caljohnsmith on 2008-09-04
> **44tr said:**
> I guess I could try, but it boots fine with the BIOS set to HDD-0 and it did also before I ever connected the SATA, which is a new edition.  It is only when I change the BIOS to boot SCSI first that there is a problem.  If it still boots fine with the slave IDE drive disconnected, exactly what does that tell us?
What I'm actually thinking is that Windows may not boot OK when you disconnect the slave IDE drive. That would definitely tell us where the problem is if that's what happens, but if disconnecting it doesn't affect anything, then that will at least tell us that reordering the HDDs is probably not the problem.

---

### Post by 44tr on 2008-09-05
It boots Windows fine with the SATA and slave IDE disconnected.

---

### Post by caljohnsmith on 2008-09-05
> **44tr said:**
> It boots Windows fine with the SATA and slave IDE disconnected.
That tells us then that Windows is probably not hanging because of your HDDs being reordered. I'm suspecting at this point it is a BIOS issue; what are your BIOS settings for your IDE and SATA HDDs? Do you have them as "autodetect"? If so, I would tell BIOS exactly what they are, IDE or SATA. Let me know what other BIOS settings you have related to your HDDs, and we can work from there I think.

---

### Post by 44tr on 2008-09-05
> **caljohnsmith said:**
> That tells us then that Windows is probably not hanging because of your HDDs being reordered. I'm suspecting at this point it is a BIOS issue; what are your BIOS settings for your IDE and SATA HDDs? Do you have them as "autodetect"? If so, I would tell BIOS exactly what they are, IDE or SATA. Let me know what other BIOS settings you have related to your HDDs, and we can work from there I think.

OK, I have an ASUS A7N8X-E Deluxe motherboard with Phoenix BIOS.

The IDE Primary Master is set to AUTO
           Access Mode is set to AUTO
The IDE Primary Slave  is set to AUTO
           Access Mode is set to AUTO

This motherboard has two SATA connectors that can be set up as a RAID, but since I only have one SATA drive, I have the 'RAID or SCSI Card Boot' set to SCSI Card.

The 1st Boot Device I switch back and forth between HDD-0 and SCSI.  The 2nd and 3rd boot devices are disabled and the 'Boot Other Device' setting is enabled.  (I don't really know what this last is for.  Is that enough?  What to change?

---

### Post by caljohnsmith on 2008-09-05
> The IDE Primary Master is set to AUTO
What are the choices other than auto? 

In the meantime, try changing the "access mode" for both your IDE and SATA drive to "LBA" instead of AUTO, reboot and see if that helps.

---

### Post by 44tr on 2008-09-05
The choices for the IDE Primary Master are Auto, Manual, None.
I changed the primary IDE Access Mode to LBA and booted from SATA; the Windows boot screen froze again.

---

### Post by 44tr on 2008-09-06
Hmmm.  Maybe we are approaching this backwards.  Here is my Windows boot.ini file:
```

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=26DYE7
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=26DYE7-BAK /Kernel=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=TMHSL1 /Kernel=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=TMHSL1-BAK
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
c:\wubildr.mbr="Ubuntu"

```

Is there a way to edit the boot.ini file to chainload grub on the SATA drive?  Would that solve the problem?  Just boot to IDE all the time and redirect to the Grub bootloader?  As much as I've used Windows, I always find it a pain to edit the system files; it isn't nearly as straightforward as GNU/Linux in that regard.  What do ya think?

---

### Post by caljohnsmith on 2008-09-06
It's definitely possible to add your Grub boot loader to that boot.ini file to chain load it, and I can give you directions how to do so if you want. But as long as you all ready have Grub4DOS installed, it would probably be easier to just chain load the SATA HDD from Grub4DOS's menu.lst. In Windows, I think the menu.lst is at C:\ubuntu\install\boot\grub\menu.lst.

I'm not sure the exact syntax for Grub4DOS, but try adding the following to the menu.lst in Windows:
```
title   Ubuntu SATA HDD
rootnoverify   (hd1)
chainloader +1
```
If it doesn't work, post your Grub4DOS's menu.lst and we can work from there.

---

### Post by egalvan on 2008-09-06
> **kansasnoob said:**
> I know this is not helpful at this point, but I'm quite serious when I say, "It's much better to have all operating systems on one drive!

I've had as many as 3 Linux OS's inside one extended partition with one shared swap (it does require some uuid tweaking) but everything still works great!

IMHO it's much more sane to install additional drives for data and resize one existing "main" drive to house all of your OS"s.

OK, I'll bite:

WHY is it "much better" to have all systems on one drive?

BTW,
I've installed multiple os's on multiple drives, and NO UUID tweaking.

---

### Post by 44tr on 2008-09-06
Well, that would work too, I imagine, but one of the goals here is to get my Ubuntu installation that is in the NTFS folder on that 80GB drive (30GB partition) onto a 100 GB ext3 partition on the SATA drive, preferably without having to recustomize everything from scratch.  Now that I like Ubuntu so much, I want to take advantage of the much higher performance and simpler setup of having Ubuntu use its own (better) filesystem.  Kubuntu that is on the SATA was just a test to see if I would actually like it more.  Since I now know that I don't have to install it separately to try KDE, I could just Overwrite the Kubuntu Installation with Ubuntu.  

So, the overall goal:  Windows XP on 120GB IDE primary master
                       Format the 80GB IDE primary slave as ext3 after transfering the rest of the data and Ubuntu OFF (or recreating).
                       Use the 320GB SATA drive as my main Ubuntu linux installation with separate /home partition and another partition that could be used to install another distro (perhaps a specialty distro for music recording and performance.) that could share the same swap partition and the same /home partition.

Hopefully what I'm trying to achieve (or think I am) is clearer now.  What do you think of my plan?  Would you do something differently?  Any advice on how to partition my drives?  I have AMD 2600+ Athlon (yes, it is getting old) and 1GB of RAM (166 Mhz).

I really appreciate you taking the time to help me out.  If the scope of this little project is getting out of hand for you, we can just work on the first piece which I guess is modifying the Windows boot.ini?  What do you advise?

---

### Post by caljohnsmith on 2008-09-06
> **44tr said:**
> Well, that would work too, I imagine, but one of the goals here is to get my Ubuntu installation that is in the NTFS folder on that 80GB drive (30GB partition) onto a 100 GB ext3 partition on the SATA drive, preferably without having to recustomize everything from scratch.  Now that I like Ubuntu so much, I want to take advantage of the much higher performance and simpler setup of having Ubuntu use its own (better) filesystem.  Kubuntu that is on the SATA was just a test to see if I would actually like it more.  Since I now know that I don't have to install it separately to try KDE, I could just Overwrite the Kubuntu Installation with Ubuntu.  

So, the overall goal:  Windows XP on 120GB IDE primary master
                       Format the 80GB IDE primary slave as ext3 after transfering the rest of the data and Ubuntu OFF (or recreating).
                       Use the 320GB SATA drive as my main Ubuntu linux installation with separate /home partition and another partition that could be used to install another distro (perhaps a specialty distro for music recording and performance.) that could share the same swap partition and the same /home partition.

Hopefully what I'm trying to achieve (or think I am) is clearer now.  What do you think of my plan?  Would you do something differently?  Any advice on how to partition my drives?  I have AMD 2600+ Athlon (yes, it is getting old) and 1GB of RAM (166 Mhz).

I really appreciate you taking the time to help me out.  If the scope of this little project is getting out of hand for you, we can just work on the first piece which I guess is modifying the Windows boot.ini?  What do you advise?
OK, first off I don't know all the ramifications involved in trying to move a Wubi install to its own ext3 partition, and I don't know if it is realistic or feasible. If you search the forums though, I'm sure you'll find others who have asked the same thing. Sorry I can't be of more help with that.

About your partitioning idea though, I think it sounds like a good plan. Since you are planning on deleting your Wubi install and I would assume Grub4DOS along with it, I can give you directions of how to add the Grub MBR to your Windows boot.ini so it is an option on start up, and then you won't need to set BIOS to boot your SATA drive directly. Given that we can't figure out how to boot Windows from your SATA, that's what I would do. So does that sound like what you want at this point?

---

### Post by 44tr on 2008-09-06
> **caljohnsmith said:**
> OK, first off I don't know all the ramifications involved in trying to move a Wubi install to its own ext3 partition, and I don't know if it is realistic or feasible. If you search the forums though, I'm sure you'll find others who have asked the same thing. Sorry I can't be of more help with that.

About your partitioning idea though, I think it sounds like a good plan. Since you are planning on deleting your Wubi install and I would assume Grub4DOS along with it, I can give you directions of how to add the Grub MBR to your Windows boot.ini so it is an option on start up, and then you won't need to set BIOS to boot your SATA drive directly. Given that we can't figure out how to boot Windows from your SATA, that's what I would do. So does that sound like what you want at this point?

Yes, that seems like the best plan right now.  If moving the install directly is not going to be straightforward, I can recreate it.  I haven't been working on it so long that I don't know mostly what I have done and part of the plan was to leave the wubi install intact until I was satisfied that my new installation was completely ready.  I might even pull the 80GB drive for use somewhere else eventually.  So how do I go about changing the boot.ini file?:)

---

### Post by caljohnsmith on 2008-09-06
[COLOR="Red"]**EDIT:** for anyone who stumbles upon this thread in the future, the following has errors and the correct way to do the "modified boot.ini" approach is in post #74. Of course post #74 would have to be modified if your set up is slightly different.
[/COLOR]

OK, first of all, the following is going to assume that you have booted off your Ubuntu SATA HDD, so that when you do:
```
sudo fdisk -lu
```
You see the HDDs in the same order as your post #11, i.e. Windows is on sdb (this is crucial). In the instructions below, make sure you get the "dd" commands exactly right or you can seriously mess up your system:
[LIST=1]
[*]First backup the partition boot record (PBR) of sdb1, because we will temporarily overwrite it but then restore it:
```

cd ~/Desktop
sudo dd if=/dev/sdb1 of=sdb1_PBR.bin bs=512 count=1
```
That will save the sdb1 PBR to your desktop.
[*]Next temporarily install Grub to the PBR of sdb1:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd1,0)  [COLOR="Blue"][this is not a typo][/COLOR]
grub> quit
```
[*]Next copy the new Grub PBR:
```
sudo dd if=/dev/sdb1 of=sdb1_grub_PBR.bin bs=512 count=1
```
[*]Then put the original sdb1 PBR back:
```
sudo dd if=sdb1_PBR.bin of=/dev/sdb1 bs=512 count=1
```
[*]Put the sdb1_grub_PBR.bin file in the Windows root directory on sdb1:
```
sudo umount /dev/sdb1  [COLOR="Blue"][just in case sdb1 is all ready mounted somewhere else][/COLOR]
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mv sdb1_grub_PBR.bin /mnt/sdb1/.
```
[*]Then edit the Windows boot.ini file:
```

sudo nano /mnt/sdb1/boot.ini
```
Add the following line at the very end and save:
```
C:\sdb1_grub_PBR.bin="Grub Menu on SATA HDD"
```
[/LIST]
I've checked everything above and don't think there are any typos, but of course let me know if you have a problem. Otherwise let me know how it goes. :)

---

### Post by 44tr on 2008-09-06
OK, I followed all directions above.  In fact I copied and pasted each into the terminal window and got no errors and everything seemed to go well.  Windows boot menu comes up fine (when IDE is selected in BIOS) and Windows boots fine when that option is selected.

However, When I choose the Grub on SATA option, the screen blanks, the word 'GRUB' appears at the top and then nothing else happens.  Is the location correct from the perspective of Windows boot loader?  I have to say this is much less frustrating to work on together. :)

---

### Post by caljohnsmith on 2008-09-06
> **44tr said:**
> OK, I followed all directions above.  In fact I copied and pasted each into the terminal window and got no errors and everything seemed to go well.  Windows boot menu comes up fine (when IDE is selected in BIOS) and Windows boots fine when that option is selected.

However, When I choose the Grub on SATA option, the screen blanks, the word 'GRUB' appears at the top and then nothing else happens.  Is the location correct from the perspective of Windows boot loader?  I have to say this is much less frustrating to work on together. :)
Unfortunately, the problem might be because Grub does not necessarily see the order of HDDs the same as BIOS does. In your next post, zip/tar/gzip that sdb1_grub_PBR.bin file and attach it to your post so I can look at it. In the meantime, try the following, and as you can see it is the same process but we will use the sdc drive instead:
[list]
[*]```

cd ~/Desktop
sudo dd if=/dev/sdc1 of=sdc1_PBR.bin bs=512 count=1
```
That will save the sdc1 PBR to your desktop.
[*]Next temporarily install Grub to the PBR of sdc1:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd2,0) 
grub> quit
```
[*]Next copy the new Grub PBR:
```
sudo dd if=/dev/sdc1 of=sdc1_grub_PBR.bin bs=512 count=1
```
[*]Then put the original sdb1 PBR back:
```
sudo dd if=sdc1_PBR.bin of=/dev/sdc1 bs=512 count=1
```
[*]Put the sdc1_grub_PBR.bin file in the Windows root directory on sdb1:
```
sudo umount /dev/sdb1  [COLOR="Blue"][just in case sdb1 is all ready mounted somewhere else][/COLOR]
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mv sdc1_grub_PBR.bin /mnt/sdb1/.
```
[*]Then edit the Windows boot.ini file:
```

sudo nano /mnt/sdb1/boot.ini
```
Add the following line at the very end and save:
```
C:\sdc1_grub_PBR.bin="Grub Menu on SATA HDD, using sdc1"
```
[/LIST]
Reboot, and let me know what happens this time. Also attach the sdc1_grub_PBR.bin file. :)

---

### Post by 44tr on 2008-09-06
Here is the file (I hope); I'll reboot and let you know what happens.

---

### Post by 44tr on 2008-09-06
Rebooted to IDE, chose Ubuntu on SATA sdc1 option, same thing happens as last time ... GRUB appears, then nothing.

I don't really understand why we have to copy and move the PBR files around.  In Ubuntu, you just edit the menu.lst file.  You can't just edit boot.ini and have the same effect?  The only reason I didn't try that, is that I didn't know what location to type in precisely.

---

### Post by caljohnsmith on 2008-09-06
> **44tr said:**
> Rebooted to IDE, chose Ubuntu on SATA sdc1 option, same thing happens as last time ... GRUB appears, then nothing.

I don't really understand why we have to copy and move the PBR files around.  In Ubuntu, you just edit the menu.lst file.  You can't just edit boot.ini and have the same effect?  The only reason I didn't try that, is that I didn't know what location to type in precisely.
Unfortunately, you can't edit the boot.ini file in the same way you do menu.lst. The files you specify in boot.ini are the boot loaders themselves (MBRs and PBRs and the like) and not their configuration files (such as menu.lst). I've successfully used the technique I gave you to boot Grub from the Windows boot loader, but with Grub on the same HDD. Once you understand the theory behind the technique though, there is no reason why it couldn't be used when there are multiple HDDs; I have a few friends who claim to have done it with no problem. Unfortunately, there might still be some issue particular with your set up that is stopping us, because we still don't know why Grub can't boot your IDE drive. So maybe the reverse is true too: maybe your IDE drive can't boot your SATA drive. 

So are you feeling adventurous enough to keep going, or are you getting tired of messing with this? I guess I'm still game if you are, as I have at least a few more ideas of how we might get this "modified boot.ini" approach to work with your set up. :)

---

### Post by 44tr on 2008-09-06
Oh, I'm game to keep going.  I need some solution that is better than switching the BIOS settings, because my wife (not an accomplished computer user) will need to access Ubuntu and Windows and changing the BIOS settings is not something she is going to do.  Until I'm ready to build another computer, I have to have Windows and I want to have Ubuntu.  

I just had a thought.  I have just one boot device listed in BIOS the other choices (2nd boot device, 3rd Boot device).  The SATA drive doesn't have to be listed 2nd in the boot order to enable it to be booted right?  I don't think so, but I'm grasping at straws.

---

### Post by 44tr on 2008-09-06
BTW, I would really prefer to boot to GRUB on SATA with the Windows bootloader as an option if possible.  It will probably be less painful in the long run if I pull that 80 GB drive and I hope to spend a lot more time in Ubuntu that Windows.

A thought:  can we get some use out of my wubi installation?  Will it list the drives differently since it is booted through windows in a windows folder on an NTFS partition.  Could we get useful information by running the disk info utilities within wubi Ubuntu?

---

### Post by 44tr on 2008-09-06
I looked at the PBR file in my windows root directory and found that I had an application associated with .bin files (VLC media player).  I deleted this association, but would it have made any difference?

---

### Post by caljohnsmith on 2008-09-06
> **44tr said:**
> 
I just had a thought.  I have just one boot device listed in BIOS the other choices (2nd boot device, 3rd Boot device).  The SATA drive doesn't have to be listed 2nd in the boot order to enable it to be booted right?  I don't think so, but I'm grasping at straws.
No, I don't think the SATA drive would need to be listed as second in the boot order in order to boot it from the Windows IDE drive; those boot order settings in BIOS might possibly affect how Grub sees the order of HDDs though, I'm not exactly sure since I've come across what seems to be contradictory evidence of that in the past. 

Because we're not even sure if it is possible for your IDE drive to boot your SATA drive (since the reverse is certainly a problem), I think we should try to use Grub4DOS to boot the SATA drive first (like you mentioned), and only if that works we can try getting the modified boot.ini approach working. How about doing what I suggested in post #37 and add the following to your C:\ubuntu\install\boot\grub\menu.lst file:
```
title   Ubuntu SATA HDD (hd1)
rootnoverify   (hd1)
chainloader +1

title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
chainloader +1
```
Also, please post the entire contents of the menu.lst file from Windows.

---

### Post by cwsnyder on 2008-09-06
Quick note:  My system boots from the PATA (IDE) drive first, then goes through Grub to boot my Ubuntu Hardy system from SATA.

eMachines T5212 quad booting hda1 - Windows XP Media Center, hda5 - Mandriva 2008.1 Spring, sda1 - Ubuntu 8.04, sda4 - Debian 5.0 Lenny (testing)

---

### Post by 44tr on 2008-09-06
> **caljohnsmith said:**
> No, I don't think the SATA drive would need to be listed as second in the boot order in order to boot it from the Windows IDE drive; those boot order settings in BIOS might possibly affect how Grub sees the order of HDDs though, I'm not exactly sure since I've come across what seems to be contradictory evidence of that in the past. 

Because we're not even sure if it is possible for your IDE drive to boot your SATA drive (since the reverse is certainly a problem), I think we should try to use Grub4DOS to boot the SATA drive first (like you mentioned), and only if that works we can try getting the modified boot.ini approach working. How about doing what I suggested in post #37 and add the following to your C:\ubuntu\install\boot\grub\menu.lst file:
```
title   Ubuntu SATA HDD (hd1)
rootnoverify   (hd1)
chainloader +1

title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
chainloader +1
```
Also, please post the entire contents of the menu.lst file from Windows.

OK, I am booted up in wubi Ubuntu through Windows.  I checked fdisk -lu and the results were identical with what I posted earlier which were run from Kubuntu on SATA (?).

I will list the menu.lst file from the wubi installation in the next post.

---

### Post by 44tr on 2008-09-06
wubi /boot/grub/menu.lst:

```
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
# kopt=root=UUID=BC48F69748F64F9E loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=BC48F69748F64F9E loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=BC48F69748F64F9E loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

---

### Post by cwsnyder on 2008-09-06
I see one problem already:  Your IDE disk should be listed as **hd(0,0)**, if this is your boot drive, but your SATA drive should be listed as **hd(1,0)** in *menu.lst* for the Grub used with Ubuntu.

---

### Post by 44tr on 2008-09-06
> **caljohnsmith said:**
> 
How about doing what I suggested in post #37 and add the following to your C:\ubuntu\install\boot\grub\menu.lst file:
```
title   Ubuntu SATA HDD (hd1)
rootnoverify   (hd1)
chainloader +1

title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
chainloader +1
```
Also, please post the entire contents of the menu.lst file from Windows.

OK, maybe I'm an idiot.  Did you mean to boot into Windows and look in the C:\ubuntu\ ...?

There isn't any C:\ubuntu directory because it is on a different disk.  Anyway for me menu.lst was in C:\work2\ubuntu\winboot\menu.lst

Here are the contents:
```
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt
```

Given that syntax, is this the file you want me to add those lines to?

---

### Post by 44tr on 2008-09-06
OK, maybe I'm a bigger idiot than even I thought :lolflag:

There is also a C:\work2\ubuntu\disks\boot\grub\menu.lst

```
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
# kopt=root=UUID=BC48F69748F64F9E loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=BC48F69748F64F9E loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=BC48F69748F64F9E loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
chainloader	+1

```

Isn't this just the same file that I printed from within wubi Ubuntu (/boot/grub/menu.lst) or not?  I don't mean have the same contents, but actually the same file just accessed two different ways?

Anyway is this the one you want me to edit?

---

### Post by cwsnyder on 2008-09-06
The menu.lst which works for your Ubuntu install (not the WUBI install) is actually on the Ubuntu partition in /boot/grub/   That is: /boot/grub/menu.lst

This should be whatever partition has your root ( / ) directory for Ubuntu.  This would have directories like /home /etc /boot /dev /mnt /media . . .etc.

Find this with your Ubuntu live disk, then change THAT menu.lst.

You can also try going into terminal ( Applications >> Accessories >> Terminal ) and typing ```
 grub
find /boot/grub/stage1 
```  The answer to the second line should return something like **(hd0,0)** .  Now type ```
root (hd0,0)
setup (hd0) 
```
replacing hd0 with whatever the response from **find** was.  This attempts to reset up grub.

---

### Post by 44tr on 2008-09-06
> **cwsnyder said:**
> The menu.lst which works for your Ubuntu install (not the WUBI install) is actually on the Ubuntu partition in /boot/grub/   That is: /boot/grub/menu.lst

This should be whatever partition has your root ( / ) directory for Ubuntu.  This would have directories like /home /etc /boot /dev /mnt /media . . .etc.

Find this with your Ubuntu live disk, then change THAT menu.lst.

You can also try going into terminal ( Applications >> Accessories >> Terminal ) and typing ```
 grub
find /boot/grub/stage1 
```  The answer to the second line should return something like **(hd0,0)** .  Now type ```
root (hd0,0)
setup (hd0) 
```
replacing hd0 with whatever the response from **find** was.  This attempts to reset up grub.

I don't think that is exactly what we were trying to do.  I want to see what the other gentleman I've been working with recommends.

---

### Post by caljohnsmith on 2008-09-06
OK, I think the menu.lst in Windows you want to edit would be the C:\work2\ubuntu\disks\boot\grub\menu.lst file. Also, I received some excellent advice from a friend who pointed out that doing mapping will be better since we won't have to change your menu.lst on your Ubuntu HDD once we get it fixed. So, in that Windows menu.lst, add the following:
```
title   Ubuntu SATA HDD (hd1)
rootnoverify   (hd1)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```
So when you boot Windows and get the Grub4DOS menu, you should see the above entries. Give them a try and let me know what happens.

---

### Post by cwsnyder on 2008-09-06
When you are booting from the IDE drive, the Master Boot Record (MBR) and Grub you actually are working from is on the IDE drive, not the SATA.  As a matter of fact, the SATA drive can have a blank MBR.  Grub then should point from the PATA drive to the root ( / ) partition of the SATA drive, where it finds the correct vmlinuz and initrd files to boot the basic system and continue with Grub in the /boot/grub/ directory with the menu.lst file in that directory.

To go to Windows from that Grub menu, you will need the ```
title     Windows 
root		(hd0,0)
savedefault
makeactive
chainloader	+1
``` code which is in the commented out portion of the menu.lst files you have, then the ```
title      Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c07604d8-bfff-4a0b-a62c-f71624d469ab ro quiet splash xforcevesa
initrd		/boot/initrd.img-2.6.24-19-generic
``` or whatever code you need to properly boot your kernel should be another selection in your menu.lst.

---

### Post by caljohnsmith on 2008-09-06
Cwsnyder, we appreciate your input, but if you would read carefully through the entire thread, you will see that we are not trying to put Grub in the MBR of his IDE drive and then point it to his SATA drive at this point; if 44tr does that, then if he disconnects the SATA HDD at any point, or if anything happens to his SATA drive, he will not be able to boot Windows. We are trying a different method by first using the Grub4dos that he all ready has installed in Windows. Thanks for your input though.

---

### Post by cwsnyder on 2008-09-06
Sorry for the confusion, it was a long thread.  I would think that if you ever disconnect the SATA drive, it would STILL cause problems.  Grub, as far as I know, which would include what I know of Grub4dos (very scanty) still points to the _last_ installed bootable partition.  Of course, that was probably what your machinations was trying to do was rebuild the MBR to point to your desired partition.

I am trying to learn, too.  That is why I am reading here!  If you had had a separate partition for the WUBI install, or had had a small Linux install on the IDE, couldn't you have used ```
root (hd0,1)
setup (hd0)
``` which would have pointed to that small Linux install and its /boot/grub/menu.lst.

---

### Post by gn2 on 2008-09-07
> **egalvan said:**
> OK, I'll bite:

WHY is it "much better" to have all systems on one drive?


Because it's much easier to manage.

> **egalvan said:**
> BTW,
I've installed multiple os's on multiple drives, and NO UUID tweaking.

You're lucky, others are not.
Much depends on the motherboard controllers and the BIOS, some are less co-operative than others.
Which is what I reckon the problem is here in this thread.

Install all the OS's on one drive and the problem would simply melt away.

---

### Post by caljohnsmith on 2008-09-07
> **cwsnyder said:**
> Sorry for the confusion, it was a long thread.  I would think that if you ever disconnect the SATA drive, it would STILL cause problems.  Grub, as far as I know, which would include what I know of Grub4dos (very scanty) still points to the _last_ installed bootable partition.  Of course, that was probably what your machinations was trying to do was rebuild the MBR to point to your desired partition.

No problem at all, this definitely is a long thread. I hope I didn't sound too brusque in my last reply, because I'm certainly not trying to discourage anyone from sharing their ideas. :) In general, you are right when you say that Grub points to the last bootable partition, but only if the OS in that partition also installed Grub, and only if the user allowed Grub to be installed to the MBR. But you don't have to install Grub to the MBR; for instance, if you install Ubuntu to partition sda2, you can tell Ubuntu to install Grub to the partition boot record (PBR) of sda2 instead of the master boot record (MBR). All you have to do at the end of the install is click the "advanced" button, and instead of letting Grub install to (hd0) or the MBR, you tell it to install to (hd0,1) or sda2. That then makes sda2 its own little self-contained bootable drive, if you want to think of it that way, because then you can "chain load" it from the Grub menu in the same way you can chain load other HDDs.  
[quote=cwsnyder]
I am trying to learn, too.  That is why I am reading here!  If you had had a separate partition for the WUBI install, or had had a small Linux install on the IDE, couldn't you have used ```
root (hd0,1)
setup (hd0)
``` which would have pointed to that small Linux install and its /boot/grub/menu.lst.[/QUOTE]
Yes, and I'm still learning too. :) I totally agree with your idea that having a small linux partition on the IDE drive would allow 44tr to use Grub on the IDE drive while keeping the IDE drive entirely independent of the SATA drive. In fact, he wouldn't even need a full linux install; you can make a super-dinky 10 MB partition dedicated only to Grub and that's all it takes. I've actually done this on my HDD so that Grub is entirely independent of all the different linux distros I have installed. I thought about this earlier, but I wasn't going to suggest that to 44tr yet, because I'm reasonably sure we can either get Grub4DOS working or the modified boot.ini strategy working.

---

### Post by 44tr on 2008-09-07
OK, I can't believe this, but...
     I added the lines to menu.lst
     I rebooted to the IDE and Windows bootloader came up.
     Selected Ubuntu (wubi install)
     Grub for DOS menu came up and selected SATA hd1 option, message said booting SATA ... but then nothing.
     Reboooted and repeated until selected SATA hd2 option, SATA grub menu immediately came up!  Yeah! :)
     Selected Ubuntu option like normal and got : Error 17, unable to mount selected partition. :(
     This is like science; you hopefully learn something from your failures that will help you succeed further on. :lolflag:
     Now what?

---

### Post by caljohnsmith on 2008-09-07
> **44tr said:**
> OK, I can't believe this, but...
     I added the lines to menu.lst
     I rebooted to the IDE and Windows bootloader came up.
     Selected Ubuntu (wubi install)
     Grub for DOS menu came up and selected SATA hd1 option, message said booting SATA ... but then nothing.
     Reboooted and repeated until selected SATA hd2 option, SATA grub menu immediately came up!  Yeah! :)
     Selected Ubuntu option like normal and got : Error 17, unable to mount selected partition. :(
     This is like science; you hopefully learn something from your failures that will help you succeed further on. :lolflag:
     Now what?
That's great news, and I think I found the problem (it was my previous mistake). Replace the SATA hd2 option in your Windows menu.lst with:
```
title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```
Also, since we know the "SATA (hd1)" option doesn't work, you can remove that if you haven't all ready. Let me know how it goes. :)

[COLOR="Red"]EDIT: the above syntax works with Grub, but does not seem to work with Grub4DOS. See post #71 for the correct syntax that worked.[/COLOR]

---

### Post by egalvan on 2008-09-07
> **caljohnsmith said:**
> No, I don't think the SATA drive would need to be listed as second in the boot order in order to boot it from the Windows IDE drive; those boot order settings in BIOS might possibly affect how Grub sees the order of HDDs though, I'm not exactly sure since I've come across what seems to be contradictory evidence of that in the past. 

OK I can chime in with some thoughts here, but it is possibly outdated.

Back when all computers had two floppys, two hard drives and no CD-ROM drives, I worked on BIOS code.

The BIOS picked up the drive/partition order differently than the operating system, including  W9x.


Assuming TWO hard drives, each with two PRIMARY partitions..

The BIOS would interrogate the first drive, then look for a valid PRIMARY PARTITION. 
If found, assign C:
Same for the second drive, except assign D:
The BIOS was blind to an EXTENDED PARTITION; to BIOS it did not exist.

This info was handed off to the OS.

The OS would interrogate drive C:, then look for ANY VALID PARTITION, primary or extended.
If any were found past the first, then letters would be assigned,
starting with the next higher letter.
Since C: and D: had both  been taken, this meant that any extra partitions would start with E:.

So the partitioning lettering would be

first drive
C: E:
D: F:


The problems started when you removed that second drive...
the partition letters changed.

single drive
C: E:

GRUB may be doing something similar.
(I stopped coding this stuff years ago, so it may have no relevance today)


ErnestG

P.S.
Back then, I "solved" this problem by using only extended partitions on the second (or third or fourth) drives.

A neat trick in those days was to use an extended on the first drive...
when someone else tried to use your machine, it would give "no operating system found". 
You needed a boot floppy to kick-start it. :). Hey, it kept the "noobs" off your machines :lolflag:

And some of us found ways around the "four-partition" limit.

---

### Post by 44tr on 2008-09-07
> **caljohnsmith said:**
> That's great news, and I think I found the problem (it was my previous mistake). Replace the SATA hd2 option in your Windows menu.lst with:
```
title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
```
Also, since we know the "SATA (hd1)" option doesn't work, you can remove that if you haven't all ready. Let me know how it goes. :)

Hmmm.  Well I removed the hdl option and changed the other one as directed above (copy and paste over).  Booted from IDE, choose wubi Ubuntu from Windows loader, selected hd2 option and got ...

loading Ubuntu SATA HDD (hd2)
GRUB
... then nothing else happened.

I'll note that before I made this change, when I selected the hd2 option and got the GRUB menu to come up on SATA a second time, I chose the Windows option that we added, and it booted to Windows on IDE just fine.  It seems like we are so close ...

---

### Post by 44tr on 2008-09-07
> **gn2 said:**
> 
You're lucky, others are not.
Much depends on the motherboard controllers and the BIOS, some are less co-operative than others.
Which is what I reckon the problem is here in this thread.

Install all the OS's on one drive and the problem would simply melt away.

Oh, I'll admit: I'm tempted at this point to reinstall Windows on the SATA and then Ubuntu, but it takes forever to get Windows back to the point of usability.  Admittedly, I wouldn't have to get it back to the point it is now, since I could move a lot of my work to Ubuntu, but it would still be a major pain.  I may end up there though if we can't find an elegant solution to my current dilemma.  Thanks.

---

### Post by caljohnsmith on 2008-09-07
Yes, we basically have it working, but I think the problem is that Grub4DOS does not use the exact same syntax as Grub. Try changing the Windows menu.lst as:
```
title   Ubuntu SATA HDD (hd2)
rootnoverify   (hd2)
map (hd2) (hd0)
chainloader +1

```
If that doesn't work, then remove the mapping line altogether, and we can tweak the menu.lst on your Ubuntu SATA drive to make things work. It is just a lot more ideal if we can do the mapping like above, because then it will be possible to boot straight from the SATA drive as well and have everything work in case your Windows IDE drive has problems at any point.

---

### Post by 44tr on 2008-09-07
> **caljohnsmith said:**
> 
Yes, and I'm still learning too. :) I totally agree with your idea that having a small linux partition on the IDE drive would allow 44tr to use Grub on the IDE drive while keeping the IDE drive entirely independent of the SATA drive. In fact, he wouldn't even need a full linux install; you can make a super-dinky 10 MB partition dedicated only to Grub and that's all it takes. I've actually done this on my HDD so that Grub is entirely independent of all the different linux distros I have installed. I thought about this earlier, but I wasn't going to suggest that to 44tr yet, because I'm reasonably sure we can either get Grub4DOS working or the modified boot.ini strategy working.

A very interesting idea.  The thing that concerns me is that I use Tune-Up Utilities 2007 on Windows XP, which you may recall writes to the Windows boot.ini file and perhaps other things when you use it to make modifications.  I really like using TU when I have to deal with Windows and I'm concerned that if I toss the Windows loader, it might have unforseen consequences.  I'm game, though, IF it turns out to be a more elegant solution AND I can boot either drive independently so if a boot record gets corrupted, I can still login and ask you guys how to fix it :)

---

### Post by 44tr on 2008-09-07
Woooo HOOOO!

Booted to IDE, Selected wubi Ubuntu, selected Ubuntu SATA hd2 got GRUB SATA menu, selected Kubuntu and it booted to Kubuntu without error; I'm using Konqueror to write this post! :guitar:

Now, if I haven't worn out everybody's patience, especially the magisterial caljohnsmith, has this success shown us the way to a more elegant solution than three boot menus to get to my main working OS? :popcorn:

---

### Post by caljohnsmith on 2008-09-07
After 73 posts to this thread, we finally have a working solution! :)

I should mention that one of my forum friends was kind enough to point out to me last night the problems with my post #42, where we were trying to do the "modified boot.ini strategy." If you want to try one last time to get that to work, I think we can do it now.

This time though, we are assuming you are booting from your IDE drive, then booting Grub on your SATA, and then finally booting into Ubuntu from the SATA drive's Grub menu.
[LIST=1]
[*]```

cd ~/Desktop
sudo dd if=/dev/sda2 of=sda2_PBR.bin bs=512 count=1
```
That will save the sda2 PBR to your desktop.
[*]Next temporarily install Grub to the PBR of sda2, but it will use special mapping so we can then move it to your Windows HDD and hopefully make it work:
```
sudo grub
grub> device (hd2) /dev/sda
grub> device (hd0) /dev/sda
grub> root (hd2,1)
grub> setup (hd0,1)
grub> quit
```
[*]Next copy the new Grub PBR:
```
sudo dd if=/dev/sda2 of=sda2_grub_PBR.bin bs=512 count=1
```
[*]Then put the original sda2 PBR back:
```
sudo dd if=sda2_PBR.bin of=/dev/sda2 bs=512 count=1
```
[*]Put the sda2_grub_PBR.bin file in the Windows root directory on sdb1:
```
sudo umount /dev/sdb1  [COLOR="Blue"][just in case sdb1 is all ready mounted somewhere else][/COLOR]
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mv sda2_grub_PBR.bin /mnt/sdb1/.
```
[*]Then edit the Windows boot.ini file:
```

sudo nano /mnt/sdb1/boot.ini
```
Add the following line at the very end and save:
```
C:\sda2_grub_PBR.bin="Grub Menu on SATA HDD"
```
[/LIST]
Let's give it at least this last try; let me know how it goes. :)

---

### Post by gn2 on 2008-09-07
> **44tr said:**
> Oh, I'll admit: I'm tempted at this point to reinstall Windows on the SATA and then Ubuntu, but it takes forever to get Windows back to the point of usability.  Admittedly, I wouldn't have to get it back to the point it is now, since I could move a lot of my work to Ubuntu, but it would still be a major pain.  I may end up there though if we can't find an elegant solution to my current dilemma.  Thanks.

You could *clone* the Windows drive from the IDE to the SATA...?

Cloning copies all your programs, settings, files etc, nothing would be lost.

---

### Post by 44tr on 2008-09-07
> **gn2 said:**
> You could *clone* the Windows drive from the IDE to the SATA...?

Cloning copies all your programs, settings, files etc, nothing would be lost.

That sounds great, however, my Windows XP installation is (excessively) complex with different partitions for the OS, application installs, data files, etc. spread across two drives.  I rather regret this now, but it seemed like a good idea at the time. :)  With any luck, I will eventually outgrow Windows entirely; I certainly don't plan to go to Vista.  Thanks for the idea, though.  I may come back to it (if an expert is available to guide me) if I get this setup a bit more evolved.

---

### Post by 44tr on 2008-09-07
Followed post #74 instructions meticulously.  Final result was error 17, unable to mount ...

Are we whipped?  Is it time to start thinking about that dinky grub partition installation on the IDE drive?  That still seems like it would keep both drives independent, not take forever to boot, and pretty easy to fix (with the right knowhow) should the MBR get mucked up.  I took the floppy drive out of the computer entirely, but I guess you can fix it from a CD-ROM boot if things get really confused.  I do happen to have a 750GB external USB2 drive that I can connect if that becomes an important tool.  USB thumb drive too.

I'll understand if this is as far as we go; it is already above and beyond the call of duty.

---

### Post by caljohnsmith on 2008-09-07
> **44tr said:**
> Followed post #74 instructions meticulously.  Final result was error 17, unable to mount ...
When you selected the "Grub Menu on SATA HDD" from you Windows boot loader menu, did you immediately get the error 17? Or did you get the Grub menu from your SATA drive, and when you tried to boot Ubuntu you got the error 17? If it is the latter case, then that is actually great news, because we can expect that error since your SATA grub menu is not set up yet to work with the "modified boot.ini" approach. 

So if that is true, when you get the Grub menu from your SATA drive, try selecting the Ubuntu entry, hit "e" to edit it, select the line that says "root (hd0,1)", hit "e", change it to "root (hd2,1)", return, then "b" to boot it. That should be all it takes to boot it. Let me know how it goes.

---

### Post by 44tr on 2008-09-07
> **caljohnsmith said:**
> When you selected the "Grub Menu on SATA HDD" from you Windows boot loader menu, did you immediately get the error 17? Or did you get the Grub menu from your SATA drive, and when you tried to boot Ubuntu you got the error 17? If it is the latter case, then that is actually great news, because we can expect that error since your SATA grub menu is not set up yet to work with the "modified boot.ini" approach. 

So if that is true, when you get the Grub menu from your SATA drive, try selecting the Ubuntu entry, hit "e" to edit it, select the line that says "root (hd0,1)", hit "e", change it to "root (hd2,1)", return, then "b" to boot it. That should be all it takes to boot it. Let me know how it goes.

Yes, it is the latter case.  If I edit as described, will the SATA still boot independently?  My guess is yes, IF we add an entry to GRUB to take care of that scenario (or add a full entry for the case described above?  Am I right?  How best to edit?

---

### Post by caljohnsmith on 2008-09-07
> **44tr said:**
> Yes, it is the latter case.  If I edit as described, will the SATA still boot independently?  My guess is yes, IF we add an entry to GRUB to take care of that scenario (or add a full entry for the case described above?  Am I right?  How best to edit?
That's great news it is the latter case, because it means the "modified boot.ini" method actually worked this time. Forum member meierfra deserves the credit for it since he pointed out the mistakes in my post #42. And you are right, you could have separate entries in your SATA's Grub menu.lst to handle the two cases of booting from SATA or booting from IDE. If you are OK with that, then all you would need to do is copy your existing Ubuntu entries in menu.lst to new lines, and change the (hd0,1) to (hd2,1). 

As you asked about earlier, one last option that is still open to you is having your own dedicated Grub partition on the IDE drive. That's fairly easy to do (that's what I've done on my HDD), and that would allow either Windows or Ubuntu to boot from the Grub menu on start up (you wouldn't have to go through more than one menu to boot Ubuntu). All you need to do is shrink the end of your Windows partition on the IDE about 10-15 MB so you can create a 10 MB primary partition in the newly created space. You can do that easily in gparted (Ubuntu's partition editor), and also format the partition to be ext2/ext3. Then it would take a few simple steps to install Grub.

---

### Post by 44tr on 2008-09-07
> **caljohnsmith said:**
> That's great news it is the latter case, because it means the "modified boot.ini" method actually worked this time. Forum member meierfra deserves the credit for it since he pointed out the mistakes in my post #42. And you are right, you could have separate entries in your SATA's Grub menu.lst to handle the two cases of booting from SATA or booting from IDE. If you are OK with that, then all you would need to do is copy your existing Ubuntu entries in menu.lst to new lines, and change the (hd0,1) to (hd2,1). 

As you asked about earlier, one last option that is still open to you is having your own dedicated Grub partition on the IDE drive. That's fairly easy to do (that's what I've done on my HDD), and that would allow either Windows or Ubuntu to boot from the Grub menu on start up (you wouldn't have to go through more than one menu to boot Ubuntu). All you need to do is shrink the end of your Windows partition on the IDE about 10-15 MB so you can create a 10 MB primary partition in the newly created space. You can do that easily in gparted (Ubuntu's partition editor), and also format the partition to be ext2/ext3. Then it would take a few simple steps to install Grub.

I'm starting to think this latter option makes sense.  I do plan to use another partition for testing other distros, perhaps taking out that 80 GB drive in the future, and who knows what other changes.  It seems the current solution may be kinda fragile and might break anytime I make a change.  The grub installation looks more robust (true?) and easier to fix should something unexpected happen.  Can you walk me through?  Any risks I should be aware of?

---

### Post by caljohnsmith on 2008-09-07
> **44tr said:**
> I'm starting to think this latter option makes sense.  I do plan to use another partition for testing other distros, perhaps taking out that 80 GB drive in the future, and who knows what other changes.  It seems the current solution may be kinda fragile and might break anytime I make a change.  The grub installation looks more robust (true?) and easier to fix should something unexpected happen.  Can you walk me through?  Any risks I should be aware of?
The only pertinent risk I think is the usual risk you take when doing any repartitioning; just make sure everything is backed up first. It wouldn't hurt to defragment your Windows partition, but all you are going to do is shrink it by only 10-15 MB, which is almost microscopic compared to its size. :) To do that, probably the easiest is to boot your Ubuntu Live CD and use gparted from there since you surely won't have the Windows HDD mounted. To run gparted, I think it is under System > Admin > Partition Editor (I'm in KDE right now so that's from memory), or just do:```

gksudo gparted

```
The main thing to remember is that gparted does not make any changes until you hit the "apply" button, so that is its insurance against screwing up. Anyway, select the Windows IDE HDD (upper right corner), select your main Windows partition, shrink it from the end by 10-15 MB, set up a new 10 MB primary partition with that space, and click apply. Then use gparted to format the new partition to either ext2 or ext3. Once you get that far I'll give you directions how to install Grub to it.

---

### Post by 44tr on 2008-09-07
> **caljohnsmith said:**
> 
The main thing to remember is that gparted does not make any changes until you hit the "apply" button, so that is its insurance against screwing up. Anyway, select the Windows IDE HDD (upper right corner), select your main Windows partition, shrink it from the end by 10-15 MB, set up a new 10 MB primary partition with that space, and click apply. Then use gparted to format the new partition to either ext2 or ext3. Once you get that far I'll give you directions how to install Grub to it.

BTW, I converted my Kubuntu installation to Ubuntu which I prefer so far.  It was easy and I am more used to it.  While I was in Ubuntu (on SATA), I thought I could just use gparted from here.  I loaded it, but it wouldn't let me shrink my windows partition (not mounted), only delete it.  It took forever to scan the devices and I got the following command line errors:

```
chris@office1:~$ gksudo gparted
======================
libparted : 1.7.1
======================
Unable to open /dev/fd0 read-write (Read-only file system).  /dev/fd0 has been opened read-only.
Input/output error during read on /dev/fd0
Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Unable to open /dev/scd1 read-write (Read-only file system).  /dev/scd1 has been opened read-only.
Unable to open /dev/scd1 - unrecognised disk label.

```

I don't have a floppy and I guess scd1 is mounted.  Do I need to worry about getting rid of these errors?  If I do, will gparted not take two or three minutes to scan the devices?  This is royal pain since every time you unmount a partition or do anything it rescans the devices for another few minutes.

Now I will go do as instructed ;) and boot from live CD.

---

### Post by 44tr on 2008-09-07
> **caljohnsmith said:**
> 
The main thing to remember is that gparted does not make any changes until you hit the "apply" button, so that is its insurance against screwing up. Anyway, select the Windows IDE HDD (upper right corner), select your main Windows partition, shrink it from the end by 10-15 MB, set up a new 10 MB primary partition with that space, and click apply. Then use gparted to format the new partition to either ext2 or ext3. Once you get that far I'll give you directions how to install Grub to it.

OK, now I have a 15.67 MB ext3 primary partition immediately after my Windows partition on the IDE drive. (rounded to nearest cylinder, it was either 7.8 or 15.67), so what next?

I guess I should also ask: will I still be able to boot to wubi Ubuntu after we do this?  I think I backed up the key stuff, so I would be OK if I couldn't; just want to know.

---

### Post by caljohnsmith on 2008-09-07
> **44tr said:**
> OK, now I have a 15.67 MB ext3 primary partition immediately after my Windows partition on the IDE drive. (rounded to nearest cylinder, it was either 7.8 or 15.67), so what next?

I guess I should also ask: will I still be able to boot to wubi Ubuntu after we do this?  I think I backed up the key stuff, so I would be OK if I couldn't; just want to know.
Sure, you haven't touched Wubi or your Windows boot loader, so you will still have those options when you boot Windows from Grub. The commands below are how to install Grub to your new IDE partition while you are in Ubuntu on your SATA drive. Note the directions assume your new Grub partition is on sdb2, so if it isn't, change the commands accordingly:
```
sudo mkdir /media/sdb2
sudo mount /dev/sdb2 /media/sdb2
sudo grub-install --root-directory=/media/sdb2 /dev/sdb
sudo cp /boot/grub/menu.lst /media/sdb2/boot/grub/.

```
Next modify the menu.lst in your new Grub partition:
```
gksudo gedit /media/sdb2/boot/grub/menu.lst &
```
For all the Ubuntu entries in menu.lst, make sure all "root (hdX,Y)" lines read "root (hd2,1)". And your Windows entry should simply be:
```
title   Windows XP
root    (hd0,0)
makeactive
chainloader +1
```
Hopefully your partitioning went OK and there won't be any issues booting Windows, but let me know what happens.

---

### Post by 44tr on 2008-09-07
Whoa! Awesome!!\\:D/  sdb3 is the name actually.  sdb2 is my extended partition and it did not rename even though it comes after sdb3.

BUT, Grub menu comes up immediately, Windows option brings Windows loader up and options work!  Choosing Ubuntu boots up Ubuntu on SATA like a charm!

Maybe some day I will understand how this all worked better, but for now I'm just happy it all WORKS!!  Thanks a bunch man.

---

### Post by caljohnsmith on 2008-09-07
> **44tr said:**
> Whoa! Awesome!!\\:D/  sdb3 is the name actually.  sdb2 is my extended partition and it did not rename even though it comes after sdb3.

BUT, Grub menu comes up immediately, Windows option brings Windows loader up and options work!  Choosing Ubuntu boots up Ubuntu on SATA like a charm!

Maybe some day I will understand how this all worked better, but for now I'm just happy it all WORKS!!  Thanks a bunch man.
You're welcome, glad that everything is booting OK for you now. :)

Just one last thing I thought I would mention: when you get new kernel upgrades in Ubuntu, it will only update your menu.lst on the SATA drive, not your new menu.lst on the IDE drive. You will have to manually copy over the new kernel entries from your SATA menu.lst to your IDE menu.lst if you want to be able to boot them. 

Anyway, cheers and have fun.

---

