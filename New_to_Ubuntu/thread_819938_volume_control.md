---
title: "volume control"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Inxsible on 2008-06-05
I have a minimal install.

I tried to control my volume from cplay - a CLI music player. and it gave me this error```
[Errno 2] No such file or directory: '/dev/mixer'
```Now I need to know what package should I install to get /dev/mixer. Is it aumixer?

---

### Post by iaculallad on 2008-06-05
Try installing the alsa-oss located at the universe repository:

```
sudo apt-get install alsa-oss
```

And open cplay with:

```
aoss cplay -v
```

---

