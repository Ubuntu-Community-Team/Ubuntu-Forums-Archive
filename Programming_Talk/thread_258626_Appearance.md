---
title: "Appearance"
date: 2006-09-16
forum: Programming Talk
---

### Post by inktomi7 on 2006-09-16
Hi there. 

I've written a small app using the Qt Toolkit on GNOME. Now I have added the app in the *Applications* menu and executes the command *gksudo print-ctrl*. The problem is that when I run it through the menu, the app looks ugly with over proportionate fonts, however if I double click on the binary file everything looks fine (using the set KDE theme).

Any ideas how to force it retain the KDE theme on GNOME when executed with the command gksudo *print-ctrl*? 

Thanks

---

### Post by nereid on 2006-09-16
gksudo uses the root user settings. Maybe you haven't styled your root user?

---

