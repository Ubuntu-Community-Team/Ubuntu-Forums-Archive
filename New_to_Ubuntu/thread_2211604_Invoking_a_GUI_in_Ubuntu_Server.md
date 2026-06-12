---
title: "Invoking a GUI in Ubuntu Server?"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by 56es8lTI on 2014-03-16
I'm sure there must be a way, but in standard config, it just shows up as command line.

I need to be able to configure video devices in ZoneMinder, can't do it in terminal.

Thanks for any help!

---

### Post by tfrue on 2014-03-17
should be ```

startx
```

Chris

---

### Post by 3rdalbum on 2014-03-17
You will need to install a GUI to run GUI programs, (something simple like openbox will do) or log into your computer from another computer using ssh with the -X flag.

---

