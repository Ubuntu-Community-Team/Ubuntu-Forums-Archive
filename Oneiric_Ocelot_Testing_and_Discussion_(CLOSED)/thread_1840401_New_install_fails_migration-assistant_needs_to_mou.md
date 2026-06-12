---
title: "New install fails: migration-assistant needs to mount.."
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by t1497f35 on 2011-09-07
Hi,
Trying to install daily live i386 from USB drive and it ends up with the error as on screenshot and the install fails. Same is true for at least the last 2 daily isos.
Can't find a bug report on this, anyone aware of it? Has it been discussed already?

---

### Post by t1497f35 on 2011-09-07
It looks like when you install on dev/sda10 Linux can't handle that, because 11.04 also fails to install on dev/sda10 and yields same (misleading) error about sda2.

Then I tried to install on dev/sda9 and anything went fine. So avoid using >= sda10.

---

