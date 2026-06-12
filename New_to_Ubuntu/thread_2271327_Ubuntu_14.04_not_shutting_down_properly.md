---
title: "Ubuntu 14.04 not shutting down properly"
date: 2015-03-29
forum: New to Ubuntu
---

### Post by FROG_ on 2015-03-29
i have a dualboot setup Windows 7 (32-bit) & Ubuntu 14.04 (32-bit), when i shut down ubuntu it stuck with this screen.
[IMG]http://s30.postimg.org/3nstoom4x/IMG_20150329_160700.jpg[/IMG]

---

### Post by egeezer on 2015-03-29
It looks like mixed signals: instead of shutdown, it signals reboot, so power down can't operate.  Try shutting down from the terminal to see how that goes.  For instance ```
sudo shutdown now -h -P
``` The -h is for halt, -P for power down.

---

