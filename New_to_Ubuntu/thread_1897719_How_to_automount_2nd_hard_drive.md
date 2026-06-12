---
title: "How to automount 2nd hard drive?"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by EddieNYC on 2011-12-19
Hi All.

I havent posted here in a while but I recently started getting back into Ubuntu.

I recently installed a 2nd HD in my Ubuntu Box for storing Media, etc.

Ive tried to edit FSTAB to automount the HD on bootup but it still will not automount. I have to manually mount it and this is causing issues because I have certain applications pointing to the 2nd drive as default storage for downloads, etc.

GParted is listing the 2nd drive as dev/sdb.

During the initial bootup process, I get an error message regarding mounting /Media. Press I to Ignore, S to skip or M for manual recovery. I can skip this process and boot into Ubuntu with no problem but /Media (2nd HD) does not automount so I assume something is wrong in my fstab config.

Here is my current FSTAB config. Please feel free to point out what I'm doing wrong?:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro   0       1
/dev/sdb        /media          ext2    defaults            0       2
# swap was on /dev/sda5 during installation
#UUID=91912f6a-52be-4b97-81f1-cd87c180287d none            swap    sw              0       0


PS - I used gparted to format/setup the drive as Ext2 when I installed it.


Thank you all for your help!):P

---

### Post by seawolf167 on 2011-12-19
Make a mount point

```
sudo mkdir /media/data
```edit /etc/fstab

```
sudo gedit /etc/fstab
```change the /dev/sdb line to this

```
/dev/sdb        /media/data          ext2    defaults            0 0
```

if you are still having problems, please post the output of 

```
mount
sudo blkid
cat /etc/fstab
```

inside [noparse]```

```[/noparse] tags

---

### Post by EddieNYC on 2011-12-19
If it helps, I forgot to mention that when I was setting up the HD, I created a mount point: /media/MyDrive 

Here's the output of those terminal commands BEFORE I make the changes youve suggested in case you can spot something.

Let me know If I can go ahead and carry out your suggested steps...

```

home@HomeUbuntu:~$ mount
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
/home/home/.Private on /home/home type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=aa304a5ad39ac617,ecryptfs_fnek_sig=4d59122416f82f70)
gvfs-fuse-daemon on /home/home/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=home)
/dev/sdb1 on /media/Media type ext2 (rw,nosuid,nodev,uhelper=udisks)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

```


```

home@HomeUbuntu:~$ sudo blkid
[sudo] password for home: 
/dev/sda1: UUID="89577dcd-68ef-4327-8177-48e5525e7446" TYPE="ext4" 
/dev/sdb1: LABEL="Media" UUID="54356970-0b18-46f1-8d4b-2df60bbea406" TYPE="ext2" 
/dev/mapper/cryptswap1: UUID="d3ce3273-7c61-4f33-b487-3909ddd481e3" TYPE="swap"
```



```

home@HomeUbuntu:~$ sudo blkid
[sudo] password for home: 
/dev/sda1: UUID="89577dcd-68ef-4327-8177-48e5525e7446" TYPE="ext4" 
/dev/sdb1: LABEL="Media" UUID="54356970-0b18-46f1-8d4b-2df60bbea406" TYPE="ext2" 
/dev/mapper/cryptswap1: UUID="d3ce3273-7c61-4f33-b487-3909ddd481e3" TYPE="swap"
```

Thanks again!

-Eddie

---

### Post by seawolf167 on 2011-12-19
You have your labeling incorrectly listed in /etc/fstab

Based on the post you just made, use this entry:

```
# Entry for /dev/sdb1
UUID=54356970-0b18-46f1-8d4b-2df60bbea406     /media/MyDrive     ext2     defaults     0     0
```Note that /media/MyDrive **is** case-sensitive

---

### Post by EddieNYC on 2011-12-19
Is there a way I can confirm the labeling for the drive?

I know I labeled it MyDrive when I created a mount point but want to be certain of the spelling....

Thanks!

---

### Post by seawolf167 on 2011-12-19
> **EddieNYC said:**
> Is there a way I can confirm the labeling for the drive

```
ls /media
```

---

### Post by EddieNYC on 2011-12-19
Awesome!

Confirmed it is indeed MyDrive.

So where in the fstab confir do I add the line you suggested?

Do I need to just add that line or modify what's in there at the moment?

You've been very helpful. I appreciate it.

---

### Post by seawolf167 on 2011-12-19
Just replace your line with the one I posted above.

---

### Post by EddieNYC on 2011-12-19
Heres what my FSTAB is looking like so far. 

What do you think?

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro   0       1
#Entry for /dev/sdb1
UUID="54356970-0B18-46F1-8D4B-2DF60BBEA406 ext2  /media/MyDrive defaults 0  0
# swap was on /dev/sda5 during installation
#UUID=91912f6a-52be-4b97-81f1-cd87c180287d none            swap    sw              0       0

```

-Eddie

---

### Post by seawolf167 on 2011-12-19
You might want to copy/paste from my post above - you have an errant quotation mark, and the mount point and type need to be reversed. Once you do that it looks good, save it after you open it for editing via *sudo* and test it out.

---

### Post by EddieNYC on 2011-12-19
Better?

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro   0       1
# Entry for /dev/sdb1
UUID=54356970-0b18-46f1-8d4b-2df60bbea406     /media/MyDrive     ext2   defaults     0     0
# swap was on /dev/sda5 during installation
#UUID=91912f6a-52be-4b97-81f1-cd87c180287d none            swap    sw              0       0

```

-Eddie

---

### Post by seawolf167 on 2011-12-19
Ensure that there are two trailing zeros and it looks good to go (I'm on my phone and I'm not sure if the scroll bars aren't showing or the final 0 isn't there)

---

