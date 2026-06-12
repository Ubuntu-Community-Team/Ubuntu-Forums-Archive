---
title: "[SOLVED] Can't Get PartImage to Create Image"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by bobsmith2 on 2008-09-08
No matter what I do, Partimage throws up the following error:

"Cannot create temp file [/sdc2]. No space left on device." 

I'm backing up a 4 GB Ubuntu partition image to an empty 10 GB partition - both the image being backed up and the empty space being backed up to are ext3. The partition I'm backing up FROM (my ubuntu partition) is NOT mounted - the partition I'm backing up TO is mounted. Every time it gets about a third of the way through and stops. 

Here's what I'm putting in the Partimage field (the second field where you're supposed to put the path of the file to be backed up TO):

" /sdc2/ubuntubkp "    (sdc2 is an empty 10 GB ext3 partition on an external USB drive)

I also tried this:

" /dev/sdc2/ubuntubkp "

I'm doing this by booting from an 8.04 Ubuntu Live CD and running Partimage from there. I ALWAYS get the same error, no matter how huge the space is I'm trying to back up to. 

What am I doing wrong? Thanks.

---

### Post by bobsmith2 on 2008-09-08
Can anyone help? Should I be posting this type of question on a different forum?

---

### Post by Titan8990 on 2008-09-08
This is the right spot. I don't have any experience with PartImage in particular but I can point out somethings that are probably an issue.

1. You can't manipulate data on a partition that is not mounted.

2. You can't write directly to a device like you are trying to do. You have to write it to it's mount point which is usually in the /media directory. To see where a device is mounted simply type "mount" in to the terminal.

```
jordan@einstein:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sdc1 on /media/backup type ext3 (rw)
```

Here I can see that my sdc drive is located at /media/backup. You might also want to look in to the dd command:

man dd

---

### Post by bumanie on 2008-09-08
I do not know a great about partimage, other than it is basically a GUI for dd commands. I would try dd commands if I were you. You could use code such as this > dd if=/dev/sda2 of=/dev/sdb2 You should do this off a live cd and of course substitute the drive names to correlate with your drives ie change sda2 and sdb2 as appropriate. Hope this helps.

---

### Post by Titan8990 on 2008-09-08
Also, be very careful when using the dd command. Misuse can lead to the loss of all the data on your drive.

---

### Post by whitethorn on 2008-09-08
> **Titan8990 said:**
> This is the right spot. I don't have any experience with PartImage in particular but I can point out somethings that are probably an issue.

1. You can't manipulate data on a partition that is not mounted.

2. You can't write directly to a device like you are trying to do. You have to write it to it's mount point which is usually in the /media directory. To see where a device is mounted simply type "mount" in to the terminal.

Here I can see that my sdc drive is located at /media/backup. You might also want to look in to the dd command:

man dd

You have to backup to the mount point.  As far as I remember you have to mount the destination drive, not the device itself.  /media/backup (if I remember correctly you have to mount the device manually so create a folder in media and mount it to that folder.  Then you can backup the other partition.)

---

### Post by oldos2er on 2008-09-08
"Cannot create temp file [/sdc2]. No space left on device." 

 No space left on device means just what it says--the partition is full.

---

### Post by bobsmith2 on 2008-09-08
Thanks to everyone for the assistance. I finally got it to work. My problem was exactly what Titan8990 & whitehorn said - I was trying to back up directly to a device. I finally got it to work by unmounting everything EXCEPT the partition I was backing up TO (sdc2) and then doing this:

sudo mkdir /backup2
sudo mount -t ext3 /dev/sdc2 /backup2

Then in Partimage I entered this path: /backup2/ubuntubkp (ubuntubkp is just the backup image's filename).

It worked! Clearly my problem is a poor grasp of the way Linux manages devices, directories and files. I have much to learn. Your help is greatly appreciated.

---

### Post by Titan8990 on 2008-09-09
Good to hear everything worked out for you. Don't worry you will get the hang of Linux and wander why you spent all that time with Windows.

---

