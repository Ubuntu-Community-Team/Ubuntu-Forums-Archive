---
title: "Do I need to turn Ext4 journaling off on a MSSD Hard Drive?"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by Lee_Duckett on 2014-01-31
Hi, 

I am a newbie to the forum.

I have just assembled an XBMC HTTPC using an Intel NUC which has a MSSD 60Gb Hard Drive.

I am using XBMC Buntu as the OS and have just upgraded the Kernal from 3.5 to 3.13RC1 to get my [COLOR=#333333]Intel Dual Wireless AC760 Card to work and the associated driver after much searching on the web.
[/COLOR]
[http://wireless.kernel.org/en/users/Drivers/iwlwifi#git_repositories](http://wireless.kernel.org/en/users/Drivers/iwlwifi#git_repositories)

[http://www.bestubuntu.com/install-linux-kernel-3-13-1-rc1-in-ubuntu-13-10-13-04.html](http://www.bestubuntu.com/install-linux-kernel-3-13-1-rc1-in-ubuntu-13-10-13-04.html)

Do I need to turn off the journaling on the MSSD Hardrive to guard against it wearing out prematurely?

If so what commands do I use? 

Can you please explain

Thanks

---

### Post by tgalati4 on 2014-01-31
It can reduce wear.  If this is a multimedia display box then your risk of losing important data is low, so you can turn off journaling.

```
man tune2fs
```

Proceed carefully.

[http://askubuntu.com/questions/76913/how-can-i-check-if-a-particular-partition-ext4-is-journaled](http://askubuntu.com/questions/76913/how-can-i-check-if-a-particular-partition-ext4-is-journaled)

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

---

### Post by Lee_Duckett on 2014-01-31
Thanks for the help. If I need to do it for the partitions what's the best way to proceed? 
Thanks

---

