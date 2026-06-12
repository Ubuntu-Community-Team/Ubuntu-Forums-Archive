---
title: "Mounting External Hard Drive not working."
date: 2008-11-03
forum: New to Ubuntu
---

### Post by justin_c18 on 2008-11-03
Currently I'm trying to mount my external hard drive as a regular user. But, now that I've deleted an entry in my /etc/fstab I can't mount it. I pretty well just want to mount it either way now. Preferably as root like it was before. I've only been mounting the darn thing for 4 years at /media/disk. Don't ask me why I changed it.

Here's dmsg: dmesg | tail
[187131.383742] kjournald starting.  Commit interval 5 seconds
[187131.385393] EXT3 FS on sdb1, internal journal
[187131.385410] EXT3-fs: mounted filesystem with ordered data mode.
[187195.850975] kjournald starting.  Commit interval 5 seconds
[187195.852463] EXT3 FS on sdb1, internal journal
[187195.852478] EXT3-fs: mounted filesystem with ordered data mode.
[187202.777130] kjournald starting.  Commit interval 5 seconds
[187202.778346] EXT3 FS on sdb1, internal journal
[187202.778358] EXT3-fs: mounted filesystem with ordered data mode.
[187229.900228] usb 7-2: USB disconnect, address 5

sudo mount /media/disk doesn't do anything. I think I have to make an /etc/fstab entry,  but the drive doesn't even mount in /etc/mtab anymore.

What can I do to fix it? I hope it's still fixable as I just bought it not too long ago after a hard drive failure.

What is the default mount entry in /etc/fstab?

Thanks, 
Justin.

---

### Post by justin_c18 on 2008-11-03
I got it to mount as /media/disk-1 now
/etc/mtab says it's /dev/sdb1 /media/disk-1 ext3 rw,nosuid,nodev,uhelper=hal 0 0

fstab says there's nothing mounted still.

What should I do to put it back to /media/disk? What fstab variables should it be?

Thanks

---

### Post by vanadium on 2008-11-03
An external disk should not need to be mounted through /etc/fstab. By default, Ubuntu auto-mounts it and uses the volume label of the disk as the name of the mount point.

Remove your line in /etc/fstab for the drive (you can put a comment sign "#" in front of the line).

Make sure the label of your volume is set to "disk" (or any other name of your choosing (see [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
).

Make sure the file system of the drive is "clean" (run a file check on the partition).

You will need to remove the existing mount point: "sudo rmdir /media/drive".

Reboot the system, and when connecting the drive, it should auto-mount.

If you want me to be more specific with my instructions, then post the output of following commands here (with the external drive connected to the system and powered on):

```

cat /etc/fstab
sudo blkid
mount
ls -l /media

```

---

### Post by justin_c18 on 2008-11-03
```

cat /etc/fstab
sudo blkid
mount
ls -l /media

```

Thanks for the reply. My drive didn't automount after I restarted. Once I restarted, it says, "Cannot mount volume. Unable to mount volule. Mount_point cannot contain the following characters, G_DIR_SEARATOR (usually /)"

Then another window comes up and says, "Unable to mount 500.1 GB Media. DBus error org.freedesktop,DBUS.Error.NoReply: Did not receive a reply. Possible causes: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I remember trying to rename the mounted drive when I had it mounted. I put /media/disk. And, a couple other things.

How do I make sure the filesystem is clean? I removed /media/disk before restarting as well.

cat /etc/fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7ae7d43a-3566-475b-baed-597318b3b721 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=c7438e7e-fb3a-408c-8ed3-dcc4a36759a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

sudo blkid:
```
/dev/sda1: UUID="7ae7d43a-3566-475b-baed-597318b3b721" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c7438e7e-fb3a-408c-8ed3-dcc4a36759a1" 
/dev/sdb1: UUID="41f8d132-6782-474c-9815-83a3e20afa19" SEC_TYPE="ext2" TYPE="ext3" 
```

mount:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/justin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=justin)

```

lsl -l media:
```
lrwxrwxrwx 1 root root    6 2008-10-27 09:37 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-10-27 09:37 cdrom0
```

Thanks again, hopefully we can get this ressolved. :)

---

### Post by justin_c18 on 2008-11-03
e2label is used ot label ext3 filesystems, apparently it's not in the repositories. Can you suggest another program?

---

### Post by justin_c18 on 2008-11-03
I've renamed the drive. 

```
sudo e2label /dev/sdb1 external
```

I tried to check it with,

```
sudo e2label /dev/sdb1
```

But, I get:

> e2label: No such file or directory while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.

Now, I'll restart, and see what's going on.

---

### Post by justin_c18 on 2008-11-03
I've restarted. It hasn't mounted. I looked in gparted, it's not listed.

sudo blkid
/dev/sda1: UUID="7ae7d43a-3566-475b-baed-597318b3b721" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="c7438e7e-fb3a-408c-8ed3-dcc4a36759a1" 
/dev/sdb1: UUID="41f8d132-6782-474c-9815-83a3e20afa19" SEC_TYPE="ext2" TYPE="ext3" 

Still exists. hmm.

---

### Post by justin_c18 on 2008-11-03
Okay, I've ressolved the issue. I'm entirely sure what I did. But, I did a ls -s /dev/sdb1 /media/. Looked at the UUID, or something. Seen that it was changed to /media/external. Once I mounted it, I removed the  vole > settings "mount point, file system I initially put down in computer > right click external > properties, etc..

Once that was done, I did a, "sudo mount /dev/sdb1 /media/external". It mounted. I seen that I still had /media/disk still there, so I deleted that providing nothing was mounted there. Which there wasn't. I umounted /media/external, restarted and it auto-mounted. 

It was something along those lines. :)

Now, one thing I'd like to do is, change permissions recursively to root on /media/external. How could I go about doing that? I still wnat to be able to read, and copy from the external drive to my desktop. But, I don't want to be able to write, or delete as a regular user. Similar to how it is on a normal setup.

---

