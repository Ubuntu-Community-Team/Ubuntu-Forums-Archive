---
title: "[SOLVED] Adding Launchpad repositories"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-07-20
I have searched around and could not find any information on this subject.  If anyone could tell me how to add these repositories to my Hardy 8.04 repository list I would appreciate it.

Donald Saunders
Alienexplorers

---

### Post by tuxxy on 2008-07-20
System > Administration > Software Sources > Third Party

---

### Post by tjwoosta on 2008-07-20
System-Administration-Software Sources

click the third party software sources tab and click add

(damn he beat me to it):)

---

### Post by iaculallad on 2008-07-20
> **alienexplorers said:**
> I have searched around and could not find any information on this subject.  If anyone could tell me how to add these repositories to my Hardy 8.04 repository list I would appreciate it.

Donald Saunders
Alienexplorers

Would that be:

```
gksudo gedit /etc/apt/sources.list
```

and insert:

> deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) hardy main

HTH

---

### Post by alienexplorers on 2008-07-21
I thought there were more launchpad repositories than the one listed.  Does any one know all of them.

---

### Post by Oldsoldier2003 on 2008-07-21
> **alienexplorers said:**
> I thought there were more launchpad repositories than the one listed.  Does any one know all of them.


Statistics

    * 3298 registered PPAs
    * 907 active PPAs
    * 4948 published sources
    * 22331 published binaries

Every launchpad member could have a PPA if they choose so its really impractical to expect that every PPA would be listed or useful to everyone.

---

### Post by GregTheGerg on 2009-09-14
I have kind of a similar question. 

I think what he was trying to get at was the *entire* launchpad repo. 

I would also like the same thing if you could help. 

Thanks! ^_^

---

