---
title: "hd0: out of disk error on boot"
date: 2012-04-19
forum: New to Ubuntu
---

### Post by Calippo on 2012-04-19
Hi,

Installed 12.04 on my Dell Mini 9 netbook, however upon booting the system I am faced with the error message:

```

hd0: out of disk
press any key to continue...

```

The computer hangs at this point indefinitely.  The only exception to this is if a USB Key/CD drive is used with the Live CD where after 3-4 minutes will proceed to boot as normal.

GParted sees the partition structure on the drive, but is unable to make any changes throwing up read/write errors, nor am I am able to reinstall using the media.

Any ideas how to proceed?

Thanks!

---

### Post by cogier on 2012-04-19
Some of the Dell Minis had quite small solid state disks (4GB). You may need to use an older version of Ubuntu (10.04 works well on mine) or get a bigger disk.

---

### Post by Calippo on 2012-04-19
I should have mentioned I upgraded the standard 8GB SSD to a 32GB one a while ago.

---

### Post by audiomick on 2012-04-19
I suspect that the partition table has somehow gone wrong.

You might get some useful information from the boot info script. Look here

[http://ubuntuforums.org/showthread.php?t=1291280]("http://ubuntuforums.org/showthread.php?t=1291280")

for instructions on how to run this, or go straight to the link from the first post in that thread where the script is available at source forge.

[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

Run the script and have a good look at it. It looks daunting, but if you look at it closely and patiently, you might see something relevant.

Post the output back here. I'm not likely to be back tonight, but maybe someone else will see it who can help you further.

---

### Post by Calippo on 2012-04-19
Here's the boot info script

```

oot Info Script 0.60-git      [23 Feb 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 32.3 GB, 32287752192 bytes
255 heads, 63 sectors/track, 3925 cylinders, total 63062016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    58,886,143    58,884,096  83 Linux
/dev/sda2          58,888,190    63,059,967     4,171,778   5 Extended
/dev/sda5          58,888,192    63,059,967     4,171,776  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3066c1ca-5bf5-4102-b597-e0358dfb6a8e   ext4       
/dev/sda5        da655b8d-8faa-4a81-813b-2fb367c48912   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt

ADDITIONAL INFORMATION :
**************** log of boot-repair 2012-04-19__19h39 ****************
boot-repair version : 3.16-0ppa10~oneiric
boot-sav version : 3.17-0ppa18~oneiric
glade2script version : 0.3.2.1-0ppa7~oneiric
internet: no-internet
LIVESESSION is : yes (Ubuntu 11.10 , oneiric , Ubuntu , i686  )
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

BYTES_BEFORE_PART[1] (sda) = 2048 sectors * 512 bytes = 1048576 bytes.

OSPROBER:
/dev/sda1:Ubuntu precise (development branch) (12.04):Ubuntu:linux

BLKID:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="3066c1ca-5bf5-4102-b597-e0358dfb6a8e" TYPE="ext4"
/dev/sda5: UUID="da655b8d-8faa-4a81-813b-2fb367c48912" TYPE="swap"

1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

Total of 1 OS detected on sda disk.
TABLE_TYPE of sda is MSDos
sda1 : sda, not-sepboot, no-grub-install, grub , no-update-grub, no-apt-nor-yum, 32, no boot, /mnt/boot-sav/sda1, with-os, no-gpt, notEFItable, no-fstab.

PARTED:

Model: ATA RunCore 32G-C (scsi)
Disk /dev/sda: 32.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  30.1GB  30.1GB  primary   ext4            boot
2      30.2GB  32.3GB  2136MB  extended
5      30.2GB  32.3GB  2136MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


MOUNT:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus cdc-wdm0 cdc-wdm1 cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse hpet input kmsg log mapper mcelog mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 serial sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 v4l vga_arbiter video0 zero
/dev/mapper:  control

DF:

Filesystem    Type    Size  Used Avail Use% Mounted on
/cow     overlayfs   1003M   56M  947M   6% /
udev      devtmpfs    995M   12K  995M   1% /dev
tmpfs        tmpfs    401M  820K  401M   1% /run
/dev/sr0   iso9660    701M  701M     0 100% /cdrom
/dev/loop0
squashfs    676M  676M     0 100% /rofs
tmpfs        tmpfs   1003M   12K 1003M   1% /tmp
none         tmpfs    5.0M  4.0K  5.0M   1% /run/lock
none         tmpfs   1003M  104K 1002M   1% /run/shm

FDISK:

Disk /dev/sda: 32.3 GB, 32287752192 bytes
255 heads, 63 sectors/track, 3925 cylinders, total 63062016 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1019

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    58886143    29442048   83  Linux
/dev/sda2        58888190    63059967     2085889    5  Extended
/dev/sda5        58888192    63059967     2085888   82  Linux swap / Solaris



************************Before mainwindow
FSCK_ACTION no PASTEBIN_ACTION yes
recommendedrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet

************************Actions
FSCK_ACTION yes PASTEBIN_ACTION yes
customrepair, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 1)
Force Unmount all blkid partitions (for fsck) except / /boot /cdrom /dev /etc /home /opt /pas /proc /rofs /sys /tmp /usr /var
fsck from util-linux 2.19.1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: recovering journal
fsck.ext4: unable to set superblock flags on /dev/sda1

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so

Will restore the MBR_TO_RESTORE : sda (mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
bootflag_action sda1 (=sda1)
parted /dev/sda set 2 boot off

                                                                          
Warning: Error fsyncing/closing /dev/sda: Input/output error

                                                                          
Error: Input/output error during write on /dev/sda
parted /dev/sda set 3 boot off

                                                                          
Error: Partition doesn't exist.

                                                                          
Warning: Error fsyncing/closing /dev/sda: Input/output error
parted /dev/sda set 4 boot off

                                                                          
Error: Partition doesn't exist.
parted /dev/sda set 1 boot on

                                                                          
Error: Input/output error during write on /dev/sda
internet: no-internet
internet: connected

```

---

### Post by audiomick on 2012-04-19
Well, I don't understand a lot of that, but there is an obvious problem right at the start

```
sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

That partition is where your system is, and there is obviously something wrong there.

Later on in the output, there is reference to FSCK, right down near the end, and lots more error messages. I'm guessing here, but I think the problem is with the partition itself and not with the file system. If you don't understand that, think of it like this: Partition is the bookshelf and filesystem is the books. Your books would be ok, but the bookshelf is broken.

I gather your install is brand new. In that case, I would just try and re-install. You should make sure the installer that you are using is ok. 
Check the md5sum of the iso that you used
[https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

Since it is a netbook, I expect you used a USB stick to install. Check that it is ok too.
Look here
[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options]("https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options")
to see how to get to that option.

You could also try looking at the SMART values of the drive. I think this should be possible from the live CD using the Hard Drive management tool. Have a look at the screenshot to see where that is in the window. Mine is in German, but you should be able to find it from the picture. It will be in the same place.

I've just looked at your first post again, and seen that you said you can't re-install. That takes us back to checking the media on the one hand, and on the other hand more in the direction of a possible fault with the drive. Is it brand new or very well used? Have you tried taking it out and re-seating it to make sure the contacts are good? Can you try it in another machine, or another drive (the original maybe...) in that machine?

It is also possible that someone else will look at your boot info script output and see something that I don know about. There is a lot of that which I don't really understand.

---

### Post by Calippo on 2012-04-19
I'll take a look at what you've suggested in your last post and come back with some more information tomorrow.

Thanks for looking at this audiomick, I'm out of my depth here so your help is really appreciated.

---

### Post by audiomick on 2012-04-19
No problems, pleased if I can help.

I'll try and have a look in tomorrow evening.

---

### Post by oldfred on 2012-04-19
I do not see anything more than audiomick in boot script. It looks like Boot-Repair tried to run fsck. I might try again and see what it says directly:


#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by Calippo on 2012-04-20
Not at home with the laptop at the moment, but I'll answer what I can until I am.
 
> **audiomick said:**
> I gather your install is brand new. In that case, I would just try and re-install. You should make sure the installer that you are using is ok. 
Check the md5sum of the iso that you used
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
 
Since it is a netbook, I expect you used a USB stick to install. Check that it is ok too.
Look here
[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)
to see how to get to that option.

 
I initially installed it with a USB stick created with UNetBootin, although I have tried with a DVD after borrowing a USB CD/DVD drive.
 
Checksums were verified prior to installation, I'm familiar with doing that through flashing custom ROMs on Android phones.
 
 
> 
You could also try looking at the SMART values of the drive. I think this should be possible from the live CD using the Hard Drive management tool. Have a look at the screenshot to see where that is in the window. Mine is in German, but you should be able to find it from the picture. It will be in the same place.

 
I've ran the Disk Utility on the LiveCD with the SMART tests and they have come back as healthy, although I will re-do these later on and post the screenshot showing the values and thresholds if it is going to be useful.
 
> 
I've just looked at your first post again, and seen that you said you can't re-install. That takes us back to checking the media on the one hand, and on the other hand more in the direction of a possible fault with the drive. Is it brand new or very well used? 

 
The SSD is about 18 months old and hasn't seen a great amount of use, bar some other distro installations and the removal of Windows entirely. Up until the installation of 12.04 I had nothing to lead me to suspect any problems with the drive.
 
> 
Have you tried taking it out and re-seating it to make sure the contacts are good? 

 
Yep, it was seated correctly.
 
> 
Can you try it in another machine, or another drive (the original maybe...) in that machine?

 
The SSD has a mini-USB socket on it, so I have connected it up to my main PC (Win 7 x64) and it is viewable in Disk Management, but can't make any changes to the partition structure nor was I able to format it via Windows Setup.
 
I have put the original 8GB SSD back in and have successfully re-installed 11.10, which seems to suggest a problem with the drive.

---

### Post by audiomick on 2012-04-20
Hmm, doesn't sound that good.

My next step would be to see if I can change the partitioning with a Linux partitioning tool like Gparted. You could plug in the drive to the Netbook via USB, or install it again and use GParted from the Live CD.

If that doesn't work, I'd be thinking about a garuantee claim if the drive isn't too old for that.

That the Windows partitioning tool can't work on the partitions doesn't surprise me. I am not absolutely sure, but I don't think it can deal with non-microsoft file systems.

Let us know how you get on, anyway.

---

### Post by Calippo on 2012-04-20
> **oldfred said:**
> 
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1


```

sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1: recovering journal
e2fsck: unable to set superblock flags on /dev/sda1

```

> 
#if errors:
sudo e2fsck -f -y -v /dev/sda1

```

sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: recovering journal
e2fsck: unable to set superblock flags on /dev/sda1

```

---

### Post by oldfred on 2012-04-20
I never had to use alternative superblocks and only consider this a last resort repair. Not even sure it works with SSD.

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda1
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Calippo on 2012-04-20
> **oldfred said:**
> I never had to use alternative superblocks and only consider this a last resort repair. Not even sure it works with SSD.


I followed the instructions to clear the inode and then attempt to recover the backed up superblock and each one comes back with:

```

/dev/sda1: recovering journal
fsck.ext4: unable to set superblock flags on /dev/sda1

```

Thanks

---

### Post by Calippo on 2012-04-23
audiomick/oldfred;
 
Just to update and close the thread.  I've arranged an RMA with the manufacturer as a hardware problem looks more likely to be causing the problems than software.
 
Once again, thank you for taking the time to help me run through a few things.

---

### Post by audiomick on 2012-04-23
> **Calippo said:**
> audiomick/oldfred;
 
Once again, thank you for taking the time to help me run through a few things.

You're welcome. I hope the manufacturer look after you properly. Thanks for letting us know how things turned out.

---

### Post by YannBuntu on 2012-04-24
Hello

For future similar cases, i just would like to come back on this:

> **oldfred said:**
> It looks like Boot-Repair tried to run fsck. I might try again and see what it says directly:


#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

As we see here on the log, Boot-Repair does not do fsck by default:
```
************************Before mainwindow
**FSCK_ACTION no** PASTEBIN_ACTION yes
**recommendedrepair**, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) ( )
internet: no-internet
```

Here we can see the options that have been chosen by the user (the user enabled the fsck option):


```
************************Actions
**FSCK_ACTION yes** PASTEBIN_ACTION yes
**customrepair**, restore, REINSTALL_POSSIBLE no PURGE_POSSIBLE
UNHIDEBOOT_ACTION yes (10s), noflag (sda1)
PART_TO_REINSTALL_GRUB , PART_TO_REINSTALL_GRUB_PURGE , FORCE_GRUB  () REMOVABLEDISK
USE_SEPARATEBOOTPART  ()  ()
UNCOMMENT_GFXMODE no ATA  ADD_KERNEL_OPTION no (acpi=off)
MBR_TO_RESTORE sda (mbr) (sda 1)
```

For information, here is the current behavior of Boot-Repair concerning the fsck option (this may be improved, **any suggestion is welcome**):
- the fsck (indeed called "Repair filesystems" in the GUI) option is never enabled by default
- Boot-Repair asks the user to backup data before using the fsck option
- the fsck option effect is the following: it makes a "ntfsfix" of all the NTFS partitions, and a "fsck -fyM" of all the other partitions.

---

