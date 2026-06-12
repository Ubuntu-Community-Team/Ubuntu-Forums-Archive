---
title: "ubuntu side bar in gnome"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-05-14
Hey guys

I've been trying to get the borders back on my windows in Ubuntu 12.04, running in gnome classic. I typed unity --rest into the terminal which gave me my borders back .. but also added the ubuntu side panel on the left. (screenshot)
how do i get rid of it now - but still keep the borders on my windows?

Thank you

Km

---

### Post by Frogs Hair on 2012-05-14
You have started unity in Gnome and you can disable it by opening the ccsm and removing the check from the Unity Plug-in box. Reseting unity will not resolve problems in Gnome and once Unity is disabled the problem may return. When you disable Unity report back.

---

### Post by kabukiM0n0 on 2012-05-14
> **Frogs Hair said:**
> You have started unity in Gnome and you can disable it by opening the ccsm and removing the check from the Unity Plug-in box. Reseting unity will not resolve problems in Gnome and once Unity is disabled the problem may return. When you disable Unity report back.


Hmm .. I ran ccsm and it automatically went back to how it was - made my top panel integrate better to my screen and the borders are still there. Seems they stuck, at least for the time being. 

Thank you

---

### Post by HiImTye on 2012-05-14
by borders do you mean menus? if so then issue this command:
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```
if you use Firefox then you will need to disable the global menu extension in Firefox to get your menus back in firefox

once you're done that, log out and log into gnome, your unity bar will no longer be there

---

