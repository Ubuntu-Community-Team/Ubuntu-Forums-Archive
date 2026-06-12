---
title: "printing landscape"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by hammeraxe on 2008-08-20
ive already had this problem for some time now... actually ive seen launchpad entries for this dating back to 2006: i cant print landscape from abiword or gnumeric. The text direction is correct but it is truncated as if it was printing portrait instead of landscape. This is said to be a libgnomeprint bug. If so why isnt this fixed/how to fix it/is there a workaround?

[https://bugs.launchpad.net/ubuntu/+source/libgnomeprint/+bug/24785](https://bugs.launchpad.net/ubuntu/+source/libgnomeprint/+bug/24785)
especially comment 20

 Thanks

---

### Post by LowSky on 2008-08-20
What Printer and Ubuntu edition are you using?

---

### Post by hammeraxe on 2008-08-20
xubuntu 8.04
HP LaserJet 6L

---

### Post by LowSky on 2008-08-20
Have you tried using OpenOffice?

---

### Post by hammeraxe on 2008-08-25
using openoffice solves the problem as it apparently uses a separate printing system... but the thing is that openoffice is quite slow on my system and i would prefer using abiword. is there really no solution for this problem?

---

### Post by aimpau on 2008-08-25
Hahaha! Sorry for the laugh but I have exactly the same problem and got annoyed when I printed something from Abi then left it for a while then all files that were supposed to be printed in landscape, are printed in portrait. :)

Anyways, here's my manual fix:

1. Your right about openoffice.org>> You can adjust the print style from within the application.

2. Regarding the GNOME office, go to Application>>Settings>>Printing then go to the Job Options Tab, then you have to adjust the rotation to 90 degrees or Landscape.

3. Once printing to Abiword, try first to print normally WITHOUT changing anything in the print settings within Abi. If it still not printing ok, then, ALSO change the layout settings within Abi.

Post back the results please. :) I think this can be included as a fix for Xubuntu Intrepid.

---

