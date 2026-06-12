---
title: "/etc/hostname and /etc/hosts files are out of sync and I don't know what to do.  Help"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by Paper Pusher on 2011-11-15
Here is the sequence of events as I remember it.

0. I'm on Ubuntu 11.4 and life is good.
1. I “upgrade” to 11.10 and all hell breaks loose.  There are a number of  bugs in 11.10 and I fix them one by one.  My final bug is that I can't see my NAS drives.
2. I start to apply fix 
[http://ubuntuforums.org/showthread.php?t=1861985](http://ubuntuforums.org/showthread.php?t=1861985)
3. I notice that the fix requires host names less than 15 characters and that my host name (picked by Ubuntu) is 22 characters long.
4. I edit the /etc/hostname file to shorten the host name as the NAS fix requires.  But I forget to edit the /etc/hosts file. The etc/hosts file continues to contain the old longer host name.
5. Now my prompt in terminal shows the new short host name.
6. But when I now type “sudo”, it gives  me the “unable to resolve host” error.                                                                                                                                                                                                                    Help.

---

### Post by anewguy on 2011-11-15
You did reboot after editing the hostname file, correct?

Dave ;)

---

### Post by dwasifar on 2011-11-15
Boot from a live CD, mount your hard drive to /media, and edit /media/etc/hosts as root.  Save and reboot.

---

