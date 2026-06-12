---
title: "[SOLVED] Where are the hard drives?"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by 59chip on 2008-08-10
I am using Xubuntu live CD, boots OK.  I can't locate any of the hard drives on the file system.  Where are they?

---

### Post by PGScooter on 2008-08-10
```

sudo fdisk -l

```

what does this bring up?

Also, in general, to see where things are mounted, use
```
mount
```

---

### Post by 59chip on 2008-08-10
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf042f042

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665317+   7  HPFS/NTFS
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

---

### Post by PGScooter on 2008-08-10
ah, I missed that you were running a live cd, so of course nothing is mounted yet! silly me.

Ok, so what I would do is make a folder:
```

sudo mkdir /media/windows1
sudo mkdir /media/windows2
mount /dev/sda1 /media/windows1
mount /dev/sda2 /media/windows2

```

now, you can navigate to /media/ and to the mounted filesystems. Are you by chance trying to recover data form a windows partition? If so, and windows did not shutdown correctly, it will be difficult to mount. You will have to force mount and that is supposedly dangerous (although I have done it 5 times with no bad luck).

---

### Post by 59chip on 2008-08-10
Almost worked, here are the results...

```
ubuntu@ubuntu:~$ sudo mkdir /media/windowsC
ubuntu@ubuntu:~$ sudo mkdir /media/windowsD
ubuntu@ubuntu:~$ mount /dev/sda1 /media/windowsC
mount: only root can do that
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/windowsC
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda1 /media/windowsC -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda1 /media/windowsC ntfs-3g force 0 0
ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda1 /media/windowsC -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.

```

THANKS!

---

### Post by InfinityCircuit on 2008-08-10
The reason why it isn't finding your drives is because they aren't clean, so it doesn't want to automatically mount them.  You should try booting into windows and running chkdsk (I think that's the name of it).  Windows will probably run this automatically on boot if the partitions have the "dirty" flag set.

---

### Post by john test on 2008-08-10
> **59chip said:**
> I am using Xubuntu live CD, boots OK.  I can't locate any of the hard drives on the file system.  Where are they?

Are you going to actually go ahead and click on install to install linux?  if you do that then the drives should show up.

---

### Post by PGScooter on 2008-08-10
59chip, we need to know more information.
Is your windows partition not working properly?

after the forced mount, it didn't work? Did you try to go to the folder after you did the force?

---

### Post by 59chip on 2008-08-10
After forced mount everything works.  I can see both hard drives under /media folder.

Both partitions work fine under Windows XP.

---

### Post by PGScooter on 2008-08-10
that's good to hear!

if you want, you can go to "threat tools" and then click on "mark thread as SOLVED"

---

