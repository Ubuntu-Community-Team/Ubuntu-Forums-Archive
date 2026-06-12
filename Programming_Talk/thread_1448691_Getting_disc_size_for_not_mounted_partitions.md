---
title: "Getting disc size for not mounted partitions"
date: 2010-04-06
forum: Programming Talk
---

### Post by GeoMX on 2010-04-06
I've been using **statvfs** for getting disc size in my c programs, it returns the number of blocks and the block size for a mounted device, but it does not work for unmounted ones. Do you know how could I get disk size for unmounted partitions?

Thanks in advance for your help.

---

### Post by GeoMX on 2010-04-09
Not what I wanted at first, but I managed to solve it by using sdparm command.

---

