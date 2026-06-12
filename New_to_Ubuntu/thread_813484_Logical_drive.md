---
title: "Logical drive"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by tonymoloney on 2008-05-30
Does anyone know if it is possible to make one logical drive across two physical drives?

---

### Post by wdaniels on 2008-05-30
You should be able to do this with [Aufs]("http://aufs.sourceforge.net/"). There might be a simpler/better method, but that's all I can think of myself...

---

### Post by MDSmith2 on 2008-05-30
I think you should use raid but i don't know anything about it so google it.

---

### Post by tonymoloney on 2008-05-30
H'mm.
Looks pretty complex and also refers to Unionfs which I will have to research also.

---

### Post by wdaniels on 2008-05-30
> **MDSmith2 said:**
> I think you should use raid but i don't know anything about it so google it.

Yes, you could use RAID 0 (I didn't think of that) but the additional storage is constrained by the size of the smallest physical disk (i.e. using a 40GB disk with a 60GB disk would only give you a 80GB array).

All other RAID levels I think use the additional physical disks for redundancy/performance.

---

