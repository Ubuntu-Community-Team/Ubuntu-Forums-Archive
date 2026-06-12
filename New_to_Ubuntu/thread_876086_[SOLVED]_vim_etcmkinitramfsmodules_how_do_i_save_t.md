---
title: "[SOLVED] vim /etc/mkinitramfs/modules how do i save this in a terminal?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-31
im trying to fix my usb drive,but i dont know how to save this file after editing,can someone help??
rick

---

### Post by Separ on 2008-07-31
in Vim command mode:
```
:wq
```
That will save the file and exit :)

---

### Post by voteforpedro36 on 2008-07-31
Or use Nano, where it's Control + O to save, Control + X to exit. Just saying, vim is a bit complicated.

By the way to save that file you will have had to run *sudo vim /etc/mkinitramfs/modules* because the file is owned by root.

---

