---
title: "[SOLVED] cleaning out your temp or swap files?"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by brhartin on 2008-10-24
Is there a way of doing this on 804 like cleaming out your XP %TEMP% folder ...or a progie that does this simular to CCleaner ...it seems my filesystem drive is growing slowly but am not sure how?

---

### Post by LowSky on 2008-10-24
open a terminal
sudo apt-get autoclean
or
sudo apt-get clean

---

### Post by cariboo on 2008-10-24
/tmp  gets cleaned out every time you shutdown. The commands the pp posted only clean out /var/cache/apt/archives and remove obsolete or auto removable programs. To clean out Firefox's temporary cache in Firefox go to Tools-->Clear Private Data. Linux cleans out temporary data, not like that other os that starts with W. :)

Jim

---

### Post by jerome1232 on 2008-10-24
Well systems do tend to slowly get bigger as you add programs and media to it. 

The first thing I can think of that tends to get looked over is when you install a program then remove, it's settings get left behind (usually a few text files) not big space eaters, it's done this way so that you can remove a program without losing the settings for it.

If you want to clear out settings when you remove programs either mark them for complete removal in synaptic, or use the -purge option from the command line ie:
```
sudo apt-get remove --purge appnamehere
```

The other thing that tends to grow is /var where your logs are kept, they get rotated and compressed but they still eat up ~3 GB on my old system, it has alot of cruft in those logs from some reporting apps i've installed (like 641 messages in system mail which is kept in /var as well)

---

### Post by bodhi.zazen on 2008-10-24
In general Linux does not need to be "cleaned" the same way as Windows.

With that said, take a look at these links :

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

    [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

    [http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html](http://ubuntu-tutorials.blogspot.com/2007/01/cleaning-up-ubuntu-gnulinux-system.html)

I would advise you read and understand what those command s are doing as if you make a mistake you can (rarely) damage your system.

---

### Post by Kellemora on 2008-10-24
Hi BRH

Don't forget to empty your TRASH Cans, there are a few to look for, some hidden as /.trash like in /root.

TTUL
Gary

---

### Post by oldos2er on 2008-10-24
> **brhartin said:**
> Is there a way of doing this on 804 like cleaming out your XP %TEMP% folder ...or a progie that does this simular to CCleaner ...it seems my filesystem drive is growing slowly but am not sure how?

 Everything in /tmp is deleted on reboot.

---

### Post by brhartin on 2008-10-26
I think it could be PAN the news reader i'm using not sure if the progie is like outlook exp in reguards to a maintance file that resets/removes downloaded files "IF" they are not going in the temp folder ...but i will do as described above...THANK YOU ALL.

---

