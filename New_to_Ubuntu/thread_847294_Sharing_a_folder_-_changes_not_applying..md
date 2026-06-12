---
title: "Sharing a folder - changes not applying."
date: 2008-07-02
forum: New to Ubuntu
---

### Post by russbook on 2008-07-02
I am trying to share an entire disk drive (not containing the O/S) with a media center enclosure that is running something called busybox linux. When I select a folder and click properties to change permissions, and I press apply to all sub folders and files, it reverts back to previous settings. I.E. "none" for group and other access. 

Similarly this happens when I try it from the command line:
```
russ@Herbie:/media$ chmod -R 777 disk
russ@Herbie:/media$ ls -l
total 24
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0
```

I am logged in as russ. Not sure why changes are not being applied? Any help appreciated.

---

### Post by russbook on 2008-07-02
Any one know a good resource to learn about this?

Is it because the drive is formatted to FAT32 that I can't chmod?

---

### Post by cariboo on 2008-07-02
You have to use sudo to change the permissions eg:

```
sudo chmod -R 777 /media/disk
```

the -R changes the permissions recursively, in other words it changes permissions on all the folders and files on /media/disk

Jim

---

### Post by pmlxuser on 2008-07-02
just do a sudo command ie.

russ@Herbie:/media$ sudo chmod -R 777 disk

that should do the trick if not print the out put again after excuting the command

---

### Post by russbook on 2008-07-02
It is still not playing ball. Is it anything to do with the fact that it is fat32?

This is what I get before and after running the command:

```
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0
russ@Herbie:/media$ sudo chmod -R 777 disk
russ@Herbie:/media$ ls -l
total 24
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0
russ@Herbie:/media$ 


```

---

### Post by drs305 on 2008-07-02
> **russbook said:**
> It is still not playing ball. Is it anything to do with the fact that it is fat32?
[/CODE]

Fat32 permissions are only set on mounting. You can add an entry to fstab or use the applicable mount command.

This would be a typical fstab entry. Name your mountpoint and make sure it exists. The umask gives rwx permissions to you and your group and rx permissions to others.:

```
/dev/sda8 /media/mountpoint vfat  utf8,uid=1000,gid=100,umask=002 0 0

```

---

### Post by russbook on 2008-07-03
Thanks. 

I am finding it difficult to understand what i need to replace in the code sample above?

Where am I going wrong?

```
russ@Herbie:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/russ/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=russ)
/dev/sdb3 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
tmpfs on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw,mode=0755)
russ@Herbie:~$ cd /dev/sda1
bash: cd: /dev/sda1: Not a directory
russ@Herbie:~$ /dev/sdb3 /media/disk vfat  utf8,uid=1000,gid=100,umask=002 0 0
bash: /dev/sdb3: Permission denied
russ@Herbie:~$ /dev/sdb3 on /media/disk type vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush, umask=002 0 0
bash: /dev/sdb3: Permission denied
russ@Herbie:~$ 

```

---

### Post by drs305 on 2008-07-03
> **russbook said:**
> Thanks. 

I am finding it difficult to understand what i need to replace in the code sample above?


This is a change to /etc/fstab and not a command-line mount command.

Backup and open fstab for editing:
```
sudo cp /etc/fstab /etc/fstab-backup
gksudo gedit /etc/fstab
```

Look for your entry with a file system listing of "vfat". You will replace one of the existing lines (the one for your vfat partition) with the one I quoted above.

If you post your fstab we can show you what lines to change:
```
cat /etc/fstab
```

---

### Post by russbook on 2008-07-03
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fffd92c2-8a30-4721-a834-6c3f72c62ec5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0bd5a337-7338-40e9-bd93-54c4c9479ffa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

I am guessing it is the first line then.

---

### Post by russbook on 2008-07-03
I can't see any mention of vfat. Have I missed something? Do I need to uncomment and change the first line?

---

### Post by drs305 on 2008-07-03
> **russbook said:**
> I can't see any mention of vfat. Have I missed something? Do I need to uncomment and change the first line?

