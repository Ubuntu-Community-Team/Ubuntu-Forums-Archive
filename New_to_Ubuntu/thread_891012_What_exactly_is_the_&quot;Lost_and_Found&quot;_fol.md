---
title: "What exactly is the &quot;Lost and Found&quot; folder?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Fzang on 2008-08-15
I can't access it and it's named Lost and Found.... 

I can't stand the curiosity!

---

### Post by Gannon8 on 2008-08-15
I was about to ask this :)
I think it is a special directory for the ext line of filesystems, because my Ubuntu OS is on an xfs filesystem and does not have it.

---

### Post by moore.bryan on 2008-08-15
afaik, it's part of the journaling function of ext3 filesystems and i don't think one would ever need direct-access to whatever would be in it.

---

### Post by Gannon8 on 2008-08-15
A quick Google finds something:
> Linux should always go through a proper shutdown. Sometimes your system might crash or a power failure might take the machine down. Either way, at the next boot, a lengthy filesystem check (the speed of this check is dependent on the type of filesystem that you actually use. ie. ext3 is faster than ext2 because it is a journalled filesystem) using fsck will be done. Fsck will go through the system and try to recover any corrupt files that it finds. The result of this recovery operation will be placed in this directory.
Found at [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by bobnutfield on 2008-08-15
Have a look at this:

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html]("http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html")

---

### Post by drs305 on 2008-08-15
The 'lost+found' folder is in each partition and is where fsck places corrupt files (bits & pieces) it finds during it's checks. The idea is that there may be some recoverable data which you might be able to find and restore within the bits & pieces. Fsck leaves them in the 'lost+found' folder for you to inspect and/or manually delete.

---

### Post by Too Late on 2008-08-15
In my opinion, Nautilus should hide that folder by default.

---

### Post by Fzang on 2008-08-15
But if it places corrupt files inside lost+found thinking we might be able to recover it, how come we don't have access to the folder?

---

### Post by drs305 on 2008-08-15
> **Too Late said:**
> In my opinion, Nautilus should hide that folder by default.

I would prefer it be hidden as well. As a workaround, you can hide the 'lost+find' folder by creating a file in the same directory called '.hidden'. Open the file and type *lost+found*.

Any file or folder listed in the .hidden text file will not be displayed if nautilus is set to hide all hidden files.

---

