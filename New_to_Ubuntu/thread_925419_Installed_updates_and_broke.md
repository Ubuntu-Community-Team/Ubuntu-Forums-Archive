---
title: "Installed updates and broke"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by crazyclown on 2008-09-20
I installed an update yesterday, and it broke stuff.  I mean I can not right click on my desktop, or goto System Settings and select Display, and configure the screensaver, background all of that.  

I restarted my computer and it worked until the screensaver came on.  Then again right click on the desktop and SS -> Display is not working.  So I decided to run ClamAV.  I scanned my home folder and found nothing, so I scanned the entire filesystem and found two viruses.  ClamAV did not say what they were.  

Only Ubuntu is installed on this HDD and the wifes Windows machine is seperated by a router.

Sadly I can't remember what was updated.  How do I find this out? How do I find out what ClamAV found?

---

### Post by vikram on 2008-09-20
In a terminal (Kmenu->System->Konsole) type

tail /var/log/dpkg.log

this will give you the last few updates on your system.

If you can't get to the desktop  you can boot into the recovery console and type these commands. try dpkg-reconfigure of the broken packages or use the ncurses (command line) tool called aptitude to reverse the broken updates.

---

### Post by crazyclown on 2008-09-20
Thanks, I did the update and it installed rdesktop
```

2008-09-19 19:18:26 status unpacked rdesktop 1.5.0-3+cvs20071006
2008-09-19 19:18:26 status half-installed rdesktop 1.5.0-3+cvs20071006
2008-09-19 19:18:26 status half-installed rdesktop 1.5.0-3+cvs20071006
2008-09-19 19:18:26 status unpacked rdesktop 1.5.0-3+cvs20071006ubuntu0.1
2008-09-19 19:18:26 status unpacked rdesktop 1.5.0-3+cvs20071006ubuntu0.1
2008-09-19 19:18:27 startup packages configure
2008-09-19 19:18:27 configure rdesktop 1.5.0-3+cvs20071006ubuntu0.1 1.5.0-3+cvs20071006ubuntu0.1
2008-09-19 19:18:27 status unpacked rdesktop 1.5.0-3+cvs20071006ubuntu0.1
2008-09-19 19:18:27 status half-configured rdesktop 1.5.0-3+cvs20071006ubuntu0.1
2008-09-19 19:18:27 status installed rdesktop 1.5.0-3+cvs20071006ubuntu0.1

```

Now I just have to figure out why it is killing my display settings.

---

### Post by crazyclown on 2008-09-20
ClamAV finally finished a full running and found out viruses this time.
```

clamscan -irl ~/scan.txt /

```

---

### Post by vikram on 2008-09-20
just curious what was the name of virus ? Haven't heard of any virus for linux 'in the wild' as yet.

---

### Post by crazyclown on 2008-09-20
I used the GUI of ClamAV.  So it never did give the name, here does it store this information so that I can retrieve it in a CLI?

---

