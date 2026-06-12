---
title: "Can I download apps from Hardy....."
date: 2008-10-22
forum: New to Ubuntu
---

### Post by J03y on 2008-10-22
Is there a way to download applications from Ubuntu 8.04 to 7.10 w/o upgrading to 8.04 using synaptic? Like changing the sources list or something? If its possible then please tell me if its safe or not.

# Wait never mind, sorry about making this thread. You can let it die now.

---

### Post by kellemes on 2008-10-22
> **J03y said:**
> Is there a way to download applications from Ubuntu 8.04 to 7.10 using synaptic? Like changing the sources list or something? If its possible then please tell me if its safe or not.

You can change the sources but it is **not safe**.
Is a distribution upgrade no option?

---

### Post by oskar2000 on 2008-10-22
possible: yes
safe: no

The problem is that a simple installation can result in a partial upgrade that can ruin your system. For example FF3 will need the new GTK, which might break a lot of other apps. If you leave the Hardy repo in, you will effectively get a system upgrade with the next update.

---

### Post by oskar2000 on 2008-10-22
> **kellemes said:**
> Is a distribution upgrade no option?
Wouldn't necessarily recommend that if 7.10 runs fine. Hardy broke a lot of hardware compatibility for me and a bunch of other people.



What do you want to install... maybe there are packages for Feisty out there.

---

### Post by Kilobyte on 2008-10-22
> **J03y said:**
> Is there a way to download applications from Ubuntu 8.04 to 7.10 w/o upgrading to 8.04 using synaptic? Like changing the sources list or something? If its possible then please tell me if its safe or not.

It is possible, but I would advise against it.
May I ask why you don't upgrade to 8.04?

---

### Post by tom56 on 2008-10-22
Enable the backports repo in System -> Administration -> Software Sources

---

