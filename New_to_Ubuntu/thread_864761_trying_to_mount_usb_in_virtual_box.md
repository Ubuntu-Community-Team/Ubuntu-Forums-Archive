---
title: "trying to mount usb in virtual box"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-07-20
using a walkthrough i found if i recall through here i had to edit some executable files and run in terminal
[B]
sudo /etc/init.d/mountkernfs.sh[/B]

i get the following error message...
Warning: mountvirtfs should be called with the 'start' argument.

any one know whats going on?

---

### Post by stmiller on 2008-07-20
Try:

sudo /etc/init.d/mountkernfs.sh start

---

