---
title: "[SOLVED] Format to ext3"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by MooseMagnet on 2008-07-26
I just purchased a USB hard drive. It's formatted in FAT32. 
How can I format it to ext3?
I've read several threads about the different formats, but haven't found specific instructions on how to reformat the drive.

Thanks.

---

### Post by SunnyRabbiera on 2008-07-26
well you can use gparted on it, mount the external and go up to system> administration> partition editor... it should be there.

---

### Post by eightmillion on 2008-07-26
You should just be able to plug it in and fire up gparted. It's fairly straight forward.

---

### Post by perlluver on 2008-07-26
Download gparted, it is in synaptics.  Or you can download the whole cd from there website.  Just google for Gparted.

---

### Post by MooseMagnet on 2008-07-26
Good deal. That was easy. Seems to be reformatted correctly.
gparted has clear instructions on their site, which helped greatly.
Thanks much.

---

### Post by perlluver on 2008-07-26
> **MooseMagnet said:**
> Good deal. That was easy. Seems to be reformatted correctly.
gparted has clear instructions on their site, which helped greatly.
Thanks much.

Your welcome, and please mark as solved, in the thread tools.

---

### Post by MooseMagnet on 2008-07-26
I spoke too soon. I did something wrong. 
I can not move anything to the external drive. Can not create a folder on the external drive. Can not paste to it, etc.

---

### Post by eightmillion on 2008-07-26
Please post the output of the 'mount' command. I suspect you're having permissions issues.

---

### Post by MooseMagnet on 2008-07-26
Here are the results of mount.

rich@rich-laptop:~$ sudo mount
Password:
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-17-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
rich@rich-laptop:~$ 

I made things worse. Tried to format back to FAT32, got an error. Tried to format back to ext3, got an error. Now it won't mount at all on the desktop.

---

### Post by eightmillion on 2008-07-26
What is the error you are recieving?

---

### Post by MooseMagnet on 2008-07-26
I restarted everything. Was able to correctly format the drive to ext3 with geparted.

But there is no icon for the drive on my desktop, and it does not list the drive in the file browser.

Will run mount again. Looks like the same results:

rich@rich-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-17-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
rich@rich-laptop:~$

---

### Post by MooseMagnet on 2008-07-26
More information:

rich@rich-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7111    57119076   83  Linux
/dev/sda2            7112        7296     1486012+   5  Extended
/dev/sda5            7112        7296     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux
rich@rich-laptop:~$

---

### Post by eightmillion on 2008-07-26
You should be able to unplug the drive and then plug it back in. Ubuntu should pick it up and mount it. If that doesn't happen, you can mount the drive manually with:
> sudo mount -t ext3 /dev/sdb1 /media/disk/
Note that you'd probably have to create the folder /media/disk beforehand.

---

### Post by MooseMagnet on 2008-07-26
Used nautilus to create the folder. Used your command to mount it.
Now it mounts on the desktop ok. The only thing in the /disk/ folder is lost+found.

Ran mount again, with these results:

rich@rich-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-17-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev)
rich@rich-laptop:~$

---

### Post by eightmillion on 2008-07-26
Try copying some files to it.

---

### Post by MooseMagnet on 2008-07-26
Can't copy to it, get this error message.

"You do not have permissions to write to this folder."

---

### Post by eightmillion on 2008-07-26
I'm sure that the folder is owned by the root user. Use this command to change it:
> sudo chown rich:rich /media/disk
Then try to copy some files.

---

### Post by MooseMagnet on 2008-07-26
Good deal. I was able to copy a file from my laptop to the external drive. Let me check a couple more things before I mark this thread as closed.
BRB.
And thank you for your help.

---

### Post by eightmillion on 2008-07-26
No problem. I'm glad that worked out. ;)

---

