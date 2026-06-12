---
title: "Dual Boot Install Issues"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by shane36 on 2015-02-18
Im a new Ubuntu user. I have rarely used it but like it. I want to install it into my machine as dual boot with window but have been running into a LOT of trouble.

#1 I used the windows disk manager to shrink the drive without formatting the unallocated space.
          a)Ubuntu didnt see the drive space.
          b) tried formatting space NTFS, Fat32 and Xfat and still Ubuntu doidnt see the partition.
#2 Tried WUBI and it just has me reboot to the same thing as just installing from the disk and not *In Windows* as I have read or as advertized
#3 When I tried to install from the disk, there is not option of *alongside windows*
#4 When I finally was able to see the primary disk, I couldnt format the spaces I needed because you can only have 4 primary partitions and the step by steps I have seen say I need 32gb sawp(2x16gb RAM), 30GB /root and the other is the rest of the drive onto /home partition... that's 3 + windows system and main= 5. 
#5 I tried setting it up on a seperate HD and it wont do it. the formatting just hangs and gives me a waring. 

I'm about to give up. I really hate windows and want to get into Linux but it looks like I would need a whole new machine. 

OH! And I tried formatting the main drive using GParted Live and installing Unbutu first and then windows and using GPL to format unalocated drive space... both with no luck.

And when I went for clean install and trying to partition the drives by selecting something else, the drive was some gigged up isw-gobbledegook and Ubuntu seemed to want dev/sda and refused to cooperate. 

HALP!

---

### Post by TheFu on 2015-02-18
wubi is dead thanks to secureboot and the needs that MSFT had to secure the boot process with efi booting.

"gigged up isw-gobbledegook" isn't quite accurate enough to be helpful.  With Linux, we need the exact information you entered AND the exact response. Copy/paste is best, quality photos next best. transcription can't usually be trusted, sorry to say.

We need exact data to help. Please create a liveCD or live-Flash install of Ubuntu and run **boot-info** to gather information about your config. Post the link that tool creates back in this thread.  You can also install and run **boot repair** to create the same information and link. That might be easier.

Have you considered contacting a local Linux Users Group for help? Sometimes installing Linux is more complex than can easily be addressed over a forum.

If you really want to wipe Windows from the machine, then Linux installations are easier.

---

### Post by shane36 on 2015-02-18
/dev/mapper/isw_bhibhcjiba_Volume01 is the gobbledegook.

And I never thought to run boot info- I'll do that... currently Im trying to repair what my last attempt did to windows- 

