---
title: "Can't get/change access to Data-partition"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by Little viking on 2013-08-17
Hallo,
I have just installed Lubuntu 13.04.
It seems to work fine, but I simply can't get user-access to my second partition (Fat32, owner root).
I use partition to keep my data after a reinstall of the system
Unfortunately the new system has given the partition root-access only.
I have tried to open pcmanref as root (which works) and then change the access rigths to "all", but after pressing "ok" it hasn't actually changed anything, ie. I am back to square one.
Tried sudo chmod a-rw /Data
in a terminal.
No change either.
Any ideas on how to solve the problem?

---

### Post by GwL3eNC on 2013-08-17
Hallo Little viking,

i dont know if i understand you right. You can enter a line in /etc/fstab (as sudo) to mount your
partition on system startup using some options. It's the same as would you use the
mount command. Assume /dev/sda3 is your partition then the line

/dev/sda3 /media/backup/ vfat defaults 0 0

should help you (the folder /media/backup must exist!), i hope.

default includes the options rw,suid,dev,exec,auto,nouser,async

---

### Post by Little viking on 2013-08-17
Hallo again and thanx for your reply.
It did make a difference and now lets all show and access the content but not change...
below fstab as I where I have changed the 3rd line from below.
How can I give all users full access to the partition?

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9e91385f-c8de-46e5-a0b2-9714462c67ba /               ext4    errors=remount-ro 0       1
# /Data was on /dev/sda2 during installation
UUID=7C4D-FB89  /Data vfat defaults 0 0
# swap was on /dev/sda3 during installation
UUID=962d9bf6-3bbe-4751-b0c6-1604194546a7 none            swap    sw              0       0

---

### Post by GwL3eNC on 2013-08-17
Hmm, strange. These are the settings you need. what says

ls -l / | grep Data

or try blind

sudo chmod a+rwx /Data

---

### Post by Little viking on 2013-08-17
Well,
I thought of something I had tried before (and only just found again).
Changed the 3rd line from below to
> /Data vfat rw,auto,user,umask=0000              0       0

and now it says that all are allowed right to both access, show and change. Good.
But I doesn't quite work the way it is supposed to:
For once I am not allowed to delete things from there the ordinary way (ie. to the bin) but only delete them directly. When trying to delete to the bin it says, that the file-system doesn't support this action (my translation from my systems german).
Furthermore it seems, that I can't move my dropbox-folder there from /home (through dropbox-settings in the tray). It starts all right but stops after making the first folder and before moving the first file which it says it cannot move there... Strange
Maybe I just have to accept things as they are now but why is this always such a hassle?

---

### Post by GwL3eNC on 2013-08-17
The previous was right! In you first post you have tried

sudo chmod a-rw

thats wrong. You must do it with a plus a+rw. Try it

---

### Post by Little viking on 2013-08-17
I hadn't tried chmod but only changed the fstab-file directly. Now I tried 
> sudo chmod a+rw /Data
but the fstab wouldn't change. It still looks like in my last post.
Well, doesn't look like I can do anything else. Thanx for your help!

---

### Post by GwL3eNC on 2013-08-17
No,

dear friend, chmod dont change the fstab. chmod set the permission of the folder Data.
with

sudo chmod a+rw /Data

everybody can read and write the folder. you can see that with an 

ls -l /

and look at the permissions on the left side. they are all set. Make your fstab like above (your second post)
where you set

UUID=7C4D-FB89  /Data vfat defaults 0 0

that was right. These two things combained must work. Remember you have to restart before changes on
fstab take effect.

---

### Post by Little viking on 2013-08-17
Thanx again. Well, I put the fstab back to defaults 0 0
AND did a sudo chmod a+rw /Data
but got to where I had beed before: permission to see and access but NOT change.
Now I am tired and will go back to 
> /Data vfat rw,auto,user,umask=0000 0 0 
which to now has worked best.
Thanx for all your help and time!

---

### Post by Morbius1 on 2013-08-17
> UUID=7C4D-FB89 /Data vfat rw,auto,user,umask=0000              0       0                      
You are close.

You can't send something to the trash because although everyone has access to the mounted partition it's still owned by root and it's root's trash you are trying to send something to and you don't have permissions. Take possession of the mounted partition:

** Unmount the partition:
```
sudo umount /Data
```
** Change the line in fstab to add your user id:
```
UUID=7C4D-FB89 /Data vfat rw,auto,user,umask=0000,**[COLOR=#0000cd]uid=1000[/COLOR]**              0       0                      
```
** Remount with this command so you don't have to do a reboot:
```
sudo mount -a
```

[COLOR=#0000cd]* Note: You can't do a chmod on a mounted fat32 partition and it's useless to do it before it's mounted as a mounted partition always replaces the permissions with it's own - true for any filesystem.*[/COLOR]

---

