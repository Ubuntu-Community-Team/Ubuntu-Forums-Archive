---
title: "Shutdown problem"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by tanelli on 2008-05-14
I have LG TX Express and Ubuntu 8.04. When I want to shut down my laptop (tried both "shutdown -H 0" and "shutdown -P 0") it almost shutdowns my laptop but I have to press power button to power off. Reboot works normally. Under Windows XP I don't have to power off manually. Anyone can help?

---

### Post by dizee on 2008-05-14
When you are booting up, when you see the GRUB menu with "Ubuntu 8.04, kernel ..." on it, press "e", and add "acpi=force" at the end of the line. 

Then press "b" to boot.

Try shutting down and see if that works - if it does, then you can make it permanent by editing the /boot/grub/menu.lst file:
```
gksu gedit /boot/grub/menu.lst
```
edit this bit:```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=f2b86bb7-b82c-441e-b31e-313193d5e61b ro quiet splash **acpi=force**
```

---

### Post by bluemarble on 2008-05-16
I have the same problem! I will try what you suggest when I get home fomr work :)

---

