---
title: "Clementine player problems"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-02-19
Hello my fellow Ubuntu users. I run on Xubuntu 12.04 LTS. I am having problems with my Clementine music player. Problem starts every time I boot my OS. It rescans the library and then it says its empty. So I have to add media all over again every time. I suspect problem is cause my media files are on different partition, but it shouldn't matter? Please help me, I found nothing good on net so far, you are my last resort, pls help.
Thanks in advance.

---

### Post by Elfy on 2013-02-19
IS the partition the music is stored on mounted at boot? 

Mine is - clementine works fine like that. 

We need more information - open a terminal and run (once the music drive is mounted)

```
mount
cat /etc/fstab
sudo blkid
```

---

### Post by LinuxUser666 on 2013-02-19
mount result:

/dev/sda9 on / type ext4 (rw,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/slayer1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=slayer1)
/dev/sda6 on /media/storage1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda5 on /media/radni type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

cat /etc/fstab results:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda9 during installation
UUID=0e85bf0b-9ad7-47c4-9a32-a43d0c303516 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=86a2e7e0-c3b3-48bd-9d86-729f3fca0f67 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

sudo blkid result: 

/dev/sda1: LABEL="XP" UUID="0094C86094C859B4" TYPE="ntfs" 
/dev/sda5: LABEL="radni" UUID="E030E2AD30E289BC" TYPE="ntfs" 
/dev/sda6: LABEL="storage1" UUID="26C8C90DC8C8DC65" TYPE="ntfs" 
/dev/sda7: LABEL="storage2" UUID="7C48EAEC48EAA3DC" TYPE="ntfs" 
/dev/sda8: UUID="86a2e7e0-c3b3-48bd-9d86-729f3fca0f67" TYPE="swap" 
/dev/sda9: UUID="0e85bf0b-9ad7-47c4-9a32-a43d0c303516" TYPE="ext4" 

Just to say my files are in /dev/sda5:

---

### Post by LinuxUser666 on 2013-02-21
Thank you Elfy, problem was indeed in mounting, my disk partition wasn't mounted at startup so Clementine did not see my files. 
Thank you for your assistance. ):P

---

