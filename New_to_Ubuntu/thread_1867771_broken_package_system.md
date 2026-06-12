---
title: "broken package system"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by jakelong00 on 2011-10-23
i found that  --libreoffice-core-- is broken and i um unable to install anything new.
how to fix this??
thnx in advance

---

### Post by TeoBigusGeekus on 2011-10-23
How did you find out?
Can you post the exact error messages you get?

---

### Post by jakelong00 on 2011-10-23
when i upgraded from 11.04 to 10 there were many errors for libre office.

i used the command -
sudo apt-get autoremove

----------------------------------------------------------

The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-calc : Depends: libreoffice-base-core (= 1:3.3.3-1ubuntu2) but 1:3.4.3-3ubuntu2 is installed
 libreoffice-common : Breaks: libreoffice-core (< 1:3.4~) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
 python-uno : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is installed
E: Unmet dependencies. Try using -f.

-----------------------------------------------------------
and when i try to install somthing like

sudo apt-get install gnome-shell
it shows

------------------------------------------------------------

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 but it is not going to be installed
               Depends: gir1.2-cogl-1.0 but it is not going to be installed
               Depends: gir1.2-folks-0.6 but it is not going to be installed
               Depends: gir1.2-gee-1.0 but it is not going to be installed
               Depends: gir1.2-json-1.0 but it is not going to be installed
               Depends: gir1.2-mutter-3.0 but it is not going to be installed
               Depends: gir1.2-networkmanager-1.0 but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not going to be installed
               Depends: gir1.2-telepathylogger-0.2 but it is not going to be installed
               Depends: gjs (>= 1.29.18) but it is not going to be installed
               Depends: libgjs0c (>= 1.29.18) but it is not going to be installed
               Depends: libmutter0 (>= 3.1.92) but it is not going to be installed
               Depends: caribou but it is not going to be installed
               Depends: gnome-icon-theme-full but it is not going to be installed
               Depends: gir1.2-accountsservice-1.0 but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not going to be installed
               Depends: gir1.2-polkit-1.0 but it is not going to be installed
               Depends: gir1.2-upowerglib-1.0 but it is not going to be installed
               Depends: mesa-utils but it is not going to be installed
               Recommends: gnome-themes-standard but it is not going to be installed
               Recommends: cups-pk-helper but it is not going to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-calc : Depends: libreoffice-base-core (= 1:3.3.3-1ubuntu2) but 1:3.4.3-3ubuntu2 is to be installed
 libreoffice-common : Breaks: libreoffice-core (< 1:3.4~) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 python-uno : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

-------------------------------------------------

---

### Post by TeoBigusGeekus on 2011-10-23
Well... try to do what it tells you
```
sudo apt-get install -f
```

---

### Post by jakelong00 on 2011-10-23
sudo apt-get install -f gnome-shell

-------------------------------------------
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gnome-shell : Depends: gir1.2-clutter-1.0 but it is not going to be installed
               Depends: gir1.2-cogl-1.0 but it is not going to be installed
               Depends: gir1.2-folks-0.6 but it is not going to be installed
               Depends: gir1.2-gee-1.0 but it is not going to be installed
               Depends: gir1.2-json-1.0 but it is not going to be installed
               Depends: gir1.2-mutter-3.0 but it is not going to be installed
               Depends: gir1.2-networkmanager-1.0 but it is not going to be installed
               Depends: gir1.2-telepathyglib-0.12 but it is not going to be installed
               Depends: gir1.2-telepathylogger-0.2 but it is not going to be installed
               Depends: gjs (>= 1.29.18) but it is not going to be installed
               Depends: libgjs0c (>= 1.29.18) but it is not going to be installed
               Depends: libmutter0 (>= 3.1.92) but it is not going to be installed
               Depends: caribou but it is not going to be installed
               Depends: gnome-icon-theme-full but it is not going to be installed
               Depends: gir1.2-accountsservice-1.0 but it is not going to be installed
               Depends: gir1.2-gkbd-3.0 but it is not going to be installed
               Depends: gir1.2-polkit-1.0 but it is not going to be installed
               Depends: gir1.2-upowerglib-1.0 but it is not going to be installed
               Depends: mesa-utils but it is not going to be installed
               Recommends: gnome-themes-standard but it is not going to be installed
               Recommends: cups-pk-helper but it is not going to be installed
               Recommends: gnome-session-fallback but it is not going to be installed
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-calc : Depends: libreoffice-base-core (= 1:3.3.3-1ubuntu2) but 1:3.4.3-3ubuntu2 is to be installed
 libreoffice-common : Breaks: libreoffice-core (< 1:3.4~) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
 python-uno : Depends: libreoffice-core (= 1:3.4.3-3ubuntu2) but 1:3.3.3-1ubuntu2 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

--------------------------------------------------

---

### Post by TeoBigusGeekus on 2011-10-23
> **jakelong00 said:**
> 
E: Unmet dependencies. Try 'apt-get -f install' with [COLOR="Red"]_**no**_[/COLOR] packages
No packages.

---

### Post by jakelong00 on 2011-10-23
thnx for the help man.
it worked this time.
you rock

---

### Post by TeoBigusGeekus on 2011-10-23
You're welcome mate.
Don't forget to mark the thread as solved.

---

