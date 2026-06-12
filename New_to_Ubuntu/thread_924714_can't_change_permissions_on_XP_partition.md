---
title: "can't change permissions on XP partition"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by garyed on 2008-09-19
Can anyone explain to me why I can't change permissions on files or folders on my XP partition. When I look at the files they have root as the owner & the group is plugdev. If I do:
```
sudo chmod 777 filename 
```
the permissions do not change. It's really not a problem but I was just experimenting with the command line & can't figure out what I'm missing.

---

### Post by iaculallad on 2008-09-19
Try to automount your windoze XP drive using your Fstab file using the following syntax below (This enables desktop users to access files/folders):

```
/dev/sdb1 /media/disk ntfs defaults,uid=1000,gid=1000,umask=007,noatime 0 0
```

To edit your fstab file:

```
gksudo gedit /etc/fstab
```

and insert the above syntax in the last part of your fstab file. You have to change the value of /dev/sdb1 and /media/disk.

/dev/sdb1 = you can get the value of this by ussuing the command **sudo fdisk -l**.
/media/disk = the mount point you created.

---

### Post by iansane on 2008-09-19
Not sure but when I was dual booting I had to boot to windows and change the permissions. Also I tried chmod 777 on the whole drive and it killed my grub so doing it from windows might be the safer route. I haven't found out why it killed my grub and apparently the whole mbr yet. I had to go get a new hard drive. Gonna post a new one about that.

---

### Post by garyed on 2008-09-19
> **iaculallad said:**
> Try to automount your windoze XP drive using your Fstab file using the following syntax below (This enables desktop users to access files/folders):

```
/dev/sdb1 /media/disk ntfs defaults,uid=1000,gid=1000,umask=007,noatime 0 0
```



I tried that but I still couldn't change permissions with chmod afterwards.
Actually after changing my fstab it only gave me read & execute permissions so I couldn't copy anything over to my xp partition like I always did before.
I'm assuming I could unmount & then remount with different permissions but I don't know the proper syntax.

---

### Post by kansasnoob on 2008-09-19
Try just adding ntfs-config:

```
sudo apt-get install ntfs-config
```

---

### Post by garyed on 2008-09-19
I'm pretty sure I've got ntfs-config installed.
When I go back to my old fstab everything works fine as far as copying files to my xp partition, reading & xing.. but I just can't change any file permissions. Here's my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=36a34c7e-bd83-4887-a8dc-d5149795394e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=97f9c820-69fb-433c-bcd0-4aa34544f95e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1 /media/windows ntfs-3g defaults,utf8,umask=007,gid=46 0 1
# /dev/sdb1 /media/windows ntfs defaults,uid=1000,gid=1000,umask=007,noatime 0 0

---

### Post by mc4man on 2008-09-19
> When I go back to my old fstab everything works fine as far as copying files to my xp partition, reading & xing.. but I just can't change any file permissions.
There's no purpose to changing the 'permissions or ownership', by default you can rw and probably x most anything on the xp partition.
If there happened to be some locked files (possibly on occasion in 'My Documents') you'd have to change their properties  in xp.

Root owns the mount point and while possibly you could chown that, to what purpose?

They only thing that matters is the mount options, right click on the xp icon -> properties -> volume. you'll see everything you need is already 'given' to you.

---

### Post by garyed on 2008-09-19
> **mc4man said:**
> ...
They only thing that matters is the mount options, right click on the xp icon -> properties -> volume. you'll see everything you need is already 'given' to you.
I understand that I don't need to change anything since everything is mounted O.K. but I was more confused as to why chmod doesn't work on the mounted file 
system. I really don't have a need to change any permissions I'm just trying to understand why I can't if I wanted to or if permissions can only be done at mounting.

---

### Post by Elephantman5 on 2008-09-19
> **garyed said:**
> I understand that I don't need to change anything since everything is mounted O.K. but I was more confused as to why chmod doesn't work on the mounted file 
system. I really don't have a need to change any permissions I'm just trying to understand why I can't if I wanted to or if permissions can only be done at mounting.
Because the partition is not linux native.

---

### Post by iansane on 2008-09-19
> **mc4man said:**
> 
If there happened to be some locked files (possibly on occasion in 'My Documents') you'd have to change their properties  in xp.

Root owns the mount point and while possibly you could chown that, to what purpose?



To be lord and master of my own system. That would be my reason.

 Actually had reason like deleting files from a window system. Don't remember now what they were but ntfs permissions weren't letting ubuntu have complete control so as you said, I had to boot windows and change them from there.

---

### Post by mc4man on 2008-09-20
There are some 'situations' where you can chmod non Ext2/3. See here though at times i think it was 'apples & oranges'
[http://ubuntuforums.org/showthread.php?t=784334&page=2](http://ubuntuforums.org/showthread.php?t=784334&page=2)

---

