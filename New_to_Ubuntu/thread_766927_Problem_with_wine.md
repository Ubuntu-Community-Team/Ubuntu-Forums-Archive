---
title: "Problem with wine"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by rajaram_s on 2008-04-25
I installed and few softwares in wine some time back. I then uninstalled some of them using the uninstall wizard. The problem is tough the software is uninstalled and non usable, it still keeps showing up on the programs menu. What do I do?

---

### Post by swoll1980 on 2008-04-25
you could right click the start menu then click edit menus and delete them that way

---

### Post by yabbies on 2008-04-25
the wine uninstall doesn't uninstall the menu items
you have to do that manually
as swoll has said
it's also useful to navigate to your .wine folder and make sure everything has been uninstalled from your c: directory.

---

### Post by rajaram_s on 2008-04-25
Ya.. thank you. I was able to take them off my menu that way. I checked the .wine folder too. It has not traces of the installed programs. But, I still feel the startup item exists since, I have only deselected the item from the prog folder. Anytime it can be reenabled. Also, in KDE, it shows up as the most recently used app after months of deletin it.

---

### Post by yabbies on 2008-04-25
you can always check the wine registry to make sure all remnants have been uninstalled

```
wine .wine/drive_c/windows/regedit.exe
```

Then navigate to

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Curr entVersion\Uninstall

Each item listed there represents a listing in the WINE Application Uninstaller. If you delete the key, you will remove the application name from the list in the uninstaller.

---

### Post by mc4man on 2008-04-25
The actual menus for individual programs installed in wine are stored in home directory @ .config/menus/applications-merged   (in gutsy, hardy)

---

### Post by rajaram_s on 2008-04-28
Great... i'll try them and get back wit the results........

---

