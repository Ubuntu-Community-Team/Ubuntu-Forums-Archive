---
title: "How do I Get a Device's UUID in Shell Script?"
date: 2010-05-02
forum: Programming Talk
---

### Post by Penguin Guy on 2010-05-02
How do I automatically get the UUID of a device from the device name? I've been trying to get it through [FONT="Courier New"]blkid[/FONT] and [FONT="Courier New"]sed[/FONT], but this is as far as I've got:
```

$ blkid /dev/sdb1 | sed 's_[^#]*UUID="\([-[:alnum:]]*\)"_\1_'
B6BF-00BD TYPE="vfat"

```

Any help would be greatly appreciated. More info [here]("http://ubuntuforums.org/showthread.php?t=1290438").


Solution:
```
blkid -o value -s UUID /dev/sdb1
```
You can also replace [FONT="Courier New"]UUID[/FONT] with [FONT="Courier New"]LABEL[/FONT] to get the label of a device.

---

### Post by slavik on 2010-05-02
> **Penguin Guy said:**
> How do I automatically get the UUID of a device from the device name? I've been trying to get it through [FONT="Courier New"]blkid[/FONT] and [FONT="Courier New"]sed[/FONT], but this is as far as I've got:
```

$ blkid /dev/sdb1 | sed 's_[^#]*UUID="\([-[:alnum:]]*\)"_\1_'
B6BF-00BD TYPE="vfat"

```

Any help would be greatly appreciated. More info [here]("http://ubuntuforums.org/showthread.php?t=1290438").
```
sudo blkid /dev/sdb1 | perl -pe 's/.*UUID="(.*?)".*/$1/'
```

---

### Post by Bachstelze on 2010-05-02
Or

```
sudo blkid /dev/sdb1 | cut -d '"' -f 2
```

---

### Post by Penguin Guy on 2010-05-02
> **Bachstelze said:**
> Or

```
sudo blkid /dev/sdb1 | cut -d '"' -f 2
```
I'm afraid that doesn't work for all devices, since the list of properties is not always in the same order.

> **slavik said:**
> ```
sudo blkid /dev/sdb1 | perl -pe 's/.*UUID="(.*?)".*/$1/'
```
Thanks, that works great!

:D

---

### Post by Penguin Guy on 2010-05-03
Hey, looks like I found a better solution in fstab itself:
```
blkid -o value -s UUID /dev/sdb1
```
Sorry for bothering you.

---

### Post by rnerwein on 2010-05-03
> **Penguin Guy said:**
> Hey, looks like I found a better solution in fstab itself:
```
blkid -o value -s UUID /dev/sdb1
```Sorry for bothering you.

hi
i propose, if you are running blkid in a script, to use the "-c" option. this causes the command to read
from a clean cache ( not /etc/blkid.tab --> /dev/.blkid.tab - those files may be previously but no more 
available ( e.g. removeable  :(    ).
use: blkid -c /dev/null /dev/xyzn     :P

ciao

---

