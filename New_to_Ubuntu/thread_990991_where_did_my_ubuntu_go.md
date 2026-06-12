---
title: "where did my ubuntu go?"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Mr. Bill on 2008-11-23
I tried to upgrade from 7.1 to 8.04.  It seemed to download ok but when it started to install it stopped at 
     generating locales
     en_AU.utf-8
it would not get past this point
now when i try to get back into 7.1 i get the username and password sign in but the desktop is blank no menu bars no time&date nothing!
what do i do

---

### Post by Michael.Godawski on 2008-11-23
It is never good when an upgrade or installation process was interrupted or terminated uncompleted. Many different things could gone awry. Difficult to tell.

Do you have any important data on the harddrive which you haven't backed up yet?
You can use the LiveCD to access the files.

It's always wise to create a backup before thinking about an upgrade.

---

### Post by xravexheavenx on 2008-11-23
I would back everything up with LiveCD and do a reinstall.

It is always a good practice to put /home in its own partition.
Or even better, another hard drive.

---

### Post by Victormd on 2008-11-23
I personally didn't have much luck upgrading through synaptic so now I always do a fresh install...
Use the live CD to backup any important data and do a fresh install of the version you want to keep...

---

### Post by kansasnoob on 2008-11-23
Upon reboot you could try going into a terminal session, or you might get to terminal by pressing Alt > F2 (and selecting run from terminal) and run this command:

```
sudo dpkg-reconfigure -phigh -a
```

Make sure you get it written down and typed in just right!

It will in my experience take at least an hour to run!

---

### Post by zvacet on 2008-11-23
@ **Mr. Bill**

Read [this]("http://ubuntuforums.org/showthread.php?t=865679&highlight=locales+error+upgrade") and maybe you find i helpful.I remember that was problem with upgrades and locales.If solution in thread doesn´t work for you search forums,because I remember that was problem with locales and upgrade.

---

