---
title: "reducing disk i/o and disk failure during hard reset"
date: 2011-09-28
forum: Philippine Team
---

### Post by kiminaiseah on 2011-09-28
file : /etc/fstab

from : 

/dev/sda1 /               ext4    errors=remount-ro 0       1
/dev/sda5 none            swap    sw              0       0

to :

/dev/sda1 /               ext4    defaults,noatime 0       1
/dev/sda5 none            swap    sw              0       0

 -- 

any in the group using same settings

 -- 

performance improvement base on hand experience

1. quick booting
2. risk reduction for hard resetting of the system
3. snappier sensation 

 --

system spec :

OS = Ubuntu / Lucid Lynx (Debian Sid/Testing) AMD64 x86_64bit
Proc = Intel i3 330M 2.13Ghz
RAM = 2x 4GB 800Mhz
HDD = 320GB 4200 RPM

 --

---

