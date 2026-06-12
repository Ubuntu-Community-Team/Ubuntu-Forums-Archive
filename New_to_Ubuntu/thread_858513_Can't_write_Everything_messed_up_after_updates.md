---
title: "Can't write? Everything messed up after updates"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by disappearedng on 2008-07-13
Hi everyone
I recently made an update, and everything failed terribly. Most of my applications can't work. I read up and realized that when my harddisk is corrupted, the drive is only mounted as read-only. When I run most of my applications using root privileges, they do work. Now my question is:

How do I diagnose this?
Do I use fsck?
How do I uninstall updates?

Hardy is REALLY BUGGY compared to Gusty.

---

### Post by unutbu on 2008-07-13
Please describe in more detail how your system is failing.

When you boot up, how far do you get before there are problems? 

Did the problem begin after upgrading from Gutsy to Hardy, or after a Hardy update?

If you can boot into Recovery mode without any problems, then I don't think you need fsck. 

Do you want to backup your data and reinstall Gutsy, or do you want to try and fix Hardy?

There is no good way to downgrade packages. (There is a way to force the installation of old versions of packages, but I'm told it can make your system unstable.)

---

