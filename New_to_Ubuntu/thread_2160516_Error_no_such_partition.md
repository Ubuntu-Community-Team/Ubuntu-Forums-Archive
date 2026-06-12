---
title: "Error: no such partition"
date: 2013-07-07
forum: New to Ubuntu
---

### Post by Sneera on 2013-07-07
Hi every1 please help "Error: no such partition grub rescue" I am using W7 ASUS laptop and last week I installed Ubuntu 12.04 alongside with W7. It was working fine until I selected windows recovery to recover windows files, on the boot window where you select ubuntu, W7. What happend is W7 recover displayed an error and I restarted the laptop and it displayed the Rescue console and I can not boot from CD/DvD and USB I can only access BIO even BIOs is no help @ this point. I have the Ubuntu 12.04 CD I can't boot on it pls help. I tried some tricks on other post I just can't get it right. I dd try set prefix=(hd0,6)/grub but wen I enter insmod normal its says no such partition.

---

### Post by Impavidus on 2013-07-07
In the bios you should be able to set the boot device to the optical disc drive or an usb drive (if supported). Then boot from your live cd and try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). It may be able to fix your problem. If not, then show us the boot info summary it generates.

---

