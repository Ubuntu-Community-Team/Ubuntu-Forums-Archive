---
title: "Wicd hosed my system"
date: 2018-06-30
forum: New to Ubuntu
---

### Post by Douglas_White on 2018-06-30
Was having some connection and throughput issues on my machine. 

Doing some research seemed Wicd was a better choice for network management than Network Manager
so, went and installed it.

Made connecting to my network difficult.
Killed the connection to my Windows 10 SMB server

Finally just bit the bullet and re-installed.

Network connection is easier and better.
Gnucash still cannot get a lock on the file on my Win 10 server and I cannot save changes.
Had to re-install Wine now my Windows based CAD program doesn't work anymore.

Be careful what you install.

Just had to vent. Sorry.

All the Best,
D. White

---

### Post by TheFu on 2018-07-01
> **Douglas_White said:**
> Was having some connection and throughput issues on my machine. 

Doing some research seemed Wicd was a better choice for network management than Network Manager
so, went and installed it.

Made connecting to my network difficult.
Killed the connection to my Windows 10 SMB server

Finally just bit the bullet and re-installed.

Network connection is easier and better.
Gnucash still cannot get a lock on the file on my Win 10 server and I cannot save changes.
Had to re-install Wine now my Windows based CAD program doesn't work anymore.

Be careful what you install.

Venting is good sometimes. Therapeutic.

Just restore from the backup you made before performing risky things.
wicd isn't necessarily "better" for everyone. I use it, but only for wifi connections and only outside the 2 normal networks that I use.  My networking needs are more complex than most and wicd lets me have easier control.  NM was getting confused, always, so for my needs, it was easier to just purge it and manually control networking.

Locks over CIFS are prone to failures. I'd script a copy-over, use, copy-back solution if you want to leave the data on Windows.  Personally, I don't leave anything important on Windows, but that is a comfort thing.  I prefer Linux-based storage.

---

