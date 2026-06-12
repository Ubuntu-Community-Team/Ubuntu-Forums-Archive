---
title: "working as root"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by geomur on 2008-07-28
Hi Folks,

Bit stuck on an aspect of working as root.  I cannot cut and paste into a folder using GNOME as access is denied because I'm not root.  Do I have to do these things via a terminal / sudo, or is there a way of accessing root and performing these functions via the GUI?

many thanks

Geoff

---

### Post by northern lights on 2008-07-28
You can also start graphical applications as root. In gnome/xfce use ```
gksu COMMAND
```Since you want to move/copy files you'd need to run ```
gksu 'nautilus --no-desktop'
```
(The '--no-desktop' flag is necessary as nautilus also draws the desktop in gnome and you'd end up with the root's preferences and wallpaper without it...)

---

### Post by eightmillion on 2008-07-28
You can open a nautilus window as root with
> gksudo nautilus

---

### Post by geomur on 2008-07-28
Many thanks, folks.  That should get me going!

Best wishes

Geoff

---

### Post by coffeecat on 2008-07-28
Add this to your bookmarks:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

After you've read it, of course. :wink:

---

