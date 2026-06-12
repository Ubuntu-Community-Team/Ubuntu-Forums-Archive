---
title: "installation problem"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by sjparida on 2011-09-17
i have just installed ubuntu 11.04 ,the problem is that whnever i used to add a ppa from command line its giving this error
----------------------------------------------------------------------------------------------------------------------------------
"sjparida@GASSP:~$ sudo add-apt-repository ppa:cairo-dock-team/ppa
[sudo] password for sjparida: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4E6B5E978E5D9070EBC365BA7274A4DAE80D6BF5
gpg: requesting key E80D6BF5 from hkp server keyserver.ubuntu.com
gpg: key E80D6BF5: "Launchpad cairo-dock" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
---------------------------------------------------------------------------------------------------------------------------------
please help me how can i add repo to install apllications

---

### Post by anewguy on 2011-09-17
If it's cairo-dock you're after, why not just use synaptic package manager to get it?

What have you done in terms of other keys, other packages, etc.?

Dave ;)

---

### Post by TeoBigusGeekus on 2011-09-17
Someone correct me if I'm wrong, but I think you've succeeded adding the ppa.

---

### Post by gandaran on 2011-09-17
if that didn't work try the other way, follow the first instructions
[https://launchpad.net/~cairo-dock-team/+archive/ppa](https://launchpad.net/~cairo-dock-team/+archive/ppa)
if you still get the key server error you can copy/paste the key file in the same web page and install manually.

---

### Post by sjparida on 2011-09-17
thanks anewguy for such a great response, when i tried to open synaptic package manager its shows me this error
----------------------------------------------------------------
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
------------------------------------------------------------------
also thnks 2 you gandaran -- i give a try to your method but it doesn't seems to be working

---

### Post by wildmanne39 on 2011-09-17
Hi, this should fix that issue.
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```
Thank you

---

### Post by Krytarik on 2011-09-17
Anyway, the Oscar goes to *TeoBigusGeekus*, for delivering the only fitting answer in this thread! =D> Up until the additional issue, of course.
> **TeoBigusGeekus said:**
> Someone correct me if I'm wrong, but I think you've succeeded adding the ppa.
Btw., the PPA has been added at least one time before successfully.

---

### Post by anewguy on 2011-09-18
But again, why?  It's in the package manager - why go to all that extra trouble?

---

### Post by Krytarik on 2011-09-18
> **anewguy said:**
> But again, why?  It's in the package manager - why go to all that extra trouble?
As it turned out, the OP currently has a general issue with the package manager, regardless if the PPA is involved or not. So, +1 for *wildmanne39*'s suggestion.

---

