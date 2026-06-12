---
title: "Patching X.org vesa driver"
date: 2005-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by khiraly on 2005-09-29
Hi!
I have never patched deb-src package until now. Now (as I have problem with my video driver) I must to patch X.org vesa driver.
I must change only one line in the x.org source:
```

-    if (pScrn->bitsPerPixel >= 8 && pVesa->vbeInfo->Capabilities[0] & 0x01)
+    if (pScrn->bitsPerPixel >= 8 && pVesa->vbeInfo->Capabilities[0] & 0x01 && !(data->data->MemoryModel & 0x6 || data->data->MemoryModel & 0x7))

```
The patch file:
[https://bugs.freedesktop.org/attachment.cgi?id=2065](https://bugs.freedesktop.org/attachment.cgi?id=2065)
More about this bug:
[https://bugs.freedesktop.org/show_bug.cgi?id=2150](https://bugs.freedesktop.org/show_bug.cgi?id=2150)
So I have downloaded the **xserver-xorg-driver-vesa** package source:
```

apt-get source xserver-xorg-driver-vesa --download-only

```
Now I have three file:
```

xorg_6.8.2-72.diff.gz  (2.4MB)
xorg_6.8.2-72.dsc      (2.7kB)
xorg_6.8.2.orig.tar.gz (48MB)

```
How can I patch these files and create a xserver-xorg-driver-vesa package?
Can somebody help me or point to the right tutorial?
Thx in advance, 
Khiraly

---

### Post by Swoop on 2005-09-29
[http://www.ubuntuforums.org/showthread.php?t=22348](http://www.ubuntuforums.org/showthread.php?t=22348)

---

