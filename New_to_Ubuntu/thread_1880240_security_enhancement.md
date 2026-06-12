---
title: "security enhancement"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by tushar maroo on 2011-11-13
recently i have upgraded from 10.04 to 11.10
my present working system is 11.10
in 10.04 i was asked my password to open ntfs drives of windows,but now i am not prompted to enter my password,so i want to enable that option,how i can do that?

---

### Post by greendragons on 2011-11-13
u mean super user password... try changing owner of mount point....
$ [B]sudo chown root <mount_point>

[/B]

---

### Post by tushar maroo on 2011-11-13
still not working :(

---

### Post by greendragons on 2011-11-13
May this need editing fstab file... im not sure..

---

