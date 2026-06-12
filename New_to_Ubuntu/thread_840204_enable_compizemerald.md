---
title: "enable compiz/emerald"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by cjnkns on 2008-06-25
I am trying to figure out how emerald fits in with compiz or does it?

Compiz is already installed on hardy, but if I import themes into emerald they don't seem to change the theme at all.

Do these two apps work together or am I not understanding this...

Thanks

---

### Post by Nepherte on 2008-06-25
You can start emerald with this command:
```
emerald --replace
```

If you want it to start upon logging in to your system, just add the command under system > preferences > session

A useful tool is fusion-icon. It resides in the notification icon area. It allows you to easily switch between gtk and compiz, or between window managers. To install:
```
sudo apt-get install fusion-icon
```

---

### Post by cjnkns on 2008-06-25
GOT IT - thanks!

---

### Post by Japanac on 2008-06-25
Thanks :)

---

