---
title: "Can't save settings?"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Document on 2013-06-16
I created a bootable USB Pendrive yesterday, then I installed Ubuntu alongside Windows. Now no matter what I do, I can't save ANY settings on my computer. Pointer Acceleration and brightness all revert back to default. I am not running it from the USB. Did I do something wrong?

---

### Post by CatKiller on 2013-06-16
Which filesystem did you use for your partitions?

---

### Post by Document on 2013-06-16
I honestly have no idea. I'm a complete noob with this.

Is there a way I could find this out?..

Would re-installing change anything?

---

### Post by CatKiller on 2013-06-17
The Disks utility should tell you.

Settings are stored in your Home folder. If you can't write there, the settings won't be saved. If it's always been like it, it seems likely that however you've formatted it (a Windows filesystem, for example) can't handle UNIX-style permissions. If it happened recently I'd suspect that you've been playing with ownership or permissions on your Home folder.

---

### Post by 3rdalbum on 2013-06-17
Can we please see the output of these commands (hit Control-Alt-T and copy and paste each line in, then copy the result out and paste it into the message):

```
mount
cat /etc/fstab
ps aux | grep "dconf"

```

And can you create or modify files in your home folder?

---

### Post by Document on 2013-06-17
> **3rdalbum said:**
> Can we please see the output of these commands (hit Control-Alt-T and copy and paste each line in, then copy the result out and paste it into the message):

```
mount
cat /etc/fstab
ps aux | grep "dconf"

```

And can you create or modify files in your home folder?


I can create and modify files in my home folder. This is the output of the commands:


/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mimzy)
mimzy@Mimzy-PC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=48a799a6-ba12-46f9-9198-b83b6b00f047 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7315c2fc-a6a0-4668-90e3-40e5627e2fe6 none            swap    sw              0       0
mimzy@Mimzy-PC:~$ ps aux | grep "dconf"
mimzy     1844  0.0  0.0  24448  2424 ?        Sl   16:45   0:00 /usr/lib/dconf/dconf-service
mimzy     2740  0.0  0.0   4448   832 pts/1    S+   16:58   0:00 grep --color=auto dconf

---

