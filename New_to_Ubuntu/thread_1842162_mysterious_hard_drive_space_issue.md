---
title: "mysterious hard drive space issue"
date: 2011-09-10
forum: New to Ubuntu
---

### Post by skyzthelimit230 on 2011-09-10
Hello,
So this morning I booted up Ubuntu and had about 10gigs free on my hard drive. Over the last hour or so, something has reduced all this space to a grissly 100 mbs. 

I haven't done anything out of the ordinary, so what stole all this space? And how can I find the culprit and eradicate it?

Thank you.

---

### Post by papibe on 2011-09-10
Could you post the results of these two commands?
```
$ sudo mount -l

$ df -h
```
Regards.

---

### Post by skyzthelimit230 on 2011-09-10
mount: invalid option -- '1'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by papibe on 2011-09-10
I think you made a typo. Try copy/paste the commands to the terminal (omit the $).

Please use the # tags (code tags) to paste the results.

Regards.

---

### Post by The Cog on 2011-09-11
That mount command had a lower-case L at the end, not a digit one. That's the cause of the error message. 

I don't see the output of **df -h** at all, which would have been more helpful. 

This program might be useful for finding the culprit:
[https://help.ubuntu.com/community/Baobab](https://help.ubuntu.com/community/Baobab)

---

### Post by skyzthelimit230 on 2011-09-11
Sorry about that haha

```

/dev/sda4 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdb1 on /media/Elements type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) [Elements]
gvfs-fuse-daemon on /home/fil/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=fil)


```


```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              45G   18G   25G  43% /
none                  2.0G  720K  2.0G   1% /dev
none                  2.0G  1.2M  2.0G   1% /dev/shm
none                  2.0G  228K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sdb1             1.9T  1.7T  198G  90% /media/Elements

```

---

### Post by skyzthelimit230 on 2011-09-11
I don't know what is going on, but this morning I booted Ubuntu and the issue is gone! It's back to the original 24 gigs free!

Anyone here a magician? I don't know what this is all about. Please enlighten me.

---

