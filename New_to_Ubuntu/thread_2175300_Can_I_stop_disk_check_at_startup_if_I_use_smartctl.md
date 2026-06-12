---
title: "Can I stop disk check at startup if I use smartctl?"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by arroy_0209 on 2013-09-18
There is a default hard disk check program with the ubuntu12.04 which runs automatically at the time of logging in, may be after a gap of every 30 or 40 sessions. However there is also a program: "smartctl" which can do the job very efficiently. If I choose to use the later to check condition of hard disk, is there any harm if I stop the default hard disk condition checker? How do I do it? I am especially worried about frequent power fluctuations at our ocality in recent times. Though the power to my desktop is through an offline UPS, I am afraid frequent power level fluctuations may soon damage the hard disk. So it is best if I get some forecast regarding that. If you know of any better program for that specific purpose, please mention it. Thanks.

---

### Post by UltimateCat on 2013-09-18
HI::P

This looks like a good application. Here is more information on it to help you know more about it-

[http://smartmontools.sourceforge.net/man/smartctl.8.html](http://smartmontools.sourceforge.net/man/smartctl.8.html)

From what I read if you skip the disk check it will do it again at the next re-start-
One of our members here disabled his here in this thread-
[h=2]How to disable checkdisk on startup[/h]http://ubuntuforums.org/showthread.php?t=2082504


There is also another application for monitoring if you'd like to consider it-
It's called CPU Frequency Monitoring

I installed in on a distro called "Voyager" which was built on Ubuntu 12.04- You can find it here:
[https://launchpad.net/ubuntu/+source/cpufrequtils](https://launchpad.net/ubuntu/+source/cpufrequtils)

> is there any harm if I stop the default hard disk condition checker

That; I don't know so be careful until another member here advises you--;)

You can also use the sensors command to see if your system is running hot-
```
sensors -f | grep -i temp

```
-f is for fahrenheit, -c is for config file, -h is for help, -s is for set root only, -u is for raw output for degug and -v is for program version.

Hope that helps-

---

### Post by oldos2er on 2013-09-18
fsck and smartctl are two different things, there's no "one replacing the other." fsck is (literally) file system check, which works with a bunch of different possible file systems; ext2, ext3, ext4, etc.

smartctl is a check of a disk drive's [SMART]("https://en.wikipedia.org/wiki/S.M.A.R.T.") data which lies "underneath" any file systems in use on the disk's partitions.

---

### Post by Dennis N on 2013-09-18
Users should know that fsck has been disabled in the past few releases and should be enabled by the user. 

See :

[http://ubuntuforums.org/showthread.php?t=2141727](http://ubuntuforums.org/showthread.php?t=2141727)

How to check if it's disabled, and how to enable fsck is explained in Post #3 of that thread.

As oldos2er points out, condition of the disk drive and condition of file system are two different things.

---

