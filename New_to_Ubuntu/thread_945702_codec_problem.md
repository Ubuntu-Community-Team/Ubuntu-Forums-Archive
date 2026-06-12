---
title: "codec problem"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by wahti on 2008-10-12
this pops up when i try to download Gstreamer codec (W: failed to fetchhttp://usarchive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.7-3ubuntu1_i386.deb)

---

### Post by Nepherte on 2008-10-12
It should be [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com). Can you verify if that's what it says in /etc/apt/sources.list:
```
gksudo gedit /etc/apt/sources.list
```

---