vfat covers the fat32 file system. It appears you have a fat32 partition on /dev/sdb3.

Backup and open fstab for editing:
```
sudo cp /etc/fstab /etc/fstab-backup
gksudo gedit /etc/fstab
```

In your fstab, add this line. Change mountpoint to the place you want your fat32 partition mounted, and make sure it exists in /media . You appear to be manually mounting it on /media/disk :
```

/dev/sdb3 /media/**mountpoint** vfat  utf8,uid=1000,gid=100,umask=002 0 0

```

---

### Post by russbook on 2008-07-03
Ok I have now done that, but now when I click on the drive I am told that "You are not privileged to mount this volume"

When you say make sure that it exists do you mean change mountpoint to "disk" as this is where it normally appears.

Or do I just need to change the last few digits after umask to alter the permission?

---

### Post by russbook on 2008-07-03
Would this then have been the correct code?

```
/dev/sdb3 /media/disk vfat  utf8,uid=1000,gid=100,umask=002 0 0
```

---

### Post by drs305 on 2008-07-03
> **russbook said:**
> Would this then have been the correct code?

```
/dev/sdb3 /media/disk vfat  utf8,uid=1000,gid=100,umask=002 0 0
```

yes, that is it. you may need to run the following:
```
sudo chown -R *yourusername* /media/disk
```

---

### Post by russbook on 2008-07-03
It does not appear to change anything.

```
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0
russ@Herbie:/media$ sudo chmod -R 777 disk
russ@Herbie:/media$ ls -l
total 24
lrwxrwxrwx 1 root  999     6 2008-06-17 23:21 cdrom -> cdrom0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 cdrom0
drwx------ 7 russ root 16384 1970-01-01 01:00 disk
lrwxrwxrwx 1 root  999     7 2008-06-17 23:21 floppy -> floppy0
drwxr-xr-x 2 root  999  4096 2008-06-17 23:21 floppy0
russ@Herbie:/media$ 

```

---

### Post by russbook on 2008-07-03
Would it help if I reformatte the disk to something other than Fat 32?

---

### Post by drs305 on 2008-07-03
> **russbook said:**
> Would it help if I reformatte the disk to something other than Fat 32?

Run these two commands, The first will unmount and the second should remount the partition again. See if partition mounts.
```

sudo umount /dev/sdb3
sudo mount /dev/sdb3

```


And personal opinion - there are windows apps that can read ext3 formats so I never use fat32 any longer.

---

### Post by russbook on 2008-07-03
> **drs305 said:**
> Run these two commands, The first will unmount and the second should remount the partition again. See if partition mounts.
```

sudo umount /dev/sdb3
sudo mount /dev/sdb3

```


And personal opinion - there are windows apps that can read ext3 formats so I never use fat32 any longer.


Yeah, I don't even need to share the drive with a windows system. Can I reformat without losing data?

This is what I get from the previous command:
```
russ@Herbie:/$ sudo mount /dev/sdb3
mount: mount point /media/disk does not exist
russ@Herbie:/$ 

```

---

### Post by drs305 on 2008-07-03
> **russbook said:**
> Yeah, I don't even need to share the drive with a windows system. Can I reformat without losing data?

This is what I get from the previous command:
```
russ@Herbie:/$ sudo mount /dev/sdb3
mount: mount point /media/disk does not exist
russ@Herbie:/$ 

```

No, reformatting will destroy the data on the disk.

To make the mount point:
```

sudo mkdir /media/disk
sudo umount -a
sudo mount -a

```

---

### Post by russbook on 2008-07-06
what does the -a mean? Should I be putting in my own values?

---

### Post by drs305 on 2008-07-06
The "-a" is a switch which tells the umount / mount command to do it to all partitions. It's sometimes easier to do "-a" than specify a particular partition, especially if the writer isn't sure of the designation of the partition. In this case, it will try to unmount all but of course it can't unmount the root partition since it is running things. Thus you will see some messages essentially telling you that.

For more information about switches, you can type "man" followed by the command name to see what options are available and what they mean.

---

