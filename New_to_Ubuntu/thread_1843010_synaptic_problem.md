---
title: "synaptic problem"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by mahir28 on 2011-09-12
i recently installed ubuntu 11.04 and while installing it couldnt complete it properly.And now everytime i try to install anything or search for any software, synaptic shuts down. 
ERROR MESSAGE:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

; 
im still a noob at this, so please help.](*,)

---

### Post by Off Shore on 2011-09-12
Sounds as if you are having some problems.
You say you couldnt complete the install?

---

### Post by audiomick on 2011-09-12
> **mahir28 said:**
> i recently installed ubuntu 11.04 and while installing it[COLOR=Red] couldnt complete it properly.[/COLOR]

Why not? What happened?

---

### Post by XubuRoxMySox on 2011-09-12
It's rare, but it could be a network issue, where the installation depends in part upon getting packages over the Internet from a server that was temporarily down.

*IF* you are sure that the LiveCD is good (a "bad burn" can cause problems, MD5 sum checks out), simply wait awhile and try it again later. Installation usually requires a good internet connection to finish the process (network servers for time and date settings, setting up the updater, etc). Rarely, a server will be down or just busy.

---

### Post by Rubi1200 on 2011-09-13
Hi and welcome to the forums mahir28 :)

Open a terminal with Ctrl+Alt+T and copy/paste the following commands and then Enter after each one:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```
The first command removes corrupted package lists, the second refreshes them.

Let us know if this helps.

---

### Post by mahir28 on 2011-09-13
trying your solution right now
HOPE THIS WORKS.#-o

---

### Post by mahir28 on 2011-09-14
thanks rubi1200 ,
it worked 
and now everything runs flawlessly.
Another thing, 
how to automount hard drives??

---

### Post by Rubi1200 on 2011-09-14
Excellent! I am really glad this worked out for you :-)

---

### Post by Elfy on 2011-09-14
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

They need to be added to the fstab file.

---

