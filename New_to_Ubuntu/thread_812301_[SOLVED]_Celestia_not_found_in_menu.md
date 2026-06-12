---
title: "[SOLVED] Celestia not found in menu"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Stargazer777 on 2008-05-29
I uploaded celestia using Applications>Accessories>Terminal and now I can only find it when i click on show search entry>search: celestria> execute celestia. Is it supposed to be in the education menu? (its not) And does any one know how to get it there?

---

### Post by unutbu on 2008-05-29
Go to your gnome-panel menu. Click System>Preferences>Main Menu. Click on Education in the left panel, and then the '+ New Item' button on the right. Add a new menu item with the name celestia (or anything you like) and command

```
/usr/bin/celestia
```

Tip: When you install a package (e.g. celestia), you can find out what files it installs by typing 

```
dpkg --listfiles <package>
```
or, in this case,
```
dpkg --listfiles celestia
```
The executable file provided by the package is usually installed in a directory with the word 'bin' in its path. So you can usually find the executable by typing 

```
dpkg --listfiles celestia | grep bin
```
If you type that in the terminal, you should get
```
/usr/bin/celestia
```

---

