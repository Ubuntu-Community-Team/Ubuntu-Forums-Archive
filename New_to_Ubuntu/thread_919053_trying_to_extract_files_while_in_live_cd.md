---
title: "trying to extract files while in live cd"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by fignig on 2008-09-13
my system got totally destroyed due to errant advice. trying to access my files thru this live cd and it says i can't mount my drive that all the information is on.

it says:
unable to mount the selected volume.
error: device /dev/sda1 is not removable

error: could not execute pmount

is there anyway to access the volume while in live cd?

---

### Post by Elfy on 2008-09-13
Try and mount through the terminal

```
sudo mkdir /mnt/temp
sudo mount -t auto /dev/sda1 /mnt/temp
```

Will be mounted under /mnt in filesystem

---

### Post by bodhi.zazen on 2008-09-13
use mount ;

```
sudo mount /dev/sda1 /mnt
```

---

