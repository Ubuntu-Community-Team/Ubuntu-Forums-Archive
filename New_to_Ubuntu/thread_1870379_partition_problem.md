---
title: "partition problem"
date: 2011-10-27
forum: New to Ubuntu
---

### Post by LukaHr on 2011-10-27
Hail! Just install my ubuntu today and got in problem. I create 3 partitions and on one install ubuntu. but on other two say that they owned by root and I can't do anything on them, no copy/paste, create folder etc. Any Idea?

---

### Post by nothingspecial on 2011-10-27
What filesytems are the other partitions?

---

### Post by LukaHr on 2011-10-27
ext3/ext4
Is it what you asking?

---

### Post by nothingspecial on 2011-10-27
Then you need to change ownership of the partitions to your user.

```
sudo chown -R $USER:$USER /moutpoint/of/each/partition
```

Where /moutpoint/of/each/partition is the actual mountpoint of each partition.

If you don't know then type ```
mount
```

---

### Post by satanselbow on 2011-10-27
[snip]

---

### Post by LukaHr on 2011-10-27
```
mount
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/luka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=luka)
/dev/sdb1 on /media/ADATA UFD type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sda5 on /media/9ef976e7-5010-407e-856e-80874d376b05 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda6 on /media/d8186a83-60a9-4a45-b97d-7173821a46d2 type ext4 (rw,nosuid,nodev,uhelper=udisks)
/home/luka/.Private on /home/luka type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=fd98083d158c9b93,ecryptfs_fnek_sig=107401bebab62736)


```

that i get when i mount in terminal

---

### Post by nothingspecial on 2011-10-27
```
sudo chown -R $USER:$USER /media/9ef976e7-5010-407e-856e-80874d376b05 
```
```

sudo chown -R $USER:$USER /media/d8186a83-60a9-4a45-b97d-7173821a46d2
```

---

### Post by LukaHr on 2011-10-27
insted of user do i write my name? sorry my first day with linux!

---

### Post by nothingspecial on 2011-10-27
If you are logged in as your user $USER will expand to your user. But you can also use your actual usernameme.

btw

**_DO NOT MAKE A TYPO[COLOR="Red"][/COLOR]_**

If you leave a space between / and media you will hose your system. Safer to copy and paste.

---

### Post by LukaHr on 2011-10-27
Thanks man, It works!

---

### Post by nothingspecial on 2011-10-27
No problem :)

---

