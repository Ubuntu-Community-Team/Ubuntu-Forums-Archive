---
title: "when hardy heron reboots screen wrong Resolution"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by jpdamigaman on 2008-05-06
Hi when I reboot ubuntu 8.04 screen Resolution always goes back to a lower 1 than I want.

I reconfigured g gibbons xserve but can only change key board comands when I try same command in hardy.

---

### Post by The Tronyx on 2008-05-06
Just out of curiosity, would you mind telling me how you reconfigured xserver?

Also, please paste the contents of /etc/X11/xorg.conf

Thanks!  Hopefully we can get this sorted out.

---

### Post by gimfred on 2008-05-07
Not the OP, but I'm having the similar problem. I however, am using a clean install.

Kubuntu 8.04 amd64
nvidia 7500 series
ide hd drives (significant as I originally upgraded from 7.10 to 8.04 and I had the weird lockup bug. Doesn't seem to be affecting the clean install, only time shall tell.)

I reconfigured via ```
sudo dpkg-reconfigure xserver-xorg
```
It only allowed me to change the keyboard options in Xorg.

I'm about to try reinstall the nvidia drivers...

---

### Post by jpdamigaman on 2008-05-07
Hi thanks to all posts

I solved problem I uninstalling old kernells and that fixed problem!

Still can't reconfig xserve though way I used to in gutsy,

by sudo dpkg-reconfigure xserver-xorg that only configs keyboard and mouse.

---

### Post by Zralou on 2008-05-07
dpkg-reconfigure doesn't work in hardy anymore.  I think itsz something like xfix now?.

Sara Lou

---

