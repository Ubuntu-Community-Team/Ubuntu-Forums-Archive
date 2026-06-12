---
title: "[SOLVED] Can I use GParted to change/specify a partition's mountpoint?"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-07-08
I can't find a way to change a partition's mountpoint in GParted. Is it possible to do this in GParted, or do I have to edit fstab?

Thanks!

---

### Post by tjwoosta on 2008-07-08
you can't do it with gparted

you will need to edit your /etc/fstab

(its actually really easy)

if you need to just post your fstab and we can help you edit it

---

### Post by crossedout on 2008-07-08
You'll need to edit fstab.  If you re-formated the partition after install make sure you note that if you need assistance editing fstab.

-Xout

---

### Post by pi.boy.travis on 2008-07-09
Here is /etc/fstab :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=f69966a9-c6bf-4e61-85ed-333a25809f49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=06f33f5a-5d8f-460f-8eb6-a9f3dbc642e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I am trying to change the mountpoint of /dev/sdb1 which is a partition on my external hard drive.

---

### Post by pi.boy.travis on 2008-07-09
OK, I figured out that I can change the mountpoint of my external drive by right-clicking on it's desktop icon, selecting properties, selecting the volume tab, and after expanding the settings menu, I found a mountpoint input box. Huzzzah!  I entered /media/SEAGATE2 (I have two external disks that identefy as SEAGATE and I wanted to be able to distinguish between them) unmounted, and then remounted.  Then I get:

Unable to mount the volume 'SEAGATE'.

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Perhaps I used characters that are not allowed?

I can't get back to the same properties dialog.  How else can I change the mountpoint?

---

### Post by crossedout on 2008-07-09
So this is an external drive.  Is the intention to have it permanently connected and accessible?  If not, then I wouldn't bother with fstab, just manually mount it where you like when the drive is initially connected.

-Xout

---

### Post by pi.boy.travis on 2008-07-09
OK, so I can manually set the mountpoint when I connect the drive.  

Is there a way to have the drive mounted automatically when I connect it?

The drive is currently formatted as FAT32,but there is no data on it so I can reformat it, etc.

---

### Post by crossedout on 2008-07-09
You'll need to add an entry similar to:
```
# /dev/sdb1
UUID=<ENTER UUID HERE> <MountPoint HERE>    <Partition Format HERE>    defaults 0       0
```

That is a very rough entry example.  You'll need some information to plug into each slot before it can be effective.
1. Backup your copy of fstab:
```
sudo cp /etc/fstab /etc/fstab_backup
```
2. Find the UUID of your partition.  Connect the drive and type:
```
sudo blkid
```
Locate the /dev/sdb1 entry and note the UUID and TYPE (partition format)
3. Determine your mount point.  Since you want to change the mount point, I assume you have a place chosen already.
4. Read over the following page to familiarize yourself with the different options involving read/write, owner, permissions, etc. since inevitably you'll want something specific.
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

-Xout

---

### Post by pi.boy.travis on 2008-07-09
Thanks!

I'll have to play around with gnome-volume-manager some time.

---

