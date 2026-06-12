---
title: "Uninstalled wine, cannot remove folder from apps menu"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by UnWarierMage224 on 2008-05-05
Hi folks, 

so i uninstalled wine and I cannot remove the folder from the applications menu. I did check `/.local/... wherever you're supposed to check and there is no .wine folder in the applications director, although using the edit menus function the wine folder still shows up and is undeleteable. I tried using sudo alacarte but under that the wine folder does not show up. 

thanks, 

-'Mage

---

### Post by forrestcupp on 2008-05-05
Go to System->Preferences->Main Menu.  You can't delete the Wine menu option, but click on it and uncheck everything in there.  Now it should be gone from your menus.

---

### Post by forestpixie on 2008-05-05
Can you clarify what it is you are trying to do please.

---

### Post by UnWarierMage224 on 2008-05-05
When I right click on applications --> edit menus the WINE folder still shows up in that list even though it doesn't show up on the apps menu. Wine is uninstalled. I checked the folder ~/.local/share/applications and there is no .wine folder in there... How do I get the wine folder from not showing up in the edit menus list?

---

### Post by forestpixie on 2008-05-05
There is another wine folder in your /home - it's hidden .wine

Do as forestcupp says to disable wine from menu

---

### Post by roderick on 2008-05-05
> **UnWarierMage224 said:**
> When I right click on applications --> edit menus the WINE folder still shows up in that list even though it doesn't show up on the apps menu. Wine is uninstalled. I checked the folder ~/.local/share/applications and there is no .wine folder in there... How do I get the wine folder from not showing up in the edit menus list?

These folders are in ~/.local/share/applications/wine and ~/.local/share/desktop-directories/wine-*

If you open a console/terminal and remove them, the wine shortcut in the menu and any other wine shortcuts will be removed from your profile.

```
rm -rf ~/.local/share/applications/wine
rm -rf ~/.local/share/desktop-directories/wine-*
```

Unfortunately, there is no simpler way. I hope that someone corrects this in future releases, as wine get's better integration in the desktop.

---

### Post by UnWarierMage224 on 2008-05-05
OK, I think that worked!
Thanks. 

-'Mage

---

### Post by roderick on 2008-05-05
No problem :)

---

