---
title: "How to get volume control back on panel"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by mrnewtothis on 2012-12-31
I removed the envelope on the panel in unbuntu 10 4 and the volume control also vanished.
I want the volume control back if possible but have no idea as it does not show up in the add to panel box.

So anyone know any way to add the volume and mute option to the panel.

Thanks

---

### Post by ubudog on 2013-01-01
The item you're looking for should be either Indicator Applet Session, Indicator Applet, or Notification Area.

On Ubuntu 10.04 you can also just reset the panels like so:
```
mkdir ~/.oldpanel
```
```
mv ~/.gconf/apps/panel ~/.oldpanel
```
```
gconftool-2 --shutdown
```
```
pkill gnome-panel
```

Hope this helps,
ubudog

---

