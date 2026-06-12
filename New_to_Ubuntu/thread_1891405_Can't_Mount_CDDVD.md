---
title: "Can't Mount CD/DVD"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by NM5TF on 2011-12-05
suddenly I cannot access my CD/DVD drive....I get this error message:

Error mounting: mount exited with exit code 1: helper failed with:
mount: mount point /media/cdrom0 does not exist

I run Lucid 10.04.3 LTS if that helps....

any help???

Tom

---

### Post by NM5TF on 2011-12-05
a little more info:

I got the CD to work by editing /etc/fstab

it now looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=81666fd2-cbcf-43d0-ac69-40e361c84629 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=87a4586c-7df5-4287-bf2e-af70ffafe7b7 none            swap    sw              0       0

the DVD still does not work, now I get this error message:

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

the output of dmesg | tail is:

tommy@tommy-desktop:~$ dmesg | tail
[  169.410950] VFS: busy inodes on changed media or resized disk sr0
[  169.417887] VFS: busy inodes on changed media or resized disk sr0
[  169.430233] VFS: busy inodes on changed media or resized disk sr0
[  169.460953] VFS: busy inodes on changed media or resized disk sr0
[  169.469391] VFS: busy inodes on changed media or resized disk sr0
[  169.474191] VFS: busy inodes on changed media or resized disk sr0
[  169.478392] VFS: busy inodes on changed media or resized disk sr0
[  169.484003] VFS: busy inodes on changed media or resized disk sr0
[  218.013929] UDF-fs: No anchor found
[  218.013938] UDF-fs: No partition found (1)


unless I am missing something, I think there should be an entry in fstab
for /dev/sr0 that tells the OS where the mount point is...yes???

---

### Post by NM5TF on 2011-12-06
> **NM5TF said:**
> a little more info:

I got the CD to work by editing /etc/fstab

it now looks like this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=81666fd2-cbcf-43d0-ac69-40e361c84629 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=87a4586c-7df5-4287-bf2e-af70ffafe7b7 none            swap    sw              0       0

the DVD still does not work, now I get this error message:

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

the output of dmesg | tail is:

tommy@tommy-desktop:~$ dmesg | tail
[  169.410950] VFS: busy inodes on changed media or resized disk sr0
[  169.417887] VFS: busy inodes on changed media or resized disk sr0
[  169.430233] VFS: busy inodes on changed media or resized disk sr0
[  169.460953] VFS: busy inodes on changed media or resized disk sr0
[  169.469391] VFS: busy inodes on changed media or resized disk sr0
[  169.474191] VFS: busy inodes on changed media or resized disk sr0
[  169.478392] VFS: busy inodes on changed media or resized disk sr0
[  169.484003] VFS: busy inodes on changed media or resized disk sr0
[  218.013929] UDF-fs: No anchor found
[  218.013938] UDF-fs: No partition found (1)


unless I am missing something, I think there should be an entry in fstab
for /dev/sr0 that tells the OS where the mount point is...yes???

as I suspected, there was no entry in /etc/fstab for the cd-rom....

here is the fix I used:

code:

gksu gedit /etc/fstab

then I added this code after the last line in fstab

code:

/dev/sr0     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

everything now works great...music cd's, data cd's, all dvd's....

---

