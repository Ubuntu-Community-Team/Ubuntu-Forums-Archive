---
title: "How To Reset The Gnome Panel To Default"
date: 2010-06-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Jakiejake on 2010-06-29
To Reset Your Gnome Panel To Default Run This In Terminal
> rm -rf .gconf/apps/panel
Log-Out and log back in and enjoy!
Enjoy!

---

### Post by Jakiejake on 2010-08-23
Anyone used it?

---

### Post by psoulocybe on 2010-08-23
I've used:
> gconftool-2 --recursive-unset /apps/panel

Log off, login.

---

### Post by Jakiejake on 2010-08-24
> **psoulocybe said:**
> I've used:


Log off, login.

Cool!

---

### Post by PrototypeAlex on 2010-08-28
Thanks guys. Was having troubles with getting network manager applet back.

---

### Post by user333 on 2010-09-09
Thanks :)

---

