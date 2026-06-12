---
title: "freeze on shutdown"
date: 2012-05-13
forum: New to Ubuntu
---

### Post by werty2010 on 2012-05-13
i'm on ubuntu 12.04 and i installed the latest stable version of virtualbox through the official site and after a few days,i've been facing this problem: 
whenever i choose to shutdown(via gui), it starts the process by showing the ubuntu logo,then showing some lines in "terminal" mode and after a line which is about like this:
```
Stopping virtualbox kernel modules                                   
```
...the system freezes.
 any help would be appreciated?

---

### Post by anewguy on 2012-05-13
Do you have virtualbox running (not necessarily an OS running in it, just virtualbox itself - the GUI) when you go to shutdown?  If so, try closing out virtualbox completely before you shutdown, then try the shutdown and post back what happens.  We may be able to find a work around.

Dave ;)

---

### Post by werty2010 on 2012-05-13
> **anewguy said:**
> Do you have virtualbox running (not necessarily an OS running in it, just virtualbox itself - the GUI) when you go to shutdown?  If so, try closing out virtualbox completely before you shutdown, then try the shutdown and post back what happens.  We may be able to find a work around.

Dave ;)

ive already done that
the same thing happens even when i haven't run virtualbox at all

---

### Post by sammiev on 2012-05-13
If you are using wireless internet try wired to see if it makes a difference. Wireless works great on my system but is slow to shut off or locks up. Wired has no issues, shuts down in 5 seconds.

---

### Post by Lisiano on 2012-05-13
Hmm. If you try to shutdown using ```
sudo shutdown -h now
``` does it still hang on virtualbox?

---

### Post by anewguy on 2012-05-17
If worse comes to worse:

- download the latest virtualbox from the Oracle site
- backup your current vm's
- remove the old virtualbox

At this point I would reboot, then try to shutdown - if it still doesn't work there are other problems.

Next:

- install the latest virtualbox
- restore your vm's
- try again

Also, to shutdown completely from terminal:  sudo shutdown -P now  => that should shutdown and power-off your PC *if* the -h (halt) option recommended by Lisiano above doesn't power off your system after shutting down Ubuntu (the way some power options work on some PC's the -h doesn't always power off).

Dave ;)

---

### Post by werty2010 on 2012-05-17
thank you all
from the beginning i had the  latest version of virtualbox
after a few updates,a few days ago, for a reason i dont know, now most of the time shuts down ok

---

### Post by 99sono on 2012-10-14
i have got the exact same problem and I am using the latest version of virtual box:
virtualbox-4.2_4.2.0-80737~Ubuntu~precise_amd64.deb

just installed this package and now shutdown never finishes with the message posted by the first poster of this thread.

---

### Post by adojaan on 2012-10-14
Installed latest virtualbox-4.2_4.2.0-80737~Ubuntu~precise_amd64.deb

Now cannot reboot, cannot even uninstall virtualbox. Cannot lsmod. If I try to uninstall or stop vboxdrv 
 * Stopping VirtualBox kernel modules  
will be displayed and nothing else happens.
Cannot Ctrl-C or cannot kill -9 lsmod.
Nothing in syslog or kern.log
My system: Linux meriroos 3.4.0-030400-generic #201205210521 SMP Mon May 21 09:22:02 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

---

