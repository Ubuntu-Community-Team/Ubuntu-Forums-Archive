---
title: "Hard drives detected/mounted but not on desktop"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Yellowbelly on 2008-11-02
Ubuntu has given me more headaches about drives than anything else but it's always a different problem. What's weird this time is that the drives are detected if not mounted but they don't show up on the desktop unless I click on it under Places. Would that mean it's not mounted unless I click on it giving it "permission"? How do I make it automount?

fdisk:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d7b9d7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10991099

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15017   120624021    b  W95 FAT32

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x730cf221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12475   100205406    b  W95 FAT32
/dev/sdc2           12476       19332    55078852+  83  Linux
/dev/sdc3           19333       19457     1004062+  82  Linux swap / Solaris






fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc2
UUID=19bc28e6-be76-489b-b184-01991598b464 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc3
UUID=a4ff4758-3a44-4029-a131-a60fe9709edc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by taurus on 2008-11-02
Which partition(s)?  If you want it to automount, you need to add an entry in /etc/fstab for it.

---

### Post by Elfy on 2008-11-02
To make them automount you need to add them to fstab, ntfs can be mounted with ntfs-config which can be installed and run from System Tools or added manually to fstab

The fat32 and linux partitions can be added to fstab.

You need to first make a folder to mount thepartition to, if the folder is in /media it shows on the desktop 

```
sudo mkdir /media/folder
```

Add to fstab either with it's UUID which you can get by running ```
sudo blkid
``` or as a logical device - eg /dev/sda1

For example

/dev/sda1 /media/folder ext3 user 0 2

You can get the correct syntx, options for different filetypes here
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

If you want help please post

```
sudo blkid
```
and which drives normally are unmounted that you wish to have mounted automatically

---

### Post by Yellowbelly on 2008-11-02
sdb and sdc are more important and would like to get them running. sda isn't as important but it would be annoying if it didn't get put in.


blkid:
/dev/sda1: UUID="A8B0D7ACB0D77F6E" TYPE="ntfs" 
/dev/sdb1: LABEL="MUSIC" UUID="4693-EB5D" TYPE="vfat" 
/dev/sdc1: LABEL="MEDIA" UUID="45D7-23C6" TYPE="vfat" 
/dev/sdc2: UUID="19bc28e6-be76-489b-b184-01991598b464" TYPE="ext3" 
/dev/sdc3: TYPE="swap" UUID="a4ff4758-3a44-4029-a131-a60fe9709edc"


A little off topic but I sdb1 and sdc2 are labeled because gnome or nautilus did away with labeling by their actual names and does it by their size. I would actually prefer their partition names so would it be easy to do from here? I actually tried to rename it by their partition names but it didn't like it for being the same name it seemed.

---

### Post by akelsall on 2008-11-02
YellowBelly, I had a similar problem getting my old Windows (slave) drive to show up on the Ubuntu desktop. I discovered (as someone already mentioned) that you need to edit fstab and mount them under the /media directory. 

Here's my fstab setup. It works perfectly. When they mount, they drive icons will be given some weird name. You can use the utility "ntfsprogs" to make them mount with the name you want:

Partial output of /etc/fstab:

/dev/sdb1 /media/winC ntfs-3g rw,nosuid,nodev,noatime,allow_other
/dev/sdb5 /media/winD ntfs-3g rw,nosuid,nodev,noatime,allow_other
/dev/sdb6 /media/winE ntfs-3g rw,nosuid,nodev,noatime,allow_other

Andy

---

### Post by Elfy on 2008-11-03
Make some folders to mount the drives in first - you can change the names as you see fit as long as the same name is used for fstab

```
sudo mkdir /media/data /media/music /media/media
```

Backup and edit fstab

```
sudo cp /etc/fstab
gksudo gedit /etc/fstab
```

Add these lines to the end of the file

```
##Added Drives

LABEL=MUSIC /media/music ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

LABEL=MEDIA /media/media ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

UUID=A8B0D7ACB0D77F6E /media/data ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

Assuming that you haven't already mounted them to the desktop then this should do so - post errors please. If they are already mounted then you need to unmount them first. They should all now mount on boot.

```
sudo mount -a
```

If you do not want them on the desktop you could use /mnt instead of /media for the mkdir and fstab BUT they will not be accessible in Places in nautilus, you have to find them in the filesystem and make a shortcut to the left hand pane.

---

### Post by Yellowbelly on 2008-11-17
> **forestpixie said:**
> Make some folders to mount the drives in first - you can change the names as you see fit as long as the same name is used for fstab

```
sudo mkdir /media/data /media/music /media/media
```

Backup and edit fstab

```
sudo cp /etc/fstab
gksudo gedit /etc/fstab
```

Add these lines to the end of the file

```
##Added Drives

LABEL=MUSIC /media/music ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

LABEL=MEDIA /media/media ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

UUID=A8B0D7ACB0D77F6E /media/data ntfs-3g auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0
```

Assuming that you haven't already mounted them to the desktop then this should do so - post errors please. If they are already mounted then you need to unmount them first. They should all now mount on boot.

```
sudo mount -a
```

If you do not want them on the desktop you could use /mnt instead of /media for the mkdir and fstab BUT they will not be accessible in Places in nautilus, you have to find them in the filesystem and make a shortcut to the left hand pane.

The NTFS drive (sda) worked, The others didn't (sdb1, sdc). I haven't had a chance to get back here with this till now. Are those label Music and Media drives supposed to be NTFS? I'm thinking that's why it's not being recognized. As far as mkdir, all it did was create folders in /media which there are already folders to the drives. It created them but they just open up to no where. That sudo cp /etc/fstab didn't work either: 
cp: missing destination file operand after `/etc/fstab'
Try `cp --help' for more information.

---

### Post by Elfy on 2008-11-17
Missed out the target for the backup in the cp command

Edit the fstab file and replace the LABEL= with UUID=

LABEL=MUSIC becomes UUID=4693-EB5D
LABEL=MEDIA becomes UUID=45D7-23C6

Information came from here

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

