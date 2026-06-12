---
title: "Is this mount error worth trying to fix?"
date: 2014-09-16
forum: New to Ubuntu
---

### Post by watson524 on 2014-09-16
Setting up a new machine after a disk failure and I have ubuntu on a USB "try" mode. Put in a 1.5TB HD that I thought I would use internally as my non OS drive and when trying to mount it I get:

Error mounting /dev/sdc1 at /media/ubuntu/15tbint: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=999,gid=999,dmask=0077,fmask=0177" "/dev/sdc1" "/media/ubuntu/15tbint"' exited with non-zero exit status 13: ntfs_mst_post_read_fixup_warn: magic: 0x001f01ff  size: 1024   usa_ofs: 257  usa_count: 65535: Invalid argument
Record 6 has no FILE magic (0x1f01ff)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdc1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Is this worth messing with at all or should I just ditch the drive? I don't think there's anything on it (tho that's what I was trying to check) so a format would likely be ok but the "or there is a hardware fault" scared me...

thanks!

---

### Post by watson524 on 2014-09-16
Update: I rebooted into win 7 and I didn't even have to tell it to, it ran chkdsk on its own and corrected some errors (they flew by so quickly I don't know what they were) and I then rebooted twice into windows and it seems like whatever it did fixed the issue at least from the windows side. I can now see a folder on the drive but it's crap and I don't really need it anyway. I then booted up into ubuntu and it seems like all is fine, it mounts the partition with no issues. So does it sound like all is ok? the only issue I have and I'm sure it's me being stupid is that I use gparted to kill what was there on the drive, created a new partition with a format of ext4 (dev/sdc1) but it won't let me write to it even tho it says it's mounted. I'm just trying to copy some test files to it.

---

### Post by watson524 on 2014-09-17
Looks like the chkdsk worked.

---

### Post by yancek on 2014-09-17
That error is usually caused by Linux/Ubuntu seeing the ntfs partition as being in an unsafe state.  There are several reasons for this, some of which were enumerated in the error report.  The standard method to repair is what you did, running chkdsk so if it's working, I wouldn't worry about it.

---

### Post by watson524 on 2014-09-17
Thanks for confirming! I'll mark this solved.

---