>.< system`MSI 67a-43b mobo, 16GB RAM, 2x 500gb HDD, 1 75BG HDD, RADEON HD 5450 video and the ethernet and sound are integrated. Using windows 7 and tried Ubuntu 12.10, 113.2 and 14.04 in an attempt to get the *alongside* option. Should be about an hour til I can do the boot info. Just to be sure... how, from the gui, do I get to the command prompt in 14.04?

---

### Post by lisati on 2015-02-18
*Thread moved to **New to Ubuntu**.*

Please read the [forum staff recommendations on Wubi]("http://ubuntuforums.org/showthread.php?t=2229766").

---

### Post by grahammechanical on 2015-02-18
> [COLOR=#000000]how, from the gui, do I get to the command prompt in 14.04?[/COLOR]

Open the Dash - click the Ubuntu icon on top of the launcher and type terminal in the search bar and wait until you see a terminal icon and click it.

Please state the new starting from scratch position that you are in. Is there any other OS now on that machine? If not and all you want to do is install Ubuntu then run the installer and choose the Use the Entire Disk option and the installer will do the rest including creating partitions.

If the situation is different then plase tell us and we can start from the present situation and not get confused with what happened in the past.

By the way, with 16 GB of RAM I would be very surprised if swap even gets used. I think the 2 x RAM for swap is old advice from the days when people did not have so much RAM. Do you intend to hibernate or suspend to disk? If we plan to do that then we need a swap size greater than the amount of RAM because when we hibernate all the data in memory is saved to the swap partition.

Regards.

---

### Post by Bucky Ball on 2015-02-18
Forget 12.10. No longer supported. Stick with one supported release (14.04 LTS probably best) and let's try and troubleshoot that.

2Gb for /swap is fine, unless you're intending to hibernate, in which case same size as installed RAM. Forget the '/swap should be double installed RAM' fable. ;)

---

### Post by mastablasta on 2015-02-19
> **shane36 said:**
>  and the step by steps I have seen say I need 32gb sawp(2x16gb RAM), 

really? where in this documentation/guide it says that?: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Linux can run from extended partitions, but you need one primary free if you use MBR. as mentioned first use this to generate a report: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

then we'll see how you have it setup.

---

### Post by oldfred on 2015-02-19
> /dev/mapper/isw_bhibhcjiba_Volume01 is the gobbledegook.

That is either RAID or LVM, both are advanced installs with special types of partitions.

Is system a newer UEFI system or BIOS. If new UEFI system then you can install both Windows & Ubuntu in either mode, but both must be installed in same boot mode. And how you boot installer UEFI or BIOS is then how it installs.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by shane36 on 2015-02-19
> **mastablasta said:**
> really? where in this documentation/guide it says that?: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Linux can run from extended partitions, but you need one primary free if you use MBR. as mentioned first use this to generate a report: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

then we'll see how you have it setup.

Not just these forums. I've seen so many different step by step instructions it's made my head spin. I took the overlaps and the minimal knowledge I have anad came to the conclusion I needed a few partitions - one for swap, one for /root and one for /home. At this point Im just looking for a step by step to load in Ubuntu 14.04.1 LTS on a machine that already has Windows 7 64bit. I have Ubuntu from 12.1 to the current version of both 32 and 64 bit. I had no issue running it in Virtual PC and in Vitual box but trying to get an MMO to run in Virtual box is like trying to baptize a cat.

I have despised windows since they claimed gaming was the reason for their security issues and created Xbox. And them messing up dual boot with anything but another flavor of windows plus the update debacles with 8 and 8.1 are just the final straw for me. My favorite MMO will run in WINE and so I want to finally move away from windows and into Linux. The only reason I even bother with windows is that so many of the programs I like are windows based. But again, I'm sure once I get used to the Linux versions and way of doing things, I will be much happier. 

I guess this post was more frustration with windows than anything else. I apologize for the inconvenience to the forum. So if there is a stable, tried and true way to dual boot Win7 and U14.04LTS and a link to it, I will give it another try on my own first. Is there a reliable link?

> **oldfred said:**
> That is either RAID or LVM, both are advanced installs with special types of partitions.

Is system a newer UEFI system or BIOS. If new UEFI system then you can  install both Windows & Ubuntu in either mode, but both must be  installed in same boot mode. And how you boot installer UEFI or BIOS is  then how it installs.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

UEFI with win7 would be a good link for me- these were most helpful and more understandable than anything else I have seen, I will see if I can find. And again... thank you for being patient with my frustration. I've been out of the PC loop for a while and relegated to telling people what they need in a laptop instead of actually working on them. I've probably forgotten more about computers than I'll ever learn again. Hence my frustration.

---

### Post by TheFu on 2015-02-20
Just so we are clear - without boot-info results, as requested in the first reply, we really can't help much.
If you are stuck, that is the 1st thing you should concentrate on - getting the link to the system results posted back here.

---

### Post by mastablasta on 2015-02-20
aside from what TheFu said about getting help & guidance  and providing sufficient data...

> **shane36 said:**
> Not just these forums. I've seen so many different step by step instructions it's made my head spin. 


which is why you should stick to official documentation. if there are any questions or if things don't work out the way they should you can always post them here.
> 
My favorite MMO will run in WINE and so I want to finally move away from windows and into Linux. 

problem with this is that MMO might get an update and then it might not work with WINE anymore.

static programs are not much of an issue if they work at certain wine version they will likely work with later versions. and if not one can always install the older version where they did work perfectly. while MMO and similar online games get constant updates, so if something works well now it might not work in the future and there might not be any way to make it work.

which is why dual boot is better solution if one plays games.

---

### Post by newb85 on 2015-02-20
I just re-read your original post, and you said you formatted the unallocated space.  Why?  If you formatted it, then it was no longer unallocated, which is why Ubuntu didn't see it.  (It may have been completely empty, but if it's formatted, the Ubuntu installer will assume it's there for a reason and won't recommend installing there.)

My recommendation is that you go back to trying to set up dual-boot like you did before, but this time leave the unallocated space *unformatted* for the Ubuntu installer.

---

### Post by shane36 on 2015-02-20
Problem one- RAID and shouldn't be....anything else?

  ```
