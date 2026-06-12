---
title: "[SOLVED] cant get past the loading screen in hardy studio"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by satanic-yobbo on 2008-05-06
i have recently upgraded from 7.10 studio to 8.04 studio and since the upgrade mu system wont get past the loading screen at all which means i cannot get to the login screen even to see what 8.04 looks like when it finally leaves the bot screen it goes to a command line type screen that is busybox and i cannot login to my system at all

anyone got any ideas on this one ??

---

### Post by Aearenda on 2008-05-06
There are several threads on busybox errors in Hardy - please do a forum search for 'hardy busybox' and see if any match your setup.

---

### Post by satanic-yobbo on 2008-05-07
no i cannot seem to find anything relating to my problem with hardy in the threads at all is there any code i can type into busybox to fix this or am i having to do a fresh install instead of an upgrade ?

---

### Post by Aearenda on 2008-05-07
I don't think reinstalling will change anything. For starters please boot into a running system off the live CD, start a command line, and post the output of ```
lspci -nn
``` 
Also please describe your computer - if it is a brand name computer tell us the brand and model number, otherwise the motherboard brand and model number; also how many disk drives, whether they are SATA or IDE, whether there are any removable hard drives present, and whether there are any relevant BIOS settings for SATA drives such as to allow them to emulate IDE drives, or to be RAID drives, and so on.

---

### Post by satanic-yobbo on 2008-05-07
this is the output 

ubuntu@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host [1039:0661] (rev 11)
00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) [1039:0003]
00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] [1039:0964] (rev 36)
00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (rev 01)
00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.1 Controller [1039:7001] (rev 0f)
00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
00:09.0 Multimedia audio controller [0401]: Creative Labs [SB Live! Value] EMU10k1X [1102:0006]
00:0a.0 Communication controller [0780]: Conexant HSF 56k HSFi Modem [14f1:2f00] (rev 01)
00:0e.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) [1002:5d44] (rev 01)


and the computer is an acer aspire t310 standard with 1gb ram and no other extra components added 

it ran gutsy really well just a problem with hardy for now that i hope can be resolved

---

### Post by Aearenda on 2008-05-07
Ok, so [http://ubuntuforums.org/showthread.php?t=634063](http://ubuntuforums.org/showthread.php?t=634063) suggests one line of attack - in Gutsy, was your first hard disk /dev/hda, or /dev/sda?

Here are the steps to find out, and to provide useful diagnostic info anyway: again running from the liveCD...
Step 1:
```
sudo fdisk -l
```
Please post the output from this. It will list all the partitions on all the drives the liveCD has found. From this, I hope you can tell which one is the partition that contains your /etc partition. Let's say that is /dev/sda1 - you can replace this in the following steps with the right one.

Step 2: Next, do this, still running on the live CD:
```
sudo mkdir /tmp/mnt
sudo mount /dev/sda1 /tmp/mnt
```
This creates a temporary directory at which we can mount the partition, and then mounts it so we can look at the files in it.

Step 3:
```
sudo cat /tmp/mnt/etc/fstab
```
Please post the output from this.

Step 4:
```
sudo vol_id --uuid /dev/sda1
```
Please repeat this for every listed partition in step 2, and post the output.

EDIT: When finished, step 5:
```
sudo umount /tmp/mnt
```

---

### Post by satanic-yobbo on 2008-05-07
ok here is the output of fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04260425

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9541    76638051   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

here is the output of sudo cat /tmp/mnt/etc/fstab

ubuntu@ubuntu:~$ sudo cat /tmp/mnt/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1d1d8338-a7f6-4ac2-8365-ec07dac7e82d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=464bd56a-b547-49bc-9fdd-8a7be52b3c3f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

here is the output for sudo vol_id --uuid /dev/sda1

1d1d8338-a7f6-4ac2-8365-ec07dac7e82d

sudo vol_id --uuid /dev/sda2 gives the response 
unknown volume type and 
sudo vol_id --uuid /dev/sda5 gives 

464bd56a-b547-49bc-9fdd-8a7be52b3c3f

i havent unmounted yet as i am not sure if there is more to do here because of the unkown file response

---

### Post by Aearenda on 2008-05-07
The response on sda2 is ok, it's the extended partition. Everything looks ok there, although [http://ubuntuforums.org/showthread.php?t=634063](http://ubuntuforums.org/showthread.php?t=634063) suggests we change fstab to use the /dev/sd* notation. That would be regressive, so I would prefer to try a different tack. Please unmount the partition, and reboot from the hard drive, but following these steps:

When you see the 'Press ESC to enter menu' message, press ESC.
At the Grub menu, press 'e'.
Use the cursor keys to move the highlighting down to the 'kernel' line shown, and press 'e' again.
Move to the end of the line, add a space if necessary, then add 'all_generic_ide' (without the quotes).
Press <ENTER> to complete the edit, and then press 'b' to boot.

If this works, you can make the result permanent by following the steps in [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15).

If this does not work, then we need to think again. FYI, it's late here - my next response may not appear for several hours!

---

### Post by satanic-yobbo on 2008-05-07
mate this worked a charm and after all the curry it has given me to have it up and running without the need for a live disk is almost worth the trip 900k,s south of here to where you are and buy you a beer but you'll just have to settle for a thanks instead for now unless i meet you in person some day and then i'll buy you a few cold beers thanks mete heaps

---

### Post by Aearenda on 2008-05-07
Yay! Good night!

---

### Post by satanic-yobbo on 2008-05-07
cheers mate ,, goodnight

---

### Post by jacobmyers on 2008-05-07
OK, this is odd. I've been getting the BusyBox thing, too. I don't know if it's because I'm making hardware changes (a few days ago, I installed a new fan, and yesterday I installed a hard drive). Every time I restart after changing something, I get the BusyBox thing. Here's the fun part - I'm still running Gutsy Studio (I haven't upgraded to Hardy yet). When I first experienced the weirdness, there was only one thread on here that had anything to do with BusyBox (and it didn't relate to my problem in any way).

 Anyway; I've managed to get things running again by reinstalling GRUB from the install CD. This is going to sound weird, but it's what's worked for me twice now:

 Restart with the CD in the drive. When the menu appears, select the "Rescue" option. Select your region and language. Then DO NOT select the keyboard layout from a list (doing so ruins everything - I can't explain that rationally - just press the keys). Then reinstall GRUB. When that's done, select the option that restarts the computer.

 It's weird freakin' mojo but it worked for me. Don't forget your rubber chicken.

---

### Post by Aearenda on 2008-05-07
Installing a new hard drive can change the order the drives are seen. When GRUB runs, it uses a 'map' of the hardware - maybe reinstalling it corrected the map after the change. Or maybe the moon was in the right quarter this time ;-)

---

