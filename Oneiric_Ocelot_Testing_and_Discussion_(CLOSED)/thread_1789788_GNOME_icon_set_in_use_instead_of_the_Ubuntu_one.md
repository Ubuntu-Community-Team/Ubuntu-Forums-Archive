---
title: "GNOME icon set in use instead of the Ubuntu one"
date: 2011-06-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-06-24
I have two up-to-date machines. One shows me the usual Humanity/Mono icons, the other one uses the GNOME icon set. How can I fix this?

Both machines return 'ubuntu-mono-dark' when issuing ```
gsettings get org.gnome.desktop.interface icon-theme
```

---

### Post by godhika on 2011-06-24
have you tried to change the icon-theme via gnome-tweak-tools ?
Maybe that works

---

### Post by Quadunit404 on 2011-06-24
> **godhika said:**
> have you tried to change the icon-theme via gnome-tweak-tools ?
Maybe that works

I have this same problem, tried GNOME Tweak Tool and that didn't work.

---

### Post by jfernyhough on 2011-06-24
Does it not use dconf now rather than gconf?

---

### Post by MacUntu on 2011-06-24
Yes.

---

### Post by tekstr1der on 2011-06-24
Do the Gnome icons show up on every boot?
Perhaps this race condition still affecting natty, and I'd assume oneiric is what you're seeing?
[https://bugs.launchpad.net/linuxmint/+bug/649809](https://bugs.launchpad.net/linuxmint/+bug/649809)

Happens to me every so often.

EDIT: Looks like this would be irrelevant if you're using lightdm.

---

### Post by lucazade on 2011-06-24
I don't know what is the cause of MacUntu issue but i'm enough sure it is not related to that bug report.
That issue is strictly related to gnome-settings-daemon, gdm and xrandr patch inside indicators.
Using lightdm this issue is no more present.

---

### Post by MacUntu on 2011-06-28
After recent updates it went away (I suspect something gdk-pixbuf related).

---

