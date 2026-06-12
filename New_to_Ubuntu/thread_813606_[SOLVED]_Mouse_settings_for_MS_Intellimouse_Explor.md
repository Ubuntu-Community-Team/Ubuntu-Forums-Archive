---
title: "[SOLVED] Mouse settings for MS Intellimouse Explorer 2.0"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Inxsible on 2008-05-31
I have a Microsoft Intellimouse Explorer 2.0. Its a hand me down - so don't bust my balls on it please ;)  It has a couple buttons (for Back and Forward in a browser) and sideways scroll which I would like to make use of.  Does anyone know what settings are needed in xorg.conf?

---

### Post by quelx on 2008-05-31
This is for Dapper but I bet it will work in your case, be sure to back up your **xorg.conf** 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.20080531
```

[http://ubuntuforums.org/showthread.php?t=183547](http://ubuntuforums.org/showthread.php?t=183547)

---

### Post by Inxsible on 2008-05-31
Doesn't work for the side buttons (as mentioned in that post) which is what I want to enable.

---

### Post by quelx on 2008-05-31
[http://onebadpixel.com/blog/2008/02/19/setting-up-ms-intellimouse-explorer-20-in-linux/](http://onebadpixel.com/blog/2008/02/19/setting-up-ms-intellimouse-explorer-20-in-linux/)

google terms:
*MS Intellimouse Explorer 2.0 xorg.conf side buttons*

---

### Post by cubeist on 2008-05-31
see the tutorial in my signature... should get your mouse buttons working great with a bit of work...

---

### Post by Inxsible on 2008-06-02
Thanks quelx...got it working just by putting the entries in xorg.conf. Didn't need to do anything else. The horizontal scroll still doesn't work...but I really don't care much about that.

---

