---
title: "[SOLVED] Problems mounting partition"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Wim De Winter on 2008-04-24
hi there,

I'm using Xubuntu 8.04 and I'm having problems mounting a fat32 partition. I normally use gparted without any problems but now I got an error message while trying to mount that partition (as in the attached error.jpg file). The error mesage states:
"org.freedesktop.hal.storage.mount-fixed
auth_admin_keep_always <-- (action,result)"
I then rebooted, using a knoppix live cd. There I was able to mount/unmount the partition without any problem, and could even read its contents. Rebooted again in xubuntu, restarted gparted, and that resulted in the same error message. I then did some research on the forums, but I'm not entirely sure what to do next. This info might come in handy for the brave soul willing to help me:

"wim@Desktop-Wim:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=183660b2-f906-4405-9762-9c7863a0a422 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0EE7-C7FB  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=F166-1C88  /media/sda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=5b983070-127d-462b-bb28-14d33d9c696b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
wim@Desktop-Wim:~$ sudo mount -a
mount: apparaat /dev/disk/by-uuid/F166-1C88 bestaat niet
wim@Desktop-Wim:~$ " -- **"bestaat niet" translates in "doesn't exist"**

The problem obviously occurs with the sda4 partition (no problems with sda1 (also fat32). Please bear in mind that I'm a newb, so please, one step at a time.

Thanks.

---

### Post by ofb on 2008-04-25
I'm afraid I'm more foolish than brave, but here are some ideas. 

Try 'sudo fdisk -l' to list your partitions. To see what shows up, and to see if it gives a more helpful error. 

I'm suspecting something to do with PolicyKit, which I don't think Knoppix has. 

When did this problem show up? Were you able to mount that partition with 8.04 before? Can you think of anything you might have done with permissions just before that partition became unmountable?

Someone has a "quick & dirty" solution over here, but I don't know if it's a good idea. I'm not an expert with this. You should probably figure out exactly what's wrong, and why, before doing alterations.
[http://www.linuxquestions.org/questions/linux-newbie-8/acces-to-partiton-612726/](http://www.linuxquestions.org/questions/linux-newbie-8/acces-to-partiton-612726/)

PolicyKit seems to be new with 8.04, so there may be more people posting similar trouble in a few days. Keep checking.

Also show us the output from 'cat /etc/PolicyKit/PolicyKit.conf'. Perhaps yours is different somehow.

---

### Post by Wim De Winter on 2008-04-27
hey ofb, thanks for the attention. First some output that might tell us/you more:

"[COLOR="RoyalBlue"]wim@Desktop-Wim:~$ sudo fdisk -l
[sudo] password for wim: 

Schijf /dev/sda: 82.3 GB, 82348277760 bytes
255 koppen, 63 sectoren/spoor, 10011 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x000b2710

 Apparaat Opstart   **Begin**       Einde     **Blokken**   ID  **Systeem**
/dev/sda1               **1**        1305    **10482381**    b  **W95 FAT32**
/dev/sda2            **9881**       10011     **1052257+**  82  **Linux wisselgeheugen**
/dev/sda3            **1306**        5221    **31455270**   83  **Linux**
/dev/sda4            **5222**        9880    **37423417+**   b  **W95 FAT32**

Partitietabel-items liggen niet in schijfvolgorde.
wim@Desktop-Wim:~$ cat /etc/PolicyKit/PolicyKit.conf
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- XML -*- -->

<!DOCTYPE pkconfig PUBLIC "-//freedesktop//DTD PolicyKit Configuration 1.0//EN"
"http://hal.freedesktop.org/releases/PolicyKit/1.0/config.dtd">

<!-- See the manual page PolicyKit.conf(5) for file format -->

<config version="0.1">
    <match user="root">
        <return result="yes"/>
    </match>
    <define_admin_auth group="admin"/>
</config>
wim@Desktop-Wim:~$[/COLOR]"

Now some translations: 
[INDENT]wisselgeheugen = swap
Partitietabel-items liggen niet in schijfvolgorde. = items in partitiontable not in disc sequence.
[/INDENT]

Some more info: Before upgrading to 8.04, I had the "problem" that sda4 didn't mount automatically, but back then I'd just do it manually (right-click > mount). That always did the trick. It somehow also unmounted automatically. I think the partition was mounted before I upgraded. It was always the first thing I did, mount that partition (my music files are stored on it). But now I can't do it, the partition seems to have been hidden from detection somehow.

---

### Post by Wim De Winter on 2008-04-27
Did some searching on the forum, and found this thread [http://ubuntuforums.org/showthread.php?t=768896]("http://ubuntuforums.org/showthread.php?t=768896"). So I installed "Storage Device Manager". sda4 mounted perfectly. I checked the option "The file system is mounted at boot time".  So now I'm going to reboot, and hope it works. fingers crossed.

---

### Post by hyper_ch on 2008-04-27
obviously the UUID of your fat32 disks have changed. So you need to address them by /dev/sdXY instead of UUID=.....

so change your fstab from
```

# /dev/sda1
UUID=0EE7-C7FB /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda4
UUID=F166-1C88 /media/sda4 vfat defaults,utf8,umask=007,gid=46 0 1

```
to
```

/dev/sda1 /media/sda1 vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda4 /media/sda4 vfat defaults,utf8,umask=007,gid=46 0 1

```

---

### Post by Wim De Winter on 2008-04-27
**SOLVED** (the "mark as solved" button seems to have disappeared?)

The "storage device manager" approach helps and works. However, the "fundamental" problem wasn't solved. hyper_ch's approach however, did solve the fundamental problem, so I chose that one. Thanks the both of you!

---

### Post by hyper_ch on 2008-04-27
or you could enter the new UUIDs into your fstab ;)

Did you repartition your drive somehow?

---

### Post by Wim De Winter on 2008-04-27
I didn't repartition it. I did try to rename the partitions, and probably did something very wrong by trying that. But hey, what's wrong with the name sda4, right?:-) Anyway, I'm leaving it as it is. It's working, that's all I need.
A little off-topic: do you know how to edit the name of this thread? The "mark as solved" button seems to have vanished?

---

### Post by hyper_ch on 2008-04-27
well, renaming the partition will alter it's UUID

---

### Post by ofb on 2008-04-28
> **Wim De Winter said:**
> A little off-topic: do you know how to edit the name of this thread? The "mark as solved" button seems to have vanished?

I just had a look through the Forum Feedback & Help section. Looks like the forum staff are aware the Solved option is missing, so hopefully it'll be back before too long. 

Regarding renaming partitions... I'm not even sure you can do that. You can have the mount point for the partition renamed anything you want of course. Is that what you wanted?

For example, look at this line in your fstab

UUID=0EE7-C7FB **/media/sda1** vfat defaults,utf8,umask=007,gid=46 0 1

'/media/sda1' is the declared mount point. To change the name of the mount point you would first create a directory anywhere you'd like of the desired name, then change the '/media/sda1' to the new path. Like this,

mkdir /Files/NewName

Then 'sudo nano /etc/fstab' to open the fstab in an editor with root permission. Then change to something like this,

UUID=0EE7-C7FB **/home/[your user name here]/Files/NewName** vfat defaults,utf8,umask=007,gid=46 0 1

Then run 'sudo mount -a' to reload the new fstab, and the files in that partition will show up in /Files/NewName, or whatever you used.

I hope that makes sense. I'm not quite awake yet.


I should say if you're new to editing fstab, you should make a backup copy first so you can correct any mistakes. Run, 

sudo cp /etc/fstab /etc/fstabBAK

---

