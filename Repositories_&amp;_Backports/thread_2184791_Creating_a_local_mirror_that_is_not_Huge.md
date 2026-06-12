---
title: "Creating a local mirror that is not Huge"
date: 2013-10-30
forum: Repositories &amp; Backports
---

### Post by stevem2 on 2013-10-30
Is there a way to use apt-mirror or something similar to create a local repository that is not more than say 4 gigs?
I tried to use apt-mirror and I think it was over 11 gigs for just Ubuntu 13.04 64bit.
I want to use this as a base for my network installs.
I use to use the "alternate" ISOs, but they are no longer available after Ubuntu 12.04.

thank you

---

### Post by TheFu on 2013-10-30
Check out **apt-cache-ng** ... don't know if you can limit the size like you want - check the man page to see.

---

### Post by stevem2 on 2013-10-30
Yeah, I was looking into apt-cache as well. I will update this post if I make any progress. Correction, I was using debmirror to create the mirrors.

---

### Post by ian-weisser on 2013-10-31
I prefer a caching proxy.
Mirroring your local cache is attractive up front, but I find it requires more manual work later dealing with upgrades.

---

### Post by stevem2 on 2013-11-01
It it possible to cache enough packages to do a complete install of systems from the mini.iso?

---

### Post by ian-weisser on 2013-11-01
Sure it's possible.
You can mirror the entire set of Ubuntu repositories if you really want to. Of course, that will run a bit over your 4 gig limit.

---

