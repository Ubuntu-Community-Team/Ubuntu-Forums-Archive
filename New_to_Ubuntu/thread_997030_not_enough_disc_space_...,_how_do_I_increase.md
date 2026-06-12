---
title: "not enough disc space ..., how do I increase?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by gychang on 2008-11-29
Installed the 8.1 using Wubi, like the Linus very much.

want to copy all my flac files 22G, but I get a warning only 2.4G is available in dual boot mode.  Likely more disc space is available but is being on the XP side of partition.

Is there a easy way to increase the disc space?

gychang

---

### Post by Olivier2371 on 2008-11-29
Have you try to run the live cd, and then go the Gparted.

---

### Post by oldos2er on 2008-11-29
> **gychang said:**
> Installed the 8.1 using Wubi, like the Linus very much.

want to copy all my flac files 22G, but I get a warning only 2.4G is available in dual boot mode.  Likely more disc space is available but is being on the XP side of partition.

Is there a easy way to increase the disc space?

gychang

 When you install with Wubi, it installs Ubuntu to the same partition your WinXP is on.

---

### Post by gychang on 2008-11-29
> **oldos2er said:**
> When you install with Wubi, it installs Ubuntu to the same partition your WinXP is on.

thanks, I forgot.

Does the Wubi install a "flexible" disc space? or am I wrong.

Anyone see a solution as to how I can increase the HD disc space?, am sure there is much more available space but likely under NTFS of XP.

gychang

---

### Post by lswest on 2008-11-29
This might help: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

Shows how to add extra virtual drives for WUBI in windows.

Basically, make a new drive, mount it to your WUBI install, and that should work.

---

