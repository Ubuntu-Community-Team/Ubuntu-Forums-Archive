---
title: "Errors when upgrading librsvg to the version 2.34.0"
date: 2011-05-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-25
You may very well get the following error when upgrading the librsvg package set to the version 2.34.0

```

/var/lib/dpkg/info/librsvg2-common.postinst: 6: dpkg-architecture: not found
dpkg: error processing librsvg2-common (--configure):
 subprocess installed post-installation script returned error exit status 127

```

The same error is evident also when upgrading the gdk-pixbuf package set to the version 2.23.3

This will lead both librsvg2-common and libgdk-pixbuf2.0-0 installation not to finish completely.

Here is the bug report on this issue:
[https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/788115](https://bugs.launchpad.net/ubuntu/+source/librsvg/+bug/788115)

---

### Post by Quackers on 2011-05-26
Is this version 2.34.0-0ubuntu5?
All the updates ran fine here (I'm on 64 bit).
That's librsvg2-2, librsvg2-bin and librsvg2-common all on the new version here.
Synaptic reports that I have no broken packages.

---

### Post by Harry33 on 2011-05-26
> **Quackers said:**
> Is this version 2.34.0-0ubuntu5?
All the updates ran fine here (I'm on 64 bit).
That's librsvg2-2, librsvg2-bin and librsvg2-common all on the new version here.
Synaptic reports that I have no broken packages.

This bug is now fixed with the latest update (2.34.0-0ubuntu5).

---

### Post by Quackers on 2011-05-26
Thanks. That would explain it then :-)

---

