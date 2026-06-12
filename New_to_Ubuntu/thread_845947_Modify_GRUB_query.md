---
title: "Modify GRUB query"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Midgetprawn on 2008-07-01
I am dual booting with XP and Edubuntu. Thanks to some support yesterday I was able to reinstate GRub. However it continues to contain a list of Kernel versions and their recovery modes. How can I edit this to show current kernel and Windows options?

---

### Post by bumanie on 2008-07-01
It is a good idea to keep one or two kernels around in case of mishap. You can stop the extra entries appearing by editing the kernel entries in /boot/grub/menu.lst by putting a # in front of the entries. This does not get rid of the kernels, but stops the entries being shown in the grub menu. gksudo gedit /boot/grub/menu.lst and # all the entries you don't want to appear. Then save once done.

---

### Post by iaculallad on 2008-07-01
You have to edit /boot/grub/menu.lst file to manually remove those extra OLD kernel boot menu.

```
gksudo gedit /boot/grub/menu.lst
```

To remove the old kernels permanently, launch Synaptics Package Manager and search for the "linux-image" string.


OR


Simply deleting the OLD kernel files using Synaptics would automatically reconfigure your /boot/grub/menu.lst file.

---

### Post by Midgetprawn on 2008-07-01
Thanks. I didn't want to lose the kernels just in case

---

### Post by kansasnoob on 2008-07-01
You can also just install

> startupmanager

from synaptic. It'll then show up in System > Administration > Startup Manager:

[ATTACH]75923[/ATTACH]

---

