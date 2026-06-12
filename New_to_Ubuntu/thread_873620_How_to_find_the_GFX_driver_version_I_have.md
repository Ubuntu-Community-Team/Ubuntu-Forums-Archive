---
title: "How to find the GFX driver version I have?"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by mingle on 2008-07-29
Hi,

I'm currently trying out Ubuntu 8.04 on my HP D530S desktop, which has an Intel 82845G graphics chipset.

The screen update is noticeably sluggish when moving windows around and the overall speed of the display update is much slower than running XP on the same box.

I was wondering if it could be that I have an old GFX driver installed, or perhaps it isn't configured correctly.

How do I check which driver version I have and how can I improve the GFX performance? (I'm talking 2D here, I'm not bothered about 3D rendering)

I have all the eye candy turned off on both OSes.

Cheers,

Mike.

---

### Post by overdrank on 2008-07-29
> **mingle said:**
> Hi,

I'm currently trying out Ubuntu 8.04 on my HP D530S desktop, which has an Intel 82845G graphics chipset.

The screen update is noticeably sluggish when moving windows around and the overall speed of the display update is much slower than running XP on the same box.

I was wondering if it could be that I have an old GFX driver installed, or perhaps it isn't configured correctly.

How do I check which driver version I have and how can I improve the GFX performance? (I'm talking 2D here, I'm not bothered about 3D rendering)

I have all the eye candy turned off on both OSes.

Cheers,

Mike.

Hi and do you have Ubuntu installed or using the live cd? The intel graphics are usually come installed with Ubuntu. If you would like to see the driver that is in use then you can use this command to view and setup your system. ```
gksu displayconfig-gtk
```

---

