---
title: "No bootable device"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by Bo0ddha on 2014-02-08
I am having a rough time trying to get my computer to boot.  I had ubuntu server running and it started to have issues.  I believe it was a bad super block.  I formatted the drive and reinstalled a few times.  Each time after the install it would reboot and drop into the initramfs prompt.  From a few searches I saw this might be a bad superblock.  I did not have anything on the drive so decided to just format and re-install.  After unplugging everything except the main drive and a few more re-installs I now have a missing operating system No bootable device on every boot.  This makes me think we have a problem with the MBR.  I ran boot repair and thought that would fix it.  Same thing.  Here is the pastebin from boot repair. [http://paste.ubuntu.com/6900267/](http://paste.ubuntu.com/6900267/)  

```
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 31Jan2013]


============================= Boot Info Summary: ===============================

 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Puppy Linux
                       Linux 2.4.22 [i486 arch]
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 16424 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
81 heads, 63 sectors/track, 287115 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048 1,465,149,167 1,465,147,120  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4012 MB, 4012900352 bytes
223 heads, 55 sectors/track, 639 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,837,695     7,835,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        b42eb87b-eafe-463c-8e48-e40017904636   ext2       
/dev/sdb1        44DC-470A                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sdb1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Boot-Repair-Disk session" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/lubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

File descriptor 8 (/proc/2519/mounts) leaked on lvscan invocation. Parent PID 8046: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-02-08__23h47 ===================
boot-repair version : 3.198~ppa16~raring
boot-sav version : 3.198~ppa16~raring
glade2script version : 3.2.2~ppa45~raring
boot-sav-extra version : 3.198~ppa16~raring
File descriptor 8 (/proc/2519/mounts) leaked on lvs invocation. Parent PID 4129: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 64bit 24avr2013, raring, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/lubuntu.seed boot=casper cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash --

=================== os-prober:
/dev/sda1:unknown Linux distribution:Linux:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="b42eb87b-eafe-463c-8e48-e40017904636" TYPE="ext2"
/dev/sdb1: LABEL="UUI" UUID="44DC-470A" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mkdir: cannot create directory &#8216;/mnt/boot-sav/sda1/var&#8217;: No space left on device
sda1 is Read-only or full
=================== No kernel in /mnt/boot-sav/sda1/boot:
vmlinuz


=================== UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-kernel,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda1.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 bytes


=================== parted -l:

Model: ATA WDC WD7500AAKS-0 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  750GB  750GB  primary  ext2


Model: SanDisk Cruzer (scsi)
Disk /dev/sdb: 4013MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4013MB  4012MB  primary  fat32        boot

=================== parted -lm:

BYT;
/dev/sda:750GB:scsi:512:512:msdos:ATA WDC WD7500AAKS-0;
1:1049kB:750GB:750GB:ext2::;

BYT;
/dev/sdb:4013MB:scsi:512:512:msdos:SanDisk Cruzer;
1:1049kB:4013MB:4012MB:fat32::boot;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdb1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/lubuntu/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=lubuntu)
/dev/sda1 on /mnt/boot-sav/sda1 type ext2 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  alarm ashmem autofs binder block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sdb sdb1 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd stderr stdin stdout uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  489M   20M  470M   4% /
udev           devtmpfs   472M   12K  472M   1% /dev
tmpfs          tmpfs       98M  784K   97M   1% /run
/dev/sdb1      vfat       3.8G  509M  3.3G  14% /cdrom
/dev/loop0     squashfs   435M  435M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      489M  8.0K  489M   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      489M     0  489M   0% /run/shm
none           tmpfs      100M   12K  100M   1% /run/user
/dev/sda1      ext2       236M  236M     0 100% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
81 heads, 63 sectors/track, 287115 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b7195

Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048  1465149167   732573560   83  Linux

Disk /dev/sdb: 4012 MB, 4012900352 bytes
223 heads, 55 sectors/track, 639 cylinders, total 7837696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000642b6

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048     7837695     3917824    b  W95 FAT32



=================== Recommended repair
Recommended-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s


Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 1 boot on

                                                                          
Information: You may need to update /etc/fstab.


Boot successfully repaired.

You can now reboot your computer.
```

I found this interesting

> 1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

mkdir: cannot create directory &#8216;/mnt/boot-sav/sda1/var&#8217;: No space left on device
sda1 is Read-only or full
=================== No kernel in /mnt/boot-sav/sda1/boot:
vmlinuz


Any advice on how to fix this?

---

### Post by tfrue on 2014-02-09
Well, this is interesting... Your boot-info says:
[LIST]
[*]Puppy Linux is installed on /dev/sda1 
[*]/dev/sda is formatted as ext2 
[*]No Grub bootloader 
[*]No boot flag for /dev/sda1 
[*]The single partition on /dev/sda is using the entire drive (Which is normal) 
[*]No kernel for /dev/sda 
[*]No mount points for /dev/sda in the /etc/fstab file 
[/LIST]

If you're going to install Ubuntu Server on this drive, I recommend using a DVD since you will have to do manual partitioning and manually choose to install Grub to your HDD if you use a USB, it's just easier to use a DVD.

What I would do is live boot, either DVD or USB, and do some partitioning from the live boot and then try and install Ubuntu whether it be server or desktop version. Some would recommend using Gparted, but I've never had luck with it or it would just freeze so I don't use it but you can use it if you want and feel comfortable using it. I use *fdisk* that is built into Ubuntu and we can use that since you aren't using a GPT disk.

Live boot, not using Ubuntu Server, and open a terminal and lets get started! Please type:

***THIS WILL REMOVE THE PARTITION ON YOUR HDD!** But we are going to create a new one from scratch to remedy your problem, I just wanted to let you know what's happening.*

***Please make sure that you don't have /dev/sda mounted anywhere when we begin to edit the disk.* **
You can use Unity to search for the *disks* program, and select the 750GB drive, then press the stop(square) symbol, if present.

```
sudo fdisk /dev/sda
d
1
w

```
That will delete the partition and we will now create a new MBR. Type:
```

partprobe (This will tell the kernel there is a new partition table so we will be editing the new stuff and hopefully returns without errors.)
sudo fdisk /dev/sda
o
w
```
That will create a new dos(MBR) partition table, and write the changes. So lets now create a new partition, so type:
```

sudo fdisk /dev/sda
n
p
enter
enter
enter
t
83
w
```
That will create a new partition that will use the entire drive with a disk type of *Linux* so we can format it as ext4. We now need to create a FS for our single partition, so type:
```
 sudo mkfs.ext4 /dev/sda1 (Make sure to add the 1 to /dev/sda1)

```
That will create a file system of ext4 on the new partition and we can now run the installer and try to install Ubuntu again.

Make sure that you are using the latest version of Ubuntu, like Ubuntu 13.10 (Which 14.04 LTS will be out in April), and put it on a disk rather than the USB and you should be good! The installer should partition as needed, and should install Grub to the appropriate drive (Which is /dev/sda).

Good luck,
Chris

---

### Post by Bo0ddha on 2014-02-11
Sorry for the long wait on the reply.  Thank you for the advice.  I was able to get it working again.  The drive did say puppy linux because I was at a point I was trying anything and everything I had laying around to get it to work.  I ended up finding out I had a bad disc image downloaded after an md5 check.  On top of that I think the usb installer was not installing correctly to install from my flash drive.  After downloading Lubuntu and using Unetbootin it ran on the first try.  I did bookmark this for a quick down and dirty repair job.

---

### Post by tfrue on 2014-02-12
That sounds good to me! When you try and install Ubuntu Server 13.10 from USB, it decides that if you say install the OS to /dev/sda (Not being the USB), install Grub to the USB anyway. So when I first installed Ubuntu Server it wouldn't boot without the USB, lesson learned.

Glad to hear that you were able to boot from the USB, I hope that you have better luck installing next time!

Good luck,
Chris

---

