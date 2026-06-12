---
title: "USB drive wont mount for some odd reason"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by driftingdunk on 2008-06-27
Let me start off by saying on a scale of 1-10 of ubuntu knowledge, im at about a 2. 

My laptop, Acer Aspire 5100, needed a hard drive replacement. I installed ubuntu 8.04 using my usb flash drive using the instructions from pendrivelinux.com. (Ive installed 7.1 on my desktop in the past with no problems at all) I would have installed it normally had acer made a half decent latop whose dvd drive didn't die a week after he end of warranty, but thats beside the point.

I updated ubuntu after installing it, and since then im presented with an error, saying the usb drive cannot be mounted.I tried it with several (all using fat32, all function on windows)(Sandisk, Memorex, generic one)I read up on the problem and tried manually, which according to other people should still work.

I used:
> sudo mount /dev/sda1

I got:
> mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I tried unmounting and mounting again, but still nothing.

I read up some more, and tried to run gconf-editor.
> /system/storage/default_options/vfat/mount_options
gave me 
> [shortname=mixed,uid=,utf8,umask=077,exec,flush]

I tried removing flush, and putting it back in, still nothing

I have a feeling that the dead dvd drive is interfering with something.

Also, i dont recall if the usb drive mounted correctly before the updates.

Any help would be great.

PS: Here is my fdisk -l and fstab

> Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbca5bca5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         767     6160896    7  HPFS/NTFS
/dev/hda2             768       19457   150127425    5  Extended
/dev/hda5             768       19128   147484701   83  Linux
/dev/hda6           19129       19457     2642661   82  Linux swap / Solaris

Disk /dev/sda: 1031 MB, 1031274496 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         125     1004031    b  W95 FAT32


> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=68eb742e-b9ea-4551-825c-7e8d050132c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda6
UUID=a70fc927-1404-46ee-a465-f2c37aa60a68 none            swap    sw              0       0
/dev/sda1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


And last couple lines of dmesg after putting the drive in

> [ 6648.949539] usb 3-1: new high speed USB device using ehci_hcd and address 9
[ 6649.093984] usb 3-1: configuration #1 chosen from 1 choice
[ 6649.140341] scsi9 : SCSI emulation for USB Mass Storage devices
[ 6649.143289] usb-storage: device found at 9
[ 6649.143299] usb-storage: waiting for device to settle before scanning
[ 6657.985334] usb-storage: device scan complete
[ 6657.986193] scsi 9:0:0:0: Direct-Access     Memorex  M-Flyer B        PMAP PQ: 0 ANSI: 0 CCS
[ 6658.137149] sd 9:0:0:0: [sda] 2014208 512-byte hardware sectors (1031 MB)
[ 6658.138271] sd 9:0:0:0: [sda] Write Protect is off
[ 6658.138280] sd 9:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 6658.138285] sd 9:0:0:0: [sda] Assuming drive cache: write through
[ 6658.141639] sd 9:0:0:0: [sda] 2014208 512-byte hardware sectors (1031 MB)
[ 6658.142645] sd 9:0:0:0: [sda] Write Protect is off
[ 6658.142653] sd 9:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 6658.142658] sd 9:0:0:0: [sda] Assuming drive cache: write through
[ 6658.142666]  sda: sda1
[ 6658.144290] sd 9:0:0:0: [sda] Attached SCSI removable disk
[ 6658.144370] sd 9:0:0:0: Attached scsi generic sg0 type 0
[ 2663.606466] UDF-fs: No VRS found
[ 2663.649328] ISOFS: Unable to identify CD-ROM format.


Sorry for the lengthy post, i would love to get this fixed though

---

### Post by leemajors on 2008-06-27
do you have a windows boot as well? if so, try booting into that, safely remove the USB drive and do a proper shut down before booting back into ubuntu. that should fix the problem.

---

### Post by driftingdunk on 2008-06-27
I installed the windows via usb drive as well, and it was a very shaky type of install, and it wont boot back into windows now. 

> Windows could not start because of a computer disk hardware configuration problem. ETC.

I would prefer to get rid of the xp install all together, if someone can guide me how to do so without affecting my ubuntu, i would greatly appreciate it.

Thanks for the quick response.

---

### Post by driftingdunk on 2008-07-08
seems like no one knows whats wrong.. If anyone could help, it would be greatly appreciated..

Thanks again

---

### Post by Rocket2DMn on 2008-07-08
If /dev/sda1 is your USB drive, then yes, it is conflicting with fstab.  fstab has /dev/sda1 as your cd/dvd drive which you said is messed up.  So, let's comment out the entry in fstab.
```
gksudo gedit /etc/fstab
```
place a # in front of the last line, save and close.
Now plug in the USB drive and it should automount.

---

