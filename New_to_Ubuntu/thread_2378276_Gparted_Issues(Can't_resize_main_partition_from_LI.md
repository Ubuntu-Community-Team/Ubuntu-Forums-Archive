---
title: "Gparted Issues(Can't resize main partition from LIVECD)"
date: 2017-11-21
forum: New to Ubuntu
---

### Post by todd4921 on 2017-11-21
Hey Im an extremely new user to Ubuntu and am running into issues resizing my primary partition....now I know you are going to say it has to be done from a LiveCD and I am using one.

The maximum I can do is resize the partition by 48MiB and I have no idea why,here is a picture of the gparted screen:(No internet on the laptop hence the phone)

[Http://imgur.com/a/WZPvT](Http://imgur.com/a/WZPvT)

Take note of the maximum and minimum size,I rarely make forum posts but every single post I found on the issue said use a liveCD and unmount the partition...as you can see I have done both

---

### Post by oldfred on 2017-11-21
You do not have Linux partitions that can be changed with gparted.
You have full drive LVM install which uses 2 standard partitions one for /boot and the other as the container for all the LVM partitions.
And with LVM you have to use LVM tools.

LVM in intended to be used for the entire hard drive. You can then resize Linux partitions inside the LVM and can do that when system is running. 

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

---

### Post by todd4921 on 2017-11-21
Can I do that from within the OS or do I have to boot from a liveCD then somehow install LVM tools on there?

Also what program would you recommend for managing my LVM disks,preferably with a GUI

---

### Post by todd4921 on 2017-11-21
You know considering that this is a new install instead of learning LVM for what should be a secondary OS I'm just gonna format the drive and reinstall without LVM to make it easier to dual boot

---

