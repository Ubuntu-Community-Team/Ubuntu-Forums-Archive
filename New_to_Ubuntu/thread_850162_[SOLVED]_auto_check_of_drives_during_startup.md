---
title: "[SOLVED] auto check of drives during startup"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by adamogardner on 2008-07-05
after every number of times that I start up, Ubuntu checks drives in /dev/sda for about five minutes.  My questioin is how do I make it do that before shutdown, rather than boot?  I'm more inclined to want to wait for the service at the end of my user session than before.

---

### Post by silkstone on 2008-07-05
As far as I know, you can't do a check at the end of a session - it has to happen at the start. However, you can force a check the next time you reboot...

```
sudo touch /forcefsck
```

... and then restart the machine so it does this.

---

### Post by brian_p on 2008-07-05
> **adamogardner said:**
> after every number of times that I start up, Ubuntu checks drives in /dev/sda for about five minutes.  My questioin is how do I make it do that before shutdown, rather than boot?  I'm more inclined to want to wait for the service at the end of my user session than before.

Googling 'fsck shutdown' will get you some, but maybe not all, information. A relevant Ubuntu thread for you is:

[http://ubuntuforums.org/showthread.php?t=605748](http://ubuntuforums.org/showthread.php?t=605748)

---

