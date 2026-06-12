---
title: "Mounting linux raid partition"
date: 2015-08-11
forum: New to Ubuntu
---

### Post by sparky7 on 2015-08-11
Good afternoon

To start I am not the Linux guys you all are so I need help please.

I have a new client with a failed Seagate NAS . Seagate was no help and they have no backup. The drive is not toast and spins up fine. I removed the drive and install on the SATA bus in my ubuntu machine. I can see many partitons but not the one that houses the data I am looking for. I think the data lives on the partition called Linux Raid. But can't mount this partition. I am sure it is just a rookie mistake. Any help would be great

Thanks in advance
Mike

Output from Fdisk:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086cd4


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   951865343   475931648   83  Linux
/dev/sda2       951867390   976771071    12451841    5  Extended
/dev/sda5       951867392   976771071    12451840   82  Linux swap / Solaris


[COLOR=#FF0000]WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.[/COLOR]
[COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes[/COLOR]
[COLOR=#FF0000]255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors[/COLOR]
[COLOR=#FF0000]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#FF0000]Sector size (logical/physical): 512 bytes / 4096 bytes[/COLOR]
[COLOR=#FF0000]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/COLOR]
[COLOR=#FF0000]Disk identifier: 0x00000000[/COLOR]
[COLOR=#FF0000]
[/COLOR]
[COLOR=#FF0000]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=#FF0000]/dev/sdb1               1  3907029167  1953514583+  ee  GPT[/COLOR]
[COLOR=#FF0000]Partition 1 does not start on physical sector boundary.[/COLOR]

THe 500 gig drive is my Ubuto machine and the 2 TB drive is the one that hopefully has data they need

Since I am not sure what I am doing I ran Testdisk. Here is the output:

TestDisk 6.14, Data Recovery Utility, July 2013
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


  TestDisk is free software, and
comes with ABSOLUTELY NO WARRANTY.


Select a media (use Arrow keys, then press Enter):
 
>Disk /dev/sdb - 2000 GB / 1863 GiB - ST2000DM001-1CH164

output after selecting the 2 TB drive in question:

Disk /dev/sdb - 2000 GB / 1863 GiB - ST2000DM001-1CH164


Please select the partition table type, press Enter when done.
 [Intel  ] Intel/PC partition
>[EFI GPT] EFI GPT partition map (Mac i386, some x86_64...)
 [Humax  ] Humax partition table
 [Mac    ] Apple partition map
 [None   ] Non partitioned media
 [Sun    ] Sun Solaris partition
 [XBox   ] XBox partition
 [Return ] Return to disk selection






Hint: EFI GPT partition table type has been detected.
Note: Do NOT select 'None' for media with only a single partition. It's very
rare for a drive to be 'Non-partitioned'.

output after selecting the highlighted default EFI GPT then anylize 

Disk /dev/sdb - 2000 GB / 1863 GiB - CHS 243201 255 63
     Partition               Start        End    Size in sectors
>P MS Data                       34      38945      38912
 P MS Data                    40960      77823      36864
 P MS Data                    77824    2031615    1953792
 P MS Data                  2031616    3983359    1951744
 P MS Data                  3983360    4374527     391168
 P Linux Swap               4374640    4374655         16
 P MS Data                  6328320    8327167    1998848
 [COLOR=#FF0000]P Linux Raid               8327168 3907026737 3898699570 [BA-001075392C39:1]
[/COLOR]

---

### Post by frostschutz on 2015-08-11
output of `sudo mdadm --examine /dev/sd*`

---

### Post by sparky7 on 2015-08-11
Thanks for the responce

Just FYI the NAS device had only one drive so it is confusing why the RAID label

/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)

---

### Post by frostschutz on 2015-08-12
I meant the * literally, your output looks like you used b instead of * ;)

* would also include output for the individual partitions and hopefully for the raid partition itself.

That should tell us what kind of raid it is and what we have to do to make it work.

---

### Post by sparky7 on 2015-08-12
Sorry my mistake. Thanks again.

Output using *

sparky@sparky-HP:~$ sudo mdadm --examine /dev/sd*
[sudo] password for sparky: 
/dev/sda:
   MBR Magic : aa55
Partition[0] :    951863296 sectors at         2048 (type 83)
Partition[1] :     24903682 sectors at    951867390 (type 05)
mdadm: No md superblock detected on /dev/sda1.
/dev/sda2:
   MBR Magic : aa55
Partition[0] :     24903680 sectors at            2 (type 82)
mdadm: No md superblock detected on /dev/sda5.
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907029167 sectors at            1 (type ee)
mdadm: No md superblock detected on /dev/sdb1.
mdadm: No md superblock detected on /dev/sdb2.
mdadm: No md superblock detected on /dev/sdb3.
mdadm: No md superblock detected on /dev/sdb4.
mdadm: No md superblock detected on /dev/sdb5.
mdadm: No md superblock detected on /dev/sdb6.
mdadm: No md superblock detected on /dev/sdb7.
/dev/sdb8:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : adbcf750:8b3d16d0:c524f0fd:8531a569
           Name : BA-001075392C39:1
  Creation Time : Sat Jul 13 23:06:18 2013
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3898699835 (1859.04 GiB 1996.13 GB)
     Array Size : 1949349781 (1859.04 GiB 1996.13 GB)
  Used Dev Size : 3898699562 (1859.04 GiB 1996.13 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 40b4a2b0:9da6e8ae:17733afb:f5d0e80e


    Update Time : Wed Jul 29 14:58:42 2015
       Checksum : e7ae29a7 - correct
         Events : 258335




   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)

---

### Post by frostschutz on 2015-08-12
OK, looks like a regular raid1 mirror, but running of only 1 out of 2 disks.

You should be able to start it:

```
sudo mdadm --assemble /dev/md42 /dev/sdb8
```

(or `cat /proc/mdstat` to check if it's already there)

and then mount it

```
sudo mkdir /mnt/thing
sudo mount /dev/md42 /mnt/thing
sudo ls -al /mnt/thing
```

Or if the mdadm refuses to start you could also try

```
sudo mount -o ro,loop,offset=$((2048*512)) /dev/sdb8 /mnt/thing
```

if mounting fails, there probably isn't a filesystem on the RAID; it could be LVM, or encryption

```
sudo file -sL /dev/md42
```

---

### Post by SeijiSensei on 2015-08-12
I have had success mounting one half of a two-disk RAID1 array as an ordinary disk and ignoring its RAID features.  You can give this a quick test with:

```

sudo mount /dev/sdb8 /mnt
ls /mnt

```

Does that work, or does mount throw errors?  Do you see any files?

---

### Post by sparky7 on 2015-08-12
Sorry I just got back to it. 

I will work on it now. Thank you again for your time.

Ran 

[COLOR=#000000][FONT=Ubuntu Mono]sudo mdadm --assemble /dev/md42 /dev/sdb8

Got This

[/FONT][/COLOR]mdadm: /dev/sdb8 is busy - skipping



[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]

Ran 

cat /proc/mdstat

Got this

Personalities : [raid1] 
md127 : active (auto-read-only) raid1 sdb8[0]
      1949349781 blocks super 1.2 [2/1] [U_]
      
unused devices: <none>

I a little confused. There was only one drive in the NAS enclosure. Not sure how it make sense to mirror a partition. It does not do anything if the drive fails!

Thanks for helping [[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195")[COLOR=#000000] 

Ran 

[/COLOR]sudo mount /dev/sdb8 /mnt

Got

mount: unknown filesystem type 'linux_raid_member'

---

### Post by steeldriver on 2015-08-12
You need to mount the assembled array /dev/md127 rather then the array member /dev/sdb8, I think

```

sudo mount /dev/md127 /mnt

```

The other issue you *may* face I think is that some (Sparc-based?) Seagate NAS boxes use large block size - I believe I've posted about that before

---

### Post by sparky7 on 2015-08-12
Thanks for helping [steeldriver]("http://ubuntuforums.org/member.php?u=1627500")

sparky@sparky-HP:~$ sudo mount /dev/md127 /mnt
[sudo] password for sparky: 
mount: unknown filesystem type 'LVM2_member'

---

### Post by steeldriver on 2015-08-12
Hmm... so maybe there's LVM on top of the RAID? What are the outputs of

```

sudo pvs

sudo lvdisplay

```

If either command is not found, you may need to install the lvm2 package

---

### Post by sparky7 on 2015-08-12
Ran 

sudo mount -o ro,loop,offset=$((2048*512)) /dev/sdb8 /mnt/thing

Thank you

Had to install lvm2


sparky@sparky-HP:~$ sudo pvs
  PV         VG   Fmt  Attr PSize PFree
  /dev/md127 vg1  lvm2 a--  1.82t    0 



sparky@sparky-HP:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg1/lv1
  LV Name                lv1
  VG Name                vg1
  LV UUID                5lh2Ph-302h-ssv1-WVzc-vTBU-0ZEm-8kM8Ee
  LV Write Access        read/write
  LV Creation host, time , 
  LV Status              NOT available
  LV Size                1.82 TiB
  Current LE             475915
  Segments               1
  Allocation             inherit
  Read ahead sectors     8192

---

### Post by frostschutz on 2015-08-12
edit: missed some replies :-) you are too quick for old frostschutz

vgchange -a y
mount /dev/vg1/lv1 /mnt/somewhere

---

### Post by sparky7 on 2015-08-12
I know [URL="http://ubuntuforums.org/member.php?u=1072388"][COLOR=#000000]
frostschutz[/COLOR][/URL]. Just trying to get data for these guys. 

I'm 53 so I know what you you mean. Been at IT since 92. Obviously not in the unix side of things :)

[URL="http://ubuntuforums.org/member.php?u=1072388"]
[/URL]

---

### Post by sparky7 on 2015-08-12
sparky@sparky-HP:~$ vgchange -a y
  /dev/mapper/control: open failed: Permission denied
  Failure to communicate with kernel device-mapper driver.
  WARNING: Running as a non-root user. Functionality may be unavailable.
  No volume groups found

---

### Post by steeldriver on 2015-08-12
OK so what happens if you try to activate the volume group?

```

sudo vgchange -ay vg1

```

If that succeeds, you can try to mount the LV

```

sudo mount /dev/vg1/lv1 /mnt

```

or possibly (using the device mapper symlink)

```

sudo mount /dev/mapper/vg1-lv1 /mnt

```

---

### Post by sparky7 on 2015-08-12
sparky@sparky-HP:~$ sudo vgchange -ay vg1
  1 logical volume(s) in volume group "vg1" now active

sparky@sparky-HP:~$ sudo mount /dev/vg1/lv1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 
sparky@sparky-HP:~$ dmesg | tail
[ 8456.802597] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 8456.873823] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[ 8456.873829] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 8456.873832] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 8456.875158] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[ 8456.875164] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 8456.875167] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 8456.875785] ata3.00: configured for UDMA/133
[ 8456.890686] ata3: EH complete
[ 8782.563776] EXT4-fs (dm-0): bad block size 65536

---

### Post by steeldriver on 2015-08-12
OK so

```

[ 8782.563776] EXT4-fs (dm-0): bad block size 65536

```

is exactly the other issue I was referring to earlier: AFAIK it's still possible to use fuseext2 to mount these - see [http://unix.stackexchange.com/questions/73536/how-can-i-mount-filesystems-with-4kb-block-sizes](http://unix.stackexchange.com/questions/73536/how-can-i-mount-filesystems-with-4kb-block-sizes)

---

### Post by sparky7 on 2015-08-12
interesting, I know see a 2 TB volume but when I go to access it complains with

Error mounting /dev/dm-0 at /media/sparky/a48ad9f5-d9db-4a97-a97b-713bb1e89533: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/dm-0" "/media/sparky/a48ad9f5-d9db-4a97-a97b-713bb1e89533"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg1-lv1, missing codepage or helper program, or other error In some cases useful info is found in syslog - try  dmesg | tail  or so

Here is log dmesg

sparky@sparky-HP:~$ dmesg | tail
[ 9656.414720] ata3: link is slow to respond, please be patient (ready=0)
[ 9657.815937] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 9657.830353] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[ 9657.830355] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 9657.830357] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 9657.831816] ata3.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[ 9657.831822] ata3.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[ 9657.831825] ata3.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[ 9657.832412] ata3.00: configured for UDMA/133
[ 9657.847946] ata3: EH complete

---

### Post by sparky7 on 2015-08-12
thanks

Installed fuseext2

Post states run 

fuseext2 -o ro -o sync_read /dev/sdb4 /mnt/

Change sdb4 to sdb8?

Sorry Im a rookie. 

When I changed to SDB8 and get this

sparky@sparky-HP:~$ fuseext2 -o ro -o sync_read /dev/sdb8 /mnt/
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]
fuse-umfuse-ext2: Error while trying to open /dev/sdb8 (rc=13) [do_probe (do_probe.c:34)]
fuse-umfuse-ext2: Probe failed [main (fuse-ext2.c:347)]

---

### Post by steeldriver on 2015-08-12
I think you would point it to the LV, since that's the thing that has the ext filesystem on it

```

sudo fuseext2 -o ro -o sync_read **/dev/mapper/vg1-lv1** /mnt/

```

(sudo required if you want to mount it in /mnt - since fuse is a user-space thing, you could create a mount point somewhere in your home directory and not need sudo)

---

### Post by sparky7 on 2015-08-12
tried this as well

fuseext2 -o ro -o sync_read /dev/vg1/lv1 /mnt

---

### Post by sparky7 on 2015-08-12
sparky@sparky-HP:~$ sudo fuseext2 -o ro -o sync_read /dev/mapper/vg1-lv1 /mnt/
[sudo] password for sparky: 
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]
fuse-umfuse-ext2: leave [do_probe (do_probe.c:55)]
fuse-umfuse-ext2: opts.device: /dev/mapper/vg1-lv1 [main (fuse-ext2.c:358)]
fuse-umfuse-ext2: opts.mnt_point: /mnt/ [main (fuse-ext2.c:359)]
fuse-umfuse-ext2: opts.volname:  [main (fuse-ext2.c:360)]
fuse-umfuse-ext2: opts.options: ro,sync_read [main (fuse-ext2.c:361)]
fuse-umfuse-ext2: parsed_options: sync_read,ro,fsname=/dev/mapper/vg1-lv1 [main (fuse-ext2.c:362)]
fuse-umfuse-ext2: mounting read-only [main (fuse-ext2.c:378)]
fuse: mountpoint is not empty
fuse: if you are sure this is safe, use the 'nonempty' mount option

There was a folder called thing in /mnt

So i created a directory called /mnt/channel and seemed to mount.

sparky@sparky-HP:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=sparky)
/dev/sdb1 on /media/sparky/9ced2102-6c8e-4e8d-9b9f-9d204fb25c87 type ext2 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb5 on /media/sparky/8c167af6-5c35-4f5c-9100-d0b0cca35f0b type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb4 on /media/sparky/9f7c0080-f64f-4741-ab78-6cd3eac87a24 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
[B]/dev/mapper/vg1-lv1 on /mnt/channel type fuse (ro,nosuid,nodev)

[/B]Still no access. I went ahead and deleted /mnt/thing but can't delete /mnt/channel since the device is mounted.

How can I dismount the volume? THis way I can delete mnt/channel and use your original command [COLOR=#000000]fuseext2 -o ro -o sync_read /dev/vg1/lv1 /mnt

I see I can use nonempty option. Should have done that before creating mnt/channel

Sorry if I messed up[/COLOR]

---

### Post by sparky7 on 2015-08-12
seems to mount other devices in /media/%username%

So I ran 

sudo fuseext2 -o ro -o sync_read -o nonempty /dev/mapper/vg1-lv1 /media/sparky 

 Used Nonempty option since media/spark was not empty

Mounted no problem. When I go to access I get something differnet now 

Unable to access “2.0 TB Volume” Error creating mount point `/media/sparky/a48ad9f5-d9db-4a97-a97b-713bb1e89533': Read-only file system

---

### Post by steeldriver on 2015-08-12
I don't think the specific mount point (directory) should matter - if it's mounted, it's mounted

It sounds like you are trying to mount the device AGAIN by clicking on the volume in the filemanager - don't do that. The files should already be available e.g.

```

ls /mnt/channel

```

or (with your new mountpoint in /media)

```

ls /media/sparky/

```

---

### Post by sparky7 on 2015-08-12
I rebooted and was now able to delete mnt/channel 

Was able to now run

 [COLOR=#000000][FONT=Ubuntu Mono]sudo fuseext2 -o ro -o sync_read [/FONT][/COLOR]**/dev/mapper/vg1-lv1**[COLOR=#000000][FONT=Ubuntu Mono] /mnt/ and it seemed to work

[/FONT][/COLOR]sparky@sparky-HP:~$ sudo fuseext2 -o ro -o sync_read /dev/mapper/vg1-lv1 /mnt/
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]
fuse-umfuse-ext2: leave [do_probe (do_probe.c:55)]
fuse-umfuse-ext2: opts.device: /dev/mapper/vg1-lv1 [main (fuse-ext2.c:358)]
fuse-umfuse-ext2: opts.mnt_point: /mnt/ [main (fuse-ext2.c:359)]
fuse-umfuse-ext2: opts.volname:  [main (fuse-ext2.c:360)]
fuse-umfuse-ext2: opts.options: ro,sync_read [main (fuse-ext2.c:361)]
fuse-umfuse-ext2: parsed_options: sync_read,ro,fsname=/dev/mapper/vg1-lv1 [main (fuse-ext2.c:362)]
fuse-umfuse-ext2: mounting read-only [main (fuse-ext2.c:378)]

Output of mount

sparky@sparky-HP:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=sparky)
/dev/sdb1 on /media/sparky/9ced2102-6c8e-4e8d-9b9f-9d204fb25c87 type ext2 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb3 on /media/sparky/db3a1c36-775f-4880-bcea-ae34c38ecbcf type ext4 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb2 on /media/sparky/5cf345ce-5b92-4cea-a02a-9200733ce756 type ext2 (rw,nosuid,nodev,uhelper=udisks2)
/dev/sdb4 on /media/sparky/9f7c0080-f64f-4741-ab78-6cd3eac87a24 type ext4 (rw,nosuid,nodev,uhelper=udisks2)
[COLOR=#ff0000]/dev/mapper/vg1-lv1 on /mnt type fuse (ro,nosuid,nodev)[/COLOR]
/dev/sdb7 on /media/sparky/b2150a8c-ddcf-434c-a90b-5e14c015afd6 type ext4 (rw,nosuid,nodev,uhelper=udisks2)

---

### Post by sparky7 on 2015-08-12
OK rebooted and ran 

sparky@sparky-HP:~$ sudo fuseext2 -o ro -o sync_read -o nonempty /dev/mapper/vg1-lv1 /media/sparky
[sudo] password for sparky: 
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]
fuse-umfuse-ext2: leave [do_probe (do_probe.c:55)]
fuse-umfuse-ext2: opts.device: /dev/mapper/vg1-lv1 [main (fuse-ext2.c:358)]
fuse-umfuse-ext2: opts.mnt_point: /media/sparky [main (fuse-ext2.c:359)]
fuse-umfuse-ext2: opts.volname:  [main (fuse-ext2.c:360)]
fuse-umfuse-ext2: opts.options: ro,sync_read,nonempty [main (fuse-ext2.c:361)]
fuse-umfuse-ext2: parsed_options: sync_read,nonempty,ro,fsname=/dev/mapper/vg1-lv1 [main (fuse-ext2.c:362)]
fuse-umfuse-ext2: mounting read-only [main (fuse-ext2.c:378)]

try and list contents of /media/sparky

sparky@sparky-HP:~$ ls /media/sparky/
ls: cannot access /media/sparky/: Permission denied
 
I dont want to waste any more of your time. You all have been very helpful.

---

### Post by steeldriver on 2015-08-12
If you mount it using sudo (i.e. as root) you may need to use sudo to view the contents

```

sudo ls /media/sparky

```

---

### Post by sparky7 on 2015-08-12
rebooted and ran 

sudo fuseext2 -o ro -o sync_read /dev/mapper/vg1-lv1 /media/sparky[sudo] password for sparky: 
fuse-umfuse-ext2: version:'0.4', fuse_version:'29' [main (fuse-ext2.c:331)]
fuse-umfuse-ext2: enter [do_probe (do_probe.c:30)]
fuse-umfuse-ext2: leave [do_probe (do_probe.c:55)]
fuse-umfuse-ext2: opts.device: /dev/mapper/vg1-lv1 [main (fuse-ext2.c:358)]
fuse-umfuse-ext2: opts.mnt_point: /media/sparky [main (fuse-ext2.c:359)]
fuse-umfuse-ext2: opts.volname:  [main (fuse-ext2.c:360)]
fuse-umfuse-ext2: opts.options: ro,sync_read [main (fuse-ext2.c:361)]
fuse-umfuse-ext2: parsed_options: sync_read,ro,fsname=/dev/mapper/vg1-lv1 [main (fuse-ext2.c:362)]
fuse-umfuse-ext2: mounting read-only [main (fuse-ext2.c:378)]

Ran 

ls /media/sparky
ls: cannot access /media/sparky: Permission denied

When I look at properties of sparky it Seems mounting it turns the directory sparky into Binary (application/octet-stream) and states contents unreadable

---

### Post by sparky7 on 2015-08-12
Thanks you soo much I see the files. How can I repay you guys for all your time!!??

sparky@sparky-HP:~$ sudo ls /media/sparky/common
2013				 marla
Admin				 NAForms
BROCHURE			 NetYield.rdp
CFP POS				 New Labels 2004
Clean Up			 New Labels 2004 - Shortcut.lnk
CN Spec Sheets Updated 4 2015	 NJ Bid
Damaged Box			 Nutritional Info
Delaware			 PC009 - Shortcut.lnk
DESIGN WORK			 Printers
Freight Release			 PRODUCTION LOT #'S
Joe				 Product Sheets
Label				 scans
Line Info			 Shared Files
Lot Inventory			 Truck Sheets
Maintenance Invoices Gloucester  Whole Grains Council
sparky@sparky-HP:~$

---

### Post by sparky7 on 2015-08-16
I was able to retrieve about 7 gig of data for my client. They were very happy. Could not of got it done without the help I received on this forum.
Thanks again to all that helped.

---