1

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   661,377,023   661,170,176   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3EB2576FB2572AA3                       ntfs       
/dev/sda2        90C05E43C05E2FA8                       ntfs       
/dev/sr0                                                iso9660    Ubuntu 14.04 LTS i386

========================= "ls -l /dev/disk/by-id" output: ======================

total 0
lrwxrwxrwx 1 root root  9 Feb 20 08:13 ata-HL-DT-ST_DVDRAM_GH24LS70_K00B63K1311 -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 20 08:36 ata-Hitachi_HDS721050CLA362_JP8521HR36Y6AV -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 20 08:13 ata-Hitachi_HDS721050CLA362_JP8521HR36Y6AV-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 20 08:13 ata-Hitachi_HDS721050CLA362_JP8521HR36Y6AV-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb 20 08:13 ata-TSSTcorpCD_DVDW_SH-S183L -> ../../sr1
lrwxrwxrwx 1 root root  9 Feb 20 08:13 usb-Generic-_Card_Reader_20060413092100000-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 Feb 20 08:36 wwn-0x5000cca378ed6e5e -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 20 08:13 wwn-0x5000cca378ed6e5e-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 20 08:13 wwn-0x5000cca378ed6e5e-part2 -> ../../sda2

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/ubuntu/3EB2576FB2572AA3 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2        /media/ubuntu/90C05E43C05E2FA8 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========= Devices which don't seem to have a corresponding hard drive: =========

sdb {All_DMRaid} 

=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
ERROR: creating degraded mirror mapping for "isw_baheadchhb_Volume0"
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
File descriptor 9 (/proc/8164/mounts) leaked on lvs invocation. Parent PID 13894: bash
File descriptor 63 (pipe:[344567]) leaked on lvs invocation. Parent PID 13894: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-info 2015-02-20__08h36 ===================
boot-info version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
boot-info is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
ls: cannot access /home/usr/.config: No such file or directory

=================== os-prober:


=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="3EB2576FB2572AA3" TYPE="ntfs"
/dev/sda2: UUID="90C05E43C05E2FA8" TYPE="ntfs"
/dev/sr0: LABEL="Ubuntu 14.04 LTS i386" TYPE="iso9660"

Windows not detected by os-prober on sda2.

=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /media/ubuntu/3EB2576FB2572AA3.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/ubuntu/90C05E43C05E2FA8.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      1049kB  106MB  105MB  primary  ntfs         boot
2      106MB   339GB  339GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

=================== parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA Hitachi HDS72105;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:339GB:339GB:ntfs::;

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!

=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL    MODEL    UUID
sda   disk isw_raid 465.8G          Hitachi
sda1  part ntfs       100M                   3EB2576FB2572AA3
sda2  part ntfs     315.3G                   90C05E43C05E2FA8
sr0   rom  iso9660    970M Ubuntu 14.04 LTS i386
DVDRAM G
sr1   rom            1024M          CD/DVDW
loop0 loop squashfs 935.2M

KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /media/ubuntu/3EB2576FB2572AA3
sda2     1  0  0         /media/ubuntu/90C05E43C05E2FA8
sr0      1  0  1 running /cdrom
sr1      1  0  1 running
loop0    1  1  0         /rofs


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/ubuntu/3EB2576FB2572AA3 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda2 on /media/ubuntu/90C05E43C05E2FA8 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log lp0 mapper mcelog mei mem net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sg0 sg1 sg2 sg3 shm snapshot snd sr0 sr1 stderr stdin stdout uhid uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  a3 2a 57 b2 6f 57 b2 3e  |.........*W.oW.>|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff a7 68 27 00 00 00 00  |..........h'....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  a8 2f 5e c0 43 5e c0 90  |........./^.C^..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200

=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  4.0G  130M  3.9G   4% /
udev           devtmpfs   4.0G   12K  4.0G   1% /dev
tmpfs          tmpfs      807M  1.2M  806M   1% /run
/dev/sr0       iso9660    970M  970M     0 100% /cdrom
/dev/loop0     squashfs   936M  936M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      4.0G  1.4M  4.0G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      4.0G   80K  4.0G   1% /run/shm
none           tmpfs      100M   48K  100M   1% /run/user
/dev/sda1      fuseblk    100M   34M   67M  34% /media/ubuntu/3EB2576FB2572AA3
/dev/sda2      fuseblk    316G   77G  240G  25% /media/ubuntu/90C05E43C05E2FA8

=================== fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa4a8ac7f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   661377023   330585088    7  HPFS/NTFS/exFAT


Partition outside the disk detected.


=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot


=================== User settings
The settings chosen by the user will not act on the boot.
```

---

### Post by oldfred on 2015-02-20
Please use code tags which can easily be added in advanced editor with #.
Also deleted many blank lines.
Better just to post link to pastebin that Boot-Repair gives you.
Also changed title as not wubi.

Was drive ever part of RAID. Do you have RAID, you only show sda.
If at some point drive was RAID, it has RAID meta-data on drive which needs to be removed for a standard install.

       Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda

Drive should be in AHCI, not RAID nor IDE mode in BIOS.

---

### Post by shane36 on 2015-02-20
I had the PC set up on RAID5. Never replace the HDD that died. Went into BIOS and changed that. From the Ubuntu disk-try ubuntu: I can now see the HDDs in the list but when I go to create the partition, I see nothing. Not even the Windows partitions(system reserved and main). I unplugged the second 500GB HDD and the 80 GB HDD to be sure that some setting wasn't putting the other 2 drives as Volume0(stranger things) and still get a HDD icon in the main menu but when I go to format, I still see nothing when I go to partition the HDD.

 UNGH~! Pause... when I switch from RAID to non RAID,  my Windows partition got wiped so I have to start over.

---

### Post by shane36 on 2015-02-20
> **mastablasta said:**
> 
problem with this is that MMO might get an update and then it might not work with WINE anymore.

Hence the reason for dual boot. This way if an update screws it up for Linux, I can boot over to Win7 and still play. From this point on I want my computing to be mainly in Linux. I never want to rely upon Microsux for the meat. It's going to be strictly for gaming that wont work on Linux.

---

### Post by shane36 on 2015-02-21
Ok- So I switch from RAID to nonRAID and I reinstall and update windows, When installing Windows, I partitioned the 500 GB drive this way... 350GB for windows and 150GB (which was left unallocated and unformatted) for linux. I back up windows on an external drive. I then put in my U14 disk and reboot. 
I get to the page that has * Erase disk and install* and select *something else* and click continue. On the *Installation Type* page, To my delight, the drive is now listed as dev/sdc and the windows partition is /dev/sdc1 ntfs. To my dismay, the 150gb partition is not listed.  

So why, after setting up the bios to be non RAID is this still telling me it is RAID?
And how do I make this happen? *The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot *



```
1
     
                                   
[LIST]
[*]Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]
 
 
============================= Boot Info Summary: ===============================
 
 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Windows 2000/XP/2003 is installed in the MBR of /dev/sdc.
 
sda1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD
 
sda2: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe
 
sdc1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   661,506,047   661,299,200   7 NTFS / exFAT / HPFS
 
 
Drive: sdc _____________________________________________________________________
 
