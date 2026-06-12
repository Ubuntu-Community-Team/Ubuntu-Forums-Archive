---
title: "Where has the &quot;Dim display when idle&quot;-option gone in Oneiric?"
date: 2011-09-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Ader_ on 2011-09-27
Where has the "Dim display when idle"-option gone in Oneiric?

---

### Post by RomeReactor on 2011-09-27
Hi. I think those setting will eventually be in System Settings (Power Cog->System Settings->Screen) but that is still a work in progress. See [this thread]("http://ubuntuforums.org/showthread.php?t=1832942") for more on that. You can install dconf-editor:
```
sudo apt-get install donf-editor
```
and go to **org->gnome->settings-daemon->plugins->power** (as per posts [16]("http://ubuntuforums.org/showpost.php?p=11199852&postcount=16") and [17]("http://ubuntuforums.org/showpost.php?p=11199881&postcount=17") on that thread), though not all the options there seem to work correctly.

---

### Post by Ader_ on 2011-09-28
Great! Thanks!

---

### Post by pressureman on 2011-09-28
System Settings > Screen

Option is labeled as "Dim screen to save power".

---

