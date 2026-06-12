---
title: "Cannot mount volume"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by elvino on 2008-11-11
I am reasonably new to Linux and certainly Ubuntu, so please excuse my newbie comments!
I have installed Ubuntu 810 on a pen drive quite satisfactorily and I am very happy with it's functionality and all of its clever and unexpected bonuses, like automatic network detection and printer detection.
But: I have a problem. When I do a fresh install to a pen drive and reboot, the HDD (containing WinXP) is immediately recognised and appears on the desktop. Excellent.
BUT: On reboot the HDD will not re-mount and I get the error 'Unable to mount the volume' and the details are 'mount: according to mtab,  /dev/sda2 is already mounted on /media/disk'
I have checked the integrity of the HDD with the Windows partition and all seems well. Windows boots perfectly. I created yet another usb install and it mounted the drive perfectly the first time, but never again.
Tell me what else you might like me to check.

---

### Post by REDace0 on 2008-11-11
Maybe this is a dumb question, but have you tried opening a terminal and going to /media/disk?

Alternatively, go look at the file /etc/mtab and see if it actually lists the drive.

Also, it sounds like we could benefit from knowing what your computer says it has mounted, could you post the output from
```

cat /etc/fstab; echo; cat /etc/mtab

```

Let's see if we can get this fixed. :)

---

### Post by elvino on 2008-11-11
Thanka for offering to help. Here is the result of the command you suggested:

ubuntu@ubuntu:~$ cat /etc/fstab; echo; cat /etc/mtab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

/proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
rootfs / rootfs rw 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
/dev/sdb1 /cdrom vfat rw,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda2 /media/disk fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
tmpfs /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=0755 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/fuse /home/ubuntu/.gvfs fuse rw,nosuid,nodev,user=ubuntu 0 0

I hope this means something to you!

---

### Post by elvino on 2008-11-11
Just to clarify the error, I am attaching a screenshot...
[IMG]http://www.maskar.org/error.jpg[/IMG]

---

### Post by The Cog on 2008-11-11
Well it seems to think that sda2 is alrady mounted on /media/disk. 

Have you looked in /media/disk to see if the disk contents are there and visible? I think they probably are. Try:
Places->Computer, Filesystem->media->disk.

---

### Post by elvino on 2008-11-11
I have looked as you suggested:
Places>Computer,Filesystem>Media - but that's it, no DISK, just .hal-mtab and .hal-mtab-lock
That any help :)

---

### Post by darksideforge on 2008-11-28
Here's a screenshot of what mine says:
[IMG]http://i38.photobucket.com/albums/e129/diveclint/Screenshot3.png[/IMG]

My DVD-RW stopped working suddenly two days ago and I can't for the life of me figure out why!:confused:

---

### Post by darksideforge on 2008-11-29
I found something over on the Kubuntu board where sometimes CD drives and DVD drives weren't recognized after v8.10 install and all that was required was a regionset. It worked PERFECTLY for me!

First:
```
sudo apt-get install regionset
```

Second: if region is already set, remove disk from drive and restart normally.

Third: if region is NOT set:
```
regionset
```

Fourth: remove disk from drive, perform normal restart, reinsert disk, and see what happens.

~Just my two cents

PS: If it works, find Mc4man and thank him!
[http://ubuntuforums.org/showthread.php?p=6277559#post6277559]("http://ubuntuforums.org/showthread.php?p=6277559#post6277559")

---