Disk /dev/sdc: 319.4 GB, 319370035200 bytes
255 heads, 63 sectors/track, 38827 cylinders, total 623769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sdc1               2,048   623,769,599   623,767,552   7 NTFS / exFAT / HPFS
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/loop0                                              squashfs   
/dev/sda1        8ABA5453BA543E3F                       ntfs       System Reserved
/dev/sda2        8A02604E02604175                       ntfs       Main
/dev/sdc1        4052B6E452B6DDBA                       ntfs       My Passport
/dev/sr0                                                iso9660    Ubuntu 14.04 LTS i386
 
========================= "ls -l /dev/disk/by-id" output: ======================
 
total 0
lrwxrwxrwx 1 root root  9 Feb 21 09:54 ata-HL-DT-ST_DVDRAM_GH24LS70_K00B63K1311 -> ../../sr0
lrwxrwxrwx 1 root root  9 Feb 21 16:01 ata-Hitachi_HDS721050CLA362_JP8521HR36Y6AV -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 21 16:02 ata-Hitachi_HDS721050CLA362_JP8521HR36Y6AV-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 21 09:54 ata-Hitachi_HDS721050CLA362_JP8521HR36Y6AV-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb 21 09:54 ata-TSSTcorpCD_DVDW_SH-S183L -> ../../sr1
lrwxrwxrwx 1 root root  9 Feb 21 16:01 ata-WDC_WD3200BMVV-11A1PS0_WD-WXD0AB9W4216 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 21 16:02 ata-WDC_WD3200BMVV-11A1PS0_WD-WXD0AB9W4216-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Feb 21 09:54 usb-Generic-_Card_Reader_20060413092100000-0:0 -> ../../sdb
lrwxrwxrwx 1 root root  9 Feb 21 16:01 wwn-0x5000cca378ed6e5e -> ../../sda
lrwxrwxrwx 1 root root 10 Feb 21 16:02 wwn-0x5000cca378ed6e5e-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb 21 09:54 wwn-0x5000cca378ed6e5e-part2 -> ../../sda2
lrwxrwxrwx 1 root root  9 Feb 21 16:01 wwn-0x50014ee2ae690f40 -> ../../sdc
lrwxrwxrwx 1 root root 10 Feb 21 16:02 wwn-0x50014ee2ae690f40-part1 -> ../../sdc1
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ubuntu/Main       fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
 
 
========= Devices which don't seem to have a corresponding hard drive: =========
 
sdb {All_DMRaid} 
 
=============================== StdErr Messages: ===============================
 
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
ERROR: creating degraded mirror mapping for "isw_baheadchhb_Volume0"
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
File descriptor 9 (/proc/8893/mounts) leaked on lvs invocation. Parent PID 15694: bash
File descriptor 63 (pipe:[166107]) leaked on lvs invocation. Parent PID 15694: bash
  No volume groups found
 
ADDITIONAL INFORMATION :
=================== log of boot-info 2015-02-21__16h01 ===================
boot-info version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33
ERROR: isw: wrong number of devices in RAID set "isw_baheadchhb_Volume0" [1/2] on /dev/sda
boot-info is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, i686)
CPU op-mode(s):        32-bit, 64-bit
file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
ls: cannot access /home/usr/.config: No such file or directory
Unmount sdc1 from /media/ubuntu/My Passport to avoid space incompatibilities
 
=================== os-prober:
 
 
=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System Reserved" UUID="8ABA5453BA543E3F" TYPE="ntfs"
/dev/sda2: LABEL="Main" UUID="8A02604E02604175" TYPE="ntfs"
/dev/sr0: LABEL="Ubuntu 14.04 LTS i386" TYPE="iso9660"
/dev/sdc1: LABEL="My Passport" UUID="4052B6E452B6DDBA" TYPE="ntfs"
 
Windows not detected by os-prober on sda2.
 
