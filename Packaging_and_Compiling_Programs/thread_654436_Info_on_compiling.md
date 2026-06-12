---
title: "Info on compiling"
date: 2007-12-31
forum: Packaging and Compiling Programs
---

### Post by fparri on 2007-12-31
I need some advice about compiling.
I would like to compile the new bluez-gnome tarball and I can download the missing libraries needed to go on,
When I apt-get one of them, though, it brings with it a lot of other libraries. Is there a way so that I can remove them once I compiled the package?

Thanks a lot in advance :)

---

### Post by foolsh on 2007-12-31
dont "apt-get install" them use "aptitude install" instead.
Aptitude keeps track of all extra packages so when you remove the first package the rest go as well.

---

### Post by fparri on 2007-12-31
Perfect that's exactly what I needed :)

---

