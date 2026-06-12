---
title: "xfce4-brightness-plugin not working in Xubuntu 13.04"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-04-27
Hi, I have just upgraded from Xubuntu 12.10 to Xubuntu 13.04 and first thing I tried was to higher the brigthness of my LCD display, but it is not working.
The slide panel is 
1. 3x times slower than in 12.10 (I have to rub the mouse wheel much more).
2. It really does nothing.

The version of xfce4-brightness-plugin is 1.2.0

Thank you for EVERY advice.

---

### Post by pqwoerituytrueiwoq on 2013-04-27
try doing this:
[[IMG]http://www.zimagez.com/miniature/screenshot-04262013-105033pm.png[/IMG]]("http://www.zimagez.com/zimage/screenshot-04262013-105033pm.php")
then run ```
sudo update-grub
``` and reboot

---

### Post by ViliX64 on 2013-04-27
Yes, it worked! Thank you :) But why it did not worked after upgrading?

---

### Post by pqwoerituytrueiwoq on 2013-04-27
it is a change in the kernel, your BIOS caters to windows 8 that is the problem
mine is the same way, but i get 2 levels of brightness without that

relevant:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1138168)
[https://bugzilla.kernel.org/show_bug.cgi?id=55161]("https://bugzilla.kernel.org/show_bug.cgi?id=55161")
be glad i saw this, it took ~5 weeks to find this solution for myself

---

### Post by ViliX64 on 2013-04-28
Oh, so.. thank you again :)

---