=================== UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.
 
 
=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,     no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,     no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,     /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,     no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,     no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,     /media/ubuntu/Main.
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,     no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,     part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,     no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,     no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,     /mnt/boot-sav/sdc1.
 
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdc    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
 
 
=================== parted -l:
 
Model: ATA Hitachi HDS72105 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End    Size   Type     File system  Flags
1      1049kB  106MB  105MB  primary  ntfs         boot
2      106MB   339GB  339GB  primary  ntfs
 
 
Model: WD My Passport 070A (scsi)
Disk /dev/sdc: 319GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
Number  Start   End    Size   Type     File system  Flags
1      1049kB  319GB  319GB  primary  ntfs
 
 
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!
 
=================== parted -lm:
 
BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA Hitachi HDS72105;
1:1049kB:106MB:105MB:ntfs::boot;
2:106MB:339GB:339GB:ntfs::;
 
BYT;
/dev/sdc:319GB:scsi:512:512:msdos:WD My Passport 070A;
1:1049kB:319GB:319GB:ntfs::;
 
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.
Error: Can't have a partition outside the disk!
 
=================== lsblk:
KNAME TYPE FSTYPE     SIZE LABEL    MODEL    UUID
sda   disk isw_raid 465.8G          Hitachi
sda1  part ntfs       100M System Reserved
8ABA5453BA543E3F
sda2  part ntfs     315.3G Main              8A02604E02604175
sdc   disk          297.4G          My Passp
sdc1  part ntfs     297.4G My Passport
4052B6E452B6DDBA
sr0   rom  iso9660    970M Ubuntu 14.04 LTS i386
DVDRAM G
sr1   rom            1024M          CD/DVDW
loop0 loop squashfs 935.2M
 
KNAME ROTA RO RM STATE   MOUNTPOINT
sda      1  0  0 running
sda1     1  0  0         /mnt/boot-sav/sda1
sda2     1  0  0         /media/ubuntu/Main
sdc      1  0  0 running
sdc1     1  0  0         /mnt/boot-sav/sdc1
sr0      1  0  1 running /cdrom
sr1      1  0  1 running
loop0    1  1  0         /rofs
 
 
=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /media/ubuntu/Main type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /mnt/boot-sav/sdc1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
 
 
=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi  capability dev device discard_alignment events events_async  events_poll_msecs ext_range holders inflight power queue range removable  ro sda1 sda2 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi  capability dev device discard_alignment events events_async  events_poll_msecs ext_range holders inflight power queue range removable  ro size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi  capability dev device discard_alignment events events_async  events_poll_msecs ext_range holders inflight power queue range removable  ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi  capability dev device discard_alignment events events_async  events_poll_msecs ext_range holders inflight power queue range removable  ro size slaves stat subsystem trace uevent
/sys/block/sr1 (filtered):  alignment_offset bdi  capability dev device discard_alignment events events_async  events_poll_msecs ext_range holders inflight power queue range removable  ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control  bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs  fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg log lp0 mapper  mcelog mei mem net network_latency network_throughput null parport0 port  ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sdb sdc sdc1  sg0 sg1 sg2 sg3 sg4 sg5 shm snapshot snd sr0 sr1 stderr stdin stdout  uhid uinput urandom vga_arbiter vhost-net zero
ls /dev/mapper:  control
 
=================== hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 1f 03 00 00 00 00 00  |................|
00000030  55 21 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |U!..............|
00000040  f6 00 00 00 01 00 00 00  3f 3e 54 ba 53 54 ba 8a  |........?>T.ST..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
 
