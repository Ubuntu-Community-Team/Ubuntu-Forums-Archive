---
title: "partimage and external HDD"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by cjv8888 on 2008-05-31
I am using Gutsy and to cut a long story short, I tried to make a partition image into my external HDD which is mounted and functioning perfectly.  However partimage could not make temp file in it and the backup was put into /.
So I went into the terminal and tried to move the backup file but there was no way I could CD into the external HD.
It will list under media as NEW VOLUME but everytime I tried it will come back with no such directory as NEW.
I am quite a noob at this and any help is greatly appreciated.

---

### Post by logos34 on 2008-05-31
What partition are you trying to image and where are you trying to store it?  The partition being imaged cannot be mounted, but the destination must be.

post your 

sudo fdisk -l

too

---

### Post by cjv8888 on 2008-05-31
I am dual booting with win98 and I am trying as an experiment to backup that partition so I am in Ubuntu and trying to back it onto an external HD. Here is the fdisk -l.  The backup was ok but it was done into the root directory and I cannot move it.
Disk /dev/sda: 20.4 GB, 20404101120 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x84c0e140

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        1163     9333765    f  W95 Ext'd (LBA)
/dev/sda2   *        1164        2480    10578802+   c  W95 FAT32 (LBA)
/dev/sda5               2        1163     9333733+   b  W95 FAT32

Disk /dev/sdb: 17.2 GB, 17245863936 bytes
255 heads, 63 sectors/track, 2096 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70a370a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2004    16097098+  83  Linux
/dev/sdb2            2005        2096      738990    5  Extended
/dev/sdb5            2005        2096      738958+  82  Linux swap / Solaris

Disk /dev/sdc: 122.9 GB, 122941341696 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbfb7b8aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6081    48845601    7  HPFS/NTFS
/dev/sdc2            6082       14946    71208112+   f  W95 Ext'd (LBA)
/dev/sdc5            6082       14946    71208081    b  W95 FAT32

---

### Post by logos34 on 2008-05-31
So you imaged/backed up sda5 (or sda2?) and it ended up on root (sdb1), and you can't cd into the external drive sdc (but which partition?) You need to be specific

post output for 

cat /etc/fstab

mount

---

### Post by cjv8888 on 2008-05-31
I imaged sda2 and it ended up in root.  I am trying to move it to sdc5.

---

### Post by cjv8888 on 2008-05-31
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=bf207d68-5f0c-4a72-9358-0c5b78b8bb37 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=37d713d5-2b84-4768-99f6-27d8e5266c3e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
clifford@cliff-linux:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc5 on /media/NEW VOLUME type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/sdc1 on /media/New Volume type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

---

### Post by logos34 on 2008-06-01
I see whats happening:

If the (compressed?) file is bigger than 4gb, fat32 can't hold it 

Also, there's a space:
> 
/dev/sdc5 on /media/**NEW VOLUME** type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,uma sk=077,usefree)

ao you need to use the tab key or put both words inside "".  So to cd over into it try

cd /media/NEW[TAB] (this will autocomplete line)

OR

cd /media/"NEW VOLUME"

To transfer the partimage file:

sudo mv nameofbackup.gz.000 /media/"NEW VOLUME"

("nameofbackup.gz.000" is just example)

Change ownership so you can restore it if need be:

sudo chown yourusername /media/sdc5/nameofbackup.gz.000

---

### Post by cjv8888 on 2008-06-01
I managed to move the file.  I think the "NEW VOLUME"  was the way
Thanks.
Next time I will try directly imaging into the ext HD again.
Do I put /dev/sdc5 into the path -  image file to create/use ?

---

### Post by logos34 on 2008-06-01
> **cjv8888 said:**
> 
Next time I will try directly imaging into the ext HD again.
Do I put /dev/sdc5 into the path -  image file to create/use ?

no, use the mounted location:
> /media/"NEW VOLUME"/backupimage

A propos the fat32 4 GB file size limit, on second thought it's probably not an issue since the default setting in Partimage is to split the image into 2037 MB chunks.  So just stick to that.

Good luck and enjoy

---

### Post by cjv8888 on 2008-06-01
I tried again to image into the ext HD.  Still got this message
Cannot create temp file [/media/"NEW   &#9474;                   
                   &#9474; VOLUME"/pia4aed6b2.tmp]. Please,       &#9474;                   
                   &#9474; check there is space enough and you    &#9474;                   
                   &#9474; have access rights.

---

### Post by logos34 on 2008-06-01
try:

> sudo mkdir /media/sdc5

sudo chmod 777 /media/sdc5

sudo umount /media/"NEW VOLUME"

sudo mount -t vfat -o umask=000 /dev/sdc5 /media/sdc5

Now see if you can write to it

---

### Post by cjv8888 on 2008-06-01
No, the same error message appears

---

### Post by logos34 on 2008-06-01
ok, I don't have any experience with fat32 partitions (never had any reason to use them), so hopefully someone else will pop in with some suggestions.  I thought the umask setting would do it (= rwx access for everyone)

---

### Post by cjv8888 on 2008-06-01
If FAT32 is the problem, may be I will try and image the backup into the NTFS partition. If it can be done then I can just move it across later.

---

