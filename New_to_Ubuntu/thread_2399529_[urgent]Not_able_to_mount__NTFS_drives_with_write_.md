---
title: "[urgent]Not able to mount  NTFS drives with write permission"
date: 2018-08-26
forum: New to Ubuntu
---

### Post by shubhamraj1in on 2018-08-26
I am not able to mount my two ntfs drive partitions with read and write permission.
They are mounting only as read only.
I have changed my /etc/fstab also, but no success.

---

### Post by bijayalaxmi1808 on 2018-08-27
I think you should check this thread out for a possible solution:
[https://ubuntuforums.org/showthread.php?t=1878229](https://ubuntuforums.org/showthread.php?t=1878229)

---

### Post by bijayalaxmi1808 on 2018-08-27
By the way what error are you getting? any trace of the error please?

you can have a screenshot or just the error message which will help to find you a solution.

---

### Post by Impavidus on 2018-08-27
Have you got Windows 8 or 10? Have you disabled Fast Startup in Windows? Fast Startup makes it look like Windows boots fast, but actually it doesn't fully shut down. In that state Ubuntu cannot write to the Windows file systems. Even if you disabled Fast Startup, updates to Windows may enable it again.
[https://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](https://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)

---

### Post by mahardi-baniadam on 2018-08-28
please share your fstab config

> cat /etc/fstab

---

