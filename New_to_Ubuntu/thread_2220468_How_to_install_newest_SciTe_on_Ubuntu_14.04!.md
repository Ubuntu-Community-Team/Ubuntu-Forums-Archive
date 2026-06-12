---
title: "How to install newest SciTe on Ubuntu 14.04!"
date: 2014-04-28
forum: New to Ubuntu
---

### Post by gchmverhaag on 2014-04-28
Hi,

The SciTe editor that came with Ubuntu 13.04 doesn't seem to work properly on 14.04, due to a flashing screen when scrolling!

That's why I want to install the newest version and compile the source!

However this requires GTK2.0 to be installed, but can't figure out how to do that with the package manager that comes with ubuntu!

Can anybody give some hints on how to tackle this issue? Thanks in advance!

Regards,
Gerard

---

### Post by slickymaster on 2014-04-28
You have both the 32-bit and 64-bit deb packages, for SciTe 3.3.5-1, available for download at [UbuntuUpdates.org]("http://www.ubuntuupdates.org/package/core/trusty/universe/base/scite"). All you have to do is to choose which one is suitable for your system, download it and simply double click on it, and then select Install Package.

---

### Post by gchmverhaag on 2014-04-28
Hi,

Thanks for your reply, but unfortunately that's the version (3.3.5-1) causing the problem.

So I need the newest version 3.4.1, and that's not available from the repository and needs to be compiled and installed from source!

Regards,
Gerard

---

### Post by slickymaster on 2014-04-28
> **gchmverhaag said:**
> <...snip...>

However this requires GTK2.0 to be installed, but can't figure out how to do that with the package manager that comes with ubuntu!

Can anybody give some hints on how to tackle this issue? Thanks in advance!

Regards,
Gerard

The package name of GTK2.0 is libgtk2.0-0, so to install it open a terminal window and run the following:```
sudo apt-get install libgtk2.0
```

---

