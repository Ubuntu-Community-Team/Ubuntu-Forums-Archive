---
title: "mounting a drive twice"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by rcatank2 on 2014-01-05
Hi,

After much research and trial and error of different ways commands, I have to come to the community to ask for help from the experts. 

Goal: Mount the main linux partition twice in different locations.

According to many, since I am past kernel 2.xx.x I should be able to take any FS and mount to as many mount points that I want. But today, for me it does not seem to be case.

Command used:
```
mount -t ext4 -o ro /dev/sda1 /myself
```

Error: 
```
mount: /dev/sda1 already mounted or /myself busy
mount: according to mtab, /dev/sda1 is mounted on /

```


Here is a quick dump of other background information:
```

tank / # lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0    20G  0 disk 
&#9500;&#9472;sda1   8:1    0  16.9G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0   3.1G  0 part [SWAP]
sr0     11:0    1  59.5M  0 rom  


tank / # blkid
/dev/sr0: LABEL="VMware Tools" TYPE="iso9660" 
/dev/sda1: UUID="7e241662-c0c1-4e8e-a202-1798846a9cc3" TYPE="ext4" 
/dev/sda5: UUID="63382cf3-faf5-43a1-bc17-cb2cd87d0b44" TYPE="swap" 



tank / # uname -r
3.11.0-12-generic


tank / # ls
bin   cdrom  etc   initrd.img      lib    lost+found  mnt     opt   root  sbin  sys  usr  vmlinuz
boot  dev    home  initrd.img.old  lib64  media       myself  proc  run   srv   tmp  var



tank / # mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
none on /sys/fs/pstore type pstore (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=tank)




```

I dont want to use bind, I just want to mount sda1 to /myself as a RO mount

---

### Post by tomearp on 2014-01-05
Hi,

Just fired up a VM for a quick experiment...

Output of mount on a fresh install:
```
tom@tom-virtual-machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
tom@tom-virtual-machine:~$
```

I made a directory to mount to:
```
sudo mkdir /myself
```

If I try to mount /dev/sda1 to /myself as a read-only partition:
```
tom@tom-virtual-machine:~$ sudo mount -o ro /dev/sda1 /myself
mount: /dev/sda1 already mounted or /myself busy
mount: according to mtab, /dev/sda1 is mounted on /
```

If I try to mount it rw then it works just fine:
```
tom@tom-virtual-machine:~$ sudo mount /dev/sda1 /myself
tom@tom-virtual-machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sda1 on /myself type ext4 (rw)
tom@tom-virtual-machine:~$
```

I powered down the VM, added a new virtual hard disk and rebooted to see if it would happen with a non-system partition...

Mounting the new partition once read/write, then trying to mount it again readonly produces the same result:
```
tom@tom-virtual-machine:~$ sudo mount /dev/sdb1 /myself
tom@tom-virtual-machine:~$ sudo mkdir /myself2
tom@tom-virtual-machine:~$ sudo mount -o ro /dev/sdb1 /myself2
mount: /dev/sdb1 already mounted or /myself2 busy
mount: according to mtab, /dev/sdb1 is mounted on /myself
tom@tom-virtual-machine:~$
```

Next I unmounted them both, mounted as readonly first, then tried to mount read/write with the same result:
```
tom@tom-virtual-machine:~$ sudo umount /myself
tom@tom-virtual-machine:~$ sudo umount /myself2
tom@tom-virtual-machine:~$ sudo mount -o ro /dev/sdb1 /myself2
tom@tom-virtual-machine:~$ sudo mount /dev/sdb1 /myself
mount: /dev/sdb1 already mounted or /myself busy
mount: according to mtab, /dev/sdb1 is mounted on /myself2
```

Then attempting to mount at /myself readonly works, resulting in it mounted twice readonly:
```
tom@tom-virtual-machine:~$ sudo mount -o ro /dev/sdb1 /myself
tom@tom-virtual-machine:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/tom/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=tom)
/dev/sdb1 on /myself2 type ext4 (ro)
/dev/sdb1 on /myself type ext4 (ro)
tom@tom-virtual-machine:~$
```

So...in summary if you have a partition mounted read/write, the second time you mount it you must also do it read/write.
If it's mounted readonly, the second time you mount it you must also do it readonly.

---

