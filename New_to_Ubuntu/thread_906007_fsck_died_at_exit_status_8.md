---
title: "fsck died at exit status 8"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by sloopveedub on 2008-08-30
Reading through the other posts didn't seem to help.  I get the fsch...status 8 error when trying to boot my Xubuntu server.  I'm probably missing something stupid, so hopefully someone can point it out for me!


```
ubuntu@ubuntu:~$ sudo blkid
/dev/sdb1: TYPE="swap" UUID="812630cd-efab-48aa-8cd4-7ce64174c95f" 
/dev/sdb2: UUID="62ca7e3f-d0e3-43e7-93b6-08db34b79707" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="d441b06e-4df5-4576-b855-d024c87565d0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: TYPE="swap" UUID="b27dcfdb-ccfa-4ee9-b3e4-a5eeb53de018" 
/dev/sdc3: UUID="2e262cf9-9dc4-40f7-a1e8-f9ac56386f0b" SEC_TYPE="ext2" TYPE="ext3" 
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdc1	/               ext3    defaults,errors=remount-ro 0       1
/dev/sdb1	none            swap    sw              0       0
/dev/sdc2	none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdc3	/home		ext3	nodev,nosuid	0	2
/dev/sdb2	/media/backups	ext3	rw,user	0	0

```

---

### Post by Bachstelze on 2008-08-31
What I'd do if I were you is boot a Live CD and run fsck on your filesystems manually. That way, you'll be able to paste the exact error messages if something goes wrong.

---

### Post by sloopveedub on 2008-08-31
> **HymnToLife said:**
> What I'd do if I were you is boot a Live CD and run fsck on your filesystems manually. That way, you'll be able to paste the exact error messages if something goes wrong.

Coming to you live from a Live CD....

Nothing unusual came up (after I remembered to umount the partitions).  They all pretty much said:
```
ubuntu@ubuntu:/$ sudo fsck /dev/sdc3
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdc3 has gone 188 days without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdc3: 22652/29032448 files (5.1% non-contiguous), 3466831/58048869 blocks
```

---

### Post by sloopveedub on 2008-09-01
Since I already had a headache and didn't need another one, I just downloaded a fresh copy of Xubuntu 8 and installed it rather than dink around to find out the root cause of my fsck problem.  

So if anyone else runs into this problem and doesn't feel like trying to figure it out, the re-install method works but be careful!  In my case I had /home set up on a separate partition.  So, it was a matter of telling gpart (the install's disk partitioning program) which partition to write as my root directory, which was /home, which was /swap, etc.  Of course, install overwrote my root directory but didn't touch /home.  If you didn't put /home on a separate partition, then the install process will overwrite your data!  Be careful!

The other problem will be that if you customized certain files (e.g., /etc/samba/smb.conf) then that too will be over-written.  Be aware that you'll either need to re-do these or restore from back-ups.

---

