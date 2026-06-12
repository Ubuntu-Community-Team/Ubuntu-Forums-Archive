---
title: "[SOLVED] bluetooth missing from System menu"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by scotcella on 2008-06-16
Hi all,

When I installed Hardy onto my laptop, I had bluetooth installed in it.

I had problems getting my laptop to recieve but had no problems sending out, but that's another issue altogether.

Now I've just realised I no longer have bluetooth on Hardy at all. How on earth can it disappear like that. How do I get it back? Via Synapotics Manager?

---

### Post by bobnutfield on 2008-06-16
Look in System>Services and make sure it is listed and activated there.  I can't think of a reason it would disappear unless it was uninstalled.

---

### Post by Kevbert on 2008-06-16
It may be due to the bluetooth manager applet not being started.  If you go to System-Preferences-Sessions and check that the Bluetooth Manager is ticked under the Startup tab.  If it isn't you may need to reboot or restart X.
Alternatively, it may be that you've just lost the shortcut. Right-click on Applications and select Edit Menus.  Goto to where you think the menu item should be and there should be a deselected menu item there.  Just make sure it's ticked.  Otherwise you need to install gnome-bluetooth, gnome-vfs-obexftp and bluez-utils (I'm not sure about software source for this one) via Synaptic.

---

