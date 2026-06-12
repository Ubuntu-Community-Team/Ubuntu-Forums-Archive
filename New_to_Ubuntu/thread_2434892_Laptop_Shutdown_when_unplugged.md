---
title: "Laptop Shutdown when unplugged"
date: 2020-01-13
forum: New to Ubuntu
---

### Post by gouravrawat255 on 2020-01-13
[COLOR=#000000]I have an Hp  laptop with Ubuntu 18  64bit installed.  I have a problem with my battery. Whenever I unplug my laptop, it will shut down within seconds even when the battery is still full. (It's not a problem with the battery itself, because in Windows it works perfectly.)[/COLOR]

---

### Post by mörgæs on 2020-01-13
It's probably linked to the hardware so a hardware description would be a good beginning. Please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it onto the command line, run it and paste lshw.txt in CODE tags.

---

