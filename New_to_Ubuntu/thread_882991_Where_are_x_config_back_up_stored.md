---
title: "Where are x config back up stored"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by SandyM on 2008-08-07
I need to restore my X config from earlier back up but don't know where these back ups are stored and how can i restore them.

---

### Post by hotstovejer on 2008-08-07
Xorg configs are stored in /etc/X11 in a file called xorg.conf

Did you make changes to your xorg.conf? If you did by using ```
sudo dpkg-reconfigure xserver-xorg
``` then there would have been a backup with the file of xorg.conf.dateandtimeofbackup.

---

### Post by overdrank on 2008-08-07
> **SandyM said:**
> I need to restore my X config from earlier back up but don't know where these back ups are stored and how can i restore them.
Thread closed duplicate [[COLOR="DarkRed"]Here[/COLOR]](http://ubuntuforums.org/showthread.php?t=882901)
Again, :( Please do not create multiple threads on the same issue.

---

