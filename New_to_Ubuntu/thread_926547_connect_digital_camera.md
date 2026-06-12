---
title: "connect digital camera"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by bjhome on 2008-09-22
Can someone please give me step by step instructions as how to connect my digital camera to digikam. the camera is a sony dsc -p32.

---

### Post by ibizatunes on 2008-09-22
I have a sony camera, that by default doesnt work, basicly there is a option on the camera to set PTP (i think) in the setting on the camera, change it to that and it should work!

---

### Post by Sealbhach on 2008-09-22
Have you tried connecting the camera?

With my Samsung digital camera, I just plug it into Ubuntu and it just works! I can either use Nautilus to retrieve the photos or F-Spot.
Have you tried already and got error messages?


.

---

### Post by halitech on 2008-09-22
have you followed the steps that vikram gave you in this thread yet?

[http://ubuntuforums.org/showthread.php?t=925434](http://ubuntuforums.org/showthread.php?t=925434)

---

### Post by bjhome on 2008-09-23
I have tried everything i have been told. i'm not sure whether i have done it in the right order or not i am quite new to all this. but i copied and pasted the commands in terminal and nothing is happening. im probably not doing it right. however i have now tried gthumb and am getting this error message.
An error occurred in the io-library ('Bad parameters') :
Could not find USB device (vendor 0x54c product 0x4e) Make sure this device is connected to computer.

---

### Post by halitech on 2008-09-23
ok, open a terminal (Applications - Accessories - Terminal)

first, connect the camera

type in ```
mount
```
then disconnect the camera, wait 1 minute and do the same command again.

then, still in the termianl, type in```
lsmod | grep usb
```

highlight the information in the terminal, right click on it and select copy. then come back here and paste that information into a message so we can see if the camera is being seen.

---

### Post by bjhome on 2008-09-24
bev@bev-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bev/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bev)
bev@bev-laptop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/bev/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bev)
bev@bev-laptop:~$ lsmod | grep usb
usbcore               146028  3 ehci_hcd,ohci_hcd
bev@bev-laptop:~$

---

### Post by bjhome on 2008-09-24
is this now correct and where do i go from here. at the moment i have fspot(which i dont like much)
digikam, gthumb and showfoto loaded on my computer which is the better one to use and how will i be able to get it to go to it by default.

---

### Post by Sef on 2008-09-24
> digikam, gthumb and showfoto loaded on my computer which is the better one to use 

Try them and see what you like.  There will be advantages and disadvantages to all of them.

---

### Post by halitech on 2008-09-24
looking at the mount info, there is no change with the camera plugged in or with it not plugged in. I'm thinking there is something wrong with either the cable or the camera or the port. Does it work on another computer with the same cable?

---

