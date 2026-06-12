---
title: "desktop vanished"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by okkie on 2008-11-17
i just received updates for 8.10 ,installed them and desktop vanished leaving only background.reboot does'nt help and only way to talk to computer seems to be command line at startup.can only get to e-mail from keyboard.
any help appreciated

---

### Post by hayden92 on 2008-11-17
Have you unistalled any programs lately? Such as Evolution... or have you changed any:
'System -> Preferences -> Sessions' options?

Please be more specific if you want any decent help

---

### Post by fooman on 2008-11-17
do you mean that you have only your desktop wallpaper,  and no top or bottom panels?

if so,  try pressing alt-f2 and see if the run dialog box pops up.

if it does,  type the following into it and press enter:

```
gnome-panel &
```

edited alt-f2

---

### Post by mapes12 on 2008-11-17
```
apt get install ubuntu-desktop
```

May help.

Next time backup your system files before updating or making any changes to your system: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

This will safe you loads of grief.

---

### Post by jenkinbr on 2008-11-17
> **fooman said:**
> do you mean that you have only your desktop wallpaper,  and no top or bottom panels?

if so,  try pressing alt-f1 and see if the run dialog box pops up.

if it does,  type the following into it and press enter:

```
gnome-panel &
```
Ummm, that would be alt+f2, not alt+f1

Alt+f1 should bring up the main menu.

---

### Post by fooman on 2008-11-17
> **jenkinbr said:**
> Ummm, that would be alt+f2, not alt+f1

Alt+f1 should bring up the main menu.

oopsie...thanks

corrected.

---

### Post by okkie on 2008-11-19
thanks to everybody for your advice.I will now run gnome-panel & from srartup as alt+ nothing works. will also try apt get install ubuntu-desktop and keep you posted.

---

### Post by okkie on 2008-11-19
sudo apt-get install gnome-panel from fail safe option at startup solved the problem and also unveiled original cause from sound and video how-to
see attached

---

### Post by okkie on 2008-11-19
here attachment to my previous post.This problem is solved. thanks everybody for your time.

---

