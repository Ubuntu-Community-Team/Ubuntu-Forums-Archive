---
title: "Adjust to KDE theme?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by thevjm on 2008-05-04
I am running Ubuntu 8.04 w/ GNOME.

Is it possible for KTorrent to automatically adjust to the color scheme which I set in the theme manager? Similar to the way Amarok does.

---

### Post by Happy_Man on 2008-05-04
KTorrent, AFAIK, doesn't do that. I think you will need to install the KDE theme manager to get it to change.

---

### Post by thevjm on 2008-05-04
How to I get the KDE theme manager?

I installed kcontrol, which also installed *a* theme manager. I have been using that one to change the colors and icons in Amarok. It doesn't seem to affect Ktorrent, though.

---

### Post by thevjm on 2008-05-04
Bump

---

### Post by thevjm on 2008-05-04
Is this possible? I have seen some screenshots of KTorrent, and they look different than mine.

---

### Post by thevjm on 2008-05-04
Final bump. Sorry.

---

### Post by Can+~ on 2008-05-04
> **thevjm said:**
> How to I get the KDE theme manager?

I installed kcontrol, which also installed *a* theme manager. I have been using that one to change the colors and icons in Amarok. It doesn't seem to affect Ktorrent, though.

Maybe KTorrent was made with QT3 directly, like Virtualbox. Try using the qt3 theme manager:

```
sudo apt-get install qt3-qtconfig
```

It won't download a truckload of files like kcontrol does, when installed you can execute it with:

```
qt3-qtconfig
```

But.. why KTorrent? Why not something that does not need KDE/QT Like Deluge or Transmission?

---

