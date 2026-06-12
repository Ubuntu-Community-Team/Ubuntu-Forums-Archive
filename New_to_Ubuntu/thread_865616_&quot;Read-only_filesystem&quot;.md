---
title: "&quot;Read-only filesystem&quot;"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-07-20
I'm having a problem working with my external harddrive.
I just formatted it to FAT32 filesystem, which as far as I understood gave me permission to read and write.  But now whenever I try to write something to the hard drive it says it's a read-only filesystem.
Also, when I look at the drive's properties it says the filesystem is msdos.  How do I enable it to allow writing

---

### Post by neurostu on 2008-07-20
find the dir where the drive is mounted, then type:
```

ls -l

```
it should list the owner and group of the drive, I'm guessing it will list root as the owner and group on that drive. To write to the drive you need to be the owner, or a member of the group that owns the drive.

You will probably need to mount the drive in a directory that you own... (like a dir under your /home dir)

I personally have been a bit confused by mounting drives in ubuntu, sometimes they automount and are writeable other times I have to mount them and no matter what I do I can't write to them (as you have to be root to mount, and then you have to be root to write to the disk)

If making a mount dir under you home dir doesn't work try using pmount to mount the drive, I have never had that fail.

---

### Post by SalsaShark on 2008-07-20
Well it says that "matt" (me) is the owner and root is the group.  But I cannot change any of the settings under "Permissions".

---

### Post by neurostu on 2008-07-20
to change group:
```

sudo chgrp -R <username> <directory>

```
like for most commands the -R is for recursive.

---

### Post by SalsaShark on 2008-07-20
OK, but that still won't let me write to it.  It still says it's read-only when I try to change the properties.

---

### Post by lswb on 2008-07-20
The msdos and vfat filesystems have no built-in provision for permissions. The permissions for the entire filesystem are set with mount options which will of course vary with what is desired.

To allow access to a vfat partition for a specific user or group, the line in /etc/fstab would be something like:

/dev/sda1 /dos  vfat  uid=1000,gid=100  0  0

You can also specify values for umask (and dmask and fmask also) to set permissions.

If the drive is removable media and does not have a line in fstab, then usually it will be mounted with rw permission for the current user when it is plugged in. 

Take a look at the man pages for mount and /etc/fstab for more info or you can google and find examples.

---

