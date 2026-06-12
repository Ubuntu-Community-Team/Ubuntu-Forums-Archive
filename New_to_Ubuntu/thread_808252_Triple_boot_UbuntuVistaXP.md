---
title: "Triple boot Ubuntu/Vista/XP ?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Drakkor on 2008-05-26
I have Ubuntu on a dedicated partiion,and Vista on the other,can I somehow add XP ? Thanks :)

---

### Post by FrozenFire on 2008-05-26
I think that you should install XP (leaving the other partitions alive),
restore GRUB stuff with livecd, and do some GRUB chainloading magic.

---

### Post by Duck2006 on 2008-05-26
Yes. Make the partition and install XP then add it to your boot loader.
If your going to use the vista drive use vista to partition the drive. 
If you use the linux drive use gparted to make the partition.

---

