---
title: "[SOLVED] Messy GRUb"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Kronie on 2008-06-09
guys, my grup is all messy... i installed ubuntu when it was 8.04.16, so then it updated to .17 and now, just couple hours ago to .18 so now i have 8 entries in grub... is there any way to remove the .16 and .17+ their recovery modes from grub, and leave only Ubuntu 8.04.18 and the recovery mode for it??

---

### Post by meierfra. on 2008-06-09
drs305 wrote a very nice HOWTO on this subject. Click on drs305 in my signature.

---

### Post by Michaelg14 on 2008-06-09
If Ubuntu is your only operating system you should be able to just delete everything after your current version from /boot/grub/menu.lst

Use  $ gksudo gedit /boot/grub/menu.lst

delete everything after:

title		Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=79b1f467-b501-4aad-a963-ebd8e34ce7e6 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

---

### Post by Kronie on 2008-06-09
thanx for all replies, i just figured it out by my self ^_^ i used startup manager..

---

### Post by Bachstelze on 2008-06-09
Actually, you can just uninstall the old kernel images from Synaptic, that will remove them from GRUB as well.

---

### Post by meierfra. on 2008-06-09
deleted

---

