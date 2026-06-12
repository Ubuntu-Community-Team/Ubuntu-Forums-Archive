---
title: "how to format my partition or external HDD?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by m_o_b on 2008-04-30
i have an external HDD formated as (MAC HDD) and a partition for that is NTFS and i want to format them as FAT32.

which program that would do it?

thanx in advance.

---

### Post by spoown on 2008-04-30
simply use this command :
```
mkfs.vfat /dev/hda1
```
if you want to format first partition on your first ide device.

---

### Post by magnus0 on 2008-04-30
Or, you can download GParted. It's a GUI disk tool.

```
sudo apt-get install gparted


```

---

### Post by m_o_b on 2008-04-30
i'll try them and let u know


thanx guys

---

### Post by kpkeerthi on 2008-04-30
I second gparted. Make sure the partitions are 'unmounted' before you format them. Ubuntu Live CD already has gparted (System -> Admin -> Disk Partitions)

---

### Post by park8b156 on 2008-04-30
Or you can use partition magic it pretty fast.

---

### Post by ad_267 on 2008-04-30
PartitionMagic is proprietary and for Windows only, use GParted. You can use it from the live cd or install it using synaptic or apt-get.

---

### Post by m_o_b on 2008-04-30
it's Working perfect.......thanx guys (i meant GParted"

---

### Post by logx on 2008-05-18
Hello,

Apart from Gparted, is there any other way to format an external HDD?

I tried the mkfs.vfat /media/ but it claims it cannot open the device :s

---

### Post by Crossroads on 2008-05-18
Is GpartEd giving you problems?

I would think that's the best way to go. Post any issues here so that they can be sorted out.

---

