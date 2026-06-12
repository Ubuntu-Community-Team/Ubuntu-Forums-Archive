---
title: "[SOLVED] home partition"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by adamogardner on 2008-10-18
I read somewhere about having the file system partitioned so the home directory is untouched like say if I were to install kicky kangaroo.  Is this correct?  How do I do it?

---

### Post by philinux on 2008-10-18
[Psychocats]("http://www.psychocats.net/ubuntu/separatehome")

Good site too.

---

### Post by adamogardner on 2008-10-18
I had help installing my rig so maybe I already have one.  Where can I look, and what does it look like?

---

### Post by benerivo on 2008-10-18
When you install linux it has to format the root partition and so you lose all the data on it. If your /home is on a separate partition then it will be untouched in thge same way that an windows xp partition is untouched by an ubuntu installation. If you don't have your /home on a separate partition then you can move it in to one using [these]("http://www.psychocats.net/ubuntu/separatehome") instructions.

---

### Post by philinux on 2008-10-18
> **adamogardner said:**
> I had help installing my rig so maybe I already have one.  Where can I look, and what does it look like?
It would look like this.
```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fbeeb82a-d82d-4896-b2e6-022d2531c3fc /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=39759482-7d7a-4398-b338-2cdf7ed2e99d **/home **          ext3    relatime        0       2

```

---

### Post by adamogardner on 2008-10-18
ok I apparently don't have one.  Thanks

---

### Post by philinux on 2008-10-18
Dont forget to back up anything important before you start! :)

---

### Post by adamogardner on 2008-10-18
well actually, I don't understand gparted and all that partition and filesystem jargon.  I read it every time.  But I never know what is going on for sure or where I'm at or what, It's just bewildering.

---

