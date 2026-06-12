---
title: "Removable media opens in VLC"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by vsiddhu on 2011-10-25
Hi,
I upgraded from 11.04 to 11.10 and after I did the upgrade I wanted to open my removable media(seagate external drive) from the Doc that comes on the left pane.
But when I click on the Icon for the removable media, the external drive opens up in VLC Player!
How do I get it to open in Nautilus?

---

### Post by mc4man on 2011-10-25
Open up a terminal & 
```
gedit ~/.local/share/applications/mimeapps.list
```

In the **[Default Applications]** section there will be a line
inode/directory=nautilus-folder-handler.desktop
Delete the whole line or you can change it to this, then do a log out if need be
```
inode/directory=nautilus-home.desktop
```
bug on
[https://bugs.launchpad.net/bugs/876788](https://bugs.launchpad.net/bugs/876788)

---

