---
title: "Permissions change"
date: 2014-06-22
forum: New to Ubuntu
---

### Post by Alan_Dean on 2014-06-22
I keep my files on an external hard drive rather than on the PC itself. Everything has worked fine but suddenly I am unable to make changes to files or delete them. The waste basket and delete options are greyed out. Is there away I can get back to return to full functionality. I have located and tried to cahnge the settings in the PERMISSIONS options (Properties) but will not allow any changes. I can't remember having donne anything to cause this change.

Thanks

Alan

---

### Post by jahidul hamid on 2014-06-22
you can try this command:
> sudo chmod -R 777 mount_point_of_external_hdd

---

### Post by Alan_Dean on 2014-06-22
Thanks I tried that but got:

alan@alan-desktop:~$ sudo chmod -R 777 mount_point_of_external_hdd 
chmod: cannot access ‘mount_point_of_external_hdd’: No such file or directory


I checked that the drive was mounted

Thanks

Alan

---

### Post by Vladlenin5000 on 2014-06-22
It should be obvious but... You must replace mount_point_of_external_hdd with the correct mount point of the external HDD.

---

### Post by LastDino on 2014-06-23
And which could be found by entering 
```
df
```
in terminal

Should have /dev/sdb under file system.

---

### Post by coffeecat on 2014-06-23
Running chmod blindly on a partition without finding out why it was previously working fine but now doesn't allow you to write changes is not a good idea. The output of "df" as LastDino suggests will give us some useful information, but please also post the terminal output of:

```
mount
``` 

We need to see the type of filesystem that is giving you trouble and what the mount options are - the output of "mount" will tell us both. It will not tell us why you have seen this change in behaviour, but will give us pointers on where to proceed.

---

### Post by Alan_Dean on 2014-06-23
Ah thank you. Although I have used Ubuntu for many years I have never really undertsood the terminal commands
```

alan@alan-desktop:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1       20633204   7809404  11752648  40% /
none                   4         0         4   0% /sys/fs/cgroup
udev             4049064         4   4049060   1% /dev
tmpfs             811724      1232    810492   1% /run
none                5120         0      5120   0% /run/lock
none             4058612        76   4058536   1% /run/shm
none              102400        44    102356   1% /run/user
/dev/sdb1      976521568 485290112 491231456  50% /media/alan/Transcend
```
```
alan@alan-desktop:~$ mount
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
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=alan)
/dev/sdb1 on /media/alan/Transcend type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)
alan@alan-desktop:~$
```

---

### Post by coffeecat on 2014-06-23
Assuming sdb is your external drive, this is the important line:

> **Alan_Dean said:**
> 
```
alan@alan-desktop:~$ mount

<snip>

/dev/sdb1 on /media/alan/Transcend type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)

```

First thing - trying to run chmod would be a complete waste of time. It won't do anything, but it would be a distraction. The filesystem is FAT32, a Microsoft filesystem, and like NTFS doesn't support Linux permissions, so chmod and chown have no effect, neither would the permissions tab in the file browser. Permissions and ownership of FAT32 and NTFS filesystems are defined by mount options, and the mount options there seem fine. It has been mounted rw (read-write) so we can infer that there is no filesystem damage, and you *should* be able to edit files and delete them. I confess I'm a bit puzzled at the moment.

Do you have access to either a Windows or Apple Mac system? If so, try plugging that drive into either Windows or MacOS or both and let us know what you can and can't do from those operating systems.

By the way, I added code tags to your two outputs - it has restored the formatting lost by simply pasting into your post.

---

### Post by Alan_Dean on 2014-06-23
Thank you very much for the information especially about trying to run chmod, that was helpful. I have tried inputting   /dev/sdb1 on /media/alan/Transcend type vfat but I got permission denied. What I will do is do a reinstall of Ubuntu. I don't have access to either a Windows or Mac OS

Thanks


Alan

---

### Post by varunendra on 2014-06-23
Are you the only user on this system? Please check your user and group IDs with the "id" command -
```
id
```
..and make sure it is "1000"

Also post the output here so we can confirm if you are the member of all necessary groups or not. For reference, here's the output for me -
```
uid=1000(varun) gid=1000(varun) groups=1000(varun),4(adm),6(disk),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),127(vboxusers)
```

---

### Post by coffeecat on 2014-06-23
> **Alan_Dean said:**
> What I will do is do a reinstall of Ubuntu.

Oh no. Please don't do that. At least not unless you have evidence that your installation is broken beyond repair. A difficulty with writing to an external drive is certainly not evidence of that. I merely suggested attempting to access your external drive from another operating system in case this added any information that would help. The problem might be with the external drive.

---

### Post by LastDino on 2014-06-23
Well, rather than doing install again just use the live mode and check if it is same over there. If checking on someone else PC is not an option.

We don't know anything about actual problem as of yet, so we can't blame it on OS.

---

### Post by 3rdalbum on 2014-06-23
I agree with Coffeecat - reinstalling your whole operating system when you encounter one problem is no solution at all. Computers are meant to make you more productive, not force you to waste major amounts of time on maintenance.

It doesn't seem like you've actually tried putting this into the terminal:

```
sudo chmod 777 /media/alan/Transcend
```

If the problem is that the mount point's permissions are wrong, that terminal command would certainly fix it. For a filesystem that doesn't support permissions, such as Fat32 or NTFS, every file and folder uses the same permissions as the mount point (/media/alan/Transcend).

One other possible reason for not being able to make any changes to the disk is that it might have some filesystem corruption, or even 'physical' damage (as in, parts of the magnetic layout of the disk have gone bad). If the system detects any corruption or damage like this it will remount the filesystem as read-only, to prevent further damage. The output from the 'mount' command you posted earlier seems to suggest that the filesystem is mounted read-write, but I'm wondering whether it might actually be mounted read-only.

Try right-clicking the disk's icon and choose Eject or Unmount (NOT "Safely Remove"). Next, put this into the terminal:

```
sudo fsck /dev/sdb1
```

This will check the filesystem of your disk and report any errors. Just say "yes" to all suggested fixes. If it gives you multiple options and you don't know which one to take, try taking the first one.

I'm guessing this disk is a flash drive - remember, they have a limited lifespan. I once killed one in three months and it gave the same symptoms as yours.

---

### Post by coffeecat on 2014-06-23
@3rdalbum:

> **3rdalbum said:**
> It doesn't seem like you've actually tried putting this into the terminal:

```
sudo chmod 777 /media/alan/Transcend
```

If the problem is that the mount point's permissions are wrong, that terminal command would certainly fix it.

<snip>

```
sudo fsck /dev/sdb1
```


We've already established that the drive is formatted FAT32. Neither chmod nor fsck are going to work. They are for Linux filesystems.

---

