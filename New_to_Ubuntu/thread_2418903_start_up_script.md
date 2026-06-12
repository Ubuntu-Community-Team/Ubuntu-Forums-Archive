---
title: "start up script"
date: 2019-05-13
forum: New to Ubuntu
---

### Post by icegood on 2019-05-13
Hi. I want to disable caps lock once and forever and i added given script to both /etc/profile and ~/.profile:

xmodmap -e "keycode 66 = Shift_L NoSymbol Shift_L"

However it doesn't work. What the proper place for a given script?

---

### Post by him610 on 2019-05-13
Comments deleted because they did not contribute to discussion.

---

### Post by cruzer001 on 2019-05-13
Have you tried ~/.Xmodmap

[https://wiki.archlinux.org/index.php/xmodmap#Turn_CapsLock_into_Control](https://wiki.archlinux.org/index.php/xmodmap#Turn_CapsLock_into_Control)

---

### Post by icegood on 2019-05-14
~/.Xmodmap with text inside 
> keycode 66 = Shift_L NoSymbol Shift_L

doesn't work as well. Neither .xsessionrc/.xsession/.Xsession with text 
> 
xmodmap -e "keycode 66 = Shift_L NoSymbol Shift_L"


---

### Post by icegood on 2019-05-14
tried setxkbmap -option caps:none as well

---

### Post by again? on 2019-05-14
Are you using Kubuntu as your distro info indicates?

---

### Post by icegood on 2019-05-15
No, unubtu 16.04 LTS. I will change setting here

---

### Post by again? on 2019-05-16
In ubuntu 16.04 you can disable with dconf via terminal....
```
dconf write /org/gnome/desktop/input-sources/xkb-options "['caps:none']"
```
To set back to default...
```
dconf reset /org/gnome/desktop/input-sources/xkb-options
```

You can find other xkb-options for the capslock key towards the end of the following file.
Open in gedit...
```
gedit /usr/share/X11/xkb/rules/base.lst
```

From memory you can also use the GUI, "gnome-tweak-tool" but be aware it may pull in gnome-shell as a dependency.
You appear to already be using gnome-shell though.

---

