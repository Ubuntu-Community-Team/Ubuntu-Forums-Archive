---
title: "unable to mount DVD"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by DrScum on 2008-08-04
Installed Xubuntu 8.04 from CD inserted into the DVD drive (see below). However, the following problem so far I was unable to solve:

When inserting a DVD into the DVD drive the icon appears on the desktop  but an error message occurs:
Failed to mount "DVD Title".
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.

When I close the error message with the ok button and click on the DVD icon again, the files on the dvd become available but VLC doesn't play the movie. When starting VCL and selecting "open disc" the movie doesn't play.
I came to the conclusion that there is something wrong with the configuration of the drives.
How can I approach this?

fstab readout:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=9875abb7-de71-4446-9fe5-ad8f37085e3c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b5ba9dfb-d6f5-4dc8-ad18-42d445f352cd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

mtab readout:
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=username 0 0

the following hardware is installed:
hdd primary master
DVD drive secondary master
CD-RW drive secondary slave


Thanks for your help.

---

### Post by northern lights on 2008-08-04
Ubuntu can read unencrypted DVDs by default. Movie DVDs are almost always a restricted format, though. To watch a movie, do this:

Navigate to "System > Administration > Software Sources". Enable all repositories but 'proposed' and 'backports'.

Then run ```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
Update (synchronize index files w/ sources), install public keyring, update again```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Install the library necessary for DVD playback```
sudo apt-get install libdvdcss2
```Install a player and a ripper```
sudo apt-get install vlc dvdrip
```

As an aside you might also like wma/wmv support, which is now possible with medibuntu enabled```
sudo apt-get install w32codecs
```

---

### Post by DrScum on 2008-08-04
Thanks a lot for your help, I try what you suggest tomorrow (it's late in my time zone).

---

### Post by dwalker0044 on 2008-08-12
Hi everyone, 
I recently installed the latest version of xubuntu and like DrScum received the error message,

```
Failed to mount "DVD Title".
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.
```

I've followed the steps proposed by northern lights, however the error remains. I also receive the following message when I try to eject the disc,

```
Failed to eject "DVD title
umount: only root can unmount /dev/scd0 from /media/cdrom0
eject: unmount of `/media/cdrom0' failed.
"
```

This has become quite a big problem as my DVD is now stuck in the drive! :S 

If it helps I did notice that VLC player attempts to auto-play - therefore I don't think it has anything to do with repositories, codecs or the like. I can also listen and auto-play CDs with rhythmbox 

Thanks for any help you can give me!

---

### Post by aimpau on 2008-08-12
I'm using xubuntu also. Here's the catch in it. Though your fstab says that your CD/DVD is mounted in /media/cdrom0 and as device /dev/scd0, I have my xine-ui configured to use /dev/cdrom1 for my CD and /dev/dvd1 for my DVD. Try reconfiguring your VLC setup so that your CD uses /dev/cdrom1 and DVD /dev/dvd1.

---

### Post by dwalker0044 on 2008-08-12
Hi again,

Thanks for the reply, but I don't really understand what is happening and I'm not sure how this would help (and that's not a criticism I'm just a beginner). 

From my understanding I thought the problem was related to how Xubuntu was mounting/configuring the drive as the problem occurs from the moment I insert a disc - not that of how/where my media player was attempting to read from (if I can say that - I may have mis-understood again). I.e. *If* the problem was with VLC player, then I would presume that I wouldn't receive any errors until I try and use it? 

However, (continuing with you suggestion) am I correct in trying to configure VLC from the File -> Open Disc directory? From here I can see a tab called "Tab (menus)" with options: 
[INDENT]Device name = /dev/scd0[/INDENT]
and then further down under "Advance options":
[INDENT]Customize = dvd:///dev/scd0[/INDENT]
Are these the things I should be trying to change? And what to?

Thanks again for your help!

---

### Post by dwalker0044 on 2008-08-13
Ok, so the mount errors remain, however I manage to solve the problem by using the advice given in this thread:
[http://ubuntuforums.org/showthread.php?t=872699](http://ubuntuforums.org/showthread.php?t=872699)

i.e. set vlc to use the video output module = x.11 video output

This problem may have occurred from when I uninstalled compiz after I realized the computer was unable to run it.  

So everything is now working although it would be really nice if someone could explain why xubuntu gives these mounting errors - I've tried everything but they still remain when I inset a DVD. 

thanks!

---

### Post by Sumerian on 2009-09-12
i can't mount my CD/DVD, it's not shown in the places neither on the desktop, when i go to media devices it shows me 2 cd folders one as a shortcut (cdrom), the othe cdrom0 while i have only one, please help!!!

sudo mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jimmy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jimmy)

sudo umount /dev/sda1
umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

sudo mount /dev/sda1 /media/cdrom -t udf
mount: /dev/sda1 already mounted or /media/cdrom busy
mount: according to mtab, /dev/sda1 is mounted on /

---

### Post by DrScum on 2009-09-13
Thanks Sumerian for your help. I did have solved the problem. I apologize for not putting "solved" in the title.

---

