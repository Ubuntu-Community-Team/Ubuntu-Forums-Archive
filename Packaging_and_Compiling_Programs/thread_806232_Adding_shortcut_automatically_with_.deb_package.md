---
title: "Adding shortcut automatically with .deb package"
date: 2008-05-24
forum: Packaging and Compiling Programs
---

### Post by Steve413z on 2008-05-24
Hello,

I'm trying to make a .deb package for a program, but what is the easiest way to make a shortcut appear in the Applications menu automatically when the user installs the deb package?

---

### Post by Steve413z on 2008-05-25
bump

---

### Post by laney on 2008-05-25
> **Steve413z said:**
> Hello,

I'm trying to make a .deb package for a program, but what is the easiest way to make a shortcut appear in the Applications menu automatically when the user installs the deb package?

You want to install a .desktop file into /usr/share/applications. Check [this page]("https://wiki.ubuntu.com/PackagingGuide/SupplementaryFiles#head-7a414412d5ee2b400b8e65afe39eb131116c3efd").

---

