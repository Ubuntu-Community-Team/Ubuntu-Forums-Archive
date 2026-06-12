---
title: "[SOLVED] changing timeout in grub"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by ben32b on 2008-05-30
How can I change the timeout in the grub menu to 3 seconds?

---

### Post by xjgnsdof on 2008-05-30
In Terminal, input the following:

```
sudo gedit /boot/grub/menu.lst
```

In the document that opens, find the line for the GRUB menu timeout and change it to 3.

---

### Post by nick_h on 2008-05-30
You should really use gksudo rather than sudo for graphical applications.
```
gksudo gedit /boot/grub/menu.lst
```
The timeout line is normally the second entry in the file.

---

### Post by Mentem on 2008-05-30
If you want to stay away from the commandline, you could also get startupmanager from synaptic, it adds startup-manager to your system->administartion, and you can also easily change the startup flash, background etc, in addition to the timeout.

---

