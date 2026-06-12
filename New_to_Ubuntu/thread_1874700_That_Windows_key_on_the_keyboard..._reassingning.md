---
title: "That Windows key on the keyboard... reassingning ?"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by Innernet on 2011-11-03
Hi
Is it possible to make that useless key to behave the same as left click from my Compaq CQ60 laptop touchpad ?  I use no external mouse.

---

### Post by Script Warlock on 2011-11-03
system settings> keyboard> shortcuts.. and reassign that key but in ubuntu 11.10 pressing this key brings out the dash

---

### Post by Majorix on 2011-11-03
First make sure that your Ubuntu setup doesn't use it already. Some distros, some DEs and some window managers use it actively.

---

### Post by Innernet on 2011-11-03
Thanks gentlemen.

Cannot find a proper 'line' to follow the instructions within the System-> Preferences -> Keyboard shortcuts.   
I find choices in there for 'Sound', 'Desktop', 'Accessiblility', 'Window management', but just graduated of idiot and cannot discern where to implement the reassigning :confused: to make the 'Windows' key work as left click.
Am running 10.10 if it is relevant.

---

### Post by Script Warlock on 2011-11-04
i made mine as F1 by typing -- gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"

---

### Post by alco75 on 2011-11-04
The Keyboard -> Application Shortcuts manager **xfce4-keyboard-settings** in Xubuntu is excellent, much more usable than I remember it being to set up keyboard shortcuts in Natty under GNOME.

I have a bunch of <Super> shortcuts that make use of the Windows key:

```
<Super>b - browser
<Super>f - App Finder
<Super>s - Settings Manager
<Super>t - Terminal

```

Love Xubuntu, me. \\:D/

---

