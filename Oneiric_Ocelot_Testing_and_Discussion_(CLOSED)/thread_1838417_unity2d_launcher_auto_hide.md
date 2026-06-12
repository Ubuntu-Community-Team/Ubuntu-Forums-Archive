---
title: "unity2d launcher auto hide"
date: 2011-09-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2011-09-03
How do i stop the auto hide of the launcher for 2d? Have tried the settings tool but the options are greyed out.

---

### Post by lucazade on 2011-09-03
> **sonicb00m said:**
> How do i stop the auto hide of the launcher for 2d? Have tried the settings tool but the options are greyed out.

to disable launcher autohide in unity2d
```
gsettings set com.canonical.Unity2d.Launcher hide-mode 0
gsettings set com.canonical.Unity2d.Launcher use-strut true
```

to enable autohide 
```
gsettings set com.canonical.Unity2d.Launcher hide-mode 2
gsettings set com.canonical.Unity2d.Launcher use-strut false
```

---

### Post by sonicb00m on 2011-09-04
Thanks, that fixed it. Seems the keys were totally missing in dconf-editor.

---

### Post by lucazade on 2011-09-04
you're welcome

---

