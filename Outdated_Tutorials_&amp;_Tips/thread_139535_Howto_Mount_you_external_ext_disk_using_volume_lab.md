---
title: "Howto: Mount you external ext disk using volume labels"
date: 2006-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by magisterludi on 2006-03-04
Having more than one external drive makes it difficult to mount them at the same point if you plug and unplug this drives in different orders.

For example the first external usb drive attached will always get the device /dev/sda the second /dev/sdb, etc

a fstab line
like 
```

/dev/sda1       /media/usb120gb   ext3 defaults                 0       0
/dev/sdb1       /media/usb300gb   ext3 defaults                 0       0

```
won't mount your 120gb drive at /media/usb120gb if you attach the 300gb drive first.

At least with following filesystems you can easily get this fixed:
ext2, ext3, XFS, JFS,Reiserfs.

Just do
```

tune2fs -L usb120gb /dev/sda1
tune2fs -L usb300gb /dev/sdb1

```
This gives you partition/disk a label.
Check with:  dumpe2fs

Then you can (auto)mount them the right way using following fstab:
```

LABEL=usb120gb /media/usb120gb ext3 defaults 0 0
LABEL=usb300gb /media/usb300gb ext3 defaults 0 0

```

---

### Post by dcstar on 2006-03-04
[QUOTE=magisterludi]
......
At least with following filesystems you can easily get this fixed:
ext2, ext3, XFS, JFS,Reiserfs.

Just do
```

tune2fs -L usb120gb /dev/sda1
tune2fs -L usb300gb /dev/sdb1

```
This gives you partition/disk a label.
Check with:  dumpe2fs

Then you can (auto)mount them the right way using following fstab:
```

LABEL=usb120gb /media/usb120gb ext3 defaults 0 0
LABEL=usb300gb /media/usb300gb ext3 defaults 0 0

```[/QUOTE]
This can also be used for your "Internal" partitions, the result is on boot-up the fsck messages refer to the disk label rather than the /dev identifier.

Also, I would recommend that "dumpe2fs" be used with the "-h" parameter to cut down on the screen output.

Very handy HOWTO.

---

### Post by dartmusic on 2006-03-17
THIS is exactly what I was looking for!  Who knew it would be this simple?  

OK...maybe not SO simple!  I am running Kubuntu Breezy on an HP zd7015 notebook and I have three external USB disks.  Two of these disks are formatted with ext3 filesystems, while the third is formatted with the vfat/fat32/whatever filesystem.  For some reason I can't get fstab to recognize the label for this drive.  

Here is the error I get when trying to set it again with tune2fs:

rickstone@kubuntu:~$ tune2fs -L Media_Drive /dev/sdc1
tune2fs 1.38 (30-Jun-2005)
tune2fs: Permission denied while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/hda3 / reiserfs notail,atime,auto,rw,dev,exec,suid,nouser 0 1
/dev/hda1 /media/hda1 ntfs defaults,uid=0,gid=0,auto,rw,nouser 0 0
/dev/hda2 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
LABEL=MEDIA_DRIVE /media/Media_Drive vfat ,uid=1000,gid=1000,auto,rw,users 0 0
LABEL=Big_Boy /media/Big_Boy ext3 ,atime,auto,rw,nodev,noexec,nosuid,users 0 0
LABEL=Little_Big_Boy /media/Little_Big_Boy ext3 ,atime,auto,rw,nodev,noexec,nosuid,users 0 0
/dev/sdd2 /media/ipod vfat ,uid=1000,gid=1000,auto,rw,users 0 0

Any ideas?

Thanks in advance and thanks again for a great howto!

---

### Post by sbassett on 2006-03-18
To the best of my knowledge, vfat (fat32) does not support labeling, as per the output:

```
rickstone@kubuntu:~$ tune2fs -L Media_Drive /dev/sdc1
tune2fs 1.38 (30-Jun-2005)
tune2fs: Permission denied while trying to open /dev/sdc1
Couldn't find valid filesystem superblock.
```

tune2fs is try to place ext2 (or ext3) parameters on this filesystem.

---

### Post by magisterludi on 2006-03-18
As said before this is only for these filesystems:
ext2, ext3, XFS, JFS,Reiserfs not vfat, ntfs, hfs+, etc.

