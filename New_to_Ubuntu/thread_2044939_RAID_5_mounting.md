---
title: "RAID 5 mounting"
date: 2012-08-20
forum: New to Ubuntu
---

### Post by wiradog on 2012-08-20
Following BVZ post from 2011 to set up RAID5 on Ubuntu 12.04 server

Created and formatted the RAID (using mdadm),tried to create the mount point thus;
#created a directory: 'sudo mkdir /mnt/mikenas'
#opened editor to change fstab file,including the line:
/dev/md0/mnt/mikenas ext4 defaults 1 2
#used 'mount -a' to mount the RAID, without restart
 
message back 'ext4 does not exist'
Have tried resetting the system, but it does not recognize the RAID drive on boot-up, although it halts looking for the drive. 
I think there is a step missing here, can anyone help please.

#-o

---

### Post by steeldriver on 2012-08-20
well for sure there's a space missing between /dev/md0 and /mnt/mikenas ;)

(hence why it thinks 'ext4' is the mountpoint and says it does not exist)

you *may* also need to use the symlink from /dev/mapper rather than specifying /dev/md0 directly - but try it your way first

---

### Post by wiradog on 2012-08-20
Thanks Steeldriver, that missing space seem to be the problem, such a small thing for such a large effect.
On to configuring SAMBA now!

---

