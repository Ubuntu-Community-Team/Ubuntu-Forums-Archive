---
title: "how can i format a external harddrive"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by blake7 on 2012-07-18
hi just got a new external harddrive and can down load on to it
so need to format it how can i do this


cheers

ps this forum looks like windows 98 on my laptop can any one help me change it back from this night mare

---

### Post by GreatDanton on 2012-07-18
Plug in your hard drive into your computer. Right click on the shortcut on the Unity bar, and select format, or you can also use Gparted.

Hope this helps.

---

### Post by audiomick on 2012-07-18
Why do you want to format it, actually? You said you could download to it; I assume you mean you can save files to it and read them back off it.

The drive is probably formatted with one partition, and with a Windows file format, maybe FAT32. This will work with your Linux install. If you may wish to use the drive with a Windows install as well, you could consider just leaving the partition as it is.

If you wish to format to a Linux file system, or even just have a look at how the drive is set up, you can look at it with a partitioning tool. I usually use Gparted, but this is not installed on newer Ubuntu releases by default. You would have to install it.

The default partitioning tool can be started from the dash on a Unity desktop. Try typing "hard drive" in the search box on the dash. I can't say for sure what it is called on an English install.

Bear in mind that you can't work on a drive/ partition that is mounted. When you plug in the drive, it will be mounted. You will have to unmount it in the partitioning program before you can do anything with the partitions.

---

### Post by mebomechanicno1 on 2012-07-18
The drive should appear on the launch bar down the left side of the desktop, but I agree, why would you want to format it?  (A question I meant to ask 4 hours ago when I first read this, but decided to come home instead)

---

