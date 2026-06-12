---
title: "Old usb mnt points"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by cjnkns on 2008-08-10
I have an external usb flash drive that I use a lot.
My ubuntu filesystem shows that there are three folders (mnt points) that have big X's on them. Now when I plug in the usb drive I get another point point and the actual path to the usb has a couple _'s underscores included in the path... So does two of the folders with X's on them.

How do I get rid of the old broken mount points with X's on them?:confused:


Thanks!

---

### Post by ajgreeny on 2008-08-10
Probably the easiest way if you are not happy about the CLI is to use ```
gksudo nautilus
``` and then delete them the normal way using the GUI.  You can, of course use ```
sudo rmdir /path/to/mount/point/
```Not sure if you need the trailing / at the end so wait for confirmation on that way first.  Just make sure that the mount point folders are definitely not used by anything else first.
EDIT:
Just tried it and you don't need the trailing /

---

### Post by cjnkns on 2008-08-10
Great - thanks that worked.

---

