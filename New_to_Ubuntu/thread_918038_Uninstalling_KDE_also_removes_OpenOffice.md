---
title: "Uninstalling KDE also removes OpenOffice"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by marty1011 on 2008-09-12
Hello everyone,
few months ago I was playing with KDE and GNOME and decided to settle with GNOME. So I uninstalled KDE and in the process I lost OpenOffice (I fixed that issue :)). But just fixing the issue has left me unsatisfied. Now I want to know what exactly went wrong. Uninstalling the KDE should only remove WM and DE related files.

I used ```
sudo aptitude install kubuntu desktop
```to install and ```
sudo aptitude remove kubuntu desktop
```to uninstall KDE.

**Should I have used apt-get instead** (I read somewhere that using aptitude for metapackages are better than apt-get).

Also, having more than one DE creates a mess in the menue, especially in GNOME. Is there any way to make it cleaner?

Thanks!

---

### Post by cdtech on 2008-09-12
To prevent KDE apps from showing up in Gnome menus and vice-versa, do the following:

If you use the Gnome desktop (like I do) try this:

Make a backup:
```
mkdir ~/.desktopbackup
cp -R /usr/share/applications/ ~/.desktopbackup
```
On a command line type:
```
for i in /usr/share/applications/kde/*; do echo "OnlyShowIn=KDE;" | sudo tee -a $i; done
```
You could also do the same with KDE by changing it to:
```
for i in /usr/share/applications/*; do echo "OnlyShowIn=GNOME;" | sudo tee -a $i; done
```

Hope this helps.........

---

### Post by SunnyRabbiera on 2008-09-12
> **marty1011 said:**
> Hello everyone,
few months ago I was playing with KDE and GNOME and decided to settle with GNOME. So I uninstalled KDE and in the process I lost OpenOffice (I fixed that issue :)). But just fixing the issue has left me unsatisfied. Now I want to know what exactly went wrong. Uninstalling the KDE should only remove WM and DE related files.

I used ```
sudo aptitude install kubuntu desktop
```to install and ```
sudo aptitude remove kubuntu desktop
```to uninstall KDE.

**Should I have used apt-get instead** (I read somewhere that using aptitude for metapackages are better than apt-get).

Also, having more than one DE creates a mess in the menue, especially in GNOME. Is there any way to make it cleaner?

Thanks!

In this case yes apt might have been better.
as for you menu entries, if you remove your KDE files such as kdebase and the like you should be able to have less clutter.

---

