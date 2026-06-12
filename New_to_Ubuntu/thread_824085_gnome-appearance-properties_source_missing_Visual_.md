---
title: "gnome-appearance-properties source missing Visual Effects tab"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by mevets on 2008-06-09
I downloaded the gnome-control-center source using apt-get hoping to inspect the source of gnome-appearance-properties. I wanted to edit to Visual Effect tab of gnome-appearance-properties, but when I found the glade file and loaded it up I found the gui but without the Visual Effects tab.

Is the Visual Effects tab's glade file included in another source package?

---

### Post by iaculallad on 2008-06-09
> **mevets said:**
> I downloaded the gnome-control-center source using apt-get hoping to inspect the source of gnome-appearance-properties. I wanted to edit to Visual Effect tab of gnome-appearance-properties, but when I found the glade file and loaded it up I found the gui but without the Visual Effects tab.

Is the Visual Effects tab's glade file included in another source package?

Do you use the compiz-effect?

> sudo apt-get update && sudo apt-get upgrade
sudo apt-get install compizconfig-settings-manager

---

### Post by Drakkor on 2008-06-09
Try installing the compizconfig-settings-manager, it's in Synaptic :)
Then go to System>Preferences>Advanced Desktop Effects Settings.

---

### Post by mevets on 2008-06-09
Maybe it was the way I phrased it but, I want to download the source of the visual effects tab so I can make my own modifications to the source. I dont want to install ccsm in order to edit my compiz configuration.

---

