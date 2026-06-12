---
title: "External devices present but unmountable - no rw"
date: 2014-04-05
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-04-05
I have two external devices that can be seen in sudo fdisk -l below. Neither of them will mount. The /sdb is rarely attached to this computer. I have it installed at the moment to transfer files from my desktop to it. Then it will be plugged into a pvr to record tv shows. The device, currently showing as /sdc is my external eSATA drive for backing up my /home. It is always physically plugged into the computer (Ubuntu 12.04) but powered up only once a week. 

/dev/sdb is formatted NTFS and /dev/sdc is formatted EXT4.

mark@Lexington:~$ sudo blkid

```
/dev/sda1: UUID="536a864f-d91c-4e3d-b6f6-108a783d5e46" TYPE="ext4" 
/dev/sda3: UUID="1455a163-528e-42ec-8b29-ca7076fc00c7" TYPE="ext4" 
/dev/sda4: UUID="19356bfa-bf91-414a-b4cb-22201d1e78d1" TYPE="swap" 
/dev/sdb1: LABEL="123456789" UUID="00013F5900013F59" TYPE="ntfs" 
/dev/sdc1: UUID="80cb5313-35a0-432b-9250-4cc62d79a3c8" TYPE="ext4" 

```

mark@Lexington:~$ sudo fdisk -l

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00084ceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    39063551    19530752   83  Linux
/dev/sda3        39063552  1937139711   949038080   83  Linux
/dev/sda4      1937139712  1953523711     8192000   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x511bee84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   625139711   312568832    7  HPFS/NTFS/exFAT


WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.

Disk /dev/sdc: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   781422767   390711383+  ee  GPT
```

I have this in my /etc/fstab:

mark@Lexington:~$ cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=536a864f-d91c-4e3d-b6f6-108a783d5e46  /            ext4  errors=remount-ro    0  1  
# /home was on /dev/sda3 during installation
UUID=1455a163-528e-42ec-8b29-ca7076fc00c7  /home        ext4  defaults             0  2  
# swap was on /dev/sda5 during installation
UUID=a37873a0-d70f-495f-92ea-fffb41041cf4  none         swap  sw                   0  0  
## below by mp 3-apr-14
UUID=80cb5313-35a0-432b-9250-4cc62d79a3c8  /media/backup  ext4  noauto,noatime,rw

/dev/sdb1                                  /media/sdb1  ext4  users,noauto,user    0  0
```

Also at power up, the splash screen says that GUID xxxxxxxx isn't mounted and **W**ait, **M**ount or **I**gnore


mark@Lexington:/$ mount

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)
```

---

### Post by steeldriver on 2014-04-05
Not clear what you're saying here - **which** UUID does the system complain about at boot time? It looks like it would be your **swap** (the UUID for swap in blkid does not agree with what's in fstab).

The other two devices are set to 'noauto' so the system shouldn't even *try* to mount them at boot time - do they mount manually if you do a 'mount -a'?

---

### Post by Mark_in_Hollywood on 2014-04-05
I have modified my etc/fstab to change the UUID for swap to match the UUID given by sudo blkid.

That's the first half of this problem solved. Thank you.

Commenting out the /etc/fstab line starting: /dev/sdb1

and issuing: sudo mount -a

has allowed the /dev/sdb1 to mount and I can transfer files.

> **steeldriver said:**
> Not clear what you're saying here - **which** UUID does the system complain about at boot time? It looks like it would be your **swap** (the UUID for swap in blkid does not agree with what's in fstab).

Yes, boot time splash screen shows the UUID for the swap. That stays on-screen all of 1 second.

The other two devices are set to 'noauto' so the system shouldn't even *try* to mount them at boot time - do they mount manually if you do a 'mount -a'?


mark@Lexington:/$ sudo mount -a
[sudo] password for mark: 
mark@Lexington:/$

These are the messages on mounting the external drives:

Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/sdb1 does not exist

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/backup

---

### Post by Double.J on 2014-04-05
Hi there!

Firstly both your external drives are set to not mount at boot with the argument noauto
Secondly the backup drive does not have an argument to allow non root user mounting. By adding user to the argument line you'll enable users other than root to umount the partition. Sudo gives the user root user privileges, but does not make you the root user. If the fstab says only the root user can mount, only the root user can mount.

If you do not see an argument under the options column in the fstab, the default options will be used. auto is the default behaviour, so noauto is stopping the mount. The other relevant default is user. by default a drive is only mounted by the root user with the nouser argument. specifying user in th options list enables you to mount the drive.


Finally the /dev/sb1 mount error - does the direcory /media/sd1 exist in /media?

Jj

---

### Post by Mark_in_Hollywood on 2014-04-06
```
mark@Lexington:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid   0  0  
# / was on /dev/sda1 during installation
UUID=536a864f-d91c-4e3d-b6f6-108a783d5e46  /            ext4  errors=remount-ro     0  1  
# /home was on /dev/sda3 during installation
UUID=1455a163-528e-42ec-8b29-ca7076fc00c7  /home        ext4  defaults              0  2  
# swap was on /dev/sda5 during installation

## UUID for swap changed by m 5-apr-14

UUID=19356bfa-bf91-414a-b4cb-22201d1e78d1  none         swap  sw                    0  0  

## below by m 3-apr-14

UUID=80cb5313-35a0-432b-9250-4cc62d79a3c8	/media/backup	ext4	noauto,noatime,user,rw	0	0

## line below commented out 5-apr-14
## /dev/sdb1                                  /media/sdb1  ext4  users,noauto,user,rw  0  0  
```

and

mark@Lexington:/media$ ls
[COLOR="#0000FF"]backup  sdb1[/COLOR] -- N.B. color is slightly different in my terminal.

for your convenience:

```
mark@Lexington:/media$ sudo blkid
/dev/sda1: UUID="536a864f-d91c-4e3d-b6f6-108a783d5e46" TYPE="ext4" 
/dev/sda3: UUID="1455a163-528e-42ec-8b29-ca7076fc00c7" TYPE="ext4" 
/dev/sda4: UUID="19356bfa-bf91-414a-b4cb-22201d1e78d1" TYPE="swap" 
/dev/sdb1: UUID="80cb5313-35a0-432b-9250-4cc62d79a3c8" TYPE="ext4" 
```

After some work on the fstab, on powering up the eSATA drive, Nautilus reports it as 400 GB Filesystem. The "Backup" program, the default to Ubuntu, has written my /home to that external drive. But to see the files or contents of the device, it must be mounted by clicking. See attached screenshot.[ATTACH=CONFIG]251773[/ATTACH]

---

### Post by steeldriver on 2014-04-06
The thread is marked as solved - is it? Or do you still want something different?

The backup device still has mount option **noauto **in your fstab file - if you want the system to *try *to mount the device on boot, but not to throw an error if it's unavailable, you could try replacing noauto with **nofail**

---

### Post by Mark_in_Hollywood on 2014-04-06
Thank you. As long as the OS will allow me to mount the device, albeit via clicking the "400 Gig Filesystem" in the file manager, I'm good to go. I did not want the device mounted at boot time only to be able to run the weekly scheduled backup of /home.

---

