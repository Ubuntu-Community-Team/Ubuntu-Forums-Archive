---
title: "USB External Drive"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2008-11-04
Since my 8.10 Upgrade, my USB external drive won't open.

If I do Places> Computer> the drive is there but it can't mount it.

Can anyone help? It's was working with 8.04.

---

### Post by vitaraq1962 on 2008-11-04
I had this once and i found that the permissions on the usb disc had changed back to root. What i did was to open nautilus in sudo mode ie sudo nautilus then navigate to the usb drive and change the permissions. This worked for me, so i hope it helps you.
Gaz.):P

---

### Post by wizard10000 on 2008-11-04
> **GaryLittlemore said:**
> Since my 8.10 Upgrade, my USB external drive won't open.

If I do Places> Computer> the drive is there but it can't mount it.

Can anyone help? It's was working with 8.04.

Grumbling yet again  ;)

I had the same problem with an 8.04 --> 8.10 upgrade.  policykit removed the right for normal users to mount external drives.  It's easy to fix once you know what to look for - look in System --> Administration --> Authorizations.  You'll see it.

Are you listening, Ubuntu developers?  Please don't change system policies during an upgrade  ):P

---

