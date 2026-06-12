---
title: "KDE3 theme on GNOME"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Fixman on 2008-05-13
I prefer using a GNOME desktop enviroment but, when I come to use applications designed for KDE 3.5, I found the interface very ugly (those damn blue buttons). So my question is, is there a way to apply a theme for KDE applications while on a GNOME desktop?

---

### Post by sdennie on 2008-05-13
I believe you can change the KDE theme (more specifically the qt theme) without installing tons of KDE stuff by installing the following:

```

sudo apt-get install qt3-qtconfig

```

That should install a new preference in System->Preferences or, you can start the theme selector from the command line with "qtconfig".

---

