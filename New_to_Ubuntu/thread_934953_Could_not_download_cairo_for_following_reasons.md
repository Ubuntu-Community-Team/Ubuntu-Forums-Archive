---
title: "Could not download cairo for following reasons"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by gotanothergrot on 2008-10-01
/tmp/cairo-dock_v1.6.1.2_i686.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.

---

### Post by Orange_and_Green on 2008-10-01
If you right-click and select Open with other application, does it give you the option "GDebi package installer"?

If so, try opening it with that.

If not, you might try reinstalling:
```
sudo apt-get install gdebi
```

Hope this helps... good luck:KS

---

### Post by xjgnsdof on 2008-11-03
Select gdebi-gtk (/usr/bin/gdebi/gtk) as the default app.

---

