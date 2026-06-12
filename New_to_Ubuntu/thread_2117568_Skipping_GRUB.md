---
title: "Skipping GRUB"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by Hex9 on 2013-02-18
Hi guys,

im about to do a reinstall of my system, which will contain Ubuntu and Debian.

I want Ubuntu to be my primary boot and wondering if i can prevent GRUB from appearing and automatically boot into Ubuntu, but say when i start booting i can press a function key to bring up GRUB?

Thanks

---

### Post by deadflowr on 2013-02-18
Run any text editor you desire as root(sudo/gksudo) and edit the file /etc/default/grub.

Look for the line "GRUB_TIMEOUT=", and change the number to zero.
Then save and exit and then update-grub.

My preference is nano, but gedit is easy enough.
Remember, nano can run with sudo, but gedit should be run with gksudo.
Run:
```
sudo update-grub
```

So that changes are actually made. Otherwise it'll run as it did.

---

### Post by mansonfan78 on 2013-02-18
After doing that, if you want to see the grub menu hold down the shift key when you start your computer.

---

### Post by Hex9 on 2013-02-18
Too easy, thanks guys :D

---

