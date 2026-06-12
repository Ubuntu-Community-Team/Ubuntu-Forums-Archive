---
title: "Re-partion"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by sudeepk on 2008-09-28
I have installed ubuntu in my 160gb hard disk in a single partition. Now i want to install windows xp in my harddisk without removing ubuntu. The problem is i have only one partition.

---

### Post by fooman on 2008-09-28
you can use gparted to create/resize partitions.  it is available in synaptic or in a terminal:

```
sudo apt-get install gparted
```

you can read up on it here:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by steveneddy on 2008-09-28
I prefer using the gparted cd.

Like a live cd, but with only one application on it (gparted)

---

### Post by kansasnoob on 2008-09-28
This guide should be helpful:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by Paqman on 2008-09-28
> **steveneddy said:**
> I prefer using the gparted cd.

Like a live cd, but with only one application on it (gparted)

Gparted is also on the Ubuntu LiveCD, so if you've got one of those kicking around there's no need to burn a separate disk.

---

