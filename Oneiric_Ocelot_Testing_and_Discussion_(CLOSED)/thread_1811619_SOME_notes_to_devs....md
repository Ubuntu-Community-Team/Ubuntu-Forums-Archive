---
title: "SOME notes to devs..."
date: 2011-07-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by forcecore on 2011-07-25
Please do not lock so many packages to others that removing some package causes autoremoving others( example: removing libedataserver terminated gnome or libunity4 removed empathy).

Some packages will need update too like n2n v2.

---

### Post by MacUntu on 2011-07-25
I suggest reading the header of this subforum. ;-)

If you feel that the dependencies of packages are wrong WRT the Debian Policy Manual [http://www.debian.org/doc/debian-policy/ch-relationships.html](http://www.debian.org/doc/debian-policy/ch-relationships.html) then file a bug report.

---

### Post by ranch hand on 2011-07-25
Yes, remember that this is the Official Ubuntu Forums, on Ubuntu Servers and therefore Ubuntu ignores anything said here.

We make up a small percentage of Ubuntu users.  Those users opinions need to be respected too,  Do not ask how Ubuntu knows what those opinions are.

---

### Post by jbicha on 2011-07-25
> **forcecore said:**
> Please do not lock so many packages to others  that removing some package causes autoremoving others( example: removing  libedataserver terminated gnome or libunity4 removed empathy).

Some packages will need update too like n2n v2.

Evolution-data-server is an essential part of Gnome.

Empathy needs the Unity libraries for its Unity launcher integration.  The libraries don't take up much space. If a little bit of Unity annoys  you then perhaps you should consider a non-Ubuntu distribution.

As far as I can tell, n2n has not released a stable version 2 yet. Nearly all of Ubuntu's software is maintained by Debian which highly values stability.

ranch hand, obviously, we don't ignore everything said here, although it would be helpful if you'd say something useful.

---

### Post by Mr. Picklesworth on 2011-07-25
> **forcecore said:**
> Please do not lock so many packages to others that removing some package causes autoremoving others( example: removing libedataserver terminated gnome or libunity4 removed empathy).

Some packages will need update too like n2n v2.

If you're particularly concerned about getting updates quickly, you might want to check if you're connecting to the main server for updates. It sometimes takes a while for the mirrors to get sorted, and that can result in more blocked updates than usual. (Of course, the main server won't be thrilled if everyone and their dog starts downloading updates from there). For what it's worth, there are many points this cycle where it doesn't hurt to run dist-upgrade (and make sure you aren't removing half the system); lots and lots of packages being switched over to differently named gtk3 versions.

---

