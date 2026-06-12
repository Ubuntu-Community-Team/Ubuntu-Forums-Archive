---
title: "Wrong dependency on usb-creator-gtk 0.2.31"
date: 2011-07-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-28
The new version (0.2.31) of usb-creator does have an unnecessary dependence.
Now usb-creator-gtk depends on gir1.2-unity-3.0 and libunity4.
This is unnecessary in cases where Unity is not even installed.
I use only gnome-shell and as a fallback gnome-panel.

Usb-creator-gtk should recommend gir1.2-unity-3.0, not depend on it.

> usb-creator (0.2.31) oneiric; urgency=low
  * Add Unity progress support.  Thanks Robert Roth!

---

### Post by tedpome on 2011-07-28
I agree: dependency on unity and unitylibs for those using other desktops and gui's will only create conflict for those exercising the freedom of choice. TP

---

### Post by Harry33 on 2011-07-29
> **tedpome said:**
> I agree: dependency on unity and unitylibs for those using other desktops and gui's will only create conflict for those exercising the freedom of choice. TP

Right, I made a bug report (817718) here:

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/817718](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/817718)

---

