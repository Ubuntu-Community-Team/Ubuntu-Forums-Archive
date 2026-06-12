---
title: "HOWTO: Add other sessions to GDM - kde openbox etc."
date: 2004-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Magneto on 2004-11-01
It took awhile for me to find the correct info on this topic.
I just installed openbox and wanted to start it without using startx so here is what you do.

To add another session to the Sessions list within GDM you must add a .desktop file to /usr/share/xsessions.

The format of the file is
```

[Desktop Entry]
Encoding=UTF-8
# Custom entry - YAY
Name=OpenBox
Comment=Finally
Exec=openbox
Icon=
Type=Application

```

save this file as openbox.desktop

now openbox will be in the gdm sessions list

This works for any other desktop manager as well- Flux,Blackbox,KDE etc 
just modify the** Exec={command} **entry to suit your needs.

Changing the sessions list has varied from gnome version to version(maybe not anymore) and OS to OS.

---

