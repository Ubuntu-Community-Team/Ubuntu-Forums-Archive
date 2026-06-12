---
title: "Slave drive cant be accessed over network"
date: 2012-03-15
forum: New to Ubuntu
---

### Post by DrGreenBean on 2012-03-15
Hi
 I have a slave drive that is shared so my server can do a backup to it. I use Ubuntu 11.4
 The problem is that the drive sleeps/spins down so nothing cant access the shares. If I go to  Places and then open the drive it spins up and I can access it from my pc and from the network.
 

 The drive only gets used for backups and when my network scanner scans to it.
 How do I solve this problem?
 

 Thanks

---

### Post by DrGreenBean on 2012-03-15
Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1a551a54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        8936    71667712    7  HPFS/NTFS
/dev/sda3            8936       18242    74750977    5  Extended
/dev/sda5            8936       17728    70625280   83  Linux
/dev/sda6           17728       18242     4124672   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb328096

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243201  1953512001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ffeacb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488383488    7  HPFS/NTFS
cp@cp-pc:~$ 

the drive in question is Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes

---

### Post by DrGreenBean on 2012-03-15
cp@cp-pc:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
//10.0.0.15/data/ on /media/data type cifs (rw,mand)
//10.0.0.15/customer/ on /media/Customer-Backup type cifs (rw,mand)
gvfs-fuse-daemon on /home/cp/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cp)
/dev/sdc1 on /media/VM type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on /media/Offsite type ext4 (rw,nosuid,nodev,uhelper=udisks,commit=0,commit=0)

---