=================== hexdump -n512 -C /dev/sda2
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 03 00  |........?....(..|
00000020  00 00 00 00 80 00 80 00  ff 9f 6a 27 00 00 00 00  |..........j'....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  75 41 60 02 4e 60 02 8a  |........uA`.N`..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
 
=================== hexdump -n512 -C /dev/sdc1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff ef 2d 25 00 00 00 00  |..........-%....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  ba dd b6 52 e4 b6 52 40  |...........R..R@|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
 
=================== df -Th:
 
Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  4.0G  114M  3.9G   3% /
udev           devtmpfs   4.0G   12K  4.0G   1% /dev
tmpfs          tmpfs      807M  1.2M  806M   1% /run
/dev/sr0       iso9660    970M  970M     0 100% /cdrom
/dev/loop0     squashfs   936M  936M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      4.0G  1.2M  4.0G   1% /tmp
none           tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs      4.0G   80K  4.0G   1% /run/shm
none           tmpfs      100M   48K  100M   1% /run/user
/dev/sda2      fuseblk    316G   89G  228G  28% /media/ubuntu/Main
/dev/sda1      fuseblk    100M   25M   76M  25% /mnt/boot-sav/sda1
/dev/sdc1      fuseblk    298G   53G  246G  18% /mnt/boot-sav/sdc1
 
=================== fdisk -l:
 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf4d62c37
 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   661506047   330649600    7  HPFS/NTFS/exFAT
 
Disk /dev/sdc: 319.4 GB, 319370035200 bytes
255 heads, 63 sectors/track, 38827 cylinders, total 623769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00035f28
 
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   623769599   311883776    7  HPFS/NTFS/exFAT
 
 
Partition outside the disk detected.
 
 
=================== Suggested repair
The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot 
[/LIST]

```

---

### Post by TheFu on 2015-02-21
> 150G unallocated and unformatted
Which is what you want. Unallocated means there isn't anything there, right?

Choose, "Do something else"
then create an extended partition with the remaining storage (all of it on the disk you'd like to install onto)
then create 3 logical partitions inside the extended one. 
* / - 25G ext4 - this will hold Ubuntu and the installed applications. Yes, that is enough.
* Linux swap - how much RAM do you have and do you need to hibernate? 4G is a min for a desktop these days, but 101% larger than RAM if you hibernate is needed.
* /home - 15G ext4 .... 
* Leave the rest unused for now - until you need it for something else.

Simple?  You have to tell the installer what each new partition is used for. Also, check "format" on those partitions.
Do not touch the existing NTFS or FAT32 partitions at all.

Logical partitions will begin with 5 and count up.  Primary and extended partitions on MBR disks are 1-4 only. This is just the way MBR disks work.  GPT removes the main limitations of MBR - I always use GPT now for a number of reasons.

Hopefully, this makes sense.

---

### Post by oldfred on 2015-02-21
You mention a second 500GB drive.
Often better to keep Windows & its boot loader on one drive and Ubuntu and its boot loader on the other drive.
To insure clean installs to each drive you can unplug all others.
But using Something Else with Ubuntu you can specify drive & where boot loader is installed. With Windows boot loader is installed to drive set in BIOS as boot drive.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

One advantage of Ubuntu on its own drive is that even if booting in BIOS mode you can use gpt partitioning on the Ubuntu drive. I dual booted XP on MBR and Ubuntu on gpt since about 10.10. And only use gpt on all new drives. But Windows will only boot in UEFI mode from a gpt partitioned drive.
You do have to have a 1 or 2MB unformatted partition with the bios_grub flag for grub to correctly install.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by shane36 on 2015-02-21
> **TheFu said:**
> Which is what you want. Unallocated means there isn't anything there, right?

Choose, "Do something else"
then create an extended partition with the remaining storage (all of it on the disk you'd like to install onto)

.

It's not showing me the unallocated space. Im thinking that the fact that the report is showing that it's still showing 1/2 RAID drives means that it WONT show the unallocated space until I can figure out why it's trying to set up as RAID when I thought I had fixed that. Or until I install a second drive into that RAID system(which I never learned how to do)

---

### Post by shane36 on 2015-02-21
> **oldfred said:**
> You mention a second 500GB drive.
Often better to keep Windows & its boot loader on one drive and Ubuntu and its boot loader on the other drive.
To insure clean installs to each drive you can unplug all others.
But using Something Else with Ubuntu you can specify drive & where boot loader is installed. With Windows boot loader is installed to drive set in BIOS as boot drive.

       

I was of the idea that you had to have dual boot on the same drive. As in getting a selection screen at boot. If I can install it on a second drive altogether, It'll save me the hassle Im going thru

EDIT: Pardon my lack of knowledge. The only Dual boots I have ever done are windows with windos. I've never done Linux/windows(can ya tell? LOL)

---

### Post by oldfred on 2015-02-21
If you unplug drives, obviously the Ubuntu install will not find Windows to add it to grub menu.
But if you run this after booting into your install, it will add Windows to grub menu.
sudo update-grub.

Of course you have to set BIOS to boot Ubuntu drive, and want to keep Windows boot loader in Windows drive just for emergency or if Windows has issues.
Still better to have repairCD or flash drive for current version of every operating system you have installed.

---

### Post by shane36 on 2015-02-21
Doesn't having to swap drives defeat the purpose of a dual boot? Thanks but no thanks. I would rather have 2 machines than to wear out my hardware switching things.

---

### Post by oldfred on 2015-02-21
You only have to disconnect drive during install, if you do not fully understand and follow the methods required to install to one hard drive without installing parts of system to the other drive.
For newer users it often is easier. But if not able or willing to disconnect drive be sure to review Something Else install examples.

---

### Post by TheFu on 2015-02-21
> **shane36 said:**
> Doesn't having to swap drives defeat the purpose of a dual boot? Thanks but no thanks. I would rather have 2 machines than to wear out my hardware switching things.

Oldfred was just trying to save you from accidentally wiping the fresh Windows install through an accident. You don't seem very confident with partitioning, so that is a real risk. A simple mistake COULD cause this.  If you are confident - then leave all the disks attached and just be careful during the partitioning parts of the installation.  

I dual boot 1 machine - generally prefer to use virtualization myself and there isn't any lack of extra computers here.  Anyway, there's no need to disconnect things or go into the BIOS to change the boot device, if you don't want that extra safety while you learn.

Again, these were just suggestions to ensure a mistake wasn't made by accident - if you can keep /dev/sda and /dev/sdb and each of the numbered partitions straight - go for it. It isn't hard. Just pay very close attention to the details.   Oh .... and every 6-12 months, Microsoft will install something that breaks the dual boot, at least that has been my experience. Then I just boot into a LiveCD and run grub-install and update-grub (don't quote me on the exact commands) to fix whatever MS did to my boot.

I hope that you realize this install that you've dealt with for .... let me look ... 3 days is really about 20-40 min of effort once you know what you're doing.  Practice and experience matter.  I didn't understand the partitioning and booting stuff exactly for many years. If you only do it 2 times every 6 yrs, how can you possibly get enough practice?  It will come. The more you see it, the easier and greater understanding you'll gain.  If you local LUG has an installfest - go and help out for a few hours. There will be people with lots of experience to help and learning when in the same room, after struggling a little yourself, is easier.

---

### Post by shane36 on 2015-02-21
Thank you all. Please dont take my frustration as callousness toward any of you. Latest frustration is that both of the 1/2T HDs were actually dying. They were 5yrs old and they randomly kept showing as offline so... went and got a couple of 1TB HDs and am starting over again. Im going to take extra time making sure everything is ship shape and then return with reullts. Probably monday before I respond...hopefully tomorrow.

---

### Post by shane36 on 2015-02-21
O   M   G! After installing the new hard drives, when I went to install Ubuntu I actually got the choice *Install alongside windows*. I feel SO ridiculous. 

THANK YOU for your help and patience. You're help gave me the push to research issues I otherwise wouldnt have thought of such as investigating causes of HDDs going offline. You guys rock. And thanks for putting up with my frustration. You can mark this one solved.

---

### Post by Bucky Ball on 2015-02-21
Good news. You can mark the thread as solved to help future travelers by going to Thread Tools at the top right of the page (see the second link in my signature). 

Good luck, enjoy the OS, the forums and the learning curve. ;)

---

### Post by shane36 on 2015-02-21
Thanks. Not used to a forum that allows self service on things like that.

---

