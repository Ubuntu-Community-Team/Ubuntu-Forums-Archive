---
title: "formatting in terminal"
date: 2008-04-27
forum: Philippine Team
---

### Post by dareymon on 2008-04-27
pano po mag format ng removable media sa terminal?

tnx

---

### Post by tech0007 on 2008-04-27
depende sa filesystem na lalagay mo.  type mo sa terminal

man mkfs

---

### Post by raxso on 2008-04-28
kung usb drive check mo muna kung ano partition siya

fdisk -l

kung alam mo na dapat naka-unmount yung drive na ifo-format mo. then type dis command

mkfs.vfat -F 32 -n label /dev/sdb1

- mkfs.vfat - kung gusto mo gawing fat ung drive
-F 32 - kung fat32 gusto mo.
-n label - kung ano gusto mong label
/dev/sdb1 - kung ano location ng gusto mong i-format.


:)

---

