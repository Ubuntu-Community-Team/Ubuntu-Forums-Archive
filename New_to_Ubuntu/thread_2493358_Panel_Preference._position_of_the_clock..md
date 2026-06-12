---
title: "Panel Preference. position of the clock."
date: 2023-12-12
forum: New to Ubuntu
---

### Post by nivek2046 on 2023-12-12
Hi I am running Ubuntu 22.04 LTS jammy on orange pi 5 (arm64).

In panel preference, i selected horizontal panel, to make it looks more than windows.

How do I place the clock on the right hand side or right-justified?

thanks..

---

### Post by MAFoElffen on 2023-12-12
How it looks is controlled by the gnome-session.css, right under the line: "/* (((((((((((Date/Time Menu )))))))))*/"

Unfortunately, it's not really documented. And this file varies on where the active copy of that is within your user directory, based on what theme is active. 

For example:
```

mafoelffen@Mikes-ThinkPad-T520:~$ find $HOME/.themes -name gnome-shell.css
/home/mafoelffen/.themes/Prof-Gnome-Dark-3.6/gnome-shell/gnome-shell.css
/home/mafoelffen/.themes/Prof-Gnome-Light-3.6/gnome-shell/gnome-shell.css
/home/mafoelffen/.themes/Prof-Gnome-Darker-3.6/gnome-shell/gnome-shell.css
/home/mafoelffen/.themes/Prof-Gnome-Light-DS-3.6/gnome-shell/gnome-shell.css
/home/mafoelffen/.themes/Yaru-dark/gnome-shell/gnome-shell.css

```
There is also this Gnome extension: [https://extensions.gnome.org/extension/2/move-clock/](https://extensions.gnome.org/extension/2/move-clock/)

---

### Post by pantazi on 2023-12-14
Using Gnome extensions manager you could install Dash to Panel. There are options in the panel settings.

---

