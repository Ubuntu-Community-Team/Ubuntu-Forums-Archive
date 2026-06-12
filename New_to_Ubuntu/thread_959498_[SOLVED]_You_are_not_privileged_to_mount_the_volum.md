---
title: "[SOLVED] You are not privileged to mount the volume 'IPOD'."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by tarheel18 on 2008-10-26
I just got a new iPod after I accidentally put my old one through the wash and I've had a few problems so far. First, I attempted to use Rhytmbox with the ipod plugin to put music on it. This is what I always did with the old ipod and it always worked fine. As soon as I dragged anything to the ipod, Rhythmbox would immediately close. The ipod statyed mounted but I couldn't put anything on it. Then I tried using my windows PC. I installed iTunes and Was able to put music on the ipod without any problems. Now, whenever I connect the ipod to my Ubuntu machine, I get the message: "You are not privileged to mount the volume 'IPOD'." Anybody know what is going on here?

---

### Post by scorchgeek on 2008-10-26
Never heard of anything like that. You might try mounting the volume manually as root. Take a look at:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=851632](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=851632)

This page is about manual mount of USB drive, but you could try it with your Ipod. I don't have an iPod, though, so I can't really help you specifically ;).

---

### Post by dracayr on 2008-10-26
Make sure that in the users-admin (System&#8594;Administration&#8594;Users and groups), the checkbox "access external storage devices automatically" is checked for your user.

dracayr

---

### Post by tarheel18 on 2008-10-26
That link was for a different problem than the one I have I think, but thanks anyway scorchgeek. And that box is checked dracayr.

---

### Post by dracayr on 2008-10-26
maybe you've encountered one of hardys automounting bugs. One way to work around it would be to make a script (let's call it iMount.sh), with these contents:

```
#! /bin/sh
pmount /dev/sdXX
```

with XX to be replaced by the corresponding file in /dev/ (probably /dev/sdb1 or /dev/sda1. You could then mount your Ipod by doubleclicking the file...

But maybe there is a better solution. please post the contents of your /etc/fstab file for this

dracayr

---

### Post by tarheel18 on 2008-10-26
Sorry, I got held up doing some things for a while. Here's my fstab file
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=128c9b69-e968-49e0-9fe9-05aaff07b456 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=4174a854-5b0a-433e-aeee-63ced7e03288 none            swap    sw              0       0
/dev/sda2       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

---

### Post by tarheel18 on 2008-10-26
bump

---

### Post by dracayr on 2008-10-27
ok, remove the line beginning with "/dev/sdc2..." from the file. 

dracayr

---

### Post by tarheel18 on 2008-10-27
I removed that line but every time I try to save it, it says "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by freqhack on 2008-10-27
I have the same problem with other usb storage devices sometimes.

If you've had the device open in windows and just pulled it out of the usb port when you were finished, instead of doing the 'safely remove usb device' option, ubuntu will usually have trouble mounting the device.

I'm fairly certain it's because when you just pull the device out, windows doesn't get a chance to close the file system properly, and this is what causes issues when you try to mount it in ubuntu.

Alternatively try installing Thunar. It's a light-weight file-manager like nautilus that's used in XFCE. It seems to automount any of my stubborn USB devices. Even if I haven't removed them properly from a windows machine.

Install it like this:

```
sudo apt-get install thunar
```

hope this helps...

---

### Post by mc4man on 2008-10-27
> I removed that line but every time I try to save it, it says "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."


Use this to edit line out
```
gksudo gedit /etc/fstab
```

---

### Post by tarheel18 on 2008-10-27
> **mc4man said:**
> Use this to edit line out
```
gksudo gedit /etc/fstab
```
That worked Perfectly, thanks everybody.

---

### Post by xannaxprozaxx on 2009-03-11
I know I am late, but just in case someone has the same probs I had;
Apparently, if you leave a USB drive plugged while booting, it gets automatically added to fstab. So it gets mounted on startup before the user login (or something of the sort, I don't really know how ubu works).
So be sure to always remove your usb drives & pens before starting your machine. If you ever forget, just gksudo gedit etc/fstab, and remove the relevant line.

---

