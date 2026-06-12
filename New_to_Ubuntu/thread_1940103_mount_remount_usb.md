---
title: "mount remount usb"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-03-13
I'm trying to read what's on my usb drive. It's plugged in and the light is on, but I can't access it.

I searched the previous posts and one suggested it was a known bug.

But I can pull the usb out and when I put it back in again Lubuntu asks me if I want to look at it with the file manager.

Here's the code.

```
k@k-TECRA-A5:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/k/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=k)
k@k-TECRA-A5:~$ ls /dev/sda1
/dev/sda1
k@k-TECRA-A5:~$ cd /dev/sda1
bash: cd: /dev/sda1: Not a directory
```

---

### Post by Gourandle on 2012-03-13
I'm quite new here so I'll just say what I know. Might be wrong.
I don't believe you can just cd into a /dev/ like that without mounting it to a mount point first.
You have to use the mount command to mount it a directory that you create and then you can cd into it and browse it like normal files.

More info at:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Hope it helps :)

---

### Post by _0R10N on 2012-03-13
> **Gourandle said:**
> I'm quite new here so I'll just say what I know. Might be wrong.
I don't believe you can just cd into a /dev/ like that without mounting it to a mount point first.
You have to use the mount command to mount it a directory that you create and then you can cd into it and browse it like normal files.

More info at:
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

Hope it helps :)

I never used Lubuntu, but my guess is that it shouldn't differ much from the original Ubuntu. By default, Ubuntu mounts additional storage devices you attach, under /media/ directory. So, if you take a look there, you should be able to visualize your device and the files in it.

Since you say you aren't able to access your device, I'm assumming there's something else going around. Do you know if it's a FAT32, NTFS, EXT3?

If the device is not actually being mounted, you'll have to mount it yourself, here are a few examples.
[http://linux.about.com/od/commands/a/blcmdl8_mountx.htm](http://linux.about.com/od/commands/a/blcmdl8_mountx.htm)

---

### Post by _0R10N on 2012-03-13
> **_0R10N said:**
> I never used Lubuntu, but my guess is that it shouldn't differ much from the original Ubuntu. By default, Ubuntu mounts additional storage devices you attach, under /media/ directory. So, if you take a look there, you should be able to visualize your device and the files in it.

Since you say you aren't able to access your device, I'm assumming there's something else going around. Do you know if it's a FAT32, NTFS, EXT3?

If the device is not actually being mounted, you'll have to mount it yourself, here are a few examples.
[http://linux.about.com/od/commands/a/blcmdl8_mountx.htm](http://linux.about.com/od/commands/a/blcmdl8_mountx.htm)

I forgot to mention that if your device has a NTFS filesystem, OSs like Debian "don't know" how to treat with such filesystems and you are required to install a few additional packages, to handle NTFS properly

---

