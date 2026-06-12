---
title: "I messed up my video driver and I have to unity-reset as root everytime I login"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by ideleted on 2013-02-19
Dash, launchers are gone. Superkey doesn't work. Only thing I can do is summon teriminal and do unity-reset as root.

---

### Post by ideleted on 2013-02-20
I am missing Top and Side Panels in Unity

---

### Post by bogan on 2013-02-21
Hi!,** ideleted**,

Edit: 'unity reset' is deprecated, rather use 'setsid unity'.

If you are running 12.10, then:

When in the blank desktop Screen, Right Click and select  'Change Desktop Background', then the 'All Settings' Tab,  then the  System> Software Sources Icon, and then the Additional Drivers Tab.

Choose which video driver to install and Activate it. Reboot and report how it goes.

If not 12.10 you will need to use the terminal, but first try booting in Recovery mode and select Resume Boot. That will boot with the default driver.

If still problems, Please Post: ```
uname -r
lspci -nnk | grep -iA3 vga
/usr/lib/nux/unity_support_test -p
```Chao!,** bogan**.

---

