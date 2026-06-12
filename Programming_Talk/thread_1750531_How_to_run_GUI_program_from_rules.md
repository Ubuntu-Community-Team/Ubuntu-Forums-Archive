---
title: "How to run GUI program from rules?"
date: 2011-05-05
forum: Programming Talk
---

### Post by Olvin0 on 2011-05-05
I created a file **/etc/udev/rules.d/mount.rules** with this content:

```
ACTION=="add" KERNEL=="sd[b-z][0-9]" RUN=="export DISPLAY=:0 && /usr/bin/gnome-terminal"
ACTION=="add" KERNEL=="sd[b-z][0-9]" RUN=="/home/olvin/MyScript"
ACTION=="add" KERNEL=="sd[b-z][0-9]" RUN+="/bin/mount /dev/%k /mnt/usb-flash"
ACTION=="remove" KERNEL=="sd[b-z][0-9]" RUN+="/bin/umount /mnt/usb-flash"

```

This rule runs the ~/MyScript. But it does not work if I try to run a graphical program. Can anyone help me?
I use Ubuntu 11.04. 

[COLOR="Gray"]P.S. I want to use my flash drive as a key for truecrypt volume. The GUI program is needed for password requestion (for double security).[/COLOR]

---

