---
title: "Graphics messed up"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by Gael33 on 2013-03-06
The graphics were reasonable on my pc until I tried to install the xorg drivers and now everything is really big and stuck on 640x480 and 0 refresh.

How do I reset the graphics to the original installation settings without having to reinstall everything? :confused:

thanks .......

---

### Post by Cheesemill on 2013-03-06
What exactly did you do to try and install drivers?

Also what graphics does your machine have? The output of
```
lspci | grep VGA
```
would be usefull please.

---

### Post by cortman on 2013-03-06
We definitely need more info on what you did, also the output of

```
xrandr
```

may be helpful.

---

