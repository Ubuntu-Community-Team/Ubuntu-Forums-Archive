---
title: "Ubuntu Software centre is not loading"
date: 2021-04-09
forum: New to Ubuntu
---

### Post by ambar686413 on 2021-04-09
Hello,
I am unable to open software centre as it is not loading after clicking on it. I am new to ubuntu. Please help me.
Regards and Thanks in advance.

---

### Post by CelticWarrior on 2021-04-09
Make sure the system is fully updated by terminal commands:
```
sudo apt update && sudo apt full-upgrade
```

---

### Post by ambar686413 on 2021-04-09
Thanks for response buddy, I have done it but after that still ubuntu software center is not loading. It is trying to open the app but ultimately getting vanished from the upper status bar as I am sharing the screenshot.

---

### Post by CelticWarrior on 2021-04-09
> **ambar686413 said:**
> I have done it but after that still ubuntu software center is not loading. 
So should we assume there were no errors reported and the system is fully updated?
If so please run 'gnome-software' in terminal and post back the error messages in full.

---

### Post by tea for one on 2021-04-09
Also, in a terminal, please run and post output:-
```
snap-store
```

I think that gnome-software is called Software and snap-store is called Ubuntu Software.

---

### Post by ambar686413 on 2021-04-09
> **tea for one said:**
> Also, in a terminal, please run and post output:-
```
snap-store
```

I think that gnome-software is called Software and snap-store is called Ubuntu Software.


[B]I have ran the command- snap-store, following is the output. 
[/B]
ambar@ambar-HP-Notebook:~$ snap-store
02:56:09:0229 Gtk Failed to load module "canberra-gtk-module"
02:56:09:0231 Gtk Failed to load module "canberra-gtk-module"
02:56:09:0290 Gs  enabled plugins: desktop-categories, fwupd, os-release, packagekit, packagekit-local, packagekit-offline, packagekit-proxy, packagekit-refine-repos, packagekit-refresh, packagekit-upgrade, packagekit-url-to-app, appstream, desktop-menu-path, hardcoded-blocklist, hardcoded-popular, modalias, odrs, packagekit-refine, rewrite-resource, packagekit-history, provenance, snap, systemd-updates, generic-updates, provenance-license, icons, key-colors, key-colors-metadata
02:56:09:0290 Gs  disabled plugins: dpkg, dummy, fedora-langpacks, fedora-pkgdb-collections, repos
02:56:09:0448 Gs  /etc/PackageKit/Vendor.conf file not found
02:56:09:0883 Gtk Could not load a pixbuf from icon theme.
This may indicate that pixbuf loaders or the mime database could not be found.
**
Gtk:ERROR:../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /snap/snap-store/518/data-dir/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)
Bail out! Gtk:ERROR:../gtk/gtkiconhelper.c:494:ensure_surface_for_gicon: assertion failed (error == NULL): Failed to load /snap/snap-store/518/data-dir/icons/Yaru/16x16/status/image-missing.png: Unrecognized image file format (gdk-pixbuf-error-quark, 3)
Aborted (core dumped)
ambar@ambar-HP-Notebook:~$

---

### Post by tea for one on 2021-04-10
Your output does not indicate a healthy snap-store.

Please try;-
```
sudo snap refresh snap-store
```

Alternatively, to remove and re-install, please try:-
```
sudo snap remove snap-store
```
```
sudo snap install snap-store
```

---

