---
title: "trying link png routines from libQt"
date: 2007-09-21
forum: Programming Talk
---

### Post by dluciv on 2007-09-21
In Ubuntu 6.10 everything was ok.

In Ubuntu 7.04 when I am trying to build any Qt application,
linker says following:

```
...
/usr/lib/libQtGui.so: undefined reference to `png_create_write_struct@PNG12_0'
/usr/lib/libQtGui.so: undefined reference to `png_write_end@PNG12_0'
/usr/lib/libQtGui.so: undefined reference to `png_set_filler@PNG12_0'
/usr/lib/libQtGui.so: undefined reference to `png_set_bgr@PNG12_0'
...
```

I properly run ./configure before make and it reports ok.
I have libpng-dev and libpngwriter-dev, however I can not imagine why does it try to locate libpng's routines in libqt...

Can You please help me with it?
Thank You.

---

