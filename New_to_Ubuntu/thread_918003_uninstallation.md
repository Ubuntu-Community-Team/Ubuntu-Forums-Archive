---
title: "uninstallation"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by rajesh_shah87 on 2008-09-12
hey plz help me out!

how i uninstall ubuntu 7.04 from my pc!

becoz i already installed 8.04?

---

### Post by nothingspecial on 2008-09-12
> **rajesh_shah87 said:**
> hey plz help me out!

how i uninstall ubuntu 7.04 from my pc!

becoz i already installed 8.04?

Have you got both versions as a dual boot?

Did you upgrade or do a clean reinstall?

---

### Post by ibuclaw on 2008-09-12
I take it that they are installed on separate partitions?

Can you post the output of these commands? They would help us greatly with your problem.

```
sudo fdisk -l
```
```
df
```
```
grep -v "#" /boot/grub/menu.lst
```

Regards
Iain

---

### Post by bhadotia on 2008-09-12
If you upgraded 7.04 to 8.04 then you don't need to uninstall it coz its become 8.04 now.
In case you have installed 8.04  on a separate partition , then just format the partition on which 7.04 is installed using System>Administration>Partition Editor and then run the following command in the terminal (Applications>Accessories>Terminal):
```
sudo update-grub
```

---

