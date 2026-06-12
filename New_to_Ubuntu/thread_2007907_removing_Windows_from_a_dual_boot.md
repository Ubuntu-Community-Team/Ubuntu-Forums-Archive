---
title: "removing Windows from a dual boot?"
date: 2012-06-21
forum: New to Ubuntu
---

### Post by Norm24 on 2012-06-21
I really have not used Windows in close to two years.Is simply deleting the windows and recovery partitions the way to do it and then update grub?

---

### Post by mike555 on 2012-06-21
I would recommend formating the Windows partition EXT4 , and use it for backup.be sure to sudo update-grub .

---

### Post by audiomick on 2012-06-21
> **mike555 said:**
> I would recommend formating the Windows partition EXT4 , and use it for backup.be sure to sudo update-grub .

That, or just expand the Ubuntu partition into the space that has become available. 

And yes, do update grub.

---

### Post by sandyd on 2012-06-21
Depends on your partition setup.

If its

1. Windows
2. Linux/Swap
Then, format Windows as Ext4 or XFS

Run update-grub
```

sudo update-grub
```

If it is

1. Linux/Swap
2. Windows
Then, delete the windows partition, run update-grub
```

sudo update-grub
```
Use Gparted on a livecd to expand your linux partitions.

---

