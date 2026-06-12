---
title: "Ubuntu become read only with data disappearance"
date: 2015-02-11
forum: New to Ubuntu
---

### Post by geeks2 on 2015-02-11
Recently an group was created in ubuntu 12.04 server and the user created when OS was installed was added in the group, but somehow the user got deleted from root privilege groups and privilege commands were not working So rebooted the system did #mount -rw -o remount / then added that user to multiple default groups like sudo,lpadmin,dip,cdrom etc, then rebooted the server and found to my horror that all the data in /home is gone and I am not even able to create anything it says permission denied even for touch command. Where it went wrong, any ideas on how to recitfy this is highly appreciated. Thanks in advance.

---

### Post by sandyd on 2015-02-11
> **geeks2 said:**
> Recently an group was created in ubuntu 12.04 server and the user created when OS was installed was added in the group, but somehow the user got deleted from root privilege groups and privilege commands were not working So rebooted the system did #mount -rw -o remount / then added that user to multiple default groups like sudo,lpadmin,dip,cdrom etc, then rebooted the server and found to my horror that all the data in /home is gone and I am not even able to create anything it says permission denied even for touch command. Where it went wrong, any ideas on how to recitfy this is highly appreciated. Thanks in advance.

Can you post the output of
```

mount -l
cat /etc/group
cat /etc/passwd
```

Please remember to remove personal information that may be in the output of /etc/group and /etc/passwd.

---

### Post by geeks2 on 2015-02-11
mount -l
/dev/mapper/auat--vg-root on / type ext4 (rw,errors=remount-ro)
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
/usr/tmp on /tmp type ext4 (rw)
/dev/sda1 on /boot type ext2 (rw)

I have attached /etc/group and /etc/passwd as attachment. Now the drive is allowing me to rw, but I have to take find ways to restore the data. Any ways/ means to do it. Nothing has been deleted from the drive. After coming out of that recovery mode this has happened

---

