---
title: "login screen problem"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by T2manner on 2008-05-07
i used to have xubuntu desktop installed and kubuntu desktop installed.
but i just now uninstalled both of them and removed just about everything that came with them except a few apps.

however, whenever i log on i still see the xfce login screen.
even though under sessions i can't log into xubuntu desktop

how do i get rid of this so i just see the default gnome login screen

---

### Post by Delever on 2008-05-07
If I understand correctly, you uninstalled them. Therefore they do not work.
Do you want to install xubuntu-desktop again?

---

### Post by T2manner on 2008-05-07
no?

when i turn my computer on and i see the login screen
it is the xfce login screen
not the gnome one

but i've uninstalled xubuntu-desktop

i want to get rid of the xfce login screen

---

### Post by frup on 2008-05-07
You mean the splash or the XFCE version of GDM?

The GDM/KDM stuff can be managed through gnome in system > administration > Login window (Actually that only seems to manage GDM) from here I have edited.

If you go in to system>admin>services you will see available services. I can see Gnome Login manager (gdm) ticked. I suppose there will be a KDM and what ever XFCE uses here too.... make sure they are not selected and that GDM is.

The splash can be changed too but at this moment I have hit a blank... Try reinstalling ubuntu-desktop, that might force it.

---

### Post by akiratheoni on 2008-05-07
Type:

```
sudo dpkg-reconfigure gdm
```

Then you should be able to choose which one is used.

---

### Post by T2manner on 2008-05-07
> You mean the splash or the XFCE version of GDM?

The GDM/KDM stuff can be managed through gnome in system > administration > Login window (Actually that only seems to manage GDM) from here I have edited.

If you go in to system>admin>services you will see available services. I can see Gnome Login manager (gdm) ticked. I suppose there will be a KDM and what ever XFCE uses here too.... make sure they are not selected and that GDM is.

The splash can be changed too but at this moment I have hit a blank... Try reinstalling ubuntu-desktop, that might force it.


thanks!
i think that did it

---

