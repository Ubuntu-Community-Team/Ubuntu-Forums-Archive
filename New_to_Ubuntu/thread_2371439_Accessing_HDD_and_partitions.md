---
title: "Accessing HDD and partitions"
date: 2017-09-14
forum: New to Ubuntu
---

### Post by maxman2 on 2017-09-14
Vbox virtualization on Win10 64bit,12gb ram, 2 tb hdd. Using ubuntu in Try mode, cannot access HDD partitions- setup Admin user and/or guest user there is function via Users.

Firefox accesses the internet, but don't see software updates installed-system seems to hang when selecting to install updates.

As a new user trying to figure out if these issues are due to not Installing Ubuntu as a standalone OS?

Any assistance will be appreciated.

Thank you.

---

### Post by oldfred on 2017-09-14
Linux NTFS driver will not mount hibernated nor NTFS needing chkdsk to prevent damage or data loss.
If Windows 8 or 10:
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

If not a full install, but in live mode it is just like a DVD read only or you cannot update it.
You can have a live installer on flash drive with some extra space or persistence, so you can save your data. But that still does not let you update system. If you download an app, it will save it, but each time you reboot you have to reinstall.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) 

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by Dennis N on 2017-09-14
> **maxman2 said:**
> Vbox virtualization on Win10 64bit,12gb ram, 2 tb hdd. **Using ubuntu in Try mode, cannot access HDD partitions**- setup Admin user and/or guest user there is function via Users. Firefox accesses the internet, but don't see software updates installed-system seems to hang when selecting to install updates. As a new user trying to figure out if these issues are due to not Installing Ubuntu as a standalone OS? Any assistance will be appreciated. Thank you.

If Ubuntu in "Try" mode is running in virtual box, you can't see the partitions on the "real" hard drive - only the virtual one. It's an isolated system. When running the Ubuntu live media, your live session user already has admin. privileges. You should be able to install software to test without using sudo and without giving a password (just **apt install program-name** is enough). But, any software installed or any updates in the "try Ubuntu" session are lost when you quit the session.

---

