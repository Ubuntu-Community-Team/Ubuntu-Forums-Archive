---
title: "disk checking"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by maheshjr2000 on 2008-11-11
is there anyway to set up an automatic disk check on reboot? Like windows?

---

### Post by philinux on 2008-11-11
sudo tune2fs -l /dev/sda1 - this shows how many boots to next check

sudo tune2fs -c 50 /dev/sda1 - this sets the check to every 50 boots. Mine is set to this. you could set it to 1 I suppose.

sudo touch /forcefsck - this forces a check next boot.

---

