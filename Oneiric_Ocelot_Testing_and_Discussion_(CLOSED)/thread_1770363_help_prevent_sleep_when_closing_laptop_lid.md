---
title: "help: prevent sleep when closing laptop lid"
date: 2011-05-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by yelo3 on 2011-05-29
Hello, I've read that it's no more possible to edit the default power management behavior for the lid closed action.
Actually the option is disappeared from the power menu.

Do you know any other way of doing it?
Thanks

---

### Post by MacUntu on 2011-05-29
Install dconf-tools and run dconf-editor.

org.gnome.settings-daemon.plugins.power

[ATTACH]193520[/ATTACH]

---

### Post by yelo3 on 2011-05-29
Thanks!!!

---

