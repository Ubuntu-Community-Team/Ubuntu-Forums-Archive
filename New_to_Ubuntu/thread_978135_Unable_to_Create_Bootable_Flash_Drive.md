---
title: "Unable to Create Bootable Flash Drive"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by gmgj on 2008-11-10
I have tried a couple of different ways to create an bootable usb flash drive.

I have used the instructions here:
[http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/](http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/)

and alternate ways, but the flash does not boot.  The CD boots fine.

My BIOS is set to boot from CDROM then USB-FDD then hardrive.
This is my Bios

BIOS Type:	Phoenix-Award
BIOS Date:	November 4th 2005
BIOS ID:	11/04/2005-P4M800Pro-823-6A7L6M4AC-00-None
BIOS OEM:	W7211VMS V1.1 12/13/05 7111 - 6.00 PG
Chipset:	VIA 82C314 rev 0
SuperIO:	Unknown
Manufacturer:	powerspec4.2b
Motherboard:	ps7111


Driver Downloads & Updates / Windows XP
Components Windows XP Driver Description 
System Board  VIA 4in1 Chipset v5.00
Video  VIA S3 K8M800 Unichrome Video Drivers
Sound  Realtek Audio Drivers
LAN  Realtek 8100C Network Drivers

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

This is what the flash drive look like from Windows XP cmd line.


c:\bat>dir e:
 Volume in drive E is ubuntu8
 Volume Serial Number is 4918-BACF

 Directory of E:\

11/10/2008  11:46 PM    <DIR>          casper
11/10/2008  10:54 PM    <DIR>          dists
11/10/2008  10:54 PM    <DIR>          install
11/10/2008  10:54 PM    <DIR>          pics
11/10/2008  10:54 PM    <DIR>          pool
11/10/2008  10:54 PM    <DIR>          preseed
11/10/2008  10:54 PM    <DIR>          .disk
11/10/2008  10:54 PM            49,179 16x16.fnt
11/10/2008  10:54 PM                 0 adtext.cfg
11/10/2008  10:54 PM             7,500 back.jpg
11/10/2008  10:54 PM             2,845 be.tr
11/10/2008  10:54 PM             2,356 bg.tr
11/10/2008  10:54 PM             2,048 boot.cat
11/10/2008  10:54 PM            99,328 bootlogo
11/10/2008  10:54 PM             1,534 bs.tr
11/10/2008  10:54 PM             8,071 ca.hlp
11/10/2008  10:55 PM             1,958 ca.tr
11/10/2008  10:55 PM             1,923 cs.tr
11/10/2008  10:55 PM             1,693 da.tr
...
11/10/2008  10:55 PM             1,629 nn.tr
11/10/2008  10:55 PM             1,997 pl.tr
11/10/2008  10:55 PM               185 po4a.cfg
11/10/2008  10:55 PM               155 prompt.cfg
11/10/2008  10:55 PM             1,926 pt.tr
11/10/2008  10:55 PM             7,373 pt_BR.hlp
11/10/2008  10:55 PM             1,807 pt_BR.tr
11/10/2008  10:55 PM             8,577 ro.hlp
11/10/2008  10:55 PM             1,895 ro.tr
11/10/2008  10:55 PM            11,354 ru.hlp
11/10/2008  10:55 PM             3,134 ru.tr
11/10/2008  10:55 PM             7,528 sk.hlp
11/10/2008  10:55 PM             1,961 sk.tr
11/10/2008  10:55 PM             1,748 sl.tr
11/10/2008  10:55 PM            19,640 splash.pcx
11/10/2008  10:55 PM            24,882 splash.png
11/10/2008  10:55 PM             1,766 sq.tr
11/10/2008  10:55 PM               360 stdmenu.cfg
11/10/2008  10:55 PM             7,237 sv.hlp
11/10/2008  10:55 PM             1,783 sv.tr
10/15/2008  05:17 PM               864 text.cfg
11/10/2008  10:55 PM             1,546 tl.tr
11/10/2008  10:55 PM             1,789 tr.tr
11/10/2008  10:55 PM             2,786 uk.tr
11/10/2008  10:55 PM           144,392 vesamenu.c32
11/10/2008  10:55 PM             2,385 vi.tr
11/10/2008  10:55 PM             6,281 zh_CN.hlp
11/10/2008  10:55 PM             1,601 zh_CN.tr
11/10/2008  10:55 PM             1,652 zh_TW.tr
11/10/2008  10:55 PM             5,086 md5sum.txt
11/10/2008  10:55 PM               223 README.diskdefines
11/10/2008  10:55 PM           124,152 mt86plus
11/10/2008  10:55 PM                76 syslinux.cfg
              93 File(s)        714,518 bytes
               7 Dir(s)   3,307,487,232 bytes free

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

