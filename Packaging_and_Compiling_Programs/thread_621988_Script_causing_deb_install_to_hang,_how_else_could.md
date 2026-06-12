---
title: "Script causing deb install to hang, how else could I run it?"
date: 2007-11-24
forum: Packaging and Compiling Programs
---

### Post by viciouslime on 2007-11-24
In my postinst script i have the following command I want to run:

```
 wpa_supplicant -i eth0 -d -B -Dwired -c /etc/wpa_supplicant.conf
```

However, it always causes the installation to hang. If i run the command in a terminal it works fine then exits. Any commands after this command in the postinst script are still being run correctly.

Any ideas anyone?

---

