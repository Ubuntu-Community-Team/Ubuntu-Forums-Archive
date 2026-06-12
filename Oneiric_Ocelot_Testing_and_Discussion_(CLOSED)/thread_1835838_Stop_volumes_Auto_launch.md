---
title: "Stop volumes Auto launch"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-08-30
How do I stop USB devices from auto launching? I can't find any options any longer for this.

Really hate it when a new nautilus window is loaded when I plug my phone or USB drive in.

---

### Post by mc4man on 2011-08-30
try setting option shown in screen to false (dconf-editor

or - 
```
gsettings set org.gnome.desktop.media-handling automount-open false
```

---

### Post by sonicb00m on 2011-08-30
Thanks!

---

