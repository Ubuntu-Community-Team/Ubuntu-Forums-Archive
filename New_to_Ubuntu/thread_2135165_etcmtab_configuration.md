---
title: "/etc/mtab configuration"
date: 2013-04-13
forum: New to Ubuntu
---

### Post by putStrLnNick on 2013-04-13
Hi, I just wanted to check if my /etc/mtab configuration was ok. It's:
```

/dev/sda3 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
/dev/sda1 /boot/efi vfat rw 0 0
/dev/sda4 /home ext4 rw 0 0
gvfsd-fuse /run/user/nick/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=nick 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/loop0 /var/spool/havp ext3 rw,mand 0 0

```
Let me know if I should provide additional info, and thanks.

---

### Post by putStrLnNick on 2013-04-13
I guess one thing I could add is that it's consistent with my partition configuration. I'm just unsure about all the extra stuff.

---

### Post by Zill on 2013-04-13
> **putStrLnNick said:**
> Hi, I just wanted to check if my /etc/mtab configuration was ok...
***If*** you have downloaded Ubuntu from a legitimate source and then run [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") to verify a good download then it *should* install to your system correctly.

As long as you do not "tinker" with the defaults until you know what you are doing then all the installed files, including mtab, should be OK.

---

### Post by putStrLnNick on 2013-04-13
Ok. Haven't been tinkering and did the md5sum check; just wanted to be sure. Thanks

---

