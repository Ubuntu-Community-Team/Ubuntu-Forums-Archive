---
title: "Booting Trouble"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by BillyMax on 2008-06-12
I am just sorting out partitions and stuff on my computer. I have xp installed on my main hard drive. I have installed ubuntu 8 inside xp and I wiped my secondary hard drive which had ubuntu 7 on it. I formatted it to ntfs just like my main hard drive so I can use it with xp. As i restarted my computer it said 'GRUB error 14'. What have I done wrong and how do I get it to boot xp?

I have tried booting from a different hard disk (in BIOS) and it doesn't work but it will boot ubuntu 8 from CD.

---

### Post by argail1980 on 2008-06-12
I think, the grub was installed on that second partition (everything but the binary, including the config-files). Now, the grub does not find any config anymore. insert a windows boot-cd, enter the rescue console and try on C:
```
fdisk /mbr
```

This will clean the master boot record of your HD from any remains of the old grub, so windows can boot (hopefully).
But you should definitively think about installing another ubuntu ;-)

---

