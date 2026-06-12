---
title: "USB Support?"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by sondosia on 2008-04-22
Does xubuntu support USB devices? I've tried to use my flash drive, mp3 player, and DVD drive, and none of them have been recognized.

Ironically, when I was running xubuntu from the livecd, it did recognize them...

What can I do to fix this?

---

### Post by RealPSL on 2008-04-23
USB devices are certainly supported. You can launch a shell with 
```
Applications > Accessories > Terminal
```

Once you have a shell you can list the attached USB devices with

```
lsusb
```

You can also generally see USB devices come online in the /var/log/messages file. If you are not getting any of this there is obviously a bigger problem.

---

### Post by nicedude on 2008-04-23
My USB storage devices pop an icon right onto the desktop upon insertion. With Ubuntu & Xubuntu and this was by default.

---

