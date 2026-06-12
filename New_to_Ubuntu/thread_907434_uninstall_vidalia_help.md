---
title: "uninstall vidalia help ?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by madmak on 2008-09-01
Hia i had a problem with using vidalia that comes as the deb file it just kept freezing evry time it tried to connect to tor so iv installed the latest version from the source code on vidalia's website only to find that wont work for me either but when iv tried to uninstall it with make uninstall theres nothing happening its just telling me

```
make: *** No rule to make target `uninstall'.  Stop.
```

Does anybody know if theres an uninstall script for this or a way to remove vidalia, its doin my head in now :confused:

cheers guys

---

### Post by atomictoaster on 2008-11-12
Hey I just had the same issue. Turns out you need to look in the install_manifest.txt file where the vidalia directory is and remove any files listed in there (sudo rm -rf $LISTEDFILES). If you still have the icon on your gnome-menu, you can go to preferences>main menu>internet and remove vidalia.

---

