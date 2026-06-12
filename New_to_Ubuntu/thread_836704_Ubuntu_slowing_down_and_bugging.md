---
title: "Ubuntu slowing down and bugging"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Bigbob22 on 2008-06-21
I got Ubuntu 3 weeks ago and instantly fell in love, but in the past week its been slow and some programs (opera, amarok) crash. I thought it was a virus (even though ubuntu is very secure) but AVG did not detect anything. I already cleaned out junkfiles by using [this file]("http://ubuntuforums.org/showthread.php?t=140920&highlight=cleaner"), but it still seems buggy. What should I do?

---

### Post by Xerp on 2008-06-21
You are correct, it is not a virus. Check the output from "top" - this will enable you to see your processor and memory usage. Your logfiles - /var/log/syslog and /var/log/messages - will enable you to see if something is reporting a problem.

---

### Post by Bigbob22 on 2008-06-21
I used Htop and it everything running looks fine.

---

### Post by nowshining on 2008-06-22
u can also try kleansweep in the repos to clean up stuff such as tmp .backup files, etc.. just be careful. However by default it asks u to create an archive - if u go root, if u press the home buttom u get the /root/ home folder, etc.. so the backup is just in-case something happens.

---

### Post by _sphinx_ on 2008-06-22
So you are saying that ubuntu was running with fine speed in first two weeks but in the last week it is slow. If it is true so don't you remember doing anything messy with this stuff??

---

### Post by Victormd on 2008-06-22
This usually happens to me after a tweaking session gone bad (without me knowing it... hehehe)
Here are a few things you might want to do:
```
sudo apt-get autoremove
```
This will remove any unecessary packages (i.e., dependencies that are no longer needed from programs that have been removed)
```
sudo apt-get autoclean
```
or
```
sudo apt-get clean
```
These will clean your HD from downloaded packages that are kept in cache (if you run these and need to re-install a package, it will simply download from the repositories instead of installing from cache)

---

### Post by Bigbob22 on 2008-06-23
well its not really slow its just mainly buggy. Like firefox, opera, amarok and other programs keep on not responding randomly so I have to force quit it.

---

### Post by Bigbob22 on 2008-06-23
> **nowshining said:**
> u can also try kleansweep in the repos to clean up stuff such as tmp .backup files, etc.. just be careful. However by default it asks u to create an archive - if u go root, if u press the home buttom u get the /root/ home folder, etc.. so the backup is just in-case something happens.
Is it okay to delete all the orphaned files or will that mess up my computer?

---

### Post by nowshining on 2008-06-23
u can try - but i don't know i've stuck with backup files & dead menu stuff, however the deadmenu u still gotta be careful. I consider backup files, tmp, ~, and .save the safest to remove. Deadmenu entries just below remove tmp, backup, etc.. - the rest I consider very risky - on orphans i took a try, but seeing too much stuff in there that might too risky unless u really know what ur doing, however if u go ahead and try use the backup file it created - u need to manually restore however it shows what folder each go in, ie: when u untar the file it will be in diff. sections, so restore is easier.

I also suggest going into the settings and making if not there /media/ an' ignore path.

---

### Post by Bigbob22 on 2008-06-23
> **nowshining said:**
> u can try - but i don't know i've stuck with backup files & dead menu stuff, however the deadmenu u still gotta be careful. I consider backup files, tmp, ~, and .save the safest to remove. Deadmenu entries just below remove tmp, backup, etc.. - the rest I consider very risky - on orphans i took a try, but seeing too much stuff in there that might too risky unless u really know what ur doing, however if u go ahead and try use the backup file it created - u need to manually restore however it shows what folder each go in, ie: when u untar the file it will be in diff. sections, so restore is easier.

I also suggest going into the settings and making if not there /media/ an' ignore path.

Thanks. It didn't fix the bugging and crashes but freed room.

---

