---
title: "debian menu"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by nynoah on 2008-08-20
Does anyone know how to get the Debian menu to install on Ubuntu.  I use to have that on my older system like 2 years ago.  Do they still have this in Hardy?

---

### Post by kellemes on 2008-08-20
```
sudo apt-get install menu
sudo apt-get install menu-xdg
sudo update-menus
```

See if its already visible..
If not then right-click on applications tab and select "menu editor", tick the debian-menu checkbox and repeat..
```
sudo update-menus
```

---

### Post by ubuntu27 on 2008-08-20
Install Debian menu:

Code:

```
sudo apt-get install menu menu-xdg
```

Update the menu entries in Debian Menu:

Code:

```
sudo update-menus
```

See if that helps.

If that doesn't work, try the following

Code:

```
sudo dpkg-reconfigure menu
```

Code:

```
sudo dpkg-reconfigure menu-xdg
```

And again:
Code:

```
sudo update-menus
```


You may also want to Kill X or Log Out and Log-in UBuntu

---

### Post by nynoah on 2008-08-20
Got it now, thanks guys.  I wonder, why is it that the Ubuntu menu does not show as many programs as the Debian menu will?

---

