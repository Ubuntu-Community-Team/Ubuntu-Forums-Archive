---
title: "How to automount partitions on boot?"
date: 2014-07-05
forum: New to Ubuntu
---

### Post by NA3OH on 2014-07-05
Looking to automount these two partitions.

```
/dev/sda6: LABEL="Media" UUID="01CF5610152D4EB0" TYPE="ntfs" 
/dev/sda8: LABEL="BackUp" UUID="01CF48949CE3FAE0" TYPE="ntfs"
```

Current /ect/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=9dcaf243-3947-46db-9b16-33c781759ee6 /               ext4    errors=remount-ro 0       1
/dev/sda7       none            swap    sw              0       0
```




Completely unsure of how to add partitions to this. Could someone explain how to add these partitions?

---

### Post by nerdtron on 2014-07-05
It's written on the fstab file itself. Syntax is

```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
```

filesystem = the dvice itself like /dev/sda1 or its UUID
mount point = where do you want the device to be mounted
type = type of filesystem the device has
options = lots of options available but "defaults" can be a good option
dump = I just leave it to 0 since I don't know the technical explanation
pass = I think this one is a sequence number for the filesystem check upon startup

Be sure that the mount points are existent:
```
sudo mkdir /media/Media
sudo mkdir /media/BackUp
```

Now you should add these two lines on your fstab.
```
UUID=01CF5610152D4EB0 /media/Media ntfs defaults 0 0
UUID=01CF48949CE3FAE0 /media/BackUp ntfs defaults 0 0
```

Now each drive should be mounted on their own folders in /media.

---

### Post by NA3OH on 2014-07-05
> **nerdtron said:**
> It's written on the fstab file itself. Syntax is

```
<file system> <mount point>   <type>  <options>       <dump>  <pass>
```

filesystem = the dvice itself like /dev/sda1 or its UUID
mount point = where do you want the device to be mounted
type = type of filesystem the device has
options = lots of options available but "defaults" can be a good option
dump = I just leave it to 0 since I don't know the technical explanation
pass = I think this one is a sequence number for the filesystem check upon startup

Be sure that the mount points are existent:
```
sudo mkdir /media/Media
sudo mkdir /media/BackUp
```

Now you should add these two lines on your fstab.
```
UUID=01CF5610152D4EB0 /media/Media ntfs defaults 0 0
UUID=01CF48949CE3FAE0 /media/BackUp ntfs defaults 0 0
```

Now each drive should be mounted on their own folders in /media.

Thanks!

---

