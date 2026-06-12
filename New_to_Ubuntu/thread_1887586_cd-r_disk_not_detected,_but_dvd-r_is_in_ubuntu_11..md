---
title: "cd-r disk not detected, but dvd-r is in ubuntu 11.10"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by wootkleb on 2011-11-27
I just loaded ubuntu 11.10 on my Dell Inspiron 1520. To get Ubuntu, I first installed ubuntu 8.10, then got online and downloaded the latest version, which I burned to my CD-R and booted and installed off of this drive (so the drive does work.) But, after logging into 11.10, I discovered that I CD-R disks that I had previously made with Windows Vista were not detected by the drive. The bootable copy of Ubuntu made during the installation process on the same brand of CD-R disk is still detected.

I've read numerous threads with cd drives not detecting certain things, but none seemed to address this issue, and I have yet to see any fix that works for me.  I have tried to mount the drive with no success:

```
~$ sudo mount /dev/sr0
[sudo] password for aaron: 
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
```

Here's what my /etc/fstab and /etc/mtab look like:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c8e50979-2ac2-4d3c-ad14-a2109363f806 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b08f527a-f52f-461f-9d3e-e3834455d559 none            swap    sw              0       0

```

```
/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0 
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0 
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/aaron/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=aaron 0 0   
```


When performing udisks --enumerate-device-files, I get the following:

```
~$ udisks --enumerate-device-files
/dev/sr0
/dev/disk/by-id/ata-HL-DT-STCD-RW_DVD-ROM_GCC-T10N
/dev/disk/by-path/pci-0000:00:1f.1-scsi-0:0:0:0
/dev/sda5
/dev/disk/by-id/ata-TOSHIBA_MK8037GSX_Y71HTVKUT-part5
/dev/disk/by-id/scsi-SATA_TOSHIBA_MK8037G_Y71HTVKUT-part5
/dev/disk/by-uuid/b08f527a-f52f-461f-9d3e-e3834455d559
/dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part5
/dev/sda
/dev/disk/by-id/ata-TOSHIBA_MK8037GSX_Y71HTVKUT
/dev/disk/by-id/scsi-SATA_TOSHIBA_MK8037G_Y71HTVKUT
/dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0
/dev/sda1
/dev/disk/by-id/ata-TOSHIBA_MK8037GSX_Y71HTVKUT-part1
/dev/disk/by-id/scsi-SATA_TOSHIBA_MK8037G_Y71HTVKUT-part1
/dev/disk/by-uuid/c8e50979-2ac2-4d3c-ad14-a2109363f806
/dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part1
/dev/sda2
/dev/disk/by-id/ata-TOSHIBA_MK8037GSX_Y71HTVKUT-part2
/dev/disk/by-id/scsi-SATA_TOSHIBA_MK8037G_Y71HTVKUT-part2
/dev/disk/by-path/pci-0000:00:1f.2-scsi-0:0:0:0-part2
```

I've also managed to play a DVD-R using Ubuntu's Movie Player that I burned on my DVD-recorder.
Does anyone have suggestions on how to get Ubuntu to recognize my data CDs?

---

### Post by gmargo on 2011-11-27
You have not provided the **mount** command with a "mount point". Without a mount point provided on the command line, program went looking into /etc/fstab but could not find a matching default.

Try providing a mount point like this:

```

mkdir /media/cdrom         # If this directory does not already exist

mount -t iso9660 -o ro /dev/sr0 /media/cdrom

```If that succeeds, you will see the CDR contents "mounted" under the **/media/cdrom** directory.

---

### Post by wootkleb on 2011-11-27
Thanks for the reply.

I had already tried this earlier. Does it matter who owns the cdrom directory? It's owned by root:

```
aaron@aaron-Inspiron-1520:/media$ ls -l
total 4
drwxr-xr-x 2 root root 4096 2011-11-27 08:41 cdrom
```


Here's what happens when I attempt to mount:

```
sudo mount -t iso9660 -o ro /dev/sr0 /media/cdrom
mount: no medium found on /dev/sr0

