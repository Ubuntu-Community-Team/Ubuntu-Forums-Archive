---
title: "bad sector disk checker"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by afeasfaerw23231233 on 2008-07-30
is there a bad sector checker utility software in ubuntu that can repartition the disk excluding the bad sectors so the disk can be usable again? 
EDIT: i have a bootdisk which called FBDISK which can check bad sectors and then repartition the disk within the good sectors automatically. i received two bad disks yesterday and i don't want to pull my box out. but FBDISK cannot recognize disk that are connected via USB. The Partition Editor in System -> Administration cannot do this trick. any idea? thanks!

---

### Post by iaculallad on 2008-07-30
> **afeasfaerw23231233 said:**
> is there a bad sector checker utility software in ubuntu that can repartition the disk excluding the bad sectors so the disk can be usable again?

On your terminal:

```
man badblocks
```

Note: This utility can't repartition your disk. You still have to rely on Gparted.

---

### Post by afeasfaerw23231233 on 2008-07-30
it hangs up. it displays a lot of 
> 500000001
500000002
.
.
.
and my disk shuts down automatically

---

