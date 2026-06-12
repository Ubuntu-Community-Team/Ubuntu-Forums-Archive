---
title: "How do you open Seahorse?"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by tom15 on 2013-08-15
I saved a couple passwords in it earlier as a test, nothing important. Now though, I start the program and all I have is a little green + to add new items, nothing indicates how to retrieve already stored items. If I try to add a password to the ring I created earlier it says "cannot add to locked ring" or similar.

I'm not going to use this as my password manager but would like to get in and remove the stuff I added.

Thanks!

---

### Post by stinkeye on 2013-08-15
> **tom15 said:**
> I saved a couple passwords in it earlier as a test, nothing important. Now though, I start the program and all I have is a little green + to add new items, nothing indicates how to retrieve already stored items. If I try to add a password to the ring I created earlier it says "cannot add to locked ring" or similar.

I'm not going to use this as my password manager but would like to get in and remove the stuff I added.

Thanks!

Passwords I have saved are accessible. 
Choose view > by keyring and select show personal.
My passwords were saved in "Login" and is unlocked when I login or can be unlocked within seahorse
by right clicking on the lock icon.

---

### Post by tom15 on 2013-08-15
> **stinkeye said:**
> Passwords I have saved are accessible. 
Choose view > by keyring and select show personal.
My passwords were saved in "Login" and is unlocked when I login or can be unlocked within seahorse
by right clicking on the lock icon.

Mine doesn't look like that. Mine has a white screen with the green + and a filter field, nothing else.

---

### Post by stinkeye on 2013-08-15
...and your view menu...

---

### Post by tom15 on 2013-08-15
> **stinkeye said:**
> ...and your view menu...

Nope, not finding a view menu.

---

### Post by stinkeye on 2013-08-15
In unity I disable the global menu but re-enabled for the purpose of this screenshot.
Mouse over left side of panel.

---

### Post by tom15 on 2013-08-15
I have nothing. I'm installing another distro now, as soon as it finishes I'll fire Ubuntu back up and see if I can get a screenshot.

---

### Post by stinkeye on 2013-08-16
> **tom15 said:**
> I have nothing. I'm installing another distro now, as soon as it finishes I'll fire Ubuntu back up and see if I can get a screenshot.
OK.
You can also try starting seahorse with this command which should show the menu in both the panel
and within seahorse.
```
APPMENU_DISPLAY_BOTH=1 seahorse
```

[COLOR="#FF0000"]EDIT[/COLOR]: The above doesn't appear to work in 13.04 but you can disable the global menu completely with...
(or boot into another desktop environment if installed)
```
echo '[ "$DESKTOP_SESSION" = "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
Log out/in


To renable...
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
Log out/in

---

### Post by tom15 on 2013-08-16
OK, with global menu disabled I can get in. I've cleaned my stuff out, should I re-enable global menu or leave it disabled? Other applications affected?

---

### Post by stinkeye on 2013-08-16
> **tom15 said:**
> OK, with global menu disabled I can get in. I've cleaned my stuff out, should I re-enable global menu or leave it disabled? Other applications affected?
It will affect all applications and users.
Personal choice really.
I leave it disabled because I use most applications in a non maximized state and find it annoying to
have to go to the panel for the menu.

---

### Post by tom15 on 2013-08-16
> **stinkeye said:**
> It will affect all applications and users.
Personal choice really.
I leave it disabled because I use most applications in a non maximized state and find it annoying to
have to go to the panel for the menu.

OK, I'm not big on maximizing either. I'll leave it this way for now. Thank you so much for your help!

---