```

Thanks again and hoping you've got more suggestions.

---

### Post by wootkleb on 2011-11-27
Sorry about that -- forgot to put the CD back in before trying that. Okay, here's what happens when the CD-R that is not recognized is placed in the drive:

```
$ sudo mount -t iso9660 -o ro /dev/sr0 /media/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by wootkleb on 2011-11-27
Something is causing an I/O error now that I've got Ubuntu.  I'm able to open and read the disk on my iMac even though it was written from the Dell when it had the Vista OS.

```
$ dmesg | tail -30
[10247.845509] Info fld=0x70ad, ILI
[10247.845513] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[10247.845523] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 70 ac 00 00 02 00
[10247.845539] end_request: I/O error, dev sr0, sector 115376
[10247.845546] quiet_error: 6 callbacks suppressed
[10247.845550] Buffer I/O error on device sr0, logical block 14422
[10247.904462] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[10247.904471] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[10247.904479] Info fld=0x70ad, ILI
[10247.904482] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[10247.904492] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 70 ac 00 00 02 00
[10247.904508] end_request: I/O error, dev sr0, sector 115376
[10247.904515] Buffer I/O error on device sr0, logical block 14422
[11160.872973] ISO 9660 Extensions: Microsoft Joliet Level 3
[11160.933114] ISO 9660 Extensions: RRIP_1991A
[14906.940545] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[14906.940553] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[14906.940561] Info fld=0x70ad, ILI
[14906.940564] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[14906.940573] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 70 ac 00 00 02 00
[14906.940589] end_request: I/O error, dev sr0, sector 115376
[14906.940594] Buffer I/O error on device sr0, logical block 14422
[14906.999538] sr 0:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[14906.999546] sr 0:0:0:0: [sr0]  Sense Key : Illegal Request [current] 
[14906.999554] Info fld=0x70ad, ILI
[14906.999557] sr 0:0:0:0: [sr0]  Add. Sense: Illegal mode for this track
[14906.999566] sr 0:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 70 ac 00 00 02 00
[14906.999582] end_request: I/O error, dev sr0, sector 115376
[14906.999588] Buffer I/O error on device sr0, logical block 14422
[14919.067789] ISOFS: Unable to identify CD-ROM format.
```

Any other ideas? Thanks again!

---

### Post by wootkleb on 2011-11-27
Fiddling around a bit more, I got it to work, but now I'm a bit worried about whether I'll have to run mount every time.

My fix was to remove the -t option and just ran:

```
sudo mount -o ro /dev/sr0 /media/cdrom
```

---

### Post by gmargo on 2011-11-27
What was the filesystem type?   Just type "mount" at the prompt, it should be clear.

---

### Post by wootkleb on 2011-11-27
Here's what I get when I run "mount". And, I realize now that although  I can view what's on the disk (and users in other accounts can as well), noone including myself can remove the disk. When I try "umount", I get that the disk is in use. I need more help!

Thanks!

```
$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aaron/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aaron)
/dev/sr0 on /media/cdrom type udf (ro)
gvfs-fuse-daemon on /home/tess/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tess)

```

---

### Post by wootkleb on 2011-11-27
I had the home folder open in two accounts -- each apparently putting a lock on umount. Any way, I was unable to umount after closing those, and I can repeat the process to mount now. But...., I'd really like this to be done automatically. So, I've been trying to edit the fstab file. Here's what I've added, but it's not doing the job. Any suggestions?

```

# I added this so anyone could mount CD
/dev/sr0    /media/cdrom    udf    rw,user,auto,sync    0    0

```

I realize that cdrom is probably not the best name for the directory, since I want to be able to burn disks too. It just so happens that the disk I had been asking about was already burned and so read-only.

Any way, I'd really appreciate help getting this to always work. Thanks again!

---

### Post by wootkleb on 2011-11-27
I changed udf to auto in the fstab file, and after rebooting, all users can mount the cd and unmount it without root permission. So that's good. But, to wrap this up cleanly, there's got to be a way to automatically mount the CD -- isn't there?

Thanks again.

---

