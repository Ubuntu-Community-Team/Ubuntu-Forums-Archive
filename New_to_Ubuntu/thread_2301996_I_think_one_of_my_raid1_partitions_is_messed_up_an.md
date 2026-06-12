---
title: "I think one of my raid1 partitions is messed up and I don't know how to fix it, help."
date: 2015-11-06
forum: New to Ubuntu
---

### Post by Alonzo_Thayn on 2015-11-06
I tried doing a boot-repair and it said to post the following URL so someone might be able to help figure out what to do. [http://paste.ubuntu.com/13099391/](http://paste.ubuntu.com/13099391/)  I am pasting the text from this URL at the bottom of this thread.


I have a raid setup and I am not sure if the partition is just messed up or if the drive is bad. I can't access the drives through the live cd to get my files out, I think I had it setup as encypted when I set it up originally. I have backups of most of the files but would prefer to salvage this setup since I have VMs and things that I would have to rebuild. Can anyone tell me what I could try? Can I just unplug sda and boot from sdb? Thanks to anyone who can help.



Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 9Feb2015[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> No known boot loader is installed in the MBR of /dev/sda.
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR]mduuid/ccc353ad871e6c98b6e6b384c46e0c8b,1[COLOR=#666666])[/COLOR]/boot/grub.

sdb1: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

md/0: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

Invalid MBR Signature found.


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1    *          2,048   953,047,039   953,044,992  fd Linux raid autodetect
/dev/sdb2         953,049,086   976,773,119    23,724,034   5 Extended
/dev/sdb5         953,049,088   976,773,119    23,724,032  82 Linux swap / Solaris


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/md/0        ccc353ad-871e-6c98-b6e6-b384c46e0c8b   linux_raid_member KubuntuServer:0
/dev/md0         ccc353ad-871e-6c98-b6e6-b384c46e0c8b   linux_raid_member KubuntuServer:0
/dev/sdb1        ccc353ad-871e-6c98-b6e6-b384c46e0c8b   linux_raid_member KubuntuServer:0
/dev/sdb5        d10d3252-d981-4684-9a15-90e6005040cf   swap       
/dev/sr0                                                iso9660    Ubuntu 14.04.3 LTS [COLOR=#B8860B]amd64[/COLOR]

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -l /dev/disk/by-id"[/COLOR] output: [COLOR=#666666]======================[/COLOR]

total 0
lrwxrwxrwx 1 root root  9 Nov  4 02:36 ata-SAMSUNG_CDRW_DVD_SM-348B -> ../../sr0
lrwxrwxrwx 1 root root  9 Nov  4 05:15 ata-ST3500418AS_5VM7FKJV -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov  4 03:32 ata-ST3500418AS_5VM7FKJV-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov  4 02:36 ata-ST3500418AS_5VM7FKJV-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov  4 02:54 ata-ST3500418AS_5VM7FKJV-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Nov  4 02:41 ata-ST3500418AS_5VM7JN16 -> ../../sda
lrwxrwxrwx 1 root root  9 Nov  4 05:15 md-name-KubuntuServer:0 -> ../../md0
lrwxrwxrwx 1 root root  9 Nov  4 05:15 md-uuid-ccc353ad:871e6c98:b6e6b384:c46e0c8b -> ../../md0
lrwxrwxrwx 1 root root  9 Nov  4 05:15 wwn-0x5000c50020bd4efa -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov  4 03:32 wwn-0x5000c50020bd4efa-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov  4 02:36 wwn-0x5000c50020bd4efa-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov  4 02:54 wwn-0x5000c50020bd4efa-part5 -> ../../sdb5
lrwxrwxrwx 1 root root  9 Nov  4 02:41 wwn-0x5000c500216276e0 -> ../../sda

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sr0         /cdrom                   iso9660    [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]


[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown MBR on /dev/sda



[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
cat: write error: Broken pipe
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/16643/mounts[COLOR=#666666])[/COLOR] leaked on lvs invocation. Parent PID 16807: bash
File descriptor 63 [COLOR=#666666]([/COLOR]pipe:[COLOR=#666666][[/COLOR]644975[COLOR=#666666]])[/COLOR] leaked on lvs invocation. Parent PID 16807: bash
  /dev/sda: [COLOR=#AA22FF]read [/COLOR]failed after 0 of 4096 at 0: Input/output error
  /dev/sda: [COLOR=#AA22FF]read [/COLOR]failed after 0 of 4096 at 4096: Input/output error
  No volume groups found
mdadm: /dev/md/0 is already in use.

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2015-11-04__03h11 [COLOR=#666666]===================[/COLOR]
boot-repair version : 4ppa33
boot-sav version : 4ppa33
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa33

BLKID BEFORE RAID ACTIVATION:
/dev/sdb1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ccc353ad-871e-6c98-b6e6-b384c46e0c8b"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"4380cf67-8fdf-831f-8d60-4b9e28e2878d"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"KubuntuServer:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sdb5: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"d10d3252-d981-4684-9a15-90e6005040cf"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sr0: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Ubuntu 14.04.3 LTS amd64"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"iso9660"[/COLOR]
ERROR: hpt37x: reading /dev/sda[COLOR=#666666][[/COLOR]Input/output error[COLOR=#666666]][/COLOR]
dmraid -si -c: no raid disks
No DMRAID disk.
RAID detected. You may want to retry after installing the [COLOR=#666666][[/COLOR]mdadm[COLOR=#666666]][/COLOR] packages. [COLOR=#666666]([/COLOR]sudo apt-get install -y --force-yes mdadm --no-install-recommends[COLOR=#666666])[/COLOR]
Warning: no DMRAID nor MD_ARRAY.
Successfully activated RAID.
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Ubuntu 14.04.3 LTS, trusty, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/ubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz quiet splash -- maybe-ubiquity
ls: cannot access /home/usr/.config: No such file or directory
Set sdb as corresponding disk of md0
Disk /dev/md0 doesn[COLOR=#BB4444]'t contain a valid partition table[/COLOR]

[COLOR=#BB4444]=================== os-prober:[/COLOR]


[COLOR=#BB4444]=================== blkid:[/COLOR]
[COLOR=#BB4444]/dev/sdb1: UUID="ccc353ad-871e-6c98-b6e6-b384c46e0c8b" UUID_SUB="4380cf67-8fdf-831f-8d60-4b9e28e2878d" LABEL="KubuntuServer:0" TYPE="linux_raid_member"[/COLOR]
[COLOR=#BB4444]/dev/loop0: TYPE="squashfs"[/COLOR]
[COLOR=#BB4444]/dev/sdb5: UUID="d10d3252-d981-4684-9a15-90e6005040cf" TYPE="swap"[/COLOR]
[COLOR=#BB4444]/dev/sr0: LABEL="Ubuntu 14.04.3 LTS amd64" TYPE="iso9660"[/COLOR]
[COLOR=#BB4444]/dev/md0: UUID="ccc353ad-871e-6c98-b6e6-b384c46e0c8b" UUID_SUB="4380cf67-8fdf-831f-8d60-4b9e28e2878d" LABEL="KubuntuServer:0" TYPE="linux_raid_member"[/COLOR]

[COLOR=#BB4444]Warning: extended partition does not start at a cylinder boundary.[/COLOR]
[COLOR=#BB4444]DOS and Linux will interpret the contents differently.[/COLOR]

[COLOR=#BB4444]=================== UEFI/Legacy mode:[/COLOR]
[COLOR=#BB4444]This live-session is not in EFI-mode.[/COLOR]
[COLOR=#BB4444]SecureBoot maybe enabled.[/COLOR]


[COLOR=#BB4444]=================== PARTITIONS & DISKS:[/COLOR]

[COLOR=#BB4444]sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	2048 sectors * 512 bytes[/COLOR]


[COLOR=#BB4444]=================== parted -l:[/COLOR]

[COLOR=#BB4444]Error: /dev/sda: unrecognised disk label[/COLOR]

[COLOR=#BB4444]Model: ATA ST3500418AS (scsi)[/COLOR]
[COLOR=#BB4444]Disk /dev/sdb: 500GB[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512B/512B[/COLOR]
[COLOR=#BB4444]Partition Table: msdos[/COLOR]

[COLOR=#BB4444]Number  Start   End    Size    Type      File system     Flags[/COLOR]
[COLOR=#BB4444]1      1049kB  488GB  488GB   primary   ext4            boot, raid[/COLOR]
[COLOR=#BB4444]2      488GB   500GB  12.1GB  extended[/COLOR]
[COLOR=#BB4444]5      488GB   500GB  12.1GB  logical   linux-swap(v1)[/COLOR]


[COLOR=#BB4444]Error: /dev/md0: unrecognised disk label[/COLOR]

[COLOR=#BB4444]Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0 has been opened read-only.[/COLOR]
[COLOR=#BB4444]Error: Can'[/COLOR]t have a partition outside the disk!

[COLOR=#666666]===================[/COLOR] parted -lm:

Error: /dev/sda: unrecognised disk label

BYT;
/dev/sdb:500GB:scsi:512:512:msdos:ATA ST3500418AS;
1:1049kB:488GB:488GB:ext4::boot, raid;
2:488GB:500GB:12.1GB:::;
5:488GB:500GB:12.1GB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

Error: /dev/md0: unrecognised disk label

Warning: Unable to open /dev/sr0 [COLOR=#AA22FF]read[/COLOR]-write [COLOR=#666666]([/COLOR]Read-only file system[COLOR=#666666])[/COLOR].  /dev/sr0 has been opened [COLOR=#AA22FF]read[/COLOR]-only.
Error: Can[COLOR=#BB4444]'t have a partition outside the disk![/COLOR]

[COLOR=#BB4444]=================== lsblk:[/COLOR]
[COLOR=#BB4444]KNAME TYPE  FSTYPE     SIZE LABEL    MODEL    UUID[/COLOR]
[COLOR=#BB4444]sda   disk           465.8G          ST350041[/COLOR]
[COLOR=#BB4444]sdb   disk           465.8G          ST350041[/COLOR]
[COLOR=#BB4444]sdb1  part  linux_ra 454.5G KubuntuServer:0[/COLOR]
[COLOR=#BB4444]ccc353ad-871e-6c98-b6e6-b384c46e0c8b[/COLOR]
[COLOR=#BB4444]md0   raid1 linux_ra 454.3G KubuntuServer:0[/COLOR]
[COLOR=#BB4444]ccc353ad-871e-6c98-b6e6-b384c46e0c8b[/COLOR]
[COLOR=#BB4444]sdb2  part               1K[/COLOR]
[COLOR=#BB4444]sdb5  part  swap      11.3G                   d10d3252-d981-4684-9a15-90e6005040cf[/COLOR]
[COLOR=#BB4444]sr0   rom   iso9660   1006M Ubuntu 14.04.3 LTS amd64[/COLOR]
[COLOR=#BB4444]CDRW/DVD[/COLOR]
[COLOR=#BB4444]loop0 loop  squashfs 962.1M[/COLOR]

[COLOR=#BB4444]KNAME ROTA RO RM STATE   MOUNTPOINT[/COLOR]
[COLOR=#BB4444]sda      1  0  0 running[/COLOR]
[COLOR=#BB4444]sdb      1  0  0 running[/COLOR]
[COLOR=#BB4444]sdb1     1  0  0[/COLOR]
[COLOR=#BB4444]md0      1  0  0[/COLOR]
[COLOR=#BB4444]sdb2     1  0  0[/COLOR]
[COLOR=#BB4444]sdb5     1  0  0[/COLOR]
[COLOR=#BB4444]sr0      1  0  1 running /cdrom[/COLOR]
[COLOR=#BB4444]loop0    1  1  0         /rofs[/COLOR]


[COLOR=#BB4444]=================== mount:[/COLOR]
[COLOR=#BB4444]/cow on / type overlay (rw)[/COLOR]
[COLOR=#BB4444]proc on /proc type proc (rw,noexec,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]udev on /dev type devtmpfs (rw,mode=0755)[/COLOR]
[COLOR=#BB4444]devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)[/COLOR]
[COLOR=#BB4444]tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)[/COLOR]
[COLOR=#BB4444]/dev/sr0 on /cdrom type iso9660 (ro,noatime)[/COLOR]
[COLOR=#BB4444]/dev/loop0 on /rofs type squashfs (ro,noatime)[/COLOR]
[COLOR=#BB4444]none on /sys/fs/cgroup type tmpfs (rw)[/COLOR]
[COLOR=#BB4444]none on /sys/fs/fuse/connections type fusectl (rw)[/COLOR]
[COLOR=#BB4444]none on /sys/kernel/debug type debugfs (rw)[/COLOR]
[COLOR=#BB4444]none on /sys/kernel/security type securityfs (rw)[/COLOR]
[COLOR=#BB4444]tmpfs on /tmp type tmpfs (rw,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)[/COLOR]
[COLOR=#BB4444]none on /run/shm type tmpfs (rw,nosuid,nodev)[/COLOR]
[COLOR=#BB4444]none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)[/COLOR]
[COLOR=#BB4444]none on /sys/fs/pstore type pstore (rw)[/COLOR]
[COLOR=#BB4444]systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)[/COLOR]
[COLOR=#BB4444]gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)[/COLOR]


[COLOR=#BB4444]=================== ls:[/COLOR]
[COLOR=#BB4444]/sys/block/fd0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/md0 (filtered):  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent[/COLOR]
[COLOR=#BB4444]/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri dvb ecryptfs fb0 fd fd0 full fuse fw0 hidraw0 hidraw1 hidraw2 hpet i2c-0 i2c-1 i2c-10 i2c-11 i2c-12 i2c-13 i2c-14 i2c-2 i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 i2c-8 i2c-9 input kmsg log lp0 mapper mcelog md md0 mem memory_bandwidth net network_latency network_throughput null parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sdb sdb1 sdb2 sdb5 sg0 sg1 sg2 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom usb v4l vbi0 vfio vga_arbiter vhci vhost-net video0 zero[/COLOR]
[COLOR=#BB4444]ls /dev/md:  0[/COLOR]
[COLOR=#BB4444]ls /dev/mapper:  control[/COLOR]
[COLOR=#BB4444]Disk /dev/md0 doesn'[/COLOR]t contain a valid partition [COLOR=#B8860B]table[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/cow           overlay   2.0G  117M  1.9G   6% /
udev           devtmpfs  1.9G   12K  1.9G   1% /dev
tmpfs          tmpfs     395M  1.3M  394M   1% /run
/dev/sr0       iso9660  1006M 1006M     0 100% /cdrom
/dev/loop0     squashfs  963M  963M     0 100% /rofs
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     2.0G  1.2M  2.0G   1% /tmp
none           tmpfs     5.0M  4.0K  5.0M   1% /run/lock
none           tmpfs     2.0G   76K  2.0G   1% /run/shm
none           tmpfs     100M   60K  100M   1% /run/user

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x0003c948

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   953047039   476522496   fd  Linux raid autodetect
/dev/sdb2       953049086   976773119    11862017    5  Extended
/dev/sdb5       953049088   976773119    11862016   82  Linux swap / Solaris

Disk /dev/md0: 487.8 GB, 487824818176 bytes
2 heads, 4 sectors/track, 119097856 cylinders, total 952782848 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00000000


Error: no [COLOR=#B8860B]partitions[/COLOR]


[COLOR=#666666]===================[/COLOR] Suggested repair
The default repair of the Boot-Repair utility would not act on the MBR.
Additional repair would be performed:  repair-filesystems


[COLOR=#666666]===================[/COLOR] User settings
The settings chosen by the user will not act on the boot.

---

### Post by TheFu on 2015-11-06
Please post the boot-repair link. The output there will line up correctly.
Or
use **code tags** above.

---

### Post by Alonzo_Thayn on 2015-11-07
I am new to the ubuntu forum. When you say the boot-repair link are you talking about the link boot repair setup with the error message? It is: [http://paste.ubuntu.com/13099391/](http://paste.ubuntu.com/13099391/)

That is the only link I can find. Thanks for your help.

---

### Post by TheFu on 2015-11-07
Yep. See how things line up in that link that don't line up above?
Much easier to read for us. 

Ok - reviewed the data. I'm seeing some settings that I've never seen before.  That isn't necessarily bad, just outside my experience. There are some warnings and errors too.  I didn't know that boot-repair could handle RAID-anything. Well, I guess it can't.  I have to admit, from the data, I can't tell for certain which type of RAID the system has - SW-RAID, Fake-RAID or HW-RAID.  The disks have a RAID partition type, which I don't use with SW-RAID here.  Never used FakeRAID (don't see the point).

Sorry I'm not any help.  I would suggested reseating any controller cards and replugging any cables. I've had a lose SATA cable drop a disk from an array before (actually almost weekly for 6+ months).  The errors here appear to be hardware. One disk is gone and the other isn't working correctly - MBR seems corrupted.

At this point, I'd pull out the backups.  If you can wait, hopefully someone with more knowledge will show up in the next day or so to help. They usually wait until I've displayed profound ignorance first. ;)

---

### Post by Alonzo_Thayn on 2015-11-08
I think it is a SW-RAID setup. I can wait a little while if anyone has suggestions. I don't need this machine currently but I will in a few weeks.

I will try disconnecting and reconnecting all the connections to see if that fixes it. Thank you for your help.

---

