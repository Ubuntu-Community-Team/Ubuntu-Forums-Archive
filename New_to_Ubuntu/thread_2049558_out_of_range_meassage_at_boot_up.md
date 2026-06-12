---
title: "out of range meassage at boot up"
date: 2012-08-28
forum: New to Ubuntu
---

### Post by Givey51 on 2012-08-28
installed ubuntu 12.4 on a system with windows xp. Told ubuntu to use dual boot mode. When I boot up system the message Out of Range appears on my monitor and the system then boots straight into ubuntu.

---

### Post by micahpage on 2012-08-28
try in terminal
```
sudo update-grub
```
you should see it recognize your windows partition
then reboot and see if you get into grub with the options of windows and linux

Could you elaborate more on your details of installation?

---

