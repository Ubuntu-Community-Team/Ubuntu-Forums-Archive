---
title: "screen resolution settings"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by anthonyms on 2008-06-12
hello guys
ever since i installed ubuntu, i've been dealing with a screen resolution of 1024x768
the "monitor resolution settings" window doesn't give me the option to choose a higher resolution
i was using windows xp before and the resolution could go till 1280x1024
my video card is built-in a pentium 3 motherboard of 1.0 Ghz

i'd be greatful for any help!

---

### Post by MmmmJoel on 2008-06-12
Are there any restricted drivers available? System -> Administration -> Hardware Drivers

If so, enable them and reboot.

---

### Post by wolfen69 on 2008-06-12
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot.

---

