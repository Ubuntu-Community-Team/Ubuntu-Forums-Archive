---
title: "Not able to mount other partitions"
date: 2011-09-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by adit on 2011-09-17
Apart from the partition in which I installed ubuntu, I could not mount any other partition.  When I try to mount by clicking an item in 'Places' Side Pane in nautilus, I get this dialog box.  See screenshot.
I am the owner and only user of this computer.

---

### Post by sanderd17 on 2011-09-17
There are other distros too where only root can mount filesystems.

Open nautilus as root and it will work:

```

gksudo nautilus

```

This will probably be fixed in the final release.

---

### Post by sonicb00m on 2011-09-17
Had this problem too with latest updates. I think it's related to lighdm. I purged lightdm and installed gdm and it seems to have fixed my problem.

---

### Post by philinux on 2011-09-17
> **adit said:**
> Apart from the partition in which I installed ubuntu, I could not mount any other partition.  When I try to mount by clicking an item in 'Places' Side Pane in nautilus, I get this dialog box.  See screenshot.
I am the owner and only user of this computer.

Yep. Same here. Gksu nautilus no good either as it can't see my other hard drive.

---

### Post by RomeReactor on 2011-09-17
Make sure you have the latest (0.9.7-0ubuntu1) version of LightDM; version 0.9.5-0ubuntu2 was the one [causing this problem]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851055").

EDIT: Although according to the [last comment]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/851055/comments/18") of the bug report, it may still affect some users.

---

