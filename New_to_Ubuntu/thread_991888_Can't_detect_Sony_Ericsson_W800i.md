---
title: "Can't detect Sony Ericsson W800i"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Shippou on 2008-11-24
Hello...

I am using Mint and it can't detect the said device. How can I make it detect it?

I am using Linux Mint Elyssa 32 bit.

---

### Post by philinux on 2008-11-24
[http://ubuntuforums.org/showthread.php?t=798359](http://ubuntuforums.org/showthread.php?t=798359)

You will need to change /dev/sdh1 to suit your system.

---

### Post by muranyia on 2010-02-25
For automount:

put somewhere in /lib/udev/rules.d/ :

```
# SonyEricsson W800i
ATTR{idVendor}=="0fce", ATTR{idProduct}=="d028", MODE="660", GROUP="audio", RUN+="/usr/bin/sudo -u yourusername /bin/mount yourmountpoint
```

---

