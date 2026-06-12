---
title: "kernel directly boots ubuntu"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by arjunrj405 on 2011-12-25
i installed ubuntu on my pc using dvd; i already had windows xp and 7.  But after installing now whenever i start my pc, the kernel page for choosing  from various operating system does not pop up, ubuntu directly starts.  What do i do?:(

---

### Post by arjunrj405 on 2011-12-25
> **arjunrj405 said:**
> i installed ubuntu on my pc using dvd; i already had windows xp and 7.  But after installing now whenever i start my pc, the kernel page for choosing  from various operating system does not pop up, ubuntu directly starts.  What do i do?:(
pls note that all three o.s are on different drives...

---

### Post by lisati on 2011-12-25
When you boot your computer, hold down the left shift key. That *should* pop up a menu.

---

### Post by emmomalick on 2011-12-25
Try re-installing your GRUB as given here.

[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

OR update your grub using Terminal from Application > Accessories > Terminal
```
sudo update-grub
```

---

### Post by lolpenguin on 2011-12-25
GRUB2 skips the boot menu by default. Hold the shift key before you reach GRUB to show the boot menu.

---

### Post by Frogs Hair on 2011-12-25
This was a surprise to me on the latest version as well . I no longer keep old kernels because I haven't had the need for one since 9.10 .

---