pendrivelinux has a script version and a manual install insturctions.  neither worked for me.

How do I tell if I created a valid boot partition?

My guess is that this a partition problem, I screwed up the first attempt and know every time I try and fdisk, it just reverts back to the old version.  see

...
partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to reboot
	to re-read your partition table. 

...
In one install attempt
When I boot from ubuntu; I see

/dev/sdb1 as FAT16, while I was installing it; it said to big, will see as FAT12?

Here is another attempt using the u810.sh script 

I get errors like this
...
Warning: You requested a partition from 0.00B to 4043MB.
The closest location we can manage is 512B to 31.7kB.  Is this still acceptable to you?

...

ubuntu@ubuntu:~$ wget pendrivelinux.com/downloads/u810/u810.sh
--2008-11-10 20:31:16--  [http://pendrivelinux.com/downloads/u810/u810.sh](http://pendrivelinux.com/downloads/u810/u810.sh)
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3074 (3.0K) [application/x-sh]
Saving to: `u810.sh'

ubuntu@ubuntu:~$ chmod +x u810.sh && sh u810.sh
############# USB INSTALLER SCRIPT #############



================================================

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd3047f66

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 8086 MB, 8086618112 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         935     7510356   83  Linux
/dev/sdb2             936         983      385560    5  Extended
/dev/sdb5             936         983      385528+  82  Linux swap / Solaris

=========== Locate your flash drive ============

Please locate your flash drive from the list of
devices displayed above and enter it's letter.

For example, if your flash drive is /dev/sdx,
you would type x and then press Enter

What is your drive letter?:
b

=========== Creating the partitions ===========

umount2: Invalid argument
umount: /dev/sdb1: not mounted
umount2: Invalid argument
umount: /dev/sdb2: not mounted
Error: Partition /dev/sdb1 is being used. You must unmount it before you modify it with Parted.
Error: Partition /dev/sdb2 is being used. You must unmount it before you modify it with Parted.
Warning: You requested a partition from 0.00B to 4043MB.
The closest location we can manage is 512B to 31.7kB.  Is this still acceptable to you?
Warning: You requested a partition from 4043MB to 8087MB.
The closest location we can manage is 8085MB to 8087MB.  Is this still acceptable to you?

============ Creating filesystem ============

mkfs.vfat 2.11 (12 Mar 2005)
umount2: Invalid argument
umount: /dev/sdb2: not mounted
mke2fs 1.41.3 (12-Oct-2008)
mkfs.ext2: Device size reported to be zero.  Invalid partition specified, or
	partition table wasn't reread after running fdisk, due to
	a modified partition being busy and in use.  You may need to reboot
	to re-read your partition table.

============ Stage 1 completed ==============

Please remove and reinsert your flash drive.
Wait for the mounted partitions to appear on
your desktop, and then press Enter to continue


===== Stage 2: creating the portable USB ====

Moving on to create the portable system.

Reading package lists... Done
Building dependency tree
Reading state information... Done
syslinux is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
/dev/sdb1: No such file or directory

Now copying files to your flash drive.
Please wait...

cp: cannot create symbolic link `/media/ubuntu8/dists/stable': Operation not permitted
cp: cannot create symbolic link `/media/ubuntu8/dists/unstable': Operation not permitted
--2008-11-10 20:42:05--  [http://pendrivelinux.com/downloads/u810/text.cfg](http://pendrivelinux.com/downloads/u810/text.cfg)
Resolving pendrivelinux.com... 69.89.27.206
Connecting to pendrivelinux.com|69.89.27.206|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 864 [text/plain]
Saving to: `text.cfg'

100%[======================================>] 864         --.-K/s   in 0s

2008-11-10 20:42:06 (46.1 MB/s) - `text.cfg' saved [864/864]


=========== Stage 2 completed =============

All finished, your flash drive is now ready
Press Enter to close this window...

xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

I just tried the new Budweiser American Ale. its a reasonable facsimile of Bass.  If your in Boston, I am buying the beer your house or mine.

I wrote my first shell script in 5 minutes, it took me a day to figure out you needed to put a . in front of it to get it to execute.

---

### Post by phidia on 2008-11-10
Did you notice the link from the link you provided [here]("http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/")?

---

### Post by bumanie on 2008-11-10
Personally, I have found bootable pendrives (with persistent), boot some computers but won't boot others - ??why?? - probably something quirky in the bios on computers that won't boot this way.

---

### Post by Arlo012 on 2008-11-10
> **bumanie said:**
> Personally, I have found bootable pendrives (with persistent), boot some computers but won't boot others - ??why?? - probably something quirky in the bios on computers that won't boot this way.

I have seen similar problems on my computers as well. Some BIOS just don't play nice when booting to USB drives. You can try it, but it's really a shot in the dark.

---

### Post by charonred on 2008-11-10
Just a suggestion; from my experience using a Mandriva 8 GB USB flash-drive; whenever I boot from a USB, I always use USB HDD (not USB FDD).

I'm in the process of getting a Kingston 16 GB USB flash-drive to run Intrepid 8.10 - I have it booting up ok, and I seemed to have 'fixed' network connection problem (still works after a couple of reboots), but still have several other issues to 'nut-out' yet :confused: but I'm getting there.

One thing that is odd with the Intrepid USB; if I want to reboot, when the PC starts booting, I quickly unplug and replug the USB in, otherwise the system just boots the hard drive ??

---

### Post by C.S.Cameron on 2008-11-10
Have you tried the usb-creator that comes with 8.10? it's located in System/Administration?
Make sure your flash drive is formatted FAT32.
In bios try to select your flash drive as first HDD.

---

### Post by charonred on 2008-11-10
I agree with C.S Cameron; the included installer in Intrepid seems to do a good job, though not without hiccups.
[see here]("http://ubuntuforums.org/showthread.php?p=6148491#post6148491") for more info

---

### Post by elvino on 2008-11-11
Just a suggestion - you probably know this already - but I found that I needed to format the pen drive using the HP format tool while in Windows. If I do it using the standard format tool in XP it always fails. When I use the HP tool it works every time
Paul

---

### Post by charonred on 2008-11-11
I just used XP to format it; then installed Live CD as per link from my previous post - but, what is a HP format tool ?

---

### Post by lisati on 2008-11-11
> **bumanie said:**
> Personally, I have found bootable pendrives (with persistent), boot some computers but won't boot others - ??why?? - probably something quirky in the bios on computers that won't boot this way.

> **Arlo012 said:**
> I have seen similar problems on my computers as well. Some BIOS just don't play nice when booting to USB drives. You can try it, but it's really a shot in the dark.

Ditto: my older laptop is happy to boot from usb DVD player but not pendrive. My desktop is happy to boot from pendrive.

---

### Post by charonred on 2008-11-11
After a bit of experimentation with the 'Live CD' USB I created, it seems it's simply an alternative 'Live' option to the CD - handy for PCs that don't have a CD/DVD drive.

But it's not a live USB 'install' of Ubuntu - can't be updated, and won't save some configurations or options; and it ends up only working on the PC it's been customised to.

So I'll create it again simply as a 'Live CD' on a USB stick with no update attempts or customisations.

---

### Post by gmgj on 2008-11-16
If anyone know how to change the bootable flash to go straight to ubuntu, that would be nice.

I have been able to get a **4gig** flash drive to boot.  In one session of testing, I can change wallpaper, add bookmarks to firefox and create text files.  

In another session, where I tried to uninstall evolution email and add the typing tutor.  I then moved it to another computer.  I ended up with a system that would boot; however, it would not display the desktop.  So I recreated the flash drive again.

I create a boot flash on my desktop and am using it on my laptop that has a broken optical drive.  When booting from my Toshiba Satellite P35, it logs this error


Nov 16 12:58:47 ubuntu kernel: [    0.348021] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Nov 16 12:58:47 ubuntu kernel: [    0.348021] ...trying to set up timer (IRQ0) through the 8259A ...
Nov 16 12:58:47 ubuntu kernel: [    0.348021] ..... (found apic 0 pin 2) ...
Nov 16 12:58:47 ubuntu kernel: [    0.389916] ....... works.

but keeps on chugging!

Thanks to all who offered help.


Kernel command line: BOOT_IMAGE=/casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

---

### Post by gmgj on 2008-11-16
Duh, I got unable to initialize HAL.  This laptop could be flaking out or perhaps its a compatibility problem.

System Type	X86-based PC	
Processor	x86 Family 15 Model 3 Stepping 4 GenuineIntel ~3200 Mhz	
BIOS Version/Date	TOSHIBA V1.40, 9/3/2005	
SMBIOS Version	2.31	

ATI MOBILITY RADEON 9000 IGP

0x00000062-0x00000062	Microsoft ACPI-Compliant Embedded Controller	OK	
0x00000066-0x00000066	Microsoft ACPI-Compliant Embedded Controller	OK	
0x0000A400-0x0000A47F	VIA OHCI Compliant IEEE 1394 Host Controller	OK	
0x0000A000-0x0000A0FF	Realtek RTL8139/810x Family Fast Ethernet NIC	OK	
0x0000FE00-0x0000FEFF	ENE CB-710/712/714/810 Cardbus Controller	OK	
0x0000FD00-0x0000FDFF	ENE CB-710/712/714/810 Cardbus Controller	OK	

Time to recreate and try on the desktop

---

### Post by PGTips91 on 2008-11-16
Hi,

I have been working on the problem of booting a USB pen drive for some time. I know it can be done because for a short while I was doing it, but, unfortunately cannot repeat the process.

I was sent an ISO file from [BakUp]("http://dreamlinuxforums.org/index.php?action=profile;u=2001") from the Dreamlinux forums and this bootable CD sometimes has been able to do the trick. I played around with this without success in booting the pendrive. 

That was until I installed another OS on the pen drive, [Cosmosis-X]("http://linuxinternationals.org/phpBB3/viewtopic.php?f=91&t=687"), which I was trying to reinstall on an older computer but could not due to CD-R errors [from the hardware as the CD is perfectly alright on another computer].

After playing around in GRUB, which was started from the 'Boot USB Dreamlinux' CD-R, and getting nowhere, I typed in 'reboot' and found myself in the pen drive installation. I had to check this a couple of times to believe it, but was then able to use the installation as a normal Hard Drive installed OS. I installed more applications, browsed the Web and added bookmarks, etc. I even rebooted and got back into the environment with all changes intact. I was using a 4 GB Rundisk USB drive and ended up with just over 1 GB of free space to store my data in - enough to download a 700 MB ISO file and burn it to CD if I wanted, so good enough for my needs.

This was brilliant, all I had ever hoped to achieve. The downside was that I didn't know the last step that had allowed it to happen. This was further complicated by discovering that now MS Windows would not boot and I had to restore the MBR, which I did with the 'Ultimate Boot Disk' and now the pen drive won't boot any more.   :confused:

My take on the situation, at present, is that if the BIOS has support for booting from a USB device, then setting the BIOS to boot from the pen drive first should work. If it does not support booting from USB device, then booting from a CD with the necessary USB drivers included in the initial ram disk image [initrd.img.gz] will allow the USB device to be recognised and then the booting process to be continued from the boot information on that device.

That is about where I am stopped as I don't know enough to build the initrd.img.gz image with the necessary drivers included.

Paul

---

### Post by charonred on 2008-11-16
1)
the Flash USB problem seems to be that the Ubuntu Live CD isn't intended to be a portable 'use and save' USB OS (whereas my Mandriva 8GB Flash updates, saves and, continues to boot almost any PC) - Ubuntu can be setup to save data and some settings; but when on a USB stick, Ubuntu the tries to update system files and save the changes which then messes up the 'Live CD' aspect of it, and usually won't run on other PCs

Suggested solution - don't do any updates, just use 'Live CD' on USB as is, and installed in 'persistent' mode if you want to save data on the USB stick - I have an Intrepid install on a 16 GB Kingston USB, but after updates, it won't run on any other PC other than the one I used when updating;  so I am going to start from scratch and set it up as is without any updates, so it will boot other PCs as well (like the 'Live CD').

[CENTER]-----------------------------------------------[/CENTER]

2)
With boot problem in above previous post; my experience has been that Grub attempts to install the bootloader on the first available IDE drive (regardless of other Sata/USB drives in system), which then messes up MBR for that drive, and thus access to any other OS you have on your PC (Grub really needs better, more 'human', way of identifying drives/partitions)

My solution so far has been to disconnect every other IDE/Sata/USB disk in my system before attempting installing OS and bootloader on selected drive; that way the bootloader gets installed on the same drive as the OS - once installed, I re-connect other drives and select the one I wish to boot from via bios (or F12 on laptops and later PCs) - bit of a pain, but it works ok for me.

---

