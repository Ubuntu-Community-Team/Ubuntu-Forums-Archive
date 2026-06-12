---
title: "Disable auto read only atribute adding for files coppied from CD"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by jonatan5 on 2008-04-26
How to disable automatic ''read only'' atribute adding for files coppied from CD.
It is anoying to uncheck every files properties. It would be simpler if read only parameter wouldn't be added at all.

---

### Post by terry_gardener on 2008-09-19
this is a confirmed bug, see link [https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/200462](https://bugs.launchpad.net/ubuntu/hardy/+source/gvfs/+bug/200462) for more details 

you can change the permissions on the folder and apply the permissions to the files within. by going to the properties of the folder and the permissions tab, then clicking the option apply permissions to enclosed files.

---

### Post by scorchgeek on 2008-09-19
Really, the bug is that it does not remove the read-only, as CD's use read-only. This happens in Windows too, although I am certainly not saying this is an excuse! Hope this gets fixed too, as this can be very annoying.

---

