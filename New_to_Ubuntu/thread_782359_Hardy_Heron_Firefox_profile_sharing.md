---
title: "Hardy Heron Firefox profile sharing"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by flamingsole on 2008-05-04
Hello,

When I was running Feisty and Gutsy, I could open up the Firefox profile manager, and select my Firefox profile that resides on another partition (where Windows can share it) for Ubuntu to use. I did this upon upgrading to Hardy Heron, and everything worked. But now, every time I shut down my system, or log out and log back in, Firefox refuses to start until I delete the .mozilla folder under /home. It gives me an error message that says that Firefox is already running.

Is there something I need to do to get Ubuntu to understand my Firefox profile? It does not have this issue in opening the Thunderbird profile. I even tried downgrading to Firefox 2, in case that was an issue, but it does not appear to be relevant.

Any thoughts?
Thanks,
Jon

---

### Post by riven0 on 2008-05-05
Perhaps Firefox really is running. Next time you get that error, try running this command: **ps aux | grep firefox***

If it's running it will give you something like this: 

> yourusername **29670**  4.6 27.6 277060 142728 ?  Sl 11:24  27:02 /usr/lib/firefox-3.0b5/firefox

The number in bold is the PID; you'll want to terminate it:

**sudo kill -s 15 *thepidnumber***

or

**sudo kill -9 *thepidnumber***

Then try running Firefox again. If it runs without giving you that "already running" error, it means there is something wrong with the way Firefox has been exiting. You may want to do a complete uninstall and re-install of Firefox.

---

### Post by flamingsole on 2008-05-05
It turns out that the issue was with the mounted drive that held the Firefox profile data. Apparently, Firefox gave the already open message because it couldn't access the drive. I needed to edit /etc/fstab:
```
/dev/sda5 /media/shared vfat defaults,umask=0700 0 0
```
Thanks,
Jon

---

