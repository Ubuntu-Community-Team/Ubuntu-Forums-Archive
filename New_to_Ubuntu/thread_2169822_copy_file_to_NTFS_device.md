---
title: "copy file to NTFS device"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by deeppow on 2013-08-23
I need to copy a file from my Desktop to an NTFS drive that is attached.  I have the drive mounted but can't copy and paste into the NTFS drive.  What do I need to do?

---

### Post by rai_shu2 on 2013-08-23
How exactly did you mount it?

---

### Post by deeppow on 2013-08-23
did an auto mount at the boot

---

### Post by coffeecat on 2013-08-23
> **deeppow said:**
> did an auto mount at the boot

That doesn't tell us much.

Post the output of this terminal command with the ntfs drive plugged in and mounted:

```
mount
```

---

### Post by deeppow on 2013-08-23
ralph@AMS2:~$ mount
/dev/sda5 on / type ext4 (rw)
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
/dev/sdb1 on /media/UserData type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/ralph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ralph)

---

### Post by coffeecat on 2013-08-23
This:

> **deeppow said:**
> ```

/dev/sdb1 on /media/UserData type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gvfs-fuse-daemon on /home/ralph/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ralph)
```

Tells us that the sdb1 partition is mounted read-write using the ntfs-3g driver. So the question is: what happens when you try to copy and paste into it? You say you can't but what happens when you try? Do you get an error message?

Also - you say "auto-mount at boot". Does that mean you simply have the drive plugged in when you boot, relying on the automounting capability of the file-manager (actually udisks) or do you have a custom line in /etc/fstab?

---

### Post by deeppow on 2013-08-24
Many thanks for you input!  

I trashed the original mount and rebuilt a new one that works fine now.

---