But there are other ways to accomplish it more generically:
Here is a link which may help you:
[http://gentoo-wiki.com/HOWTO_Customizing_UDEV#Example:_Writing_a_rule_for_my_USB-Storage_digital_camera]("http://gentoo-wiki.com/HOWTO_Customizing_UDEV#Example:_Writing_a_rule_for_my_USB-Storage_digital_camera")

---

### Post by dartmusic on 2006-03-20
Thanks for the responses.  I have to say that the UDEV wiki bit I think is a little over my head as I couldn't get it to work.  

SO...what I'm wondering is why I couldn't simply replace this line:

LABEL=MEDIA_DRIVE /media/Media_Drive vfat ,uid=1000,gid=1000,auto,rw,users 0 0

with this:

UID="the_UID_of_this_drive" /media/Media_Drive vfat ,uid=1000,gid=1000,auto,rw,users 0 0

?

So, I did.  I found the UID of the drive (can't remember now the command but it was something in the UDEV wiki listed above) and it doesn't work.  I guess I don't understand why I couldn't use another parameter in place of LABEL?  I didn't type the UID in quotes as I did above, either.  I'm at work, so not in front of my (home) computer with the appropriate info.  Is there another unique parameter that I could use in place of LABEL, or is this something that is simply not going to work with a vfat drive?  I kind of want to keep one drive formatted as such, as I still have to have XP on this machine for music writing/recording stuff.

---

### Post by dartmusic on 2006-03-20
Like I said above, I'm not at home, but I did run across this article:

[http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://ubuntu.wordpress.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

Might be the answer?  Anybody tried this?

---

### Post by lyly on 2006-03-23
I have a reiserfs external disk and edit the label with reiserfstune (Breezy). Then I tried to add 

LABEL=MyDisk        /media/MyDisk       reiserfs        defaults        0       0

in /etc/fstab. The problem is that I cannot write on the mounted disk, unless I am root...

I would like any user on the computer to be able to write on the disk root... Which options should I add? Thx

---

### Post by magisterludi on 2006-03-23
With the disk mounted do:

```

chown -R root:yourusergroupname /media/thenameofthemountedreiserfs
chmod -R g+w /media/thenameofthemountedreiserfs

```

---

### Post by dartmusic on 2006-03-23
Whoa Nelly!

What is the "chmod g+w" bit?  Can you explain?  I'm having permissions problems on just ONE of my reiserfs drives...of course the drive that holds my music collection and I need to make changes to tags fairly often and get the wonderful glass-breaking sound an an error popup that actually doesn't tell me what the error is!

---

### Post by magisterludi on 2006-03-23
the chown command above sets the group of the partition to you usergroup the chmod command sets the permission of the group to g+w which is write.
g for group and w for write.

read man chmod and man chown.

maybe you have to be superuser to make the changes above.
so type
sudo chown...
and 
sudo chmod..

---

### Post by dartmusic on 2006-03-23
Damned Microsoft!!  I can't check these out until I get home, but thanks!  I know about chown, but chmod I've only really used to make a file executable, but never really researched it's full potential.

Thanks...this is quite possibly the answer to a very perplexing problem.  

Oh, and I do believe that you have to sudo these commands.

Thanks again.

---

### Post by lyly on 2006-03-24
[QUOTE=magisterludi]With the disk mounted do:
```

chown -R root:yourusergroupname /media/thenameofthemountedreiserfs
chmod -R g+w /media/thenameofthemountedreiserfs

```[/QUOTE]

Is there any way to have it automatically, I don't want each time I use the disk to type it again... 

Will my permission on reiserfs preserved if I use the 'guid=user,umask=0007' attribute in /etc/fstab?

---

### Post by magisterludi on 2006-03-24
if you done it one time it should be enough since reiser supports permissions.

---

### Post by lyly on 2006-03-24
[QUOTE=magisterludi]if you done it one time it should be enough since reiser supports permissions.[/QUOTE]
Actually the folder is deleted each time by the system... so I cannot do it only once. I manage to make what I wanted in modifing /etc/fstab:
```
LABEL=MyDisk /media/MyDisk reiserfs defaults,noauto,noatime,**gid=users,umask=0005** 0 0
```

---

### Post by dcstar on 2006-06-21
[QUOTE=magisterludi]
........
Just do
```

tune2fs -L usb120gb /dev/sda1
tune2fs -L usb300gb /dev/sdb1

```
This gives you partition/disk a label.
Check with:  dumpe2fs
.......[/QUOTE]
Actually there might be a less risky way of labelling:
```
**e2label** /dev/... "Name"
```
for those who don't want to risk using the far more powerful **tune2fs** command.

---

### Post by pmorton on 2007-10-23
> **lyly said:**
> I have a reiserfs external disk and edit the label with reiserfstune (Breezy). Then I tried to add 
LABEL=MyDisk        /media/MyDisk       reiserfs        defaults        0       0
in /etc/fstab. The problem is that I cannot write on the mounted disk, unless I am root...


Got a similar problem with external USB2 reiserfs drive, but I can't mount it at all with a label.  

I gave it a volume label with:

reiserfstune   -l   icybox    /dev/sdc1

and reiserfstune reports:

LABEL: icybox  (which seems to indicate it's labelled the volume)

I then added the following line to fstab:

LABEL=icybox	/media/icybox 	reiserfs	defaults	1	1

but sudo  mount -a gives  error:

mount: special device /dev/disk/by-label/icybox does not exist

Anyone know about this?

---

### Post by pmorton on 2007-10-24
I've half answered my own question by disconnecting the USB2 drive, waiting and reconnecting. Command  "mount -a" then mounts it as required.  "e2label /dev/sdc1" still doesn't register the label, but I assume that's because it only recognises ext2 and ext3 files systems and not reiserfs.

Anyone know how to check for a disk label on a reiserfs partition?

Another issue is that  an icon for the USB2 drive doesn't come up on the Gnome desktop when the drive mounts  (although system tools:configuration editor:apps:nautilus:desktop is checked correctly to "make volumes_visible"). Is there another way of getting that to work?

---

